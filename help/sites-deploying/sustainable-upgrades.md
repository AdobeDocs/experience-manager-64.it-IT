---
title: Aggiornamenti sostenibili
seo-title: Sustainable Upgrades
description: Scopri gli aggiornamenti sostenibili in AEM 6.4.
seo-description: Learn about sustainable upgrades in AEM 6.4.
uuid: 59d64af5-6ee0-40c8-b24a-c06848f70daa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 5ca8dd7a-4efd-493e-8022-d2f10903b0a2
feature: Upgrading
exl-id: 765efa8d-1548-4db3-ba87-baa02075eaf6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 1%

---

# Aggiornamenti sostenibili{#sustainable-upgrades}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Framework di personalizzazione {#customization-framework}

### Architettura (funzionale/infrastruttura/contenuto/applicazione)  {#architecture-functional-infrastructure-content-application}

La funzione di Customization Framework è progettata per contribuire a ridurre le violazioni nelle aree non estensibili del codice (come APIS) o del contenuto (come le sovrapposizioni) che non sono compatibili con l’aggiornamento.

Sono disponibili due componenti del framework di personalizzazione: la **Superficie API** e **Classificazione dei contenuti**.

#### Superficie API {#api-surface}

Nelle versioni precedenti di AEM molte API sono state esposte tramite il Jar Uber. Alcune di queste API non erano destinate ai clienti, ma erano esposte al supporto della funzionalità AEM tra i bundle. In futuro, le API Java saranno contrassegnate come pubbliche o private per indicare ai clienti quali API possono essere utilizzate in modo sicuro nel contesto degli aggiornamenti. Altre specifiche includono:

* API Java contrassegnate come `Public` può essere utilizzato e a cui fanno riferimento i bundle di implementazione personalizzati.

* Le API pubbliche saranno compatibili con l’installazione di un pacchetto di compatibilità.
* Il pacchetto di compatibilità conterrà un file JAR Uber compatibile per garantire la compatibilità con le versioni precedenti
* API Java contrassegnate come `Private` sono destinati ad essere utilizzati solo AEM bundle interni e non devono essere utilizzati da bundle personalizzati.

>[!NOTE]
>
>Il concetto di `Private` e `Public` in questo contesto non va confuso con le nozioni Java di classi pubbliche e private.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Classificazioni di contenuto {#content-classifications}

AEM utilizza da tempo l’entità principale delle sovrapposizioni e di Sling Resource Merger per consentire ai clienti di estendere e personalizzare AEM funzionalità. Le funzionalità predefinite per l’attivazione delle console AEM e dell’interfaccia utente sono memorizzate in **/libs**. I clienti non devono mai modificare nulla sotto di esso **/libs** ma potrebbe aggiungere ulteriore contenuto sotto **/apps** per sovrapporre ed estendere la funzionalità definita in **/libs** Per ulteriori informazioni, consulta Sviluppo con sovrapposizioni . Ciò causava ancora numerosi problemi durante l&#39;aggiornamento AEM come contenuto in **/libs** potrebbe cambiare causando la rottura della funzionalità di sovrapposizione in modo imprevisto. I clienti possono anche estendere AEM componenti tramite ereditarietà tramite `sling:resourceSuperType`oppure fai semplicemente riferimento a un componente in **/libs** direttamente tramite sling:resourceType. Problemi simili possono verificarsi con casi di utilizzo di riferimento e di sostituzione.

Per rendere più sicuro e facile per i clienti capire quali aree **/libs** sono sicuri di utilizzare e sovrapporre il contenuto in **/libs** è stato classificato con le seguenti miscele:

* **Public (granite:PublicArea)** - Definisce un nodo come pubblico in modo che possa essere sovrapposto, ereditato ( `sling:resourceSuperType`) o utilizzati direttamente ( `sling:resourceType`). I nodi sotto /libs contrassegnati come pubblici saranno sicuri da aggiornare con l’aggiunta di un pacchetto di compatibilità. In generale, i clienti devono sfruttare solo i nodi contrassegnati come pubblici.

* **Abstract (granite:AbstractArea)** - Definisce un nodo come astratto. I nodi possono essere sovrapposti o ereditati ( `sling:resourceSupertype`) ma non deve essere utilizzato direttamente ( `sling:resourceType`).

* **Finale (granite:FinalArea)** - Definisce un nodo come finale. I nodi classificati come finali non possono essere sovrapposti o ereditati. I nodi finali possono essere utilizzati direttamente tramite `sling:resourceType`. I sottonodi sotto il nodo finale sono considerati interni per impostazione predefinita

* **Interno (granite:InternalArea)** - Definisce un nodo come interno. I nodi classificati come interni non possono essere sovrapposti, ereditati o utilizzati direttamente. Questi nodi sono destinati solo alla funzionalità interna di AEM

* **Nessuna annotazione** - I nodi ereditano la classificazione in base alla gerarchia degli alberi. Il / root è per impostazione predefinita Public. **Anche i nodi con una controllante classificata come interni o finali devono essere trattati come interni.**

>[!NOTE]
>
>Questi criteri vengono applicati solo rispetto ai meccanismi basati sul percorso di ricerca Sling. Altre aree **/libs** come una libreria lato client può essere contrassegnata come `Internal`, ma potrebbe essere ancora utilizzato con l’inclusione clientlib standard. È importante che un cliente continui a rispettare la classificazione interna in questi casi.

#### Indicatori del tipo di contenuto di CRXDE Lite {#crxde-lite-content-type-indicators}

I mixin applicati in CRXDE Lite mostrano nodi di contenuto e alberi contrassegnati come `INTERNAL` come in grigio. Per `FINAL` solo l’icona è disattivata. Anche gli elementi secondari di questi nodi appariranno grigi. La funzionalità Sovrapponi nodo è disabilitata in entrambi i casi.

**Pubblico**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Finale**

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Interno**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Verifica dello stato del contenuto**

AEM 6.4 viene fornito con un controllo dello stato di salute per avvisare i clienti se il contenuto sovrapposto o di riferimento viene utilizzato in modo non coerente con la classificazione del contenuto.

La **Controllo dell’accesso ai contenuti Sling/Granite** è una nuova verifica dello stato che monitora l’archivio per vedere se il codice cliente accede in modo errato ai nodi protetti in AEM.

Questa operazione verrà eseguita **/apps** e in genere il completamento richiede diversi secondi.

Per accedere a questo nuovo controllo di integrità, è necessario effettuare le seguenti operazioni:

1. Dalla schermata iniziale AEM, passa a **Strumenti > Operazioni > Rapporti stato**
1. Fai clic sul pulsante **Controllo dell’accesso ai contenuti Sling/Granite** come mostrato di seguito:

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Una volta completata la scansione, verrà visualizzato un elenco di avvisi che avvisano un utente finale del nodo protetto a cui viene fatto riferimento in modo improprio:

![screenshot-2018-2-5health-reports](assets/screenshot-2018-2-5healthreports.png)

Dopo aver riparato le violazioni, tornerà allo stato verde:

![screenshot-2018-2-5health-reports-rules](assets/screenshot-2018-2-5healthreports-violations.png)

Il controllo dello stato di salute visualizza le informazioni raccolte da un servizio in background che controlla in modo asincrono ogni volta che una sovrapposizione o un tipo di risorsa viene utilizzato in tutti i percorsi di ricerca Sling. Se i mixin di contenuto vengono utilizzati in modo errato, segnala una violazione.
