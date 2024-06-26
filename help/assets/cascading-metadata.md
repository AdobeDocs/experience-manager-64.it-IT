---
title: Metadati a cascata
description: Questo articolo descrive come definire i metadati a cascata per le risorse.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: ea6187e8-075d-4666-afc5-01c97deccc11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 12%

---

# Metadati a cascata {#cascading-metadata}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questo articolo descrive come definire i metadati a cascata per le risorse.

>[!CAUTION]
>
>I metadati a cascata non sono supportati per i frammenti di contenuto.

Durante l’acquisizione delle informazioni sui metadati di una risorsa, gli utenti forniscono informazioni nei vari campi disponibili. Puoi visualizzare campi di metadati o valori di campo specifici che dipendono dalle opzioni selezionate negli altri campi. Tale visualizzazione condizionale dei metadati è denominata metadati a cascata. In altre parole, puoi creare una dipendenza tra un particolare campo/valore di metadati e uno o più campi e/o i relativi valori.

Utilizza gli schemi di metadati per definire le regole per la visualizzazione dei metadati a cascata. Ad esempio, se lo schema metadati include un campo del tipo di risorsa, puoi definire un set pertinente di campi da visualizzare in base al tipo di risorsa selezionata dall’utente.

Di seguito sono riportati alcuni casi d’uso per i quali è possibile definire metadati a cascata:

* Se è richiesta la posizione dell&#39;utente, visualizzare i nomi delle città pertinenti in base alla scelta del paese e dello stato dell&#39;utente.
* Carica i nomi di marchio pertinenti in un elenco in base alla scelta dell’utente della categoria di prodotto.
* Attiva o disattiva la visibilità di un particolare campo in base al valore specificato in un altro campo. Ad esempio, visualizzare campi di indirizzo di spedizione separati se l’utente desidera che la spedizione venga consegnata a un indirizzo diverso.
* Designare un campo come obbligatorio in base al valore specificato in un altro campo.
* Modifica le opzioni visualizzate per un campo specifico in base al valore specificato in un altro campo.
* Imposta il valore dei metadati predefiniti in un particolare campo in base al valore specificato in un altro campo.

## Configurare i metadati a cascata in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Considera uno scenario in cui desideri visualizzare i metadati a cascata in base al tipo di risorsa selezionata. Alcuni esempi

* Per un video, visualizza i campi applicabili, ad esempio il formato, il codec, la durata e così via.
* Per un documento Word o PDF, visualizzare campi quali conteggio delle pagine, autore e così via.

Indipendentemente dal tipo di risorsa scelto, visualizza le informazioni sul copyright come campo obbligatorio.

1. Tocca o fai clic sul pulsante [!DNL Experience Manager] e vai a **[!UICONTROL Strumenti]** > **[!UICONTROL Risorse]** > **[!UICONTROL Schemi metadati]**.
1. Nella pagina **[!UICONTROL Moduli schema]** seleziona un modulo schema, quindi, per modificare lo schema, dalla barra degli strumenti tocca o fai clic su **[!UICONTROL Modifica]**.

   ![select_form](assets/select_form.png)

1. (Facoltativo) Nell’editor dello schema metadati, crea un nuovo campo da personalizzare. Specifica un nome e un percorso di proprietà nel **[!UICONTROL Impostazioni]** scheda .

   Per creare una nuova scheda, tocca o fai clic su **[!UICONTROL +]** per aggiungere una scheda e quindi un campo metadati.

   ![add_tab](assets/add_tab.png)

1. Aggiungi un campo a discesa per il tipo di risorsa. Specifica un nome e un percorso di proprietà nel **[!UICONTROL Impostazioni]** scheda . Aggiungi una descrizione facoltativa.

   ![asset_type_field](assets/asset_type_field.png)

