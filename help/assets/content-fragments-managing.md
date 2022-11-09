---
title: Gestione dei frammenti di contenuto
seo-title: Managing Content Fragments
description: I frammenti di contenuto sono memorizzati come risorse e vengono gestiti principalmente dalla console Risorse.
seo-description: Content Fragments are stored as Assets, so are primarily managed from the Assets console.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
exl-id: b21ba7a1-6e6f-4b95-9336-b49f7e932af5
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 63%

---

# Gestione dei frammenti di contenuto {#managing-content-fragments}

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

I frammenti di contenuto sono memorizzati come **[!UICONTROL Risorse]**, così come vengono gestiti principalmente dal **[!UICONTROL Risorse]** console.

>[!NOTE]
>
>I frammenti di contenuto vengono quindi utilizzati con le pagine di authoring; vedere [Authoring delle pagine con frammenti di contenuto](/help/sites-authoring/content-fragments.md).

## Creazione di frammenti di contenuto {#creating-content-fragments}

### Creazione di un modello di contenuto {#creating-a-content-model}

È possibile abilitare e creare i [modelli per frammenti di contenuto](content-fragments-models.md) prima della creazione dei frammenti di contenuto con una struttura.

>[!NOTE]
>
>Vedi [Sviluppo di frammenti di contenuto](/help/sites-developing/customizing-content-fragments.md) per ulteriori informazioni sui modelli; utilizzato per frammenti di contenuto semplici.

### Creazione di un frammento di contenuto {#creating-a-content-fragment}

Il metodo di creazione di un frammento di contenuto è sostanzialmente lo stesso per i frammenti semplici e strutturati:

1. Passa alla cartella **[!UICONTROL Risorse]** in cui desideri creare il frammento.
1. Per aprire la procedura guidata, seleziona **[!UICONTROL Crea]**, quindi **[!UICONTROL Frammento di contenuto]**.
1. Il primo passaggio della procedura guidata richiede di specificare la base del nuovo frammento.

   * Può trattarsi di:

      * [Modello](/help/sites-developing/content-fragment-templates.md) - ad esempio **[!UICONTROL Frammento semplice]**
      * [Modello](content-fragments-models.md) - utilizzato per creare un frammento che richiede contenuto strutturato; ad esempio **Aeroporto** model
   * Vengono visualizzati tutti i modelli disponibili.

   Dopo la selezione, utilizza **[!UICONTROL Successivo]** per procedere.

   ![cfm-6420-15](assets/cfm-6420-15.png)

1. Nel passaggio **[!UICONTROL Proprietà]** specifica:

   * **[!UICONTROL Base]**

      * **[!UICONTROL Titolo]**

         Titolo del frammento.

         Obbligatorio.

      * **[!UICONTROL Descrizione]**
      * **[!UICONTROL Tag]**
   * **[!UICONTROL Avanzate]**

      * **[!UICONTROL Nome]**

         il nome; verrà utilizzato per formare l’URL.

         Obbligatorio; viene derivato automaticamente dal titolo, ma può essere aggiornato.


1. Seleziona **[!UICONTROL Crea]** per completare l’azione, quindi **[!UICONTROL Apri]** il frammento per la modifica oppure tornare alla console facendo clic su **[!UICONTROL Fine]**.

## Azioni per un frammento di contenuto {#actions-for-a-content-fragment}

In **[!UICONTROL Risorse]** per i frammenti di contenuto sono disponibili diverse azioni:

* Dalla barra degli strumenti; dopo aver selezionato il frammento sono disponibili tutte le azioni appropriate.
* Come [azioni rapide](/help/sites-authoring/basic-handling.md#quick-actions); un sottoinsieme di azioni disponibili per le singole schede di frammento.

![cfm-6420-17](assets/cfm-6420-17.png)

Seleziona il frammento per visualizzare la barra degli strumenti con le azioni applicabili:

* **[!UICONTROL Download]**

   * Salvare il frammento come file ZIP; puoi definire se includere elementi, varianti, metadati.

* **[!UICONTROL Crea]**
* **[!UICONTROL Pagamento]**
* **[!UICONTROL Proprietà]**

   * Consente di visualizzare e/o modificare i metadati del frammento.

* **[!UICONTROL Modifica]**

   * Permette di [aprire il frammento per la modifica del contenuto](content-fragments-variations.md) insieme ai relativi elementi, varianti, contenuti associati e metadati.

* **[!UICONTROL Gestisci i tag]**
* **[!UICONTROL Alla raccolta]**

   * Aggiungi il frammento a una raccolta.
   * Questo può essere fatto anche quando [associazione di una raccolta con il frammento](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL Copia/Incolla]**
* **[!UICONTROL Sposta]**
* **[!UICONTROL Pubblicazione rapida]**
* **[!UICONTROL Gestisci pubblicazione]**
* **[!UICONTROL Eliminare]**

>[!NOTE]
>
>Molti di questi sono [azioni standard per Assets](managing-assets-touch-ui.md) e/o [app desktop](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=it).

## Apertura dell’Editor frammento {#opening-the-fragment-editor}

Per aprire la pagina per la modifica:

>[!CAUTION]
>
>Per modificare un frammento di contenuto sono necessarie [le autorizzazioni appropriate](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Se riscontri problemi, contatta l’amministratore del sistema.

1. Utilizza la **[!UICONTROL Risorse]** per passare alla posizione del frammento di contenuto.
1. Apri il frammento per la modifica:

   * Tocca o fai clic sul collegamento frammento o frammento (a seconda della vista della console).
   * Selezione del frammento, quindi **[!UICONTROL Modifica]** dalla barra degli strumenti.

   Viene aperto l’editor frammenti:

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Se in una pagina di contenuto è già presente un riferimento al frammento, viene visualizzato un messaggio.
   >
   >2. Il pannello laterale può essere nascosto o visualizzato utilizzando l’icona **[!UICONTROL Attiva/Disattiva pannello laterale]**.


1. Per spostarti tra le tre modalità, usa le icone nel pannello laterale:

   * Varianti: [Modifica del contenuto](#editing-the-content-of-your-fragment) e [Gestione delle varianti](#creating-and-managing-variations-within-your-fragment)
   * [Annotazioni](content-fragments-variations.md#annotating-a-content-fragment)
   * [Contenuto associato ](#associating-content-with-your-fragment)
   * [Metadati](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. Dopo aver apportato le modifiche, utilizza **[!UICONTROL Salva]** o **[!UICONTROL Annulla]** se necessario.

   >[!NOTE]
   >
   >Sia l’azione **[!UICONTROL Salva]** che **[!UICONTROL Annulla]** causeranno l’uscita dall’editor. Per informazioni complete sul funzionamento di entrambe le opzioni dei frammenti di contenuto, consulta la sezione [Salva, Annulla e Versioni](#save-cancel-and-versions).

## Salva, Annulla e Versioni {#save-cancel-and-versions}

>[!NOTE]
>
>Le versioni possono anche essere [create, confrontate e ripristinate dalla timeline](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments).

L’editor dispone di due opzioni:

* **[!UICONTROL Salva]**

   Salva le modifiche più recenti e chiude l’editor.

   >[!CAUTION]
   >
   >Per modificare un frammento di contenuto sono necessarie [le autorizzazioni appropriate](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Se riscontri problemi, contatta l’amministratore del sistema.

   >[!NOTE]
   >
   >È possibile rimanere nell&#39;editor, apportando una serie di modifiche, prima di selezionare **[!UICONTROL Salva]**.

   >[!CAUTION]
   >
   >Oltre al semplice salvataggio delle modifiche, **[!UICONTROL Salva]** aggiorna anche tutti i riferimenti e assicura che il dispatcher venga scaricato come necessario. L’elaborazione di queste modifiche può richiedere del tempo. Per questo motivo, può esserci un impatto sulle prestazioni su un sistema di grandi dimensioni, complesso o con un carico elevato.
   >
   >
   >Tieni presente questo aspetto quando utilizzi **[!UICONTROL Salva]** quindi è possibile reimmettere rapidamente l’editor frammenti per apportare e salvare ulteriori modifiche.

* **[!UICONTROL Annulla]**

   Uscirà dall’editor senza salvare le modifiche più recenti.

Durante la modifica del frammento di contenuto AEM crea automaticamente delle versioni per garantire che il contenuto precedente possa essere ripristinato se **[!UICONTROL Annulla]** le modifiche:

1. Quando un frammento di contenuto viene aperto per apportare modiche, AEM verifica l’esistenza del token basato su cookie che indica se esiste una *sessione di modifica*:

   1. Se il token viene trovato, il frammento viene considerato parte della sessione di modifica esistente.
   1. Se il token *non* è disponibile e l’utente inizia a modificare il contenuto, viene creata una versione e inviato al client un token per questa nuova sessione di modifica, che verrà salvato in un cookie.

1. Durante una sessione di modifica *attiva*, il contenuto in fase di modifica viene salvato automaticamente ogni 600 secondi (impostazione predefinita).

   >[!NOTE]
   >
   >L’intervallo di salvataggio automatico è configurabile utilizzando il comando `/conf`.
   >
   >Valore predefinito, vedi:
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. Se l’utente seleziona **[!UICONTROL Annulla]** la modifica, la versione creata all&#39;inizio della sessione di modifica viene ripristinata e il token viene rimosso per terminare la sessione di modifica.
1. Se l’utente **[!UICONTROL Salva]** le modifiche, gli elementi/varianti aggiornate vengono rese permanenti e il token viene rimosso per terminare la sessione di modifica.

## Modifica del contenuto del frammento {#editing-the-content-of-your-fragment}

Dopo aver aperto il frammento, puoi utilizzare la scheda [Varianti](content-fragments-variations.md) per effettuare l’authoring dei contenuti.

## Creazione e gestione di varianti all’interno del frammento {#creating-and-managing-variations-within-your-fragment}

Dopo aver creato il contenuto primario, puoi creare e gestire le [Varianti](content-fragments-variations.md) di tale contenuto.

## Associazione di contenuto al frammento {#associating-content-with-your-fragment}

È inoltre possibile [associare il contenuto](content-fragments-assoc-content.md) a un frammento. In questo modo si fornisce una connessione in modo che le risorse (ad esempio le immagini) possano essere (facoltativamente) utilizzate con il frammento quando viene aggiunto a una pagina di contenuto.

## Visualizzazione e modifica dei metadati (proprietà) del frammento {#viewing-and-editing-the-metadata-properties-of-your-fragment}

Puoi visualizzare e modificare le proprietà di un frammento utilizzando la scheda [[!UICONTROL Metadati]](content-fragments-metadata.md).

## Timeline per i frammenti di contenuto {#timeline-for-content-fragments}

Oltre alle opzioni standard, [Timeline](managing-assets-touch-ui.md#timeline) fornisce sia informazioni che azioni specifiche relative ai frammenti di contenuto:

* Visualizza informazioni su versioni, commenti e annotazioni
* Azioni per le versioni

   * **[[!UICONTROL Ripristina questa versione]](#reverting-to-a-version)** (seleziona un frammento esistente, quindi una versione specifica)
   * **[[!UICONTROL Confronta con corrente]](#comparing-fragment-versions)** (seleziona un frammento esistente, quindi una versione specifica)
   * Aggiungi un’**[!UICONTROL Etichetta]** e/o un **[!UICONTROL Commento]** (seleziona un frammento esistente, quindi una versione specifica)
   * **[!UICONTROL Salva come versione]** (seleziona un frammento esistente, quindi la freccia su nella parte inferiore della timeline)

* Azioni per le annotazioni

   * **[!UICONTROL Eliminare]**

>[!NOTE]
>
>I commenti sono:
>
>* Funzionalità standard per tutte le risorse
>* Effettuati nella timeline
>* Correlati alla risorsa frammento
>
>Le annotazioni (per i frammenti di contenuto) sono:
>
>* Inserite nell’editor frammenti
>* Specifiche per un segmento di testo selezionato all’interno del frammento


Esempio:

![cfm-6420-19](assets/cfm-6420-19.png)

## Confronto delle versioni dei frammenti {#comparing-fragment-versions}

L’azione **[!UICONTROL Confronta con corrente]** è disponibile nella [[!UICONTROL Timeline] dopo aver selezionato una versione specifica.](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments)

Si aprirà:

* la versione **[!UICONTROL Corrente]** (più recente) (a sinistra)

* la versione selezionata **v&lt;*x.y*>** (a destra)

Vengono visualizzati uno accanto all’altro, dove:

* Eventuali differenze sono evidenziate

   * Testo eliminato: rosso
   * Testo inserito: verde
   * Testo sostituito: blu

* L’icona a schermo intero consente di aprire una delle due versioni da sola; quindi di tornare alla vista parallela
* È possibile **[!UICONTROL ritornare]** alla versione specifica
* **[!UICONTROL Fine]** riporta alla console

>[!NOTE]
>
>Non è possibile modificare il contenuto del frammento nella modalità di confronto.

![cfm-6420-20](assets/cfm-6420-20.png)

## Ripristino di una versione  {#reverting-to-a-version}

È possibile ripristinare una versione specifica del frammento:

* Direttamente dalla [[!UICONTROL timeline]](content-fragments-managing.md#timeline-for-content-fragments).

   Seleziona la versione richiesta, quindi l’azione **[!UICONTROL Ripristina questa versione]**.

* Durante il [confronto di una versione con la versione corrente](content-fragments-managing.md#comparing-fragment-versions) è possibile **[!UICONTROL ritornare]** alla versione selezionata.

## Pubblicazione e riferimento a un frammento {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Se il frammento è basato su un modello, assicurati che il [modello sia stato pubblicato](content-fragments-models.md#publishing-a-content-fragment-model).
>
>Se pubblichi un frammento di contenuto per il quale il modello non è ancora stato pubblicato, questo sarà segnalato in un elenco di selezione e il modello verrà pubblicato con il frammento.

I frammenti di contenuto devono essere pubblicati per l’utilizzo nell’ambiente di pubblicazione. Possono essere pubblicati:

* Dopo la creazione; dal **[!UICONTROL Risorse]** console.
* Quando [pubblicare una pagina che utilizza il frammento](/help/sites-authoring/content-fragments.md#publishing); il frammento viene elencato nei riferimenti di pagina.

>[!CAUTION]
>
>Dopo la pubblicazione e/o il riferimento a un frammento, AEM mostra un avviso quando un autore riapre il frammento per la modifica. L’avviso informa l’utente che le modifiche al frammento avranno effetto anche sulle pagine a cui si fa riferimento.

## Eliminazione di un frammento {#deleting-a-fragment}

Per eliminare un frammento:

1. Nella console **[!UICONTROL Risorse]** passa alla posizione del frammento di contenuto.
1. Seleziona il frammento.

   >[!NOTE]
   >
   >L’azione **[!UICONTROL Elimina]** non è disponibile come azione rapida.

1. Seleziona **[!UICONTROL Elimina]** dalla barra degli strumenti.
1. Conferma l’azione **[!UICONTROL Elimina]**.

   >[!CAUTION]
   >
   >Se in una pagina è già presente un riferimento al frammento, verrà visualizzato un messaggio di avviso e sarà necessario confermare che si desidera procedere con **[!UICONTROL Forza eliminazione]**. Il frammento, insieme al relativo componente di frammento di contenuto, verrà eliminato da tutte le pagine di contenuto.
