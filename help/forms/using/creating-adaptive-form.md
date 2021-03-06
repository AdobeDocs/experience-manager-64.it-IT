---
title: Creazione di un modulo adattivo
seo-title: Creazione di un modulo adattivo
description: Come creare un modulo adattivo utilizzando AEM Forms. I moduli adattivi sono moduli HTML5 reattivi che semplificano la raccolta e l’elaborazione delle informazioni.
seo-description: Come creare un modulo adattivo utilizzando AEM Forms. I moduli adattivi sono moduli HTML5 reattivi che semplificano la raccolta e l’elaborazione delle informazioni.
uuid: 444f461a-9e88-4385-b5ee-e985067ab7bc
content-type: reference
topic-tags: author
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f06b8cb2-6f98-465f-beec-1e91e3f45707
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2044'
ht-degree: 0%

---


# Creazione di un modulo adattivo {#creating-an-adaptive-form}

## <strong>Creare un modulo adattivo</strong> {#strong-create-an-adaptive-form-strong}

Per creare un modulo adattivo, effettua le seguenti operazioni.

1. Accedi all’istanza di authoring di AEM Forms all’indirizzo `https://[server]:[port]/<custom-context-if-any>.`

   ```
   
   ```

1. Immetti le credenziali nella pagina di accesso AEM.

   Dopo aver effettuato l’accesso, tocca **[!UICONTROL Adobe Experience Manager > Forms > Forms e documenti]** nell’angolo in alto a sinistra.

   >[!NOTE]
   >
   >Per un&#39;installazione predefinita, l&#39;accesso è `admin` e la password è `admin`.

