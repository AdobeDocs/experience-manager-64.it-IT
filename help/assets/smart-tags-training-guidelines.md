---
title: Linee guida per la formazione sui servizi di contenuto avanzato
description: Formazione del servizio AI per l'applicazione di smart tag alle risorse
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
uuid: 1c011496-be6e-470b-9da8-48db8c6d1108
contentOwner: AG
discoiquuid: a5aab094-8b2d-4a23-890f-be6f9e5137bd
translation-type: tm+mt
source-git-commit: dc779a0d89dc4c044ca4f3e3f92c4a9b651d09a8

---


# Linee guida per la formazione sui servizi di contenuto avanzato {#smart-content-service-training-guidelines}

Per poter etichettare efficacemente le immagini del tuo marchio, Smart Content Service richiede che le immagini di formazione siano conformi a determinate linee guida.

## Orientamenti per la formazione {#guidelines-for-training}

Per risultati ottimali, le immagini del set di formazione devono essere conformi alle seguenti linee guida:

**Quantity and size (Quantità e dimensioni)****: almeno 30 immagini per tag**. Almeno 500 pixel sul lato più lungo.

**Coerenza**: Le immagini di un tag devono essere visivamente simili.

Ad esempio, non è consigliabile assegnare a tutte queste immagini il tag *di mia parte* (per la formazione) perché non sono visivamente simili.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/coherence.png)

**Copertura**: Dovrebbe esserci una varietà sufficiente nelle immagini della formazione. L’idea è di fornire alcuni esempi, ma con una discreta diversità, in modo che AEM possa concentrarsi sulle cose giuste. Se applicate lo stesso tag a immagini visivamente diverse, includete almeno cinque esempi di ciascun tipo.

Ad esempio, per il tag *model-down-pose*, includete più immagini di formazione simili all’immagine evidenziata di seguito per il servizio, in modo da identificare immagini simili con maggiore precisione durante l’assegnazione dei tag.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/coverage_1.png)

**Distrazione/ostruzione**: Il servizio si allena meglio sulle immagini con meno distrazioni (sfondi visibili, accompagnamento indipendenti, come oggetti/persone con il soggetto principale).

Ad esempio, per il tag *casual-shoe*, la seconda immagine non è un buon candidato per l&#39;addestramento.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/distraction.png)

**Completeness (Completezza):** se un’immagine è idonea per più tag, aggiungi tutti i tag applicabili prima di includere l’immagine nella formazione. Ad esempio, per tag quali *raincoat* e *model-side-view*, aggiungi entrambi i tag alla risorsa idonea prima di includerla nella formazione.

![Immagini illustrative per esemplificare le linee guida per la formazione](assets/do-not-localize/completeness.png)

## Limiti {#limitations}

Gli smart tag avanzati si basano su modelli di apprendimento delle immagini del marchio e dei relativi tag. Questi modelli non sempre sono perfetti per identificare i tag. La versione corrente di Smart Content Service presenta i seguenti limiti:

* Incapacità di riconoscere sottili differenze nelle immagini. Ad esempio, camicie sottili o regolari.
* Impossibile identificare i tag in base a piccoli pattern/parti di un’immagine. Ad esempio, i logo delle T-shirt.
* I tag sono supportati nelle impostazioni internazionali in cui AEM è supportato. Per un elenco delle lingue, consultate [Note](/help/release-notes/smart-content-service-release-notes.md)sulla versione di Smart Content Services.

Per cercare le risorse con gli smart tag (regolari o avanzati), usate la ricerca Omni delle risorse (ricerca full-text). Non esiste un predicato di ricerca separato per gli smart tag.

>[!NOTE]
>
>La capacità di Smart Content Service di formare i tag e applicarli ad altre immagini dipende dalla qualità delle immagini utilizzate per la formazione.
>
>Per risultati ottimali, Adobe consiglia di usare immagini visivamente simili per formare il servizio per ciascun tag.

