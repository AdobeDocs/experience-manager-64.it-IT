---
title: Genera l’anteprima HTML5 di un modulo XDP
seo-title: Genera l’anteprima HTML5 di un modulo XDP
description: La scheda Anteprima HTML in Progettazione LiveCycli può essere utilizzata per visualizzare l’anteprima dei moduli così come sono visualizzati in un browser.
seo-description: La scheda Anteprima HTML in Progettazione LiveCycli può essere utilizzata per visualizzare l’anteprima dei moduli così come sono visualizzati in un browser.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 16%

---


# Genera l’anteprima HTML5 di un modulo XDP {#generate-html-preview-of-an-xdp-form}

Durante la progettazione di un modulo in AEM Forms Designer, oltre a visualizzare l’anteprima del rendering PDF di un modulo, è anche possibile visualizzarne l’anteprima in anteprima il rendering HTML5. È possibile utilizzare la scheda **Anteprima HTML** per visualizzare in anteprima un modulo così come apparirebbe in un browser.

## Abilitare l’anteprima HTML per i moduli XDP in Designer {#html-preview-of-forms-in-forms-designer}

Per consentire a Designer di generare un’anteprima HTML dei moduli XDP, esegui le seguenti configurazioni:

* Configurare il servizio di autenticazione Apache Sling
* Disattiva modalità protetta
* Fornire i dettagli del server AEM Forms

### Configurare il servizio di autenticazione Apache Sling {#configure-apache-sling-authentication-service}

1. Vai a `https://[server]:[port]/system/console/configMgr` su AEM Forms in esecuzione su OSGi o

   `https://[server]:[port]/lc/system/console/configMgr` su AEM Forms in esecuzione su JEE.

1. Individua e fai clic su **Configurazione di Apache Sling Authentication Service** per aprirla in modalità di modifica.

1. A seconda che AEM Forms sia in esecuzione su OSGi o JEE, aggiungi quanto segue nel campo **Requisiti di autenticazione** :

   * AEM Forms su JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM Forms su OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Non copiare e incollare il valore specificato nel campo Requisiti di autenticazione in quanto potrebbe danneggiare i caratteri speciali nel valore. Digita invece il valore specificato nel campo .

1. Specificare un nome utente e una password nei campi **[!UICONTROL Nome utente anonimo]** e **[!UICONTROL Password utente anonima]**, rispettivamente. Le credenziali specificate vengono utilizzate per gestire l&#39;autenticazione anonima e consentire l&#39;accesso agli utenti anonimi.
1. Fai clic su **Salva** per salvare la configurazione.

### Disattiva modalità protetta {#disable-protected-mode}

Per impostazione predefinita, la [modalità protetta](/help/forms/using/get-xdp-pdf-documents-aem.md) è attivata. Mantenetela abilitata per gli ambienti di produzione. È possibile disattivarlo per un ambiente di sviluppo per visualizzare in anteprima HTML5 Forms nella progettazione. Esegui i seguenti passaggi per disattivarlo:

1. Accedi a AEM console Web come amministratore.

   * L&#39;URL per AEM Forms su OSGi è `https://[server]:[port]/system/console/configMgr`
   * L&#39;URL per AEM Forms su JEE è `https://[server]:[port]/lc/system/console/configMgr`

1. Apri **[!UICONTROL Configurazioni Forms mobili]** per la modifica.
1. Deseleziona l&#39;opzione **[!UICONTROL Modalità protetta]** e fai clic su **[!UICONTROL Salva]**.

### Fornire i dettagli del server AEM Forms {#provide-details-of-aem-forms-server}

1. In Designer, passare a **Strumenti** > **Opzioni**.
1. Nella finestra Opzioni, selezionare la pagina **Opzioni server**, fornire i seguenti dettagli e fare clic su **OK**.

   * **URL** server: URL del server AEM Forms.
   * **Numero** di porta HTTP: AEM porta server. Il valore predefinito è 4502.
   * **Contesto anteprima HTML:** percorso del profilo per il rendering dei moduli XFA. I seguenti profili predefiniti vengono utilizzati per visualizzare l’anteprima del modulo in Designer. Tuttavia, puoi anche specificare il percorso di un profilo personalizzato.

      * `/content/xfaforms/profiles/default.html` (AEM Forms su OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms su JEE)
   * **Contesto di Forms Manager:** percorso contestuale in cui viene distribuita l’interfaccia utente di Forms Manager. I valori predefiniti sono:

      * `/aem/forms` (AEM Forms su OSGi)
      * `/lc/forms` (AEM Forms su JEE)

   **Nota:** *assicurati che il server AEM Forms sia in esecuzione. L&#39;anteprima HTML si connette al server CRX per* generare *un&#39;anteprima.*

   ![Opzioni di AEM Forms Designer  ](assets/server_options.png)

   Opzioni di AEM Forms Designer

1. Per visualizzare l’anteprima di un modulo in HTML, fare clic sulla scheda **Anteprima HTML**.

   >[!NOTE]
   >
   >Se la scheda Anteprima HTML è chiusa, premere F4 per aprire la scheda Anteprima HTML. È inoltre possibile selezionare Anteprima HTML dal menu Visualizza per aprire la scheda Anteprima HTML.

   >[!NOTE]
   >
   >L’anteprima HTML non supporta i documenti PDF, l’anteprima HTML è solo per i documenti XDP.

## Visualizzazione in anteprima di un modulo con dati di esempio {#to-preview-a-form-using-sample-data}

Designer consente di visualizzare l’anteprima del modulo e di verificarne il funzionamento mediante l’uso di dati XML di esempio. È consigliabile eseguire frequentemente delle verifiche del modulo e dei dati di esempio per assicurarsi che sul modulo venga eseguito correttamente il rendering.

Se non sono disponibili dati di esempio, è possibile crearli manualmente o automaticamente tramite Designer. (Vedere [Generazione automatica di dati di esempio per la visualizzazione in anteprima del modulo](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) e [Creazione di dati di esempio per la visualizzazione in anteprima del modulo](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

La verifica del modulo mediante un’origine dati di esempio garantisce la mappatura dei dati e dei campi e la corretta ripetizione dei sottomoduli. È possibile creare un layout di modulo bilanciato che fornisce lo spazio appropriato per la visualizzazione dei dati uniti a ciascun oggetto.

1. Selezionare **File > Proprietà modulo**.

1. Fare clic sulla scheda **Anteprima** e, nella casella File dati, digitare il percorso completo del file di dati di prova. È inoltre possibile utilizzare il pulsante Sfoglia per individuare il file desiderato.

1. Fai clic su **OK**. Alla successiva visualizzazione in anteprima del modulo nella scheda **Anteprima HTML**, i valori dei dati del file XML di esempio verranno visualizzati nei rispettivi oggetti.

## Anteprima dei moduli che si trovano in un archivio {#html-preview-of-forms-in-forms-manager}

In AEM Forms è possibile visualizzare in anteprima moduli e documenti in un archivio. L’anteprima consente di sapere esattamente l’aspetto e il funzionamento dei moduli così come verranno utilizzati dagli utenti finali.

[**Contatta il supporto**](https://www.adobe.com/account/sign-in.supportportal.html)
