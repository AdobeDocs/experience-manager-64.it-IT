---
title: Sono stati migliorati i tag avanzati
description: Sono stati migliorati i tag avanzati
uuid: 4452ca05-1f20-4f80-884a-a739ae7b8b0e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: c1b52aac-1eaf-4cfa-801f-77aeca0d90ea
feature: Tag avanzati, ricerca
role: User
exl-id: 21a9f130-ea91-45bf-adc8-8a73a2a00c77
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 18%

---

# Sono stati migliorati i tag avanzati {#enhanced-smart-tags}

## Panoramica dei tag avanzati migliorati {#overview-of-enhanced-smart-tags}

Le organizzazioni che si occupano di risorse digitali utilizzano sempre più vocabolario controllato dalla tassonomia nei metadati delle risorse. In sostanza, include un elenco di parole chiave a cui i dipendenti, i partner e i clienti utilizzano comunemente per fare riferimento e cercare risorse digitali di una particolare classe. L’assegnazione di tag alle risorse tramite un vocabolario controllato dalla tassonomia ne garantisce l’identificazione e il recupero mediante ricerche basate sui tag.

Rispetto ai vocabolari linguistici naturali, l’assegnazione di tag alle risorse digitali in base alla tassonomia aziendale consente di allinearle con il business di un’azienda e assicura che le risorse più rilevanti vengano visualizzate nelle ricerche.

Ad esempio, un produttore di auto può assegnare tag alle immagini di un&#39;auto con nomi di modello in modo che vengano visualizzate solo immagini rilevanti quando vengono ricercate immagini di vari modelli per progettare una campagna promozionale.

Affinché il Servizio di contenuti avanzati possa applicare i tag giusti, devi addestrarlo a riconoscere la tassonomia. Per addestrare il servizio, cura innanzitutto un insieme di risorse e tag che descrivono al meglio queste risorse. Applica questi tag alle risorse ed esegui un flusso di lavoro di formazione per aiutare il servizio a imparare.

Una volta che un tag è stato addestrato e pronto, il servizio può ora applicare questi tag alle risorse tramite un flusso di lavoro di assegnazione tag.

In background, il Servizio di contenuti avanzati utilizza il framework AI di Adobe Sensei per addestrare il suo algoritmo di riconoscimento delle immagini sulla struttura dei tag e sulla tassonomia aziendale. Questa funzione di content intelligence viene quindi utilizzata per applicare tag rilevanti a un diverso set di risorse.

Il Servizio di contenuti avanzati è un servizio cloud ospitato su [!DNL Adobe I/O]. Per utilizzarlo in Adobe Experience Manager (AEM), l’amministratore di sistema deve integrare l’istanza AEM con [!DNL Adobe I/O].

In sintesi, ecco i passaggi principali per l’utilizzo del Servizio di contenuti avanzati:

* Onboarding
* Verifica di risorse e tag (definizione della tassonomia)
* Formazione del Servizio di contenuti avanzati
* Assegnazione tag automatica

![diagramma di flusso](assets/flowchart.gif)

## Prerequisiti {#prerequisites}

Prima di poter utilizzare il Servizio di contenuti avanzati, verifica quanto segue per creare un’integrazione su [!DNL Adobe I/O]:

* Disponi di un account Adobe ID con privilegi di amministratore dell’organizzazione.
* Il Servizio di contenuti avanzati è abilitato per la tua organizzazione.

## Onboarding {#onboarding}

Il Servizio di contenuti avanzati è acquistabile come componente aggiuntivo per AEM. Dopo l’acquisto, viene inviata un’e-mail all’amministratore dell’organizzazione con un collegamento ad [!DNL Adobe I/O].

L’amministratore può seguire il collegamento per integrare il Servizio di contenuti avanzati con AEM. Per integrare il servizio con AEM Assets, consulta [Configurare tag avanzati](config-smart-tagging.md).

Il processo di onboarding è completo quando l’amministratore configura il servizio e aggiunge utenti in AEM.

