---
title: Sviluppo proxy risorse
description: 'Un proxy è un''istanza AEM che utilizza i proxy worker per elaborare i processi. Scoprite come configurare un AEM proxy, le operazioni supportate, i componenti proxy e come sviluppare un lavoratore proxy personalizzato. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0560d47dcffbf9b74a36ea00e118f8a176adafcd
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# Sviluppo proxy risorse {#assets-proxy-development}

Adobe Experience Manager (AEM) Assets utilizza un proxy per distribuire l&#39;elaborazione per determinate attività.

Un proxy è un&#39;istanza AEM specifica (e a volte separata) che utilizza i proxy worker come processori responsabili della gestione di un processo e della creazione di un risultato. Un lavoratore proxy può essere utilizzato per un&#39;ampia gamma di attività. Nel caso di un proxy AEM Assets  può essere utilizzato per caricare le risorse per il rendering all&#39;interno  AEM Assets. Ad esempio, il lavoratore proxy [IDS](indesign.md) utilizza un InDesign Server  per elaborare i file da utilizzare in  AEM Assets.

Se il proxy è un’istanza AEM separata, questo consente di ridurre il carico sulle istanze di authoring AEM. Per impostazione predefinita,  AEM Assets esegue le attività di elaborazione delle risorse nella stessa JVM (esternalizzata tramite proxy) per ridurre il carico sull’istanza di creazione AEM.

## Proxy (accesso HTTP) {#proxy-http-access}

Un proxy è disponibile tramite il servlet HTTP quando è configurato per accettare processi di elaborazione in: `/libs/dam/cloud/proxy`. Questo servlet crea un processo di sling dai parametri inseriti. Questo viene aggiunto alla coda di processo del proxy e collegato al lavoratore proxy appropriato.

### Operazioni supportate {#supported-operations}

* `job`

   **Requisiti**: il parametro  `jobevent` deve essere impostato come una mappa di valore serializzata. Viene utilizzato per creare un `Event` per un processore di processo.

   **Risultato**: Aggiunge un nuovo processo. In caso di esito positivo, viene restituito un ID di processo univoco.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Requisiti**: il parametro  `jobid` deve essere impostato.

   **Risultato**: Restituisce una rappresentazione JSON del nodo risultato creato dal processore del processo.

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

   **Risultati**: Rimuove un processo se viene trovato.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Proxy Worker {#proxy-worker}

Un lavoratore proxy è un processore responsabile della gestione di un processo e della creazione di un risultato. I lavoratori risiedono nell&#39;istanza proxy e devono implementare [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) per essere riconosciuti come proxy.

>[!NOTE]
>
>Il lavoratore deve implementare [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) per essere riconosciuto come lavoratore proxy.

### API client {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html) è disponibile come servizio OSGi che fornisce metodi per creare processi, rimuovere processi e ottenere risultati da tali processi. L&#39;implementazione predefinita di questo servizio (`JobServiceImpl`) utilizza il client HTTP per comunicare con il servlet proxy remoto.

Esempio di utilizzo delle API:

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
>La documentazione di riferimento per l&#39;API proxy è disponibile in [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html).

Sia le configurazioni di proxy che quelle di proxy sono disponibili tramite configurazioni di servizi cloud accessibili dalla console  AEM Assets **Tools** o in `/etc/cloudservices/proxy`. Ogni lavoratore proxy deve aggiungere un nodo in `/etc/cloudservices/proxy` per i dettagli di configurazione specifici del lavoratore (ad esempio, `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Per ulteriori informazioni, vedere [Configurazione del Proxy Worker di Indesign Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) e [configurazione dei Cloud Services](../sites-developing/extending-cloud-config.md).

Esempio di utilizzo delle API:

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

### Sviluppo di un Proxy Worker personalizzato {#developing-a-customized-proxy-worker}

Il lavoratore proxy [IDS](indesign.md) è un esempio di un lavoratore proxy AEM Assets  già fornito out-of-the-box per esternalizzare l&#39;elaborazione delle risorse Indesign.

È inoltre possibile sviluppare e configurare un proprio  AEM Assets proxy Worker per creare un lavoratore specializzato per l&#39;invio e l&#39;outsourcing  attività di elaborazione AEM Assets.

Per impostare un lavoratore proxy personalizzato è necessario:

* Configurare e implementare (utilizzando Sling eventing):

   * un argomento del processo personalizzato
   * un gestore eventi di processo personalizzato

* Quindi utilizzate l&#39;API JobService per:

   * invio del processo personalizzato al proxy
   * gestire il lavoro

* Se desiderate utilizzare il proxy da un flusso di lavoro, dovete implementare un passaggio esterno personalizzato utilizzando l&#39;API WorkflowExternalProcess e l&#39;API JobService.

Nel diagramma seguente e nei passaggi viene descritto come procedere:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>Nei passaggi seguenti, gli equivalenti di Indesign sono indicati come esempi di riferimento.

1. Viene utilizzato un [processo Sling](https://sling.apache.org/site/eventing-and-jobs.html), pertanto è necessario definire un argomento del processo per il caso d&#39;uso.

   Ad esempio, vedere `IDSJob.IDS_EXTENDSCRIPT_JOB` per il lavoratore proxy IDS.

1. Il passaggio esterno viene utilizzato per attivare l’evento e quindi attendere che sia terminato; questo viene fatto tramite un sondaggio sull&#39;ID. Per implementare le nuove funzionalità è necessario sviluppare un proprio passaggio.

   Implementate un `WorkflowExternalProcess`, quindi utilizzate l&#39;API JobService e l&#39;argomento del processo per preparare un evento di processo e inviarlo a JobService (un servizio OSGi).

   Ad esempio, vedere `INDDMediaExtractProcess`.java per il lavoratore proxy IDS.

1. Implementare un gestore di processi per l’argomento. Questo gestore richiede lo sviluppo in modo che esegua l&#39;azione specifica e sia considerato come implementazione del lavoratore.

   Ad esempio, vedere `IDSJobProcessor.java` per il lavoratore proxy IDS.

1. Utilizzare `ProxyUtil.java` in dam-commons. Questo consente di inviare i processi ai lavoratori utilizzando il proxy DAM.

>[!NOTE]
>
>Ciò che il framework proxy AEM Assets  non fornisce è il meccanismo del pool.
>
>L&#39;integrazione  InDesign consente l&#39;accesso a un pool di server indesign (IDSPool). Questo pool è specifico per l&#39;integrazione Indesign e non fa parte del framework proxy AEM Assets .

>[!NOTE]
>
>Sincronizzazione dei risultati:
>
>In caso di n istanze che utilizzano lo stesso proxy, il risultato dell&#39;elaborazione rimane con il proxy. È compito del client (AEM Author) richiedere il risultato utilizzando lo stesso ID processo univoco fornito al client al momento della creazione del processo. Il proxy ottiene semplicemente il lavoro e mantiene il risultato pronto per essere richiesto.
