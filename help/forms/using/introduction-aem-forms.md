---
title: Introduzione ad AEM Forms
seo-title: Introduction to AEM Forms
description: Con Adobe Experience Manager Forms, gli utenti aziendali possono integrare moduli coinvolgenti, reattivi e adattivi nei siti web e mobili, semplificando il processo di iscrizione digitale e aumentando i tassi di conversione dei clienti.
seo-description: With Adobe Experience Manager Forms, business users can integrate engaging, responsive, and adaptive forms into web and mobile sites, simplifying the digital enrollment process and increasing customer conversion rates.
uuid: 9e9a164a-4a74-4096-98b8-800ea610edd8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: a976a854-4bf2-49f8-871e-28bc597ac496
feature: Adaptive Forms
exl-id: 0a79111d-e42f-4eb6-8bc4-ab97424e7f90
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 10%

---

# Introduzione ad AEM Forms {#introduction-to-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per informazioni sulle funzioni e sui miglioramenti più recenti in AEM Forms, vedi [Novità di AEM Forms](/help/forms/using/whats-new.md).

## Informazioni su AEM Forms {#about-aem-forms}

Adobe Experience Manager (AEM) offre una soluzione facile da usare per creare, gestire, pubblicare e aggiornare moduli digitali complessi, da integrare con processi di back-end, regole aziendali e dati.

AEM Forms combina l’authoring, la gestione e la pubblicazione dei moduli con funzionalità di gestione della corrispondenza, sicurezza dei documenti e analisi integrate per creare esperienze end-to-end coinvolgenti. Progettato per funzionare su canali web e mobili, AEM Forms può essere integrato in modo efficiente nei processi aziendali, riducendo i processi e gli errori cartacei e migliorando al contempo l&#39;efficienza.

AEM Forms sfrutta ed estende le funzionalità degli investimenti esistenti nei moduli XFA e nella soluzione di LiveCycle Adobe.

Nelle grandi aziende, i moduli sono spesso creati una volta sola, per poi essere riutilizzati copiandoli in un sistema di gestione dei contenuti. Mantenere aggiornato un ampio database di moduli e renderlo individuabile può essere una sfida notevole. AEM fornisce un Forms Portal personalizzabile che consente ai clienti di trovare e accedere ai moduli necessari sia sui canali web che mobile.

AEM Forms fornisce strumenti di gestione dei moduli che consentono non solo di gestire i moduli adattivi, ma anche moduli XFA, PDF forms e risorse correlate. Per ulteriori informazioni, consulta [Introduzione alla gestione dei moduli](/help/forms/using/introduction-managing-forms.md).

![](do-not-localize/4th-draft.gif)

### Funzionalità principali {#key-capabilities}

In sintesi, AEM Forms offre potenti funzioni di gestione dei moduli, come le seguenti, che riducono i processi manuali e aumentano la soddisfazione del cliente.

* Un portale Forms centralizzato per la progettazione e la distribuzione di moduli dinamici, inclusi PDF, HTML5 e moduli adattivi
* Interfaccia grafica di facile utilizzo per consentire agli utenti aziendali di importare, gestire, visualizzare in anteprima e pubblicare facilmente i moduli
* Una directory di moduli reattivi con potenti funzioni di ricerca utilizzando parole chiave, tag e metadati
* Rilevamento dinamico del dispositivo e della posizione di un utente per eseguire il rendering del modulo in modo appropriato su canali web e mobili
* Integrazione con Adobe Analytics per misurare in modo efficace le metriche di utilizzo dei moduli
* Integrazione con i servizi eSign di Adobe Document Cloud o Scribble per la firma elettronica di documenti contenenti informazioni riservate
* Funzionalità automatizzate di pubblicazione dei moduli e capacità di fornire comunicazioni tempestive, personalizzate e coerenti tramite più canali

## Tipi di moduli AEM {#aem-form-types}

AEM Forms consente di estendere moduli nuovi ed esistenti per creare:

* HTML e PDF forms impaginati e perfetti in pixel, quasi come carta, oppure
* moduli adattivi per il rendering automatico del dispositivo e del browser di un utente.

**PDF forms**

È possibile compilare i PDF forms offline, salvarli localmente e inviare i dati del modulo una volta online. È possibile utilizzare codici a barre 2D per acquisire i dati dei moduli e firme digitali per convalidare l’autenticità degli utenti.

**Moduli HTML**

I moduli basati su browser HTML5 possono essere visualizzati sia sui dispositivi mobili che sui browser desktop. È possibile firmare elettronicamente i moduli di HTML utilizzando i servizi Scribble o eSign.

**Moduli adattivi**

I moduli adattivi possono adattarsi in modo dinamico alle risposte degli utenti aggiungendo o rimuovendo campi o sezioni in base alle esigenze. AEM consente di riutilizzare modelli di moduli XML di Adobe per creare moduli adattivi.

### Funzioni supportate {#supported-features}

Tutti i tipi di modulo supportano le seguenti funzioni:

* Layout dinamico
* Convalida del campo del modulo
* Guida sensibile al contesto
* Scripting e gestione dei dati XML
* Progettazione e controllo dell’accessibilità
* Possibilità di salvare i moduli sul lato server
* Supporto per gli allegati di file
* Integrazione con HTML Workspace per l’acquisizione dei dati

## Raccolta dati offline {#offline-data-collection-br}

Una volta inviati i dati del modulo, Adobe Experience Manager collega i dati del modulo con i sistemi esistenti, le regole aziendali e le persone richieste.

AEM Forms fornisce Forms Workspace, un’app mobile che estende i processi aziendali digitali ai dispositivi mobili. Utilizzando Forms Workspace, puoi raccogliere e registrare dati anche offline. Forms Workspace sfrutta le funzionalità del tuo dispositivo mobile e ti consente di acquisire foto, video e raccogliere dati come marche temporali e altre informazioni. La prossima volta che ti connetti a una rete, puoi sincronizzare i dati raccolti.

L’acquisizione dei dati offline e la successiva sincronizzazione dei dati online sono particolarmente utili per le persone sul campo. Migliora la produttività e riduce gli errori.

**Vantaggi dell’utilizzo di Forms Workspace per la raccolta dati offline**

* Applicazione workspace HTML facile da usare per l&#39;assegnazione e il tracciamento delle attività
* Ambiente di progettazione del flusso di lavoro con trascinamento della selezione
* Connettori per la gestione dei contenuti aziendali (ECM)
* Supporto di standard aperti, inclusi XML e SOAP, per la connessione dei dati dei moduli con i sistemi aziendali
* I rapporti predefiniti di HTML controllano i backlog, le code di lavoro e gli indicatori prestazioni chiave (KPI, Key Performance Indicators)
* Dashboard personalizzabili per informazioni in tempo reale sulle operazioni aziendali
* API per la connessione con strumenti di reporting di terze parti

![](do-not-localize/3rd-draft.gif)

## Comunicazione personalizzata {#personalized-communication}

Un componente importante di un’esperienza digitale self-service efficiente è la comunicazione tempestiva e personalizzata di informazioni a cui gli utenti possono accedere da qualsiasi luogo e su qualsiasi dispositivo. Le comunicazioni personalizzate e tempestive possono migliorare sia i tassi di conversione che la soddisfazione degli utenti.

Utilizzando AEM Forms, gli utenti aziendali possono creare esperienze utente personalizzate avvincenti personalizzando modelli di documenti, incorporando informazioni provenienti dai processi back-end e componenti interattivi inclusi. Un’interfaccia utente intuitiva consente agli utenti non tecnici di sviluppare regole aziendali che decidono quando generare una comunicazione basata su un’interrogazione o avviare una risposta generata dall’utente.

I documenti personalizzati, come le ricevute, i kit di benvenuto e le istruzioni, possono essere facilmente consegnati su più canali. Le organizzazioni possono indirizzare il traffico verso portali web personalizzati, con conseguente registrazione o acquisto di servizi aggiuntivi.

**Funzioni principali**

* Ambiente di authoring per corrispondenza con supporto di modelli, blocchi di contenuto, regole business e altro ancora
* Conversione e assemblaggio dei documenti
* Supporto per la consegna di documenti on-demand o batch tramite più canali, inclusi web, e-mail e carta
* Audit trail con cronologia delle modifiche
* Supporto delle firme digitali per convalidare l’integrità dei contenuti e l’identità del firmatario
* Componente aggiuntivo per la sicurezza dei documenti per AEM Forms, inclusi crittografia, criteri di utilizzo, tracciamento e controllo

![](do-not-localize/layout-02.png)
**Figura:** *Workflow di comunicazione personalizzato semplificato*
