---
title: Sviluppo proxy risorse
description: 'Un proxy è un proxy  [!DNL Experience Manager] instance that uses proxy workers to process jobs. Learn how to configure an [!DNL Experience Manager] proxy, operazioni supportate, componenti proxy e come sviluppare un proxy worker personalizzato. '
contentOwner: AG
feature: Asset Processing
role: Admin, Architect
exl-id: c7511326-697e-4749-ab46-513cdbaa00d8
source-git-commit: a778c3bbd0e15bb7b6de2d673b4553a7bd146143
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# Sviluppo proxy risorse {#assets-proxy-development}

Adobe Experience Manager Assets utilizza un proxy per distribuire l’elaborazione per determinate attività.

Un proxy è un&#39;istanza [!DNL Experience Manager] specifica (e a volte separata) che utilizza i processi di lavoro proxy come processori responsabili della gestione di un lavoro e della creazione di un risultato. Un proxy worker può essere utilizzato per un&#39;ampia varietà di attività. Nel caso di un proxy di [!DNL Experience Manager] risorse , può essere utilizzato per caricare le risorse per il rendering all’interno di [!DNL Experience Manager] risorse. Ad esempio, il proxy worker [IDS](indesign.md) utilizza un InDesign Server per elaborare i file da utilizzare in [!DNL Experience Manager] Assets.

Quando il proxy è un&#39;istanza [!DNL Experience Manager] separata, questo aiuta a ridurre il carico sulle [!DNL Experience Manager] istanze di authoring. Per impostazione predefinita, [!DNL Experience Manager] Assets esegue le attività di elaborazione delle risorse nella stessa JVM (esternalizzata tramite Proxy) per ridurre il carico sull’ [!DNL Experience Manager] istanza di authoring.

## Proxy (accesso HTTP) {#proxy-http-access}

Un proxy è disponibile tramite il servlet HTTP quando è configurato per accettare processi di elaborazione in: `/libs/dam/cloud/proxy`. Questo servlet crea un lavoro sling dai parametri inviati. Questo viene quindi aggiunto alla coda del processo proxy e collegato al processo di lavoro proxy appropriato.

### Operazioni supportate {#supported-operations}

* `job`

   **Requisiti**: il parametro  `jobevent` deve essere impostato come mappa del valore serializzato. Viene utilizzato per creare un `Event` per un processore di processo.

   **Risultato**: Aggiunge un nuovo processo. In caso di esito positivo, viene restituito un ID processo univoco.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Requisiti**: il parametro  `jobid` deve essere impostato.

   **Risultato**: Restituisce una rappresentazione JSON del Nodo risultato creato dal processore del processo.

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **Requisiti**: il parametro jobid deve essere impostato.

   **Risultato**: Restituisce una risorsa associata al processo specificato.

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **Requisiti**: il parametro jobid deve essere impostato.

   **Risultati**: Rimuove un processo se trovato.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Proxy Worker {#proxy-worker}

Un proxy worker è un processore responsabile della gestione di un processo e della creazione di un risultato. I lavoratori risiedono nell&#39;istanza proxy e devono implementare [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) per essere riconosciuti come proxy worker.

>[!NOTE]
>
>Il processo di lavoro deve implementare [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) per essere riconosciuto come proxy worker.

### API client {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) è disponibile come servizio OSGi che fornisce metodi per creare lavori, rimuovere lavori e ottenere risultati da tali processi. L&#39;implementazione predefinita di questo servizio (`JobServiceImpl`) utilizza il client HTTP per comunicare con il servlet proxy remoto.

Di seguito è riportato un esempio di utilizzo API:

```java
@Reference
 JobService proxyJobService;

 // to create a new job
 final Hashtable props = new Hashtable();
 props.put("someproperty", "some value");
 props.put(JobUtil.PROPERTY_JOB_TOPIC, "myworker/job"); // this is an identifier of the worker
 final String jobId = proxyJobService.addJob(props, new Asset[]{asset});

 // to check status (returns JobService.STATUS_FINISHED or JobService.STATUS_INPROGRESS)
 int status = proxyJobService.getStatus(jobId)

 // to get the result
 final String jsonString = proxyJobService.getResult(jobId);

 // to remove job and cleanup
 proxyJobService.removeJob(jobId);
```

### Configurazioni Cloud Service {#cloud-service-configurations}

>[!NOTE]
>
>La documentazione di riferimento per l&#39;API proxy è disponibile in [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/commons/proxy/package-summary.html).

Le configurazioni del proxy e del proxy worker sono disponibili tramite configurazioni di servizi cloud accessibili dalla console [!DNL Experience Manager] Risorse **Strumenti** o in `/etc/cloudservices/proxy`. Ogni proxy worker deve aggiungere un nodo in `/etc/cloudservices/proxy` per i dettagli di configurazione specifici del processo di lavoro (ad esempio, `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Per ulteriori informazioni, vedere [Configurazione del proxy worker di Indesign Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) e [Configurazione dei Cloud Services](../sites-developing/extending-cloud-config.md).

Di seguito è riportato un esempio di utilizzo API:

```java
@Reference(policy = ReferencePolicy.STATIC)
 ProxyConfig proxyConfig;
 
 // to get proxy config
 Configuration cloudConfig = proxyConfig.getConfiguration();
 final String value = cloudConfig.get("someProperty", "defaultValue");

 // to get worker config
 Configuration cloudConfig = proxyConfig.getConfiguration("workername");
 final String value = cloudConfig.get("someProperty", "defaultValue");
```

### Sviluppo di un proxy worker personalizzato {#developing-a-customized-proxy-worker}

Il [proxy worker IDS](indesign.md) è un esempio di un processo di lavoro proxy [!DNL Experience Manager] Assets già fornito come predefinito per esternalizzare l’elaborazione delle risorse di Indesign.

Puoi anche sviluppare e configurare il tuo [!DNL Experience Manager] lavoratore proxy Assets per creare un processo di lavoro specializzato per inviare ed esternalizzare le tue [!DNL Experience Manager] attività di elaborazione Assets.

Per configurare un processo di lavoro proxy personalizzato è necessario:

* Configurazione e implementazione (utilizzando l’evento Sling):

   * un argomento di lavoro personalizzato
   * un gestore di eventi di lavoro personalizzato

* Quindi utilizza l’API JobService per:

   * invia il processo personalizzato al proxy
   * gestire il proprio lavoro

* Se desideri utilizzare il proxy da un flusso di lavoro, devi implementare un passaggio esterno personalizzato utilizzando l’API WorkflowExternalProcess e l’API JobService.

Il diagramma seguente e i passaggi descrivono come procedere:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>Nei passaggi seguenti, gli equivalenti di Indesign sono indicati come esempi di riferimento.

1. Viene utilizzato un [processo Sling](https://sling.apache.org/site/eventing-and-jobs.html), quindi devi definire un argomento di lavoro per il tuo caso d’uso.

   Ad esempio, vedi `IDSJob.IDS_EXTENDSCRIPT_JOB` per il proxy worker IDS.

1. Il passaggio esterno viene utilizzato per attivare l’evento e quindi attendere fino al termine; questo viene fatto tramite sondaggi sull&#39;id. Devi sviluppare un tuo passaggio per implementare nuove funzionalità.

   Implementa un `WorkflowExternalProcess`, quindi utilizza l&#39;API JobService e l&#39;argomento del tuo lavoro per preparare un evento di lavoro e inviarlo al JobService (un servizio OSGi).

   Ad esempio, vedi `INDDMediaExtractProcess`.java per il processo di lavoro proxy IDS.

1. Implementa un gestore di processi per l’argomento. Questo gestore richiede lo sviluppo in modo che esegua l&#39;azione specifica ed è considerato l&#39;implementazione del processo di lavoro.

   Ad esempio, vedi `IDSJobProcessor.java` per il proxy worker IDS.

1. Utilizza `ProxyUtil.java` in dam-commons. Questo consente di inviare i lavori ai lavoratori utilizzando il proxy dam.

>[!NOTE]
>
>Il meccanismo pool non è disponibile nel framework proxy di [!DNL Experience Manager] Assets.
>
>L’integrazione di InDesign consente l’accesso a un pool di server indesign (IDSPool). Questo pool è specifico per l’integrazione di Indesign e non fa parte del framework proxy [!DNL Experience Manager] Assets.

>[!NOTE]
>
>Sincronizzazione dei risultati:
>
>Con n istanze che utilizzano lo stesso proxy, il risultato dell&#39;elaborazione rimane con il proxy. È compito del client ([!DNL Experience Manager] Autore) richiedere il risultato utilizzando lo stesso ID di processo univoco assegnato al client al momento della creazione del processo. Il proxy ottiene semplicemente il lavoro svolto e mantiene il risultato pronto per essere richiesto.
