---
title: Gestione dei frammenti di contenuto
seo-title: Gestione dei frammenti di contenuto
description: I frammenti di contenuto sono memorizzati come risorse e sono gestiti principalmente dalla console Risorse.
seo-description: I frammenti di contenuto sono memorizzati come risorse e sono gestiti principalmente dalla console Risorse.
uuid: 0659cf03-b4e8-4b8b-bec7-0082f980115a
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: da8f968b-91cc-45a8-ae4b-757b4f840b8e
translation-type: tm+mt
source-git-commit: 5ba23738118d7944026f405110e25b6a7f90866b
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 11%

---


# Gestione dei frammenti di contenuto {#managing-content-fragments}

>[!CAUTION]
>
>Alcune funzionalità per i frammenti di contenuto richiedono l&#39;applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o versioni successive](/help/release-notes/sp-release-notes.md).

I frammenti di contenuto sono memorizzati come **[!UICONTROL Risorse]**, pertanto vengono gestiti principalmente dalla console **[!UICONTROL Risorse]**.

>[!NOTE]
>
>I frammenti di contenuto vengono quindi utilizzati con le pagine di authoring; consultate [Authoring delle pagine con frammenti di contenuto](/help/sites-authoring/content-fragments.md).

## Creazione di frammenti di contenuto {#creating-content-fragments}

### Creazione di un modello di contenuto {#creating-a-content-model}

[La ](content-fragments-models.md) modellizzazione dei frammenti di contenuto può essere abilitata e creata prima della creazione di frammenti di contenuto con contenuto strutturato.

>[!NOTE]
>
>Per ulteriori informazioni sui modelli, vedere [Sviluppo di frammenti di contenuto](/help/sites-developing/customizing-content-fragments.md); utilizzato per i frammenti di contenuto semplici.

### Creazione di un frammento di contenuto {#creating-a-content-fragment}

Il metodo di creazione di un frammento di contenuto è sostanzialmente lo stesso per i frammenti semplici e strutturati:

1. Passa alla cartella **[!UICONTROL Risorse]** in cui desideri creare il frammento.
1. Per aprire la procedura guidata, seleziona **[!UICONTROL Crea]**, quindi **[!UICONTROL Frammento di contenuto]**.
1. Il primo passaggio della procedura guidata richiede di specificare la base del nuovo frammento.

   * Può trattarsi di:

      * [Modello](/help/sites-developing/content-fragment-templates.md) , ad esempio  **[!UICONTROL Frammento semplice]**
      * [Modello](content-fragments-models.md) : utilizzato per creare un frammento che richiede contenuto strutturato; ad esempio, il modello  **** Airportmodel
   * Vengono visualizzati tutti i modelli disponibili.

   Dopo la selezione, utilizzare **[!UICONTROL Next]** per continuare.

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

         il nome; verrà utilizzato per formare l&#39;URL.

         Obbligatorio; viene derivato automaticamente dal titolo, ma può essere aggiornato.


1. Seleziona **[!UICONTROL Crea]** per completare l’azione, quindi **[!UICONTROL Apri]** il frammento per la modifica oppure tornare alla console facendo clic su **[!UICONTROL Fine]**.

## Azioni per un frammento di contenuto {#actions-for-a-content-fragment}

Nella console **[!UICONTROL Risorse]** sono disponibili diverse azioni per i frammenti di contenuto:

* Dalla barra degli strumenti; dopo aver selezionato il frammento, sono disponibili tutte le azioni appropriate.
* Come [azioni rapide](/help/sites-authoring/basic-handling.md#quick-actions); un sottoinsieme di azioni disponibili per le singole schede frammento.

![cfm-6420-17](assets/cfm-6420-17.png)

Selezionare il frammento per visualizzare la barra degli strumenti con le azioni applicabili:

* **[!UICONTROL Scarica]**

   * Salvare il frammento come file ZIP; potete definire se includere elementi, varianti, metadati.

* **[!UICONTROL Crea]**
* **[!UICONTROL Pagamento]**
* **[!UICONTROL Proprietà]**

   * Consente di visualizzare e/o modificare i metadati del frammento.

* **[!UICONTROL Modifica]**

   * Consente di [aprire il frammento per la modifica di contenuto](content-fragments-variations.md) con i relativi elementi, varianti, contenuto associato e metadati.

* **[!UICONTROL Gestisci i tag]**
* **[!UICONTROL Alla raccolta]**

   * Aggiungere il frammento a una raccolta.
   * Questa operazione può essere eseguita anche quando [associando una raccolta al frammento](content-fragments-assoc-content.md#adding-associated-content).

* **[!UICONTROL Copia/Incolla]**
* **[!UICONTROL Sposta]**
* **[!UICONTROL Pubblicazione rapida]**
* **[!UICONTROL Gestisci pubblicazione]**
* **[!UICONTROL Elimina]**

>[!NOTE]
>
>Molte di queste sono [azioni standard per Assets](managing-assets-touch-ui.md) e/o l&#39;app [desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

## Apertura dell&#39;Editor frammento {#opening-the-fragment-editor}

Per aprire il frammento per la modifica:

>[!CAUTION]
>
>Per modificare un frammento di contenuto è necessario disporre di [le autorizzazioni appropriate](/help/sites-developing/customizing-content-fragments.md#asset-permissions). In caso di problemi, contattate l&#39;amministratore di sistema.

1. Utilizzate la console **[!UICONTROL Risorse]** per individuare la posizione del frammento di contenuto.
1. Aprire il frammento per la modifica:

   * Toccando o facendo clic sul collegamento del frammento o del frammento (a seconda della vista della console).
   * Selezionare il frammento, quindi **[!UICONTROL Modifica]** dalla barra degli strumenti.

   Viene aperto l’editor frammento:

   ![cfm-6420-18](assets/cfm-6420-18.png)

   >[!NOTE]
   >
   >1. Viene visualizzato un messaggio se al frammento è già fatto riferimento in una pagina di contenuto.
      >
      >
   2. Il pannello laterale può essere nascosto o visualizzato utilizzando l&#39;icona **[!UICONTROL Attiva/disattiva pannello laterale]**.


1. Per spostarsi tra le tre modalità, usate le icone nel pannello laterale:

   * Variazioni: [Modifica dei contenuti](#editing-the-content-of-your-fragment) e [Gestione delle varianti](#creating-and-managing-variations-within-your-fragment)
   * [Annotazioni](content-fragments-variations.md#annotating-a-content-fragment)
   * [Contenuto associato](#associating-content-with-your-fragment)
   * [Metadati](#viewing-and-editing-the-metadata-properties-of-your-fragment)

   ![cfm-10](assets/cfm-10.png)

1. Dopo aver apportato le modifiche, utilizzare **[!UICONTROL Save]** o **[!UICONTROL Cancel]** come necessario.

   >[!NOTE]
   >
   >Sia l’azione **[!UICONTROL Salva]** che **[!UICONTROL Annulla]** causeranno l’uscita dall’editor. Per informazioni complete sul funzionamento di entrambe le opzioni dei frammenti di contenuto, consulta la sezione [Salva, Annulla e Versioni](#save-cancel-and-versions).

## Salva, Annulla e Versioni {#save-cancel-and-versions}

>[!NOTE]
>
>È inoltre possibile creare [versioni, confrontarle e ripristinarle dalla Timeline](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments).

L&#39;editor dispone di due opzioni:

* **[!UICONTROL Salva]**

   Salvare le modifiche più recenti e uscire dall&#39;editor.

   >[!CAUTION]
   >
   >Per modificare un frammento di contenuto è necessario disporre di [le autorizzazioni appropriate](/help/sites-developing/customizing-content-fragments.md#asset-permissions). In caso di problemi, contattate l&#39;amministratore di sistema.

   >[!NOTE]
   >
   >È possibile restare nell&#39;editor, apportando una serie di modifiche, prima di selezionare **[!UICONTROL Save]**.

   >[!CAUTION]
   >
   >Oltre a salvare semplicemente le modifiche, **[!UICONTROL Save]** aggiorna anche tutti i riferimenti e assicura che il dispatcher venga scaricato come necessario. L&#39;elaborazione di queste modifiche può richiedere del tempo. A causa di ciò, può verificarsi un impatto sulle prestazioni di un sistema di grandi dimensioni/complesso/pesantemente caricato.
   >
   >
   >Tenere presente questo aspetto quando si utilizza **[!UICONTROL Save]** e quindi si reinserisce rapidamente nell&#39;editor frammenti per apportare e salvare ulteriori modifiche.

* **[!UICONTROL Annulla]**

   Uscirà dall’editor senza salvare le modifiche più recenti.

Durante la modifica del frammento di contenuto AEM vengono create automaticamente delle versioni che garantiscono il ripristino del contenuto precedente in caso di **[!UICONTROL Annulla]** modifiche:

1. Quando un frammento di contenuto viene aperto per la modifica AEM verifica l&#39;esistenza del token basato su cookie che indica se esiste una *sessione di modifica*:

   1. Se il token viene trovato, il frammento viene considerato parte della sessione di modifica esistente.
   1. Se il token è *not* disponibile e l&#39;utente avvia la modifica del contenuto, viene creata una versione e viene inviato un token per questa nuova sessione di modifica al client, dove viene salvato in un cookie.

1. In presenza di una sessione di modifica *attiva*, il contenuto in corso di modifica viene salvato automaticamente ogni 600 secondi (impostazione predefinita).

   >[!NOTE]
   >
   >L&#39;intervallo di salvataggio automatico è configurabile utilizzando il meccanismo `/conf`.
   >
   >Valore predefinito, vedere:
   >
   >`/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

1. Se l&#39;utente seleziona l&#39;opzione **[!UICONTROL Annulla]** per la modifica, la versione creata all&#39;inizio della sessione di modifica viene ripristinata e il token viene rimosso per terminare la sessione di modifica.
1. Se l&#39;utente seleziona **[!UICONTROL Salva]** le modifiche, gli elementi/varianti aggiornati vengono memorizzati e il token viene rimosso per terminare la sessione di modifica.

## Modifica del contenuto del frammento {#editing-the-content-of-your-fragment}

Dopo aver aperto il frammento, è possibile utilizzare la scheda [Variazioni](content-fragments-variations.md) per creare il contenuto.

## Creazione e gestione di varianti all&#39;interno del frammento {#creating-and-managing-variations-within-your-fragment}

Dopo aver creato il contenuto principale, potete creare e gestire [Variazioni](content-fragments-variations.md) di tale contenuto.

## Associazione di contenuto al frammento {#associating-content-with-your-fragment}

È inoltre possibile associare [contenuto](content-fragments-assoc-content.md) a un frammento. Questa funzione consente una connessione in modo che le risorse (ad es. immagini) possano essere (facoltativamente) utilizzate con il frammento quando questo viene aggiunto a una pagina di contenuto.

## Visualizzazione e modifica dei metadati (proprietà) del frammento {#viewing-and-editing-the-metadata-properties-of-your-fragment}

È possibile visualizzare e modificare le proprietà di un frammento utilizzando la scheda [[!UICONTROL Metadati]](content-fragments-metadata.md).

## Timeline per frammenti di contenuto {#timeline-for-content-fragments}

Oltre alle opzioni standard, [Timeline](managing-assets-touch-ui.md#timeline) fornisce informazioni e azioni specifiche per i frammenti di contenuto:

* Visualizzazione di informazioni su versioni, commenti e annotazioni
* Azioni per le versioni

   * **[[!UICONTROL Ripristina questa versione]](#reverting-to-a-version)**  (selezionare un frammento esistente, quindi una versione specifica)
   * **[[!UICONTROL Confronta con corrente]](#comparing-fragment-versions)**  (selezionare un frammento esistente, quindi una versione specifica)
   * Aggiungere un **[!UICONTROL Label]** e/o un **[!UICONTROL Commento]** (selezionare un frammento esistente, quindi una versione specifica)
   * **[!UICONTROL Salva come versione]**  (selezionare un frammento esistente, quindi la freccia su nella parte inferiore della timeline)

* Azioni per le annotazioni

   * **[!UICONTROL Elimina]**

>[!NOTE]
>
>I commenti sono:
>
>* Funzionalità standard per tutte le risorse
>* Realizzato nella timeline
>* Relativa alla risorsa frammento

>
>
Le annotazioni (per i frammenti di contenuto) sono:
>
>* Inserito nell’editor frammento
>* Specifica per un segmento di testo selezionato all&#39;interno del frammento


Esempio:

![cfm-6420-19](assets/cfm-6420-19.png)

## Confronto delle versioni dei frammenti {#comparing-fragment-versions}

L&#39;azione **[!UICONTROL Confronta con corrente]** è disponibile dalla [[!UICONTROL Timeline]](https://helpx.adobe.com/experience-manager/6-3/assets/using/content-fragments-managing.html#timeline-for-content-fragments) dopo aver selezionato una versione specifica.

Verrà aperto:

* la versione **[!UICONTROL Current]** (più recente) (sinistra)

* la versione selezionata **v&lt;*x.y*>** (destra)

Vengono visualizzati affiancati, dove:

* Eventuali differenze sono evidenziate

   * Testo eliminato - rosso
   * Testo inserito - verde
   * Testo sostituito - blu

* L’icona a schermo intero consente di aprire una delle due versioni da sola; quindi tornate alla visualizzazione parallela
* È possibile **[!UICONTROL Ripristinare]** la versione specifica
* **[!UICONTROL Ti]** restituiranno la console

>[!NOTE]
>
>Non è possibile modificare il contenuto del frammento durante il confronto dei frammenti.

![cfm-6420-20](assets/cfm-6420-20.png)

## Ripristino della versione {#reverting-to-a-version}

È possibile ripristinare una versione specifica del frammento:

* Direttamente dalla [[!UICONTROL Timeline]](content-fragments-managing.md#timeline-for-content-fragments).

   Selezionate la versione richiesta, quindi l&#39;azione **[!UICONTROL Ripristina questa versione]**.

* Mentre [confrontando una versione con la versione corrente](content-fragments-managing.md#comparing-fragment-versions) è possibile **[!UICONTROL Ripristinare]** la versione selezionata.

## Pubblicazione e riferimento a un frammento {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Se il frammento è basato su un modello, verificare che il modello [sia stato pubblicato](content-fragments-models.md#publishing-a-content-fragment-model).
>
>Se si pubblica un frammento di contenuto per il quale il modello non è ancora stato pubblicato, verrà visualizzato un elenco di selezione e il modello verrà pubblicato insieme al frammento.

I frammenti di contenuto devono essere pubblicati per l’utilizzo nell’ambiente di pubblicazione. Possono essere pubblicati:

* Dopo la creazione; dalla console **[!UICONTROL Risorse]**.
* Quando si [pubblica una pagina che utilizza il frammento](/help/sites-authoring/content-fragments.md#publishing); il frammento verrà elencato nei riferimenti di pagina.

>[!CAUTION]
>
>Dopo aver pubblicato e/o fatto riferimento a un frammento, AEM viene visualizzato un avviso quando un autore riapre il frammento per la modifica. In questo modo viene segnalato che le modifiche apportate al frammento avranno effetto anche sulle pagine di riferimento.

## Eliminazione di un frammento {#deleting-a-fragment}

Per eliminare un frammento:

1. Nella console **[!UICONTROL Risorse]** individuate la posizione del frammento di contenuto.
1. Selezionare il frammento.

   >[!NOTE]
   >
   >L&#39;azione **[!UICONTROL Elimina]** non è disponibile come azione rapida.

1. Selezionare **[!UICONTROL Elimina]** dalla barra degli strumenti.
1. Confermare l&#39;azione **[!UICONTROL Elimina]**.

   >[!CAUTION]
   >
   >Se in una pagina è già presente un riferimento al frammento, verrà visualizzato un messaggio di avviso e sarà necessario confermare che si desidera procedere con **[!UICONTROL Forza eliminazione]**. Il frammento, insieme al relativo componente di frammento di contenuto, verrà eliminato da tutte le pagine di contenuto.

