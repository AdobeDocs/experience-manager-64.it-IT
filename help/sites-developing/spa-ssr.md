---
title: Rendering lato SPA e server
seo-title: SPA and Server-Side Rendering
description: "Rendering lato server e SPA"
seo-description: null
uuid: fbf7d0d1-865d-45d2-aeec-a7e3caf3fcb2
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 30d25772-0df7-468e-bcbd-c6fb2e962662
exl-id: 89e45231-885a-4d35-839b-2b50239503ad
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1807'
ht-degree: 2%

---

# Rendering lato SPA e server{#spa-and-server-side-rendering}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>La funzione Editor per applicazioni a pagina singola (SPA) richiede [AEM 6.4 service pack 2](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html) o più recente.
>
>L’editor di SPA è la soluzione consigliata per i progetti che richiedono SPA rendering lato client basato su framework (ad esempio, React o Angular).

>[!NOTE]
>
>Per utilizzare le funzioni di rendering lato server SPA come descritto in questo documento, è necessario AEM 6.4.5.0 o versioni successive.

## Panoramica {#overview}

Le applicazioni a pagina singola (SPA) possono offrire all’utente esperienze avanzate e dinamiche che reagiscono e si comportano in modo familiare, spesso come le applicazioni native. [Questo si ottiene facendo affidamento sul client per caricare il contenuto in anticipo e poi fare il sollevamento pesante dell&#39;interazione dell&#39;utente di gestione](/help/sites-developing/spa-walkthrough.md#how-does-a-spa-work) riducendo al minimo la quantità di comunicazione necessaria tra client e server, rendendo l&#39;app più reattiva.

Tuttavia, questo può causare tempi di caricamento iniziali più lunghi, soprattutto se il SPA è grande e ricco di contenuti. Per ottimizzare i tempi di caricamento, è possibile eseguire il rendering di alcuni contenuti lato server. L’utilizzo del rendering lato server (SSR) può accelerare il caricamento iniziale della pagina e quindi passare ulteriori rendering al client.

## Quando utilizzare SSR {#when-to-use-ssr}

SSR non è richiesto per tutti i progetti. Anche se AEM supporta completamente JS SSR per SPA, Adobe consiglia di non implementarlo sistematicamente per ogni progetto.

Quando si decide di implementare SSR, è innanzitutto necessario stimare la complessità, lo sforzo e i costi aggiuntivi che l’SSR rappresenta realisticamente per il progetto, inclusa la manutenzione a lungo termine. È opportuno scegliere un’architettura SSR solo quando il valore aggiunto supera chiaramente i costi stimati.

SSR di solito fornisce un certo valore quando c&#39;è un chiaro &quot;sì&quot; a una delle seguenti domande:

* **SEO:** SSR è ancora effettivamente necessario per il tuo sito per essere indicizzato correttamente dai motori di ricerca che portano traffico? Tieni presente che i principali crawler del motore di ricerca ora valutano JS.
* **Velocità pagina:** L’SSR fornisce un miglioramento della velocità misurabile negli ambienti reali e aggiunge all’esperienza complessiva dell’utente?

Solo quando almeno una di queste due domande riceve risposta con un chiaro &quot;sì&quot; per il progetto, si consiglia di implementare SSR, ad Adobe. Le sezioni seguenti descrivono come eseguire questa operazione utilizzando Adobe I/O Runtime.

## Adobe I/O Runtime {#adobe-io-runtime}

Se sei [convinto che il tuo progetto richieda l’implementazione di SSR](#when-to-use-ssr), la soluzione consigliata di Adobe è l’utilizzo di Adobe I/O Runtime.

Per ulteriori informazioni su Adobe I/O Runtime, consulta

* [https://www.adobe.io/apis/experienceplatform/runtime.html](https://www.adobe.io/apis/experienceplatform/runtime.html) - per una panoramica del servizio
* [https://www.adobe.io/apis/experienceplatform/runtime/docs.html](https://www.adobe.io/apis/experienceplatform/runtime/docs.html) - per la documentazione dettagliata sulla piattaforma

Nelle sezioni seguenti viene illustrato come Adobe I/O Runtime può essere utilizzato per implementare SSR per la tua SPA in due modelli diversi:

* [Flusso di comunicazione AEM](#aem-driven-communication-flow)
* [Flusso di comunicazione guidato da Adobe I/O-Runtime](#adobe-io-driven-communication-flow)

>[!NOTE]
>
>Adobe consiglia un’area di lavoro Adobe I/O Runtime separata per ambiente (stage, prod, test, ecc.). Ciò consente modelli tipici del ciclo di vita dello sviluppo dei sistemi (SDLC) con diverse versioni di una singola applicazione implementate in ambienti diversi. Vedere il documento [CI/CD per applicazioni di Project App Builder](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) per ulteriori informazioni.
>
>Un’area di lavoro separata non è necessaria per istanza (autore, pubblicazione) a meno che non vi siano differenze nell’implementazione di runtime per tipo di istanza.

## Configurazione del modulo di rendering del contenuto remoto {#remote-content-renderer-configuration}

AEM sapere dove è possibile recuperare il contenuto di cui è stato eseguito il rendering in remoto. Indipendentemente dal [quale modello si sceglie di implementare per SSR](#adobe-io-runtime), sarà necessario specificare AEM modalità di accesso a questo servizio di rendering remoto.

Questo avviene tramite il **RemoteContentRenderer - Configuration Factory** Servizio OSGi. Cerca la stringa &quot;RemoteContentRenderer&quot; nella console Configurazione console Web Console in `http://<host>:<port>/system/console/configMgr`.

![](assets/rendererconfig.png)

Per la configurazione sono disponibili i campi seguenti:

* **Pattern di percorso del contenuto** - Espressione regolare per far corrispondere una parte del contenuto, se necessario
* **URL endpoint remoto** - URL dell’endpoint responsabile della generazione del contenuto
   * Utilizzare il protocollo HTTPS protetto se non nella rete locale.
* **Intestazioni di richiesta aggiuntive** - Intestazioni aggiuntive da aggiungere alla richiesta inviata all&#39;endpoint remoto
   * Pattern: `key=value`
* **Timeout richiesta** - Timeout della richiesta host remoto in millisecondi

>[!NOTE]
>
>Indipendentemente da se scegli di implementare il [Flusso di comunicazione AEM](#aem-driven-communication-flow) o [Flusso basato su Adobe I/O Runtime](#adobe-io-driven-communication-flow), è necessario definire una configurazione di rendering del contenuto remoto.
>
>Questa configurazione deve essere definita anche se scegli di [utilizzare un server Node.js personalizzato](#using-node-js).

>[!NOTE]
>
>Questa configurazione sfrutta la [Renderer di contenuti remoti](#remote-content-renderer), che dispone di ulteriori opzioni di estensione e personalizzazione.

## Flusso di comunicazione AEM {#aem-driven-communication-flow}

Quando utilizzi SSR, la [flusso di lavoro di interazione dei componenti](/help/sites-developing/spa-overview.md#workflow) di SPA in AEM include una fase in cui il contenuto iniziale dell’app viene generato da Adobe I/O Runtime.

1. Il browser richiede il contenuto SSR da AEM.
1. AEM il modello pubblicato su Adobe I/O Runtime.
1. Adobe I/O Runtime restituisce il contenuto generato
1. AEM serve il HTML restituito da Adobe I/O Runtime tramite il modello HTL del componente della pagina di back-end.

![server-side-rendering-cms-Drivenaemnode](assets/server-side-rendering-cms-drivenaemnode-adobeio.png)

### Flusso di comunicazione basato su Adobe I/O Runtime {#adobe-io-driven-communication-flow}

La sezione [Flusso di comunicazione AEM](#aem-driven-communication-flow) descrive l’implementazione standard e consigliata del rendering lato server per quanto riguarda SPA in AEM, dove AEM esegue il bootstrap e il serving del contenuto.

In alternativa, SSR può essere implementato in modo che Adobe I/O Runtime sia responsabile del bootstrap, invertendo efficacemente il flusso di comunicazione.

Entrambi i modelli sono validi e supportati da AEM. Tuttavia, è opportuno considerare i vantaggi e gli svantaggi di ciascuno prima di implementare un particolare modello.

| Bootstrap | Vantaggi | Svantaggi |
|---|---|---|
| via AEM | AEM gestisce l’inserimento delle librerie laddove necessario<br>Le risorse devono essere mantenute solo su AEM | Probabilmente non familiare allo sviluppatore SPA |
| tramite Adobe I/O Runtime | Più familiare agli sviluppatori SPA | Le risorse clientlib richieste dall’applicazione, come CSS e JavaScript, dovranno essere rese disponibili dallo sviluppatore AEM tramite il [`allowProxy` property](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)<br>Le risorse devono essere sincronizzate tra AEM e Adobe I/O Runtime<br>Per abilitare l&#39;authoring del SPA, potrebbe essere necessario un server proxy per Adobe I/O Runtime |

## Pianificazione del SSR {#planning-for-ssr}

Generalmente solo una parte di un&#39;applicazione deve essere sottoposta a rendering sul lato server. L’esempio comune è il contenuto che verrà visualizzato sopra la piega al caricamento iniziale della pagina e deve essere rappresentato lato server. Questo consente di risparmiare tempo distribuendo al client contenuti già sottoposti a rendering. Quando l’utente interagisce con il SPA, il client esegue il rendering del contenuto aggiuntivo.

Quando prendi in considerazione l’implementazione del rendering lato server per il tuo SPA, devi verificare quali parti dell’app richiederà SSR.

## Sviluppo di un SPA utilizzando SSR {#developing-an-spa-using-ssr}

È possibile eseguire il rendering dei componenti SPA dal lato client (nel browser) o server. Quando viene eseguito il rendering sul lato server, le proprietà del browser, ad esempio le dimensioni e la posizione della finestra, non sono presenti. Pertanto, SPA componenti dovrebbero essere isomorfi, senza prendere in considerazione dove saranno resi.

Per sfruttare SSR, dovrai distribuire il codice in AEM e su Adobe I/O Runtime, responsabile del rendering lato server. La maggior parte del codice sarà la stessa, ma le attività specifiche del server saranno diverse.

## SSR per SPA in AEM {#ssr-for-spas-in-aem}

SSR per SPA in AEM richiede Adobe I/O Runtime, che è chiamato per il rendering del lato server del contenuto dell’app. All’interno dell’HTL dell’app, viene chiamata una risorsa su Adobe I/O Runtime per eseguire il rendering del contenuto.

Proprio come AEM supporta i framework Angular e React SPA pronti all’uso, anche il rendering lato server è supportato per le app Angular e React. Per ulteriori informazioni, consulta la documentazione NPM per entrambi i framework.

* Reagire: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)
* Angular: [https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component](https://github.com/adobe/aem-sample-we-retail-journal/blob/master/react-app/DEVELOPMENT.md#enabling-the-server-side-rendering-using-the-aem-page-component)

Per un esempio semplicistico, consulta la sezione [App Journal We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal). Esegue il rendering dell&#39;intero lato server dell&#39;applicazione. Anche se questo non è un esempio reale, illustra ciò che è necessario per implementare SSR.

>[!CAUTION]
>La [App Journal We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) è solo a scopo dimostrativo e utilizza pertanto Node.js come esempio semplice invece del Adobe I/O Runtime consigliato. Questo esempio non deve essere utilizzato per alcun lavoro di progetto.

>[!NOTE]
>Qualsiasi progetto AEM deve utilizzare l’[archetipo di progetto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=it), che supporta progetti SPA utilizzando React o Angular e sfrutta l’SDK di SPA.

## Utilizzo di Node.js {#using-node-js}

Adobe I/O Runtime è la soluzione consigliata per l’implementazione di SSR per SPA in AEM.

Per le istanze AEM on-premesis, è anche possibile implementare SSR utilizzando un&#39;istanza Node.js personalizzata nello stesso modo descritto sopra. Anche se supportato da Adobe, non è consigliato.

Node.js non è supportato per le istanze AEM ospitate da Adobe.

>[!NOTE]
>
>Se SSR deve essere implementato tramite Node.js, Adobe consiglia un&#39;istanza Node.js separata per ogni ambiente AEM (autore, pubblicazione, stage, ecc.).

## Renderer di contenuti remoti {#remote-content-renderer}

La [Configurazione del modulo di rendering del contenuto remoto](#remote-content-renderer-configuration) che è necessario utilizzare SSR con il tuo SPA in AEM tocco in un servizio di rendering più generalizzato che può essere esteso e personalizzato per soddisfare le tue esigenze.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` è un servizio OSGi per recuperare il contenuto di cui è stato eseguito il rendering su un server remoto, ad esempio da Adobe I/O. Il contenuto inviato al server remoto si basa sul parametro della richiesta trasmesso.

`RemoteContentRenderingService` può essere inserito dall’inversione della dipendenza in un modello Sling personalizzato o in un servlet quando è necessaria un’ulteriore manipolazione del contenuto.

Questo servizio è utilizzato internamente dal [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

La `RemoteContentRendererRequestHandlerServlet` può essere utilizzato per impostare programmaticamente la configurazione della richiesta. `DefaultRemoteContentRendererRequestHandlerImpl`, l’implementazione predefinita del gestore delle richieste fornita, consente di creare più configurazioni OSGi per mappare una posizione nella struttura del contenuto a un endpoint remoto.

Per aggiungere un gestore di richieste personalizzato, implementa `RemoteContentRendererRequestHandler` interfaccia. Assicurati di impostare il `Constants.SERVICE_RANKING` proprietà del componente a un numero intero superiore a 100, che è la classificazione del `DefaultRemoteContentRendererRequestHandlerImpl`.

```
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Configurare la configurazione OSGi del gestore predefinito {#configure-default-handler}

La configurazione del gestore predefinito deve essere configurata come descritto nella sezione [Configurazione del modulo di rendering del contenuto remoto](#remote-content-renderer-configuration).

Utilizzo del modulo di rendering remoto ### {#usage}

Per ottenere un servlet di recupero e restituire alcuni contenuti che possono essere inseriti nella pagina:

1. Verificare che il server remoto sia accessibile.
1. Aggiungi uno dei seguenti snippet al modello HTL di un componente AEM.
1. Facoltativamente, crea o modifica le configurazioni OSGi.
1. Sfoglia il contenuto del sito

Di solito, il modello HTL di un componente pagina è il destinatario principale di tale funzione.

```
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Requisiti {#requirements}

I servlet sfruttano l’esportatore di modelli Sling per serializzare i dati dei componenti. Per impostazione predefinita, entrambe le `com.adobe.cq.export.json.ContainerExporter` e `com.adobe.cq.export.json.ComponentExporter` sono supportate come schede di rete Sling Model. Se necessario, puoi aggiungere classi alle quali la richiesta deve essere adattata utilizzando il `RemoteContentRendererServlet` e l&#39;attuazione `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`. Le classi aggiuntive devono estendere il `ComponentExporter`.