1. Tocca **[!UICONTROL Crea]** e seleziona **[!UICONTROL Modulo adattivo]**.
1. Viene visualizzata un’opzione per selezionare un modello. Per ulteriori informazioni sui modelli, vedere [Modelli di moduli adattivi](/help/forms/using/creating-adaptive-form.md#p-adaptive-form-templates-p). Toccare un modello per selezionarlo e toccare Avanti.
1. Viene visualizzata l’opzione &quot;Aggiungi proprietà&quot;. Specifica i valori per i seguenti campi di proprietà. I campi Titolo e Nome sono obbligatori:

   * **[!UICONTROL Titolo:]** specifica il nome visualizzato del modulo. Il titolo consente di identificare il modulo nell’interfaccia utente di AEM Forms.
   * **[!UICONTROL Nome:]** specifica il nome del modulo. Nel repository viene creato un nodo con il nome specificato. Quando si inizia a digitare un titolo, il valore del campo nome viene generato automaticamente. È possibile modificare il valore suggerito. Il campo name può includere solo caratteri alfanumerici, trattini e caratteri di sottolineatura. Tutti gli input non validi vengono sostituiti con un trattino.
   * **[!UICONTROL Descrizione:]** specifica le informazioni dettagliate sul modulo.
   * **[!UICONTROL Tag:]** specifica i tag per identificare in modo univoco il modulo adattivo. I tag consentono di cercare il modulo. Per creare i tag, digita nuovi nomi di tag nella casella **Tag** .

1. È possibile creare un modulo adattivo basato su uno dei seguenti modelli di modulo:

   * [Modello dati modulo](#fdm)
   * [Modello di modulo XFA](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)
   * [Schema XML o JSON](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)
   * Nessuno o senza un modello di modulo

   Puoi configurarli dalla scheda **[!UICONTROL Modello di modulo]** nella pagina **[!UICONTROL Aggiungi proprietà]** . Per impostazione predefinita, il modello di modulo selezionato è **[!UICONTROL Nessuno]**.

1. Tocca **Crea**. Viene creato un modulo adattivo e viene visualizzata una finestra di dialogo per aprire il modulo per la modifica.

   Dopo aver specificato tutte le proprietà, fai clic su **[!UICONTROL Crea]**. Viene creato un modulo adattivo e viene visualizzata una finestra di dialogo per aprire il modulo per la modifica.

   Dopo aver specificato tutte le proprietà, fai clic su **[!UICONTROL Crea]**. Viene creato un modulo adattivo e viene visualizzata una finestra di dialogo per aprire il modulo per la modifica.

1. Tocca **[!UICONTROL Apri]** per aprire il modulo appena creato in una nuova scheda. Il modulo viene aperto per la modifica e visualizza il contenuto disponibile nel modello. Visualizza inoltre la barra laterale per personalizzare il modulo appena creato in base alle esigenze.

   In base al tipo di modulo adattivo, gli elementi del modulo presenti nel modello di modulo XFA, nello schema XML o nello schema JSON associati vengono visualizzati nella scheda **[!UICONTROL Oggetti modello dati]** della scheda **[!UICONTROL Browser contenuti]** nella barra laterale. Puoi anche trascinare questi elementi per creare il modulo adattivo.

   Per informazioni sull’interfaccia per la creazione di moduli adattivi e sui componenti disponibili, consulta [Introduzione alla creazione di moduli adattivi](/help/forms/using/introduction-forms-authoring.md).

   >[!NOTE]
   >
   >Consente alle finestre a comparsa nel browser di aprire il modulo appena creato in una nuova scheda.

## Creare un modulo adattivo basato su un modello di dati modulo {#fdm}

[L’](/help/forms/using/data-integration.md) integrazione dei dati di AEM Forms consente di integrare più origini dati e di riunire le relative entità e servizi per creare un modello di dati del modulo. È un&#39;estensione dello schema JSON. È possibile utilizzare un modello dati modulo per creare un modulo adattivo. Le entità o gli oggetti modello dati configurati in un modello dati modulo sono disponibili come oggetti modello dati per la creazione di moduli. Sono associati alle rispettive origini dati e vengono utilizzati per precompilare un modulo e riscrivere i dati inviati alle rispettive origini dati. È inoltre possibile richiamare servizi configurati in un modello dati modulo utilizzando regole del modulo adattivo.

Per utilizzare un modello dati modulo per la creazione di un modulo adattivo:

1. Nella scheda Modello modulo della schermata Aggiungi proprietà, selezionare **[!UICONTROL Modello dati modulo]** nell’elenco a discesa **[!UICONTROL Seleziona da]**.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Tocca per espandere **[!UICONTROL Seleziona modello dati modulo]**. Sono elencati tutti i modelli di dati modulo disponibili.

   Seleziona un modello dati da.

   ![create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>È inoltre possibile modificare il modello dati del modulo per un modulo adattivo. Per passaggi dettagliati, vedere [Modifica proprietà modello di modulo di un modulo adattivo](#edit-form-model).

## Creare un modulo adattivo basato su un modello di modulo XFA {#create-an-adaptive-form-based-on-an-xfa-form-template}

È possibile riutilizzare i modelli di modulo XFA per creare moduli adattivi. Per riutilizzare, caricare e associare un modello di modulo XFA a un modulo adattivo. Gli elementi del modello di modulo (modulo XFA) sono resi disponibili per l’utilizzo in Content Finder al momento della creazione di moduli adattivi. Da Content Finder è possibile trascinare gli elementi del modello di modulo sul modulo.

>[!NOTE]
>
>[Carica il ](/help/forms/using/get-xdp-pdf-documents-aem.md) modello di modulo XFA in AEM Forms prima di iniziare a creare un modulo adattivo basato sul modello di modulo.

Per utilizzare un modello di modulo XFA come modello di modulo per il modulo adattivo, procedi come segue:

1. Nella pagina **[!UICONTROL Aggiungi proprietà]**, apri la scheda **[!UICONTROL Modello di modulo]** .
1. Nella scheda Modello modulo, dall’elenco a discesa, selezionare **[!UICONTROL Modelli di modulo]**. Sono elencati per selezione tutti i modelli di modulo caricati nell’archivio tramite l’interfaccia utente di AEM Forms. Seleziona un modello dall’elenco.

   ![Associare il modello di modulo XFA a un modulo adattivo](assets/form_model_xfa_associate.png)
   **Figura:** *selezione di un modello di modulo*

   >[!NOTE]
   >
   >È inoltre possibile modificare il modello di modulo per un modulo adattivo. Per passaggi dettagliati, vedere [Modifica proprietà modello di modulo di un modulo adattivo](#edit-form-model).

## Creare un modulo adattivo basato su uno schema XML o JSON {#create-an-adaptive-form-based-on-xml-or-json-schema}

Gli schemi XML e JSON rappresentano la struttura in cui i dati vengono prodotti o utilizzati dal sistema back-end della tua organizzazione. È possibile associare uno schema a un modulo adattivo e utilizzarne gli elementi per aggiungere contenuto dinamico al modulo adattivo. Gli elementi dello schema sono disponibili nella scheda Oggetto modello dati del browser del contenuto per la creazione di moduli adattivi. È possibile trascinare gli elementi dello schema per creare il modulo.

Per informazioni su come progettare uno schema XML o JSON per la creazione di moduli adattivi, consulta i documenti seguenti.

* [Creazione di moduli adattivi tramite schema XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Creazione di moduli adattivi tramite lo schema JSON](/help/forms/using/adaptive-form-json-schema-form-model.md)

Per utilizzare lo schema XML o JSON come modello di modulo per un modulo adattivo, procedi come segue:

1. Nel passaggio **[!UICONTROL Aggiungi proprietà]** della pagina di creazione di moduli adattivi, tocca la scheda **[!UICONTROL Modello di modulo]** .
1. Nella scheda Modello modulo, selezionare **[!UICONTROL Schema]** dal campo a discesa **[!UICONTROL Seleziona da]**.

1. Tocca **[!UICONTROL Seleziona schema]** ed effettua una delle seguenti operazioni:

   * **[!UICONTROL Caricamento dal disco]** : seleziona questa opzione e tocca Carica definizione schema per sfogliare e caricare uno schema XML o uno schema JSON dal file system. Il file di schema caricato si trova con il modulo e non è accessibile ad altri moduli adattivi.
   * **[!UICONTROL Ricerca nel repository]** : selezionare questa opzione per selezionare dall&#39;elenco dei file di definizione dello schema disponibili nel repository. Selezionare il file di schema XML o JSON come modello di modulo. Lo schema selezionato sarà associato al modulo mediante riferimento e sarà accessibile per l’uso in altri moduli adattivi.

   >[!CAUTION]
   >
   >Assicurati che il nome del file dello schema JSON termini con **.schema.json**. Ad esempio: mySchema.schema.json

   ![Selezione dello schema XML o JSON](assets/upload-schema.png)
   **Figura:** *selezione dello schema XML o JSON*

1. (Solo per schema XML) Dopo aver selezionato o caricato uno schema XML, specificare un elemento principale del file XSD selezionato da mappare con il modulo adattivo.

   ![Selezione dell&#39;elemento principale XSD](assets/xsd-root-element.png)
   **Figura:** *selezione dell&#39;elemento principale XSD*

>[!NOTE]
>
>È inoltre possibile modificare lo schema di un modulo adattivo. Per passaggi dettagliati, vedere [Modifica proprietà modello di modulo di un modulo adattivo](#edit-form-model).

## Modelli di modulo adattivo {#adaptive-form-templates}

Un modello fornisce una struttura di base e definisce l’aspetto (layout e stili) di un modulo adattivo. Dispone di componenti preformattati contenenti determinate proprietà e struttura del contenuto. Con AEM Forms sono disponibili alcuni modelli di modulo adattivi. Per ottenere il pacchetto completo dei modelli, inclusi i modelli avanzati, devi installare il pacchetto dei componenti aggiuntivi AEM Forms. Per ulteriori informazioni, consulta [Installazione del pacchetto aggiuntivo di AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).

Inoltre, puoi utilizzare l’editor modelli per creare modelli personalizzati. Per ulteriori informazioni sull&#39;utilizzo dei modelli, vedere [Modelli di moduli adattivi](/help/forms/using/template-editor.md).

>[!NOTE]
>
>Quando si apre un modulo adattivo creato utilizzando il modello avanzato per la modifica, viene visualizzato un messaggio di errore. Il modello avanzato dispone di un componente Passaggio firma e Adobe Sign è abilitato per impostazione predefinita. Crea e seleziona una [configurazione cloud Adobe Sign](/help/forms/using/adobe-sign-integration-adaptive-forms.md) e [configura un firmatario](/help/forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) per risolvere l&#39;errore.

## Modificare le proprietà del modello di modulo di un modulo adattivo {#edit-form-model}

I moduli adattivi vengono creati senza un modello di modulo (utilizzando l’opzione Nessuno per il modello di modulo) o utilizzando un modello di modulo, ad esempio un modello di modulo, uno schema XML o uno schema JSON o un modello di dati modulo. È possibile modificare il modello di modulo per un modulo adattivo da Nessuno a un altro modello di modulo. Per i moduli adattivi basati su un modello di modulo, è possibile scegliere un altro modello di modulo, schema XML, schema JSON o modello di dati modulo per lo stesso modello di modulo. Tuttavia, non è possibile passare da un modello di modulo all’altro.

1. Seleziona il modulo adattivo e tocca l’icona **Proprietà** .
1. Apri la scheda **[!UICONTROL Modello di modulo]** ed effettua una delle seguenti operazioni.

   * Se il modulo adattivo non dispone di un modello di modulo, è possibile scegliere un altro modello di modulo e quindi selezionare un modello di modulo, uno schema XML o JSON o un modello di dati modulo.
   * Se il modulo adattivo è basato su un modello di modulo, è possibile scegliere un altro modello di modulo, schema XML o JSON o modello di dati modulo per lo stesso modello di modulo.

1. Tocca **[!UICONTROL Salva]** per salvare le proprietà.

## Salvataggio automatico di un modulo adattivo {#auto-save-an-adaptive-form}

Per impostazione predefinita, il contenuto di un modulo adattivo viene salvato in seguito a un’azione dell’utente, ad esempio premendo il pulsante salva. È inoltre possibile configurare un modulo adattivo per iniziare automaticamente a salvare il contenuto in base a un evento o a un intervallo di tempo. L’opzione di salvataggio automatico è utile in:

* Salvataggio automatico del contenuto per utenti anonimi e connessi
* Salvataggio del contenuto di un modulo senza o con intervento minimo dell’utente
* Inizio del salvataggio del contenuto di un modulo in base a un evento utente
* Salvataggio ripetuto del contenuto di un modulo dopo un intervallo di tempo specificato

### Abilita salvataggio automatico per un modulo adattivo {#enable-auto-save-for-an-adaptive-form}

Per impostazione predefinita, l’opzione di salvataggio automatico non è abilitata. È possibile abilitare l’opzione di salvataggio automatico dalla scheda Salvataggio automatico di un modulo adattivo. La scheda Salvataggio automatico fornisce anche diverse altre opzioni di configurazione. Esegui i seguenti passaggi per abilitare e configurare l’opzione di salvataggio automatico per un modulo adattivo:

1. Per accedere alla sezione di salvataggio automatico nelle proprietà, seleziona un componente, quindi tocca ![livello campo](assets/field-level.png) > **[!UICONTROL Contenitore modulo adattivo]**, quindi tocca ![cmppr](assets/cmppr.png).
1. Nella sezione **[!UICONTROL Salvataggio automatico]**, **[!UICONTROL Abilita]** l&#39;opzione di salvataggio automatico.
1. Nella casella **[!UICONTROL Evento modulo adattivo]**, specificare 1 o TRUE per iniziare automaticamente il salvataggio del modulo quando il modulo viene caricato nel browser. È inoltre possibile specificare un&#39;espressione condizionale per un evento che, quando attivato e restituito vero, inizia a salvare il contenuto del modulo.
1. Specifica il trigger. Il salvataggio automatico viene attivato in base alla configurazione. Le opzioni disponibili sono:

   * **[!UICONTROL Basato su tempo:]** seleziona l’opzione per iniziare a salvare il contenuto in base a un intervallo di tempo specifico.
   * **[!UICONTROL Basato su evento:]** seleziona l’opzione per iniziare a salvare il contenuto in base all’attivazione di un evento.

   Quando selezioni un trigger, la casella Configurazione strategia è abilitata. La casella Configurazione strategia consente di:

   * Specificare un intervallo di tempo se si seleziona il trigger **[!UICONTROL Time based]**.
   * Specifica un nome evento se selezioni il trigger **[!UICONTROL Basato su evento]** .

   Puoi anche creare e aggiungere all’elenco una strategia personalizzata. Per informazioni dettagliate, vedere [Implementare una strategia personalizzata per l&#39;salvataggio automatico dei moduli](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Solo salvataggio automatico basato su tempo) Esegui i seguenti passaggi per configurare le opzioni per l’salvataggio automatico basato su tempo.

   1. Nella casella **[!UICONTROL Salvataggio automatico in questo intervallo]**, specificare l&#39;intervallo di tempo in secondi. Il modulo viene salvato ripetutamente dopo la scadenza del numero di secondi specificato nella casella Intervallo.

1. (Solo salvataggio automatico basato su eventi) Esegui i seguenti passaggi per configurare le opzioni per il salvataggio automatico basato su eventi.

   1. Nella casella **Salvataggio automatico dopo questo evento**, specificare un evento [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html). Il modulo viene salvato ogni volta che l’espressione restituisce TRUE.

1. (Facoltativo) Per salvare automaticamente il contenuto per gli utenti anonimi, selezionare l&#39;opzione **Abilita salvataggio automatico per utenti anonimi** e fare clic su **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Affinché l’opzione di salvataggio automatico funzioni per gli utenti anonimi, è necessario configurare il servizio di configurazione comune di Forms per consentire a tutti gli utenti di visualizzare in anteprima, verificare e firmare i moduli.
   >
   >Per configurare il servizio, accedi AEM configurazione della console Web in `https://[server]:[host]/system/console/configMgr` e modifica il **[!UICONTROL Servizio di configurazione comune Forms]** per scegliere l&#39;opzione **[!UICONTROL Tutti gli utenti]** nel campo **[!UICONTROL Consenti]** e salvare la configurazione.