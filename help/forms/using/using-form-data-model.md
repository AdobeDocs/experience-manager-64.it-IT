---
title: Utilizzare il modello dati del modulo
seo-title: Use form data model
description: Scopri come utilizzare il modello dati del modulo per creare e utilizzare moduli adattivi e comunicazioni interattive.
seo-description: Learn how to use form data model to create and work with adaptive forms and interactive communications.
uuid: 9a8bd44a-34a1-41ef-a57b-d5e3dd0a77ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 7a1bfd43-39b1-478b-a294-92c78eaebbf2
feature: Form Data Model
exl-id: 39408af6-439c-4ade-8062-155be9141dfa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 0%

---

# Utilizzare il modello dati del modulo {#use-form-data-model}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

![](do-not-localize/data-integeration.png)

L’integrazione dei dati di AEM Forms consente di utilizzare origini dati back-end diverse per creare un modello di dati modulo da utilizzare come schema in vari moduli adattivi e flussi di lavoro di comunicazione interattiva. Richiede la configurazione delle origini dati e la creazione del modello dati del modulo in base agli oggetti e ai servizi del modello dati disponibili nelle origini dati. Per ulteriori informazioni, consulta quanto segue:

* [Integrazione dei dati di AEM Forms](/help/forms/using/data-integration.md)
* [Configurare origini dati](/help/forms/using/configure-data-sources.md)
* [Crea modello dati modulo](/help/forms/using/create-form-data-models.md)
* [Utilizzare il modello dati del modulo](/help/forms/using/work-with-form-data-model.md)

Un modello di dati modulo è un’estensione dello schema JSON che può essere utilizzata per:

