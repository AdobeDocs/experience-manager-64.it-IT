---
title: Linee guida per la formazione sui servizi di contenuti avanzati
description: Addestra il servizio AI all’applicazione di tag avanzati alle risorse
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
feature: Tagging,Metadata,Smart Tags
role: User
exl-id: 14241f8d-fd0b-4bcf-b2bb-1d0e52bf7748
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 13%

---

# Linee guida per la formazione sui servizi di contenuti avanzati {#smart-content-service-training-guidelines}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per poter assegnare tag efficaci alle immagini del tuo marchio, il Servizio di contenuti avanzati richiede che le immagini di formazione siano conformi a determinate linee guida.

## Orientamenti per la formazione {#guidelines-for-training}

Per ottenere i migliori risultati, le immagini del set di formazione devono essere conformi alle seguenti linee guida:

**Quantity and size (Quantità e dimensioni)****: almeno 30 immagini per tag**. Almeno 500 pixel sul lato più lungo.

**Coerenza**: Le immagini di un tag devono essere visivamente simili.

Ad esempio, non è consigliabile assegnare a tutte queste immagini il tag *mia festa* (per la formazione) perché non sono visivamente simili.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/coherence.png)

**Copertura**: Dovrebbe esserci una varietà sufficiente nelle immagini nell&#39;addestramento. L&#39;idea è di fornire alcuni esempi, ma ragionevolmente diversi, in modo che [!DNL Experience Manager] impara a concentrarsi sulle cose giuste. Se applichi lo stesso tag a immagini visivamente diverse, includi almeno cinque esempi di ogni tipo.

Ad esempio, per il tag *modello in giù*, includi più immagini di formazione simili all’immagine evidenziata qui sotto per consentire al servizio di identificare immagini simili con maggiore precisione durante l’assegnazione tag.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/coverage_1.png)

**Distrazione/ostruzione**: Il servizio si allena meglio sulle immagini che hanno meno distrazioni (sfondi ben visibili, accompagnamento indipendenti, come oggetti/persone con il soggetto principale).

Ad esempio, per il tag *scarpa casuale*, la seconda immagine non è un buon candidato per la formazione.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/distraction.png)

**Completeness (Completezza):** se un’immagine è idonea per più tag, aggiungi tutti i tag applicabili prima di includere l’immagine nella formazione. Ad esempio, per tag quali *raincoat* e *model-side-view*, aggiungi entrambi i tag alla risorsa idonea prima di includerla nella formazione.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/completeness.png)

## Limitazioni {#limitations}

Gli smart tag migliorati si basano su modelli di apprendimento delle immagini del marchio e dei relativi tag. Questi modelli non sono sempre perfetti per identificare i tag. La versione corrente del Servizio di contenuti avanzati presenta le seguenti limitazioni:

* Incapacità di riconoscere sottili differenze nelle immagini. Ad esempio, camicie sottili o regolari.
* Incapacità di identificare i tag in base a piccoli pattern/parti di un’immagine. Ad esempio, i loghi sulle T-shirt.
* L’assegnazione tag è supportata nelle impostazioni internazionali che [!DNL Experience Manager] è supportato in . Per un elenco delle lingue, vedi [Note sulla versione di Smart Content Services](/help/release-notes/smart-content-service-release-notes.md).

Per cercare le risorse con tag avanzati (regolari o migliorati), utilizza la ricerca Omni di Assets (ricerca full-text). Non esiste un predicato di ricerca separato per gli smart tag.

>[!NOTE]
>
>La capacità del Servizio di contenuti avanzati di addestrare i tag e applicarli ad altre immagini dipende dalla qualità delle immagini utilizzate per la formazione.
>
>Per ottenere risultati ottimali, l’Adobe consiglia di utilizzare immagini visivamente simili per addestrare il servizio per ogni tag.