1. Le coppie chiave-valore sono le opzioni fornite a un utente del modulo. Puoi fornire le coppie chiave-valore manualmente o da un file JSON.

   * Per specificare manualmente i valori, seleziona **[!UICONTROL Aggiungi manualmente]** e tocca o fai clic su **[!UICONTROL Aggiungi scelta]** e specifica il testo e il valore dell&#39;opzione. Ad esempio, specifica i tipi di risorse Video, PDF, Word e Immagine.
   * Per recuperare dinamicamente i valori da un file JSON, seleziona **[!UICONTROL Aggiungi tramite percorso JSON]** e fornire il percorso del file JSON. [!DNL Experience Manager] recupera le coppie chiave-valore in tempo reale quando il modulo viene presentato all’utente.

   Entrambe le opzioni si escludono a vicenda. Non puoi importare le opzioni da un file JSON e modificarle manualmente.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >Quando si aggiunge un file JSON, le coppie chiave-valore non vengono visualizzate nell’editor dello schema dei metadati, ma sono disponibili nel modulo pubblicato.

   >[!NOTE]
   >
   >Quando si aggiungono scelte, se si fa clic sul campo a discesa , l’interfaccia viene distorta e l’icona di eliminazione per le scelte smette di funzionare. Quando aggiungi le scelte al menu a discesa, non fare clic nuovamente sul menu a discesa finché non vengono salvate le modifiche. Se si verifica questo problema, salva lo schema e riaprilo per continuare la modifica.

1. (Facoltativo) Aggiungi gli altri campi obbligatori. Ad esempio, il formato, il codec e la durata del video del tipo di risorsa.

   Allo stesso modo, aggiungi campi dipendenti per altri tipi di risorse. Ad esempio, aggiungere i campi conteggio pagine e creazione per le risorse del documento, come i file PDF e Word.

   ![campi_dipendenti_video](assets/video_dependent_fields.png)

1. Per creare una dipendenza tra il campo del tipo di risorsa e gli altri campi, scegli il campo dipendente e apri la **[!UICONTROL Regole]** scheda .

   ![select_dependentfield](assets/select_dependentfield.png)

1. Sotto **[!UICONTROL Requisito]**, scegli **[!UICONTROL Obbligatorio, in base a una nuova regola]** opzione .
1. Tocca o fai clic su **[!UICONTROL Aggiungi regola]** e scegli il campo **[!UICONTROL Tipo di risorsa]** per creare una dipendenza. Scegli anche il valore del campo in cui creare la dipendenza. In questo caso, scegli **[!UICONTROL Video]**. Per salvare le modifiche, Tocca o fai clic su **[!UICONTROL Fine]**.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >Con le regole è possibile utilizzare un elenco a discesa con valori predefiniti manualmente. I menu a discesa con percorso JSON configurato non possono essere utilizzati con regole che utilizzano valori predefiniti per applicare condizioni. Se i valori vengono caricati da JSON in fase di runtime, non è possibile applicare una regola predefinita.

1. In **[!UICONTROL Visibilità]**, scegli l’opzione **[!UICONTROL Visibile, in base alla nuova regola]**.

1. Tocca o fai clic su **[!UICONTROL Aggiungi regola]** e scegli il campo **[!UICONTROL Tipo di risorsa]** per creare una dipendenza. Scegli anche il valore del campo in cui creare la dipendenza. In questo caso, scegli **[!UICONTROL Video]**. Per salvare le modifiche, Tocca o fai clic su **[!UICONTROL Fine]**.

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Toccando o facendo clic sugli spazi bianchi (o in un punto qualsiasi diverso dai valori) i valori verranno reimpostati. In questo caso, è necessario selezionarli di nuovo.

   >[!NOTE]
   >
   >Puoi applicare la condizione **[!UICONTROL Requisito]** e **[!UICONTROL Visibilità]**, pur lasciandole indipendenti tra di loro.

1. Analogamente, crea una dipendenza tra il valore Video nel campo Tipo di risorsa e altri campi, come Codec e Durata.
1. Ripeti i passaggi per creare una dipendenza tra le risorse del documento (PDF e Word) nel **[!UICONTROL Tipo di risorsa]** e campi, ad esempio Conteggio pagine e Autore.
1. Fai clic su **[!UICONTROL Salva]**. Applicare lo schema metadati a una cartella.

1. Passa alla cartella alla quale hai applicato lo schema metadati e apri la pagina delle proprietà di una risorsa. A seconda della scelta effettuata nel campo Tipo di risorsa , vengono visualizzati i campi pertinenti di metadati a cascata.

   ![Metadati a cascata per la risorsa Video](assets/video_asset.png)

   *Figura: Metadati a cascata per la risorsa Video*

   ![Metadati a cascata per la risorsa del documento](assets/doc_type_fields.png)

   *Figura: Metadati a cascata per la risorsa del documento*