* [Creazione di moduli adattivi e frammenti](#create-af)
* [Creare comunicazioni interattive e blocchi predefiniti quali frammenti di testo, elenco e condizione](#create-ic)
* [Anteprima di comunicazioni interattive con dati di esempio](#preview-ic)
* [Precompilazione di moduli adattivi e comunicazioni interattive](#prefill)
* [Scrivere di nuovo i dati del modulo adattivo inviati nelle origini dati](#write-af)
* [Richiamare i servizi utilizzando le regole del modulo adattivo](#invoke-services)

## Creazione di moduli adattivi e frammenti {#create-af}

Puoi creare [moduli adattivi](/help/forms/using/creating-adaptive-form.md) e [frammenti di modulo adattivi](/help/forms/using/adaptive-form-fragments.md) basato su un modello dati del modulo. Effettuare le seguenti operazioni per utilizzare un modello dati modulo durante la creazione di un modulo adattivo o di un frammento di modulo adattivo:

1. Nella scheda Modello modulo della schermata Aggiungi proprietà, selezionare **[!UICONTROL Modello dati modulo]** in **[!UICONTROL Seleziona da]** elenco a discesa.

   ![create-af-1](assets/create-af-1.png)

1. Tocca per espandere **[!UICONTROL Seleziona modello dati modulo]**. Sono elencati tutti i modelli di dati modulo disponibili.

   Seleziona un modello dati da.

   ![create-af-2](assets/create-af-2.png)

1. (**Solo frammenti di modulo adattivi**) È possibile creare un frammento di modulo adattivo basato su un solo oggetto modello dati all’interno di un modello dati modulo. Espandi **[!UICONTROL Definizioni dei modelli di dati del modulo]** a discesa. Elenca tutti gli oggetti del modello dati nel modello dati del modulo specificato. Selezionare un oggetto modello dati dall’elenco.

   ![create-af-3](assets/create-af-3.png)

Una volta creato il modulo adattivo o il frammento di modulo adattivo basato su un modello dati del modulo, gli oggetti del modello dati del modulo vengono visualizzati nella **[!UICONTROL Oggetti del modello dati]** della scheda del browser Contenuto nell’editor di moduli adattivi.

>[!NOTE]
>
>Per un frammento di modulo adattivo, nella scheda Oggetti modello dati viene visualizzato solo l’oggetto modello dati selezionato al momento della creazione e gli oggetti modello dati associati.

![data-model-objects-tab](assets/data-model-objects-tab.png)

Per aggiungere campi modulo è possibile trascinare oggetti modello dati sul modulo adattivo o sul frammento. I campi modulo aggiunti mantengono le proprietà dei metadati e il binding con le proprietà dell’oggetto modello dati. Il binding assicura che i valori dei campi vengano aggiornati nelle origini dati corrispondenti all’invio del modulo e precompilati al momento del rendering del modulo.

## Creare comunicazioni interattive {#create-ic}

È possibile creare una comunicazione interattiva basata su un modello di dati modulo che è possibile utilizzare per precompilare la comunicazione interattiva con i dati provenienti da origini dati configurate. Inoltre, gli elementi di base di una comunicazione interattiva, come i frammenti di testo, elenco e condizione del documento, possono essere basati su un modello dati del modulo.

È possibile scegliere un modello dati modulo durante la creazione di una comunicazione interattiva o di un frammento di documento. L’immagine seguente mostra la scheda Generale della finestra di dialogo Crea comunicazione interattiva .

![create-ic](assets/create-ic.png)

Scheda Generale della finestra di dialogo Crea comunicazione interattiva

Per ulteriori informazioni, consulta:

[Creare una comunicazione interattiva](/help/forms/using/create-interactive-communication.md)

[Testo nelle comunicazioni interattive](/help/forms/using/texts-interactive-communications.md)

[Condizioni delle comunicazioni interattive](/help/forms/using/conditions-interactive-communications.md)

[Elencare frammenti](/help/forms/using/lists.md)

## Anteprima con dati di esempio {#preview-ic}

L’editor del modello dati modulo consente di generare e modificare dati di esempio per gli oggetti del modello dati nel modello dati del modulo. È possibile utilizzare questi dati per visualizzare in anteprima e testare le comunicazioni interattive e i moduli adattivi. È necessario generare i dati di esempio prima di visualizzare l’anteprima come descritto in [Utilizzare il modello dati del modulo](/help/forms/using/work-with-form-data-model.md#sample).

Per visualizzare in anteprima una comunicazione interattiva con dati del modello dati del modulo di esempio:

1. Nell&#39;istanza AEM autore, passa a **[!UICONTROL Forms > Forms e documenti]**.
1. Seleziona una comunicazione interattiva e tocca **[!UICONTROL Anteprima]** nella barra degli strumenti da selezionare **[!UICONTROL Canale web]**, **[!UICONTROL Canale di stampa]** oppure **[!UICONTROL Entrambi i canali]** per visualizzare in anteprima la comunicazione interattiva.
1. Nell’anteprima [*canale*] di dialogo, **[!UICONTROL Dati di prova del modello dati del modulo]** è selezionato e tocca **[!UICONTROL Anteprima]**.

Si apre la comunicazione interattiva con dati di esempio precompilati.

![anteprima web](assets/web-preview.png)

Allo stesso modo, per visualizzare in anteprima un modulo adattivo con dati di esempio, apri il modulo adattivo in modalità di authoring e tocca **[!UICONTROL Anteprima]**.

## Precompilazione tramite il servizio del modello dati del modulo {#prefill}

AEM Forms fornisce il servizio di precompilazione dei modelli di dati per moduli pronto all’uso che è possibile abilitare per i moduli adattivi e le comunicazioni interattive basate sul modello di dati del modulo. Il servizio di precompilazione esegue una query sulle origini dati per gli oggetti del modello dati nel modulo adattivo e nella comunicazione interattiva e quindi precompila i dati durante il rendering del modulo o della comunicazione.

Per abilitare il servizio di precompilazione del modello di dati modulo per un modulo adattivo, apri le proprietà del contenitore di modulo adattivo e seleziona **[!UICONTROL Servizio di precompilazione modello dati modulo]** dal **[!UICONTROL Servizio di precompilazione]** a discesa nel pannello a soffietto Base. Quindi, salva le proprietà.

![servizio di precompilazione](assets/prefill-service.png)

Per configurare il servizio di precompilazione del modello dati modulo in una comunicazione interattiva, è possibile selezionare Servizio di precompilazione modello dati modulo dal menu a discesa Servizio di precompilazione durante la creazione del servizio o in un secondo momento, modificando le proprietà.

![edit-ic-props](assets/edit-ic-props.png)

Finestra di dialogo Modifica proprietà per una comunicazione interattiva

## Scrivere i dati del modulo adattivo inviati nelle origini dati {#write-af}

Quando un utente invia un modulo basato su un modello di dati modulo, è possibile configurare il modulo in modo da scrivere i dati inviati per un oggetto modello dati nelle relative origini dati. Per ottenere questo caso d’uso, AEM Forms fornisce [Azione di invio del modello dati modulo](/help/forms/using/configuring-submit-actions.md), disponibile solo per i moduli adattivi basati su un modello dati del modulo. Scrive i dati inviati per un oggetto modello dati nella relativa origine dati.

Per configurare l’azione di invio Modello dati modulo, apri le proprietà Contenitore modulo adattivo e seleziona **[!UICONTROL Invia utilizzando il modello dati del modulo]** dal menu a discesa Invia azione sotto il pannello a soffietto Invio. Quindi, sfoglia e seleziona un oggetto modello dati dal **[!UICONTROL Nome dell’oggetto modello dati da inviare]** a discesa. Salva le proprietà.

All’invio del modulo, i dati per l’oggetto modello dati configurato vengono scritti nella rispettiva origine dati.

![presentazione dei dati](assets/data-submission.png)

È inoltre possibile inviare allegati modulo a un’origine dati utilizzando la proprietà dell’oggetto modello dati binario. Per inviare allegati a un’origine dati JDBC, effettua le seguenti operazioni:

1. Aggiungere un oggetto modello dati che include una proprietà binaria al modello dati del modulo.
1. Nel modulo adattivo, trascina **[!UICONTROL File allegato]** dal browser Componenti al modulo adattivo.
1. Tocca per selezionare il componente aggiunto e tocca ![settings_icon](assets/settings_icon.png) per aprire il browser Proprietà del componente.
1. Nel campo Riferimento binding , tocca ![cartella_18](assets/foldersearch_18.png) e selezionare la proprietà binaria aggiunta nel modello dati del modulo. Configura altre proprietà, a seconda delle necessità.

   Tocca ![pulsante di controllo](assets/check-button.png) per salvare le proprietà. Il campo allegato è ora associato alla proprietà binaria del modello dati del modulo.

1. Nella sezione Invio delle proprietà del contenitore di moduli adattivi, abilita **[!UICONTROL Invia allegati modulo]**. Invia l’allegato nel campo della proprietà binaria all’origine dati all’invio del modulo.

## Richiamare i servizi nei moduli adattivi utilizzando le regole {#invoke-services}

In un modulo adattivo basato su un modello di dati del modulo, è possibile [creare regole](/help/forms/using/rule-editor.md) per richiamare servizi configurati nel modello dati del modulo. La **[!UICONTROL Richiamare i servizi]** in una regola sono elencati tutti i servizi disponibili nel modello dati del modulo e consentono di selezionare i campi di input e output per il servizio. È inoltre possibile utilizzare **Imposta valore** tipo di regola per richiamare un servizio modello dati modulo e impostare il valore di un campo sull&#39;output restituito dal servizio.

Ad esempio, la regola seguente richiama un servizio get che utilizza l&#39;ID dipendente come input e i valori restituiti sono compilati nei corrispondenti campi ID dipendente, Cognome, Nome e Genere del modulo.

![invoke-service](assets/invoke-service.png)

Inoltre, puoi utilizzare la `guidelib.dataIntegrationUtils.executeOperation` API per scrivere un JavaScript nell&#39;editor di codice per l&#39;editor di regole. Per informazioni dettagliate sull’API, consulta [API per richiamare il servizio del modello dati del modulo](/help/forms/using/invoke-form-data-model-services.md).