>[!NOTE]
>
>Se utilizzi AEM versione 6.3 o precedente e hai bisogno del servizio di assegnazione tag automatica per le risorse, consulta [Tag avanzati](https://helpx.adobe.com/experience-manager/6-3/assets/using/touch-ui-smart-tags.html). I tag avanzati non utilizzano le funzionalità di intelligenza artificiale e sono meno precisi della funzionalità di assegnazione tag avanzati migliorata.

## Verifica di risorse e tag {#reviewing-assets-and-tags}

Dopo l’onboarding, la prima cosa da fare è identificare un set di tag che descrivono al meglio queste immagini nel contesto della tua attività.

Quindi, rivedi le immagini per identificare un set di immagini che meglio rappresentano il tuo prodotto per un particolare requisito aziendale. Assicurati che le risorse nel set curato siano conformi alle [linee guida per la formazione Servizio di contenuti avanzati](smart-tags-training-guidelines.md).

Aggiungi le risorse a una cartella e applica i tag a ciascuna risorsa dalla pagina delle proprietà. Quindi, esegui il flusso di lavoro di formazione su questa cartella. Il set di risorse curato consente al Servizio di contenuti avanzati di addestrare in modo efficace più risorse utilizzando le definizioni di tassonomia.

>[!NOTE]
>
>1. La formazione è un processo irrevocabile. Adobe consiglia di rivedere i tag nel set di risorse curato molto prima di addestrare il Servizio di contenuti avanzati sui tag.
>1. Leggi le [linee guida per la formazione su Smart Content Service](smart-tags-training-guidelines.md) prima di iniziare la formazione per qualsiasi tag.
>1. Quando si prepara il Servizio di contenuti avanzati per la prima volta, Adobe consiglia di addestrarlo su almeno due tag distinti.

>



## Formazione del Servizio di contenuti avanzati {#training-the-smart-content-service}

Affinché il Servizio di contenuti avanzati riconosca la tassonomia aziendale, eseguilo su un set di risorse che già includono tag rilevanti per la tua azienda. Dopo la formazione, il servizio può applicare la stessa tassonomia su un set di risorse simile.

È possibile addestrare il servizio più volte per migliorarne la capacità di applicare tag pertinenti. Dopo ogni ciclo di formazione, esegui un flusso di lavoro di assegnazione tag e verifica se le risorse sono state contrassegnate in modo appropriato.

Puoi addestrare il Servizio di contenuti avanzati periodicamente o su richiesta.

>[!NOTE]
>
>Il flusso di lavoro di formazione viene eseguito solo sulle cartelle.

### Formazione periodica {#periodic-training}

Puoi abilitare il Servizio di contenuti avanzati per addestrare periodicamente le risorse e i tag associati all’interno di una cartella. Apri la pagina delle proprietà della cartella risorse, seleziona **[!UICONTROL Abilita tag avanzati]** nella scheda **[!UICONTROL Dettagli]** e salva le modifiche.

![enable_smart_tags](assets/enable_smart_tags.png)

Una volta selezionata questa opzione per una cartella, AEM esegue automaticamente un flusso di lavoro di formazione per addestrare il Servizio di contenuti avanzati sulle risorse delle cartelle e sui relativi tag. Per impostazione predefinita, il flusso di lavoro di formazione viene eseguito settimanalmente alle 12:30 del sabato.

### Formazione on-demand {#on-demand-training}

Puoi addestrare il Servizio di contenuti avanzati tutte le volte che lo desideri dalla console Flusso di lavoro.

1. Tocca o fai clic sul logo AEM, quindi vai a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Dalla pagina **[!UICONTROL Modelli di flusso di lavoro]**, seleziona il flusso di lavoro **[!UICONTROL Apprendimento dei tag avanzati]**, quindi dalla barra degli strumenti tocca o fai clic su **[!UICONTROL Avvia flusso di lavoro]**.
1. Nella finestra di dialogo **[!UICONTROL Esegui flusso di lavoro]** , individua la cartella del payload che include le risorse con tag per la formazione del servizio.
1. Specifica un titolo per il flusso di lavoro e un commento da aggiungere. Quindi, tocca o fai clic su **[!UICONTROL Esegui]**. Le risorse e i tag vengono inviati per la formazione.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Una volta elaborate le risorse di una cartella per la formazione, solo le risorse modificate vengono elaborate nei cicli di formazione successivi.

### Visualizzazione dei rapporti di formazione {#viewing-training-reports}

Per verificare se il Servizio di contenuti avanzati è addestrato sui tag nel set di risorse di formazione, controlla il rapporto del flusso di lavoro di formazione dalla console Rapporti.

1. Tocca o fai clic sul logo AEM, quindi vai a **[!UICONTROL Strumenti > Risorse > Rapporti]**.
1. Nella pagina **[!UICONTROL Rapporti su risorse]**, tocca o fai clic su **[!UICONTROL Crea]**.
1. Seleziona il rapporto **[!UICONTROL Apprendimento dei tag avanzati]**, quindi tocca o fai clic su **[!UICONTROL Avanti]** nella barra degli strumenti.
1. Specifica un titolo e una descrizione per il rapporto. In **[!UICONTROL Pianifica rapporto]**, lascia selezionata l’opzione **[!UICONTROL Now (Ora)]**. Se vuoi pianificare il rapporto per un momento successivo, seleziona **[!UICONTROL Later (Più tardi)]** e specifica una data e un’ora. Quindi nella barra degli strumenti, tocca o fai clic su **[!UICONTROL Crea]**.
1. Nella pagina **[!UICONTROL Rapporti su risorse]**, seleziona il rapporto generato. Per visualizzare il rapporto, tocca o fai clic sull’icona **[!UICONTROL Visualizza]** nella barra degli strumenti.
1. Rivedi i dettagli del rapporto.

   Il rapporto mostra lo stato di formazione per i tag che hai appreso. La presenza del colore verde nella colonna **[!UICONTROL Training Status (Stato formazione)]** indica che per il tag è stato eseguito il training del servizio di contenuti avanzati. Se invece del verde è presente il colore giallo, il training del servizio di contenuti avanzati non è stato completato per un tag specifico. In questo caso, aggiungi altre immagini che contengono il tag in questione ed esegui il flusso di lavoro di formazione per completare il training del servizio per quel tag.

   Se i tag non vengono visualizzati in questo rapporto, esegui nuovamente il flusso di lavoro di formazione per questi tag.

1. Per scaricare il rapporto, selezionalo dall’elenco e tocca o fai clic sull’icona **[!UICONTROL Scarica]** nella barra degli strumenti. Il rapporto viene scaricato come file Excel.

## Assegnazione automatica dei tag alle risorse {#tagging-assets-automatically}

Dopo aver completato il training del Servizio di contenuti avanzati, puoi attivare il flusso di lavoro di assegnazione tag per applicare automaticamente i tag appropriati a un set diverso di risorse simili.

Puoi eseguire il flusso di lavoro dei tag periodicamente o quando necessario.

>[!NOTE]
>
>Il flusso di lavoro di assegnazione tag viene eseguito sia sulle risorse che sulle cartelle.

### Assegnazione periodica di tag {#periodic-tagging}

È possibile abilitare il Servizio di contenuti avanzati per assegnare periodicamente tag alle risorse all’interno di una cartella. Apri la pagina delle proprietà della cartella risorse, seleziona **[!UICONTROL Abilita tag avanzati]** nella scheda **[!UICONTROL Dettagli]** e salva le modifiche.

Una volta selezionata questa opzione per una cartella, il Servizio di contenuti avanzati assegna automaticamente i tag alle risorse all’interno della cartella. Per impostazione predefinita, il flusso di lavoro di assegnazione tag viene eseguito ogni giorno alle 12:00.

### Assegnazione tag su richiesta {#on-demand-tagging}

Puoi attivare il flusso di lavoro dei tag dalle seguenti opzioni per assegnare tag istantanei alle risorse:

* Console del flusso di lavoro
* Timeline 

>[!NOTE]
>
>Se esegui il flusso di lavoro di assegnazione tag dalla timeline, puoi applicare tag a un massimo di 15 risorse alla volta.

#### Assegnazione di tag alle risorse dalla console Flusso di lavoro {#tagging-assets-from-the-workflow-console}

1. Tocca o fai clic sul logo AEM, quindi vai a **[!UICONTROL Strumenti > Flusso di lavoro > Modelli]**.
1. Dalla pagina **[!UICONTROL Modelli di flusso di lavoro]**, seleziona il flusso di lavoro **[!UICONTROL Risorse di tag avanzati DAM]**, quindi dalla barra degli strumenti tocca o fai clic su **[!UICONTROL Avvia flusso di lavoro]**.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Nella finestra di dialogo **[!UICONTROL Esegui flusso di lavoro]**, individua la cartella del payload contenente le risorse sulle quali desideri applicare automaticamente i tag.
1. Specifica un titolo per il flusso di lavoro e un commento facoltativo. Quindi, tocca o fai clic su **[!UICONTROL Esegui]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Vai alla cartella delle risorse e controlla i tag per verificare se il Servizio di contenuti avanzati ha applicato correttamente i tag alle risorse. Per informazioni dettagliate, consulta [Gestione dei tag avanzati](managing-smart-tags.md).

#### Assegnazione di tag alle risorse dalla timeline {#tagging-assets-from-the-timeline}

1. Dall’interfaccia utente Assets, seleziona la cartella contenente le risorse o le risorse specifiche a cui desideri applicare gli smart tag.
1. Tocca o fai clic sull’icona di Navigazione globale e apri la timeline.
1. Tocca o fai clic sulla freccia in basso, quindi tocca o fai clic su **[!UICONTROL Avvia flusso di lavoro]**.

   ![start_workflow](assets/start_workflow.png)

1. Seleziona il flusso di lavoro **[!UICONTROL DAM Smart Tag Assets]** e specifica un titolo per il flusso di lavoro.
1. Tocca o fai clic su **[!UICONTROL Avvia]**. Il flusso di lavoro applica i tag alle risorse. Vai alla cartella delle risorse e controlla i tag per verificare se il Servizio di contenuti avanzati ha applicato correttamente i tag alle risorse. Per informazioni dettagliate, consulta [Gestione dei tag avanzati](managing-smart-tags.md).

>[!NOTE]
>
>Nei cicli di assegnazione tag successivi, solo le risorse modificate vengono nuovamente taggate con tag di nuova formazione.
>
>Tuttavia, anche le risorse non modificate vengono contrassegnate se il divario tra l’ultimo ciclo di assegnazione tag e quello corrente per il flusso di lavoro di assegnazione tag supera le 24 ore.
>
>Per i flussi di lavoro con tag periodici, le risorse non modificate vengono contrassegnate quando il gap supera i 6 mesi.
