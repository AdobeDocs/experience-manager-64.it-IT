---
title: Utilizzo di Acrobat Sign in un modulo adattivo
seo-title: Using Acrobat Sign in an adaptive form
description: Attiva i flussi di lavoro di firma elettronica (Acrobat Sign) per un modulo adattivo per automatizzare i flussi di lavoro di firma, semplificare i processi di firma singola e multipla e per firmare elettronicamente i moduli dai dispositivi mobili.
seo-description: Enable e-signature (Acrobat Sign) workflows for an adaptive form to automate signing workflows, simplify single and multi-signature processes, and to electronically sign forms from mobile devices.
uuid: 9c65dc44-c1a5-44df-8659-6efbe347575b
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29fc297e-0a95-4d2a-bfe6-5676d53624db
noindex: true
feature: Adaptive Forms, Acrobat Sign
exl-id: 5922ea6e-8be9-4e65-89a6-67b6cc12c4ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3598'
ht-degree: 0%

---

# Utilizzo di Acrobat Sign in un modulo adattivo {#using-adobe-sign-in-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Attiva i flussi di lavoro di firma elettronica (Acrobat Sign) per un modulo adattivo per automatizzare i flussi di lavoro di firma, semplificare i processi di firma singola e multipla e per firmare elettronicamente i moduli dai dispositivi mobili.

Acrobat Sign abilita i flussi di lavoro di firma elettronica per i moduli adattivi. Le firme elettroniche migliorano i flussi di lavoro per elaborare i documenti per aree legali, di vendita, di retribuzione, di gestione delle risorse umane e per altre aree.

In uno scenario tipico di Acrobat Sign e moduli adattivi, un utente compila un modulo adattivo da richiedere per un servizio. Ad esempio, una domanda di mutuo e di carta di credito richiede firme legali da parte di tutti i mutuatari e co-richiedenti. Per abilitare i flussi di lavoro di firma elettronica per scenari simili, è possibile integrare Acrobat Sign con AEM Forms. Altri esempi sono disponibili in Acrobat Sign per:

* Chiudi le offerte da qualsiasi dispositivo con processi di proposta, preventivo e contratto completamente automatizzati.
* Completa più velocemente i processi delle risorse umane e dai ai tuoi dipendenti le esperienze digitali.
* Taglia i tempi del ciclo di contratto e accedi più rapidamente ai tuoi fornitori.
* Crea flussi di lavoro digitali per automatizzare i processi comuni.

L’integrazione di Acrobat Sign con AEM Forms supporta:

* Flussi di lavoro di firma singoli e multipli
* Flussi di lavoro di firma sequenziali e simultanei
* Esperienze di firma in-form e out-of-form
* Firma dei moduli come utente anonimo o connesso
* Processi di firma dinamici (integrazione con il flusso di lavoro AEM Forms)
* Autenticazione tramite una knowledge base, un telefono e profili social

Scopri le [best practice per l’utilizzo di Acrobat Sign con moduli adattivi](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) per creare esperienze di firma migliori.

## Prerequisiti {#prerequisites}

Prima di utilizzare Acrobat Sign in un modulo adattivo:

* Verifica che il servizio cloud AEM Forms sia configurato per l’utilizzo di Acrobat Sign. Per maggiori dettagli, vedi [Integrare Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).
* Prepara l’elenco dei firmatari. È necessario almeno un indirizzo e-mail per ogni firmatario.

## Configurare Acrobat Sign per un modulo adattivo {#configure-adobe-sign-for-an-adaptive-form}

Esegui i seguenti passaggi per configurare Acrobat Sign per un modulo adattivo:

1. [Modifica delle proprietà dei moduli adattivi per Acrobat Sign](#enableadobesign)
1. [Aggiungere campi Acrobat Sign a un modulo adattivo](#addadobesignfieldstoanadaptiveform)
1. [Abilitare Acrobat Sign per un modulo adattivo](#enableadobsignforanadaptiveform)
1. [Selezionare Acrobat Sign Cloud Service per un modulo adattivo](#selectadobesigncloudserviceforanadaptiveform)

1. [Aggiungere firmatari di Acrobat Sign a un modulo adattivo](#addsignerstoanadaptiveform)
1. [Selezionare Invia azione per un modulo adattivo](#selectsubmitactionforanadaptiveform)

![dettagli del firmatario](assets/signer-details.png)

### Modifica delle proprietà dei moduli adattivi per Acrobat Sign {#enableadobesign}

Configura le proprietà del modulo adattivo per Acrobat Sign per un modulo esistente o per un nuovo modulo adattivo.

[Creare un modulo adattivo per Acrobat Sign](/help/forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) descrive i passaggi necessari per creare un modulo adattivo di base. Vedi [Creazione di un modulo adattivo](/help/forms/using/creating-adaptive-form.md) per altre opzioni disponibili durante la creazione di un modulo adattivo.

#### Creare un modulo adattivo per Acrobat Sign {#create-an-adaptive-form-for-adobe-sign}

Per creare un modulo adattivo per Acrobat Sign, effettua le seguenti operazioni:

1. Passa a **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms e documenti]**.
1. Tocca **[!UICONTROL Crea]** e seleziona **[!UICONTROL Modulo adattivo]**. Viene visualizzato un elenco di modelli. Seleziona il modello e tocca **[!UICONTROL Successivo]**.
1. In **[!UICONTROL Base]** scheda:

   1. Specifica la **Nome** e **Titolo** per il modulo adattivo.
   1. Seleziona la [contenitore di configurazione](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) creato durante la configurazione di Acrobat Sign con AEM Forms.

      >[!NOTE]
      >
      >La **[!UICONTROL Cloud Service Acrobat Sign]** nell’elenco a discesa vengono visualizzati i servizi cloud configurati nel contenitore di configurazione selezionato in questo campo. La **[!UICONTROL Cloud Service Acrobat Sign]** l’elenco a discesa è disponibile nella **[!UICONTROL Firma elettronica]** della sezione delle proprietà del modulo adattivo quando si seleziona la **[!UICONTROL Abilita Acrobat Sign]** opzione .

1. In **[!UICONTROL Modello Modulo]** seleziona una delle opzioni seguenti:

   * Seleziona la **[!UICONTROL Associa modello di modulo come modello del documento di record]** e selezionare un modello Documento di record. Se si utilizza un modulo adattivo basato su un modello di modulo, i documenti inviati per la firma visualizzano solo i campi basati sul modello di modulo associato. Non vengono visualizzati tutti i campi del modulo adattivo.
   * Seleziona la **[!UICONTROL Genera documento di registrazione]** opzione . Se si utilizza un modulo adattivo abilitato per l’opzione Documento di record, il documento inviato per la firma visualizza tutti i campi del modulo adattivo.

1. Tocca **[!UICONTROL Crea.]** Viene creato un modulo adattivo abilitato per la firma, che può essere utilizzato per aggiungere campi Acrobat Sign.

#### Modificare un modulo adattivo per Acrobat Sign {#editafsign}

Per utilizzare Acrobat Sign in un modulo adattivo esistente, effettua le seguenti operazioni:

1. Passa a **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]**> **[!UICONTROL Forms e documenti]**.
1. Seleziona il modulo adattivo e tocca **[!UICONTROL Proprietà]**.
1. In **[!UICONTROL Base]** seleziona la scheda [contenitore di configurazione](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) creato durante la configurazione di Acrobat Sign con AEM Forms.
1. In **[!UICONTROL Modello Modulo]** seleziona una delle opzioni seguenti:

   * Seleziona la **[!UICONTROL Associa modello di modulo come modello del documento di record]** e selezionare un modello Documento di record. Se si utilizza un modulo adattivo basato su un modello di modulo, i documenti inviati per la firma visualizzano solo i campi basati sul modello di modulo associato. Non vengono visualizzati tutti i campi del modulo adattivo.
   * Seleziona la **[!UICONTROL Genera documento di registrazione]** opzione . Se si utilizza un modulo adattivo abilitato per l’opzione Documento di record, il documento inviato per la firma visualizza tutti i campi del modulo adattivo.

1. Tocca **[!UICONTROL Salva e chiudi]**. Il modulo adattivo è abilitato per Acrobat Sign.

### Aggiungere campi Acrobat Sign a un modulo adattivo {#addadobesignfieldstoanadaptiveform}

Acrobat Sign dispone di vari campi che possono essere inseriti in un modulo adattivo. Questi campi accettano vari tipi di dati, ad esempio firme, iniziali, aziendali o titoli, e consentono di raccogliere ulteriori informazioni durante la firma, insieme alle firme. Puoi utilizzare il componente Blocco di Acrobat Sign per posizionare i campi Acrobat Sign in diverse posizioni in un modulo adattivo.

Per aggiungere campi a un modulo adattivo e personalizzare varie opzioni relative a tali campi, effettua le seguenti operazioni:

1. Trascinamento della selezione **Blocco Acrobat Sign** dal browser Componenti al modulo adattivo. Il componente Blocco Acrobat Sign contiene tutti i campi Acrobat Sign supportati. Per impostazione predefinita, aggiunge un **Firma** al modulo adattivo.

   ![blocco](assets/sign-block.png)

   Per impostazione predefinita, il blocco Acrobat Sign non è visibile nel modulo adattivo pubblicato. È visibile solo nei documenti firmati. Puoi modificare la visibilità del blocco Acrobat Sign dalle proprietà del componente Blocco Acrobat Sign.

   >[!NOTE]
   >
   >* L’utilizzo del blocco Acrobat Sign non è obbligatorio per utilizzare Acrobat Sign in un modulo adattivo. Se non si utilizza il blocco Acrobat Sign e si aggiungono campi per i firmatari, il campo firma predefinito viene visualizzato nella parte inferiore dei documenti di firma.
   >* Usa il blocco Acrobat Sign solo per i moduli adattivi che generano automaticamente il documento di record. Se si utilizza un XDP personalizzato per la generazione di un modulo adattivo basato su un documento di record o su un modello di modulo, non è necessario un blocco Acrobat Sign.


1. Seleziona la **Blocco Acrobat Sign** e tocca **Modifica** ![aem_6_3_edit](assets/aem_6_3_edit.png) icona. Visualizza le opzioni per aggiungere campi e formattare l’aspetto di un campo.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Seleziona e aggiungi campi Acrobat Sign. **B.** Espandi il blocco Acrobat Sign alla visualizzazione a schermo intero

1. Tocca **Campo Acrobat Sign** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) icona. Visualizza le opzioni per selezionare e aggiungere campi Acrobat Sign.

   Espandi la **Tipo** campo a discesa per selezionare un campo Acrobat Sign e toccare Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per aggiungere il campo selezionato al blocco Acrobat Sign. La **Tipo** Il campo a discesa include i tipi di campo Firma, Informazioni firmatario e Dati. Integrazione di Acrobat Sign con i campi di supporto di AEM Forms elencati solo nella casella a discesa Tipo . Per informazioni dettagliate sui campi di Acrobat Sign, vedi [Documentazione di Acrobat Sign](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   È obbligatorio fornire un nome univoco per un campo. È inoltre possibile selezionare l’opzione richiesta per contrassegnare un campo obbligatorio. Oltre al **Nome** e **Obbligatorio** alcuni campi di Acrobat Sign dispongono di più opzioni. Ad esempio, maschera e linea multipla. Inoltre, specifica un nome univoco per ciascun campo Acrobat Sign se i campi si trovano negli stessi blocchi Acrobat Sign o in blocchi diversi.

### Abilitare Acrobat Sign per un modulo adattivo {#enableadobsignforanadaptiveform}

Con questa opzione, Acrobat Sign non è abilitato per un modulo adattivo. Esegui i seguenti passaggi per abilitarlo:

1. Nel browser Contenuto, tocca **Contenitore modulo** e tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del contenitore Modulo adattivo.
1. Nel browser delle proprietà, espandi la **Firma elettronica** a soffietto e seleziona la **Abilita Acrobat Sign** opzione . Abilita Acrobat Sign per un modulo adattivo.

### Selezionare il Cloud Service Acrobat Sign e l’ordine di firma {#selectadobesigncloudserviceforanadaptiveform}

Puoi configurare più servizi Acrobat Sign per un’istanza di AEM Forms. È consigliabile disporre di un insieme separato di servizi per ciascuna funzione (risorse umane, finanze e altro ancora). Semplifica il tracciamento e il reporting dei documenti firmati. Ad esempio, una banca ha più reparti. Puoi disporre di una configurazione separata per ogni reparto per un migliore monitoraggio dei documenti.

Un documento può anche avere più firmatari. Ad esempio, una domanda con carta di credito può avere più candidati. Una banca richiede la firma di tutti i richiedenti prima di iniziare la domanda di elaborazione. Per scenari con più firmatari, è possibile selezionare per firmare il documento in ordine sequenziale o simultaneo.

Esegui i seguenti passaggi per selezionare un servizio cloud e l’ordine di firma:

![servizio cloud](assets/cloud-service.png)

1. Nel browser Contenuto, tocca **Contenitore modulo** e tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del contenitore Modulo adattivo.
1. Nel browser delle proprietà, espandi la **Firma elettronica** a soffietto e seleziona la **Abilita Acrobat Sign** opzione . Abilita Acrobat Sign per un modulo adattivo.
1. Seleziona un servizio cloud dall’elenco di Cloud Services Acrobat Sign già configurati.

   Se la **Cloud Service Acrobat Sign** elenco vuoto, seguire [Configurare Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) articolo per configurare il servizio.

   L’elenco a discesa elenca i servizi cloud presenti nel `global` cartella in Strumenti > **[!UICONTROL Cloud Services]** > **[!UICONTROL Acrobat Sign]**. Inoltre, il menu a discesa elenca anche i servizi cloud presenti nella cartella selezionata nella **[!UICONTROL Contenitore di configurazione]** quando si crea un modulo adattivo.

1. Seleziona l’ordine di firma dal **Firma dei firmatari** finestra di dialogo. I cantanti Acrobat Sign possono firmare un modulo adattivo **Sequenziale** - uno dopo l&#39;altro firmatario, oppure **Simultaneamente** - in qualsiasi ordine.

   In ordine sequenziale, un firmatario riceve il modulo per la firma, alla volta. Al termine della firma del documento da parte di un firmatario, il modulo viene inviato al firmatario successivo e così via.

   In ordine simultaneo, più firmatari possono firmare un modulo alla volta.

1. [Aggiungere firmatari a un modulo adattivo](#addsignerstoanadaptiveform) quindi tocca l’icona Fine per salvare le modifiche.

### Aggiungere firmatari a un modulo adattivo {#addsignerstoanadaptiveform}

Per un modulo adattivo è possibile avere un solo firmatario o più firmatari. Quando aggiungi un firmatario, puoi anche configurare i dettagli di autenticazione per il firmatario. È inoltre possibile selezionare se il compilatore e il cantante sono la stessa persona. Esegui i seguenti passaggi per aggiungere e fornire vari dettagli su un firmatario:

1. Nel browser Contenuto, tocca **Contenitore modulo** e tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà con le proprietà del contenitore Modulo adattivo.
1. Nel browser delle proprietà, espandi la **Firma elettronica** a soffietto e seleziona la **Abilita Acrobat Sign** opzione . Abilita Acrobat Sign per un modulo adattivo.
1. Tocca **Aggiungi firmatario** sotto **Configurazione del firmatario.** Aggiunge un firmatario al modulo adattivo. È possibile aggiungere più firmatari di Acrobat Sign a un modulo adattivo.
1. ![dettagli telefonici](assets/phone-details.png)

   Fai clic sul pulsante **Modifica** ![aem_6_3_edit](assets/aem_6_3_edit.png) per specificare le seguenti informazioni sul firmatario:

   * **Titolo:** Specifica un titolo per identificare in modo univoco un firmatario.
   * **Il firmatario e la persona che compila il modulo sono uguali?:** Seleziona **Sì**, se il compilatore e il primo firmatario sono la stessa persona. Se l’opzione è impostata su **No,** quindi non utilizzare il componente del passaggio firma nel modulo adattivo. Se il modulo contiene un componente Passaggio firma, il campo viene automaticamente impostato su Sì.
   * **Indirizzo e-mail del firmatario:** Specifica l’indirizzo e-mail del firmatario. Il firmatario riceve documenti/moduli firmati all’indirizzo e-mail specificato. È possibile scegliere di utilizzare un indirizzo e-mail fornito in un campo modulo, AEM profilo utente dell’utente connesso oppure immettere manualmente un indirizzo e-mail. Si tratta di un passo obbligatorio. Inoltre, se hai configurato un solo firmatario, accertati che l’indirizzo e-mail del firmatario non sia identico all’account Acrobat Sign utilizzato per configurare AEM Cloud Services.
   * **Metodo di autenticazione del firmatario:** Specificare il metodo di autenticazione di un utente prima di aprire un modulo per la firma. È possibile scegliere tra telefono, knowledge base e autenticazione basata sull&#39;identità social.

   >[!NOTE]
   >
   >* Per impostazione predefinita, l’autenticazione basata sull’identità social fornisce un’opzione per l’autenticazione tramite Facebook, Google e LinkedIn. Puoi contattare il supporto Acrobat Sign per abilitare altri provider di autenticazione social.


   * **Campi Acrobat Sign da compilare o firmare:** Selezionare i campi Acrobat Sign per il firmatario. Un modulo adattivo può avere più campi Acrobat Sign. Puoi scegliere di abilitare campi specifici per un firmatario. Nel campo vengono visualizzati tutti i blocchi Acrobat Sign disponibili. Quando selezioni un blocco, vengono selezionati tutti i campi del blocco. Puoi usare l’icona X per deselezionare un campo.

   ![signer-details-1](assets/signer-details-1.png)

   L’immagine di cui sopra ha due esempi di blocchi Acrobat Sign: Informazioni personali e dettagli dell&#39;ufficio

   Tocca Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) icona. Il firmatario viene aggiunto e configurato.

### Selezionare Invia azione per un modulo adattivo {#selectsubmitactionforanadaptiveform}

Dopo aver aggiunto i campi Acrobat Sign a un modulo adattivo, aver abilitato Acrobat Sign dal contenitore modulo, aver selezionato Cloud Service Acrobat Sign e aver aggiunto i firmatari di Acrobat Sign, selezionare un’azione di invio appropriata per il modulo adattivo. Per informazioni dettagliate sulle azioni di invio dei moduli adattivi, consulta [Configurazione dell’azione Invia](/help/forms/using/configuring-submit-actions.md).

Inoltre, un modulo adattivo abilitato per Acrobat Sign viene inviato solo dopo che tutti i firmatari hanno firmato il modulo. È possibile trovare il modulo firmato parzialmente nella sezione Firma in sospeso del portale dei moduli. Il servizio di configurazione Acrobat Sign continua a eseguire il polling del server Acrobat Sign all&#39;indirizzo [intervalli regolari](/help/forms/using/adobe-sign-integration-adaptive-forms.md) per verificare lo stato delle firme. Se tutti i firmatari completano la firma del modulo, viene avviato il servizio di invio dell’azione e il modulo viene inviato. Se si utilizza un’azione di invio personalizzata e il modulo utilizza Acrobat Sign, aggiornare l’azione di invio personalizzata per utilizzare il servizio di azione di invio.

>[!NOTE]
>
>I dati del modulo adattivo vengono temporaneamente memorizzati su Forms Portal. Si consiglia di utilizzare [archiviazione personalizzata per Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). In questo modo i dati PII (informazioni personali) non vengono memorizzati sui server AEM.

L’esperienza di firma del modulo è pronta. È possibile visualizzare un’anteprima del modulo per verificare l’esperienza di firma. Nel modulo pubblicato, i campi Blocco Acrobat Sign vengono visualizzati quando un firmatario riceve il modulo per la firma tramite e-mail. Questa esperienza è nota anche come esperienza di firma fuori forma. Puoi anche configurare un’esperienza di firma in-form per il primo firmatario, per i passaggi dettagliati vedi [Creare un’esperienza di firma in-form](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Configurare le firme cloud per un modulo adattivo {#configure-cloud-signatures-for-an-adaptive-form}

Le firme digitali o le firme remote basate su cloud sono una nuova generazione di firme digitali che funzionano su desktop, dispositivi mobili e web e soddisfano i più alti livelli di conformità e garanzia per l’autenticazione dei firmatari. È possibile firmare un modulo adattivo con firme digitali basate su cloud.

Dopo [modifica delle proprietà dei moduli adattivi per Acrobat Sign](#enableadobesign), effettua le seguenti operazioni per aggiungere il campo firma cloud a un modulo adattivo:

1. Trascinamento della selezione **Blocco Acrobat Sign** dal browser Componenti al modulo adattivo. Il componente Blocco Acrobat Sign contiene tutti i campi Acrobat Sign supportati. Per impostazione predefinita, aggiunge un **Firma** al modulo adattivo.

   ![blocco](assets/sign-block.png)

1. Seleziona la **Blocco Acrobat Sign** e tocca **Modifica** ![aem_6_3_edit](assets/aem_6_3_edit.png) icona. Visualizza le opzioni per aggiungere campi e formattare l’aspetto di un campo.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Seleziona e aggiungi campi Acrobat Sign. **B.** Espandi il blocco Acrobat Sign alla visualizzazione a schermo intero

1. Tocca **Campo Acrobat Sign** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) icona. Visualizza le opzioni per selezionare e aggiungere campi Acrobat Sign.

   Espandi la **Tipo** campo a discesa da selezionare **Firma digitale** e tocca Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per aggiungere il campo selezionato al blocco Acrobat Sign.

   ![digital_signatures](assets/digital_signatures.png)

   È obbligatorio fornire un nome univoco per un campo.

   Applicare le firme digitali al modulo adattivo utilizzando:

   * Firme cloud: Firma con un [ID digitale](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) ospitato da un provider di servizi attendibili.
   * Adobe Acrobat o Reader: Scarica e apri il documento con Adobe Acrobat o Reader per firmare utilizzando una smart card, un token USB o un ID digitale basato su file.

   Dopo aver aggiunto il campo firma cloud al modulo adattivo, esegui i seguenti passaggi per completare il processo di configurazione:

   * [Abilitare Acrobat Sign per un modulo adattivo](#enableadobsignforanadaptiveform)
   * [Selezionare Acrobat Sign Cloud Service per un modulo adattivo](#selectadobesigncloudserviceforanadaptiveform)
   * [Aggiungere firmatari di Acrobat Sign a un modulo adattivo](#addsignerstoanadaptiveform)
   * [Selezionare Invia azione per un modulo adattivo](#selectsubmitactionforanadaptiveform)


## Creare un’esperienza di firma in-form {#create-in-form-signing-experience}

Un utente può inoltre firmare un modulo adattivo durante la compilazione del modulo. Questa esperienza è nota anche come esperienza di firma in-form. L’esperienza di firma in-form è disponibile solo per il primo firmatario in un ambiente con più firmatari. Per creare un’esperienza di firma all’interno del modulo adattivo, effettua le seguenti operazioni:

1. [Aggiungere e configurare il componente Passaggio firma](#add-and-configure-the-signature-step-component).
1. [Aggiungi il componente Passaggio di riepilogo](#configure-the-thank-you-page-or-summary-step-component).

![esperienza di firma in-form](assets/in-form-signing-experience.png)

### Aggiungere e configurare il componente Passaggio firma {#add-and-configure-the-signature-step-component}

Utilizzare il componente Passaggio firma per fornire un’area per firmare elettronicamente il modulo compilato. Quando viene eseguito il rendering della sezione contenente il componente Passaggio firma, viene visualizzata una versione PDF segnalabile del modulo compilato. Il componente Passaggio firma occupa la larghezza completa disponibile per il modulo. Si consiglia di non avere alcun altro componente nella sezione contenente il componente Passaggio firma.

Esegui i seguenti passaggi per configurare il componente Passaggio firma:

1. Trascina e rilascia la **Passaggio firma** dal browser Componenti al modulo.
1. Seleziona il componente del passaggio Firma appena aggiunto e tocca il **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del passaggio Firma. Configura le seguenti proprietà:

   * **Nome elemento**: Specifica il nome del componente.
   * **Titolo:** Specifica il titolo univoco del componente.
   * **Messaggio del modello:** Specificare il messaggio da visualizzare durante il caricamento del PDF firma. I servizi Acrobat Sign impiegano un po&#39; di tempo per preparare e caricare signature PDF.
   * **Servizio di firma:** Seleziona la **Acrobat Sign** opzione .
   * **Usa componente e-sign legacy**: Se utilizzi il rispettivo modulo adattivo in [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md), l’app AEM Forms o il modulo adattivo sottostante ha un componente di firma elettronica legacy, seleziona la **Usa componente e-sign legacy** opzione .
   * **Configurazione**: Seleziona una configurazione (Cloud Service Acrobat Sign). La casella a discesa è disponibile solo se **Usa componente e-sign legacy** è abilitata.

   Tocca Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per salvare le modifiche.

   ![fase della firma](assets/signature-step.png)

   >[!NOTE]
   >
   >* Quando trascini e rilascia la **[!UICONTROL Passaggio firma]** al modulo, la **[!UICONTROL Il firmatario e la persona che compila il modulo sono uguali?]** è automaticamente impostato su **Sì**. È necessario mantenere il funzionamento del modulo.
   >* I moduli adattivi abilitati per Acrobat Sign non supportano l’uso del pulsante Invia nella sezione o nel pannello utilizzando il componente Passaggio firma . È possibile aggiungere un passaggio di riepilogo dopo l&#39;attivazione del passaggio Firma per l&#39;invio manuale o l&#39;invio automatico dopo l&#39;intervallo impostato utilizzando [Servizio di configurazione di Acrobat Sign](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).


### Configura la pagina di ringraziamento o il componente del passaggio di riepilogo {#configure-the-thank-you-page-or-summary-step-component}

La **Passaggio di riepilogo** il componente invia automaticamente il modulo, compila le informazioni all’interno della pagina di riepilogo personalizzata e visualizza il riepilogo del modulo inviato. Ottiene anche le informazioni richieste nella mappa di ritorno. Il componente Passo di riepilogo occupa la larghezza completa disponibile per il modulo. Si consiglia di non avere nessun altro componente nella sezione contenente il componente Passaggio di riepilogo .

A questo punto, l’esperienza di firma in modulo è pronta. È possibile visualizzare un’anteprima del modulo per verificare l’esperienza di firma.

## Domande frequenti {#frequently-asked-questions}

**D: È possibile incorporare un modulo adattivo in un altro modulo adattivo. È possibile abilitare Acrobat Sign per il modulo adattivo incorporato?**

**Ans:** No, AEM Forms non supporta l’uso di un modulo adattivo che incorpora un modulo adattivo abilitato per Acrobat Sign per la firma.

**D: Quando creo un modulo adattivo utilizzando il modello avanzato e lo apro per la modifica, viene visualizzato un messaggio di errore &quot;Le firme elettroniche o i firmatari non sono configurati correttamente&quot;. appare. Come risolvere il messaggio di errore?**

**Ans:** Il modulo adattivo creato utilizzando il modello avanzato è configurato per l’utilizzo di Acrobat Sign. Per risolvere l’errore, crea e seleziona una configurazione cloud Acrobat Sign e configura un firmatario Acrobat Sign per il modulo adattivo.

**D: Posso usare i tag di testo di Acrobat Sign in un componente di testo statico di un modulo adattivo?**

**Ans:** Sì, è possibile utilizzare i tag di testo in un componente di testo per aggiungere campi Acrobat Sign a un [Documento di registrazione](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) Il modulo adattivo abilitato (solo opzione per il documento generato automaticamente). Per informazioni sulla procedura e le regole per creare un tag di testo, consulta [Documentazione di Acrobat Sign](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/advanced-tasks-admins/adobe-sign-text-tagging.html). Inoltre, i moduli adattivi hanno un supporto limitato per i tag di testo. È possibile utilizzare i tag di testo per creare solo i campi supportati da Acrobat Sign Block.

**D: AEM Forms fornisce sia componenti blocco Acrobat Sign che componenti passo firma. Possono essere utilizzati simultaneamente in un modulo adattivo?**

**Ans:** È possibile utilizzare entrambi i componenti contemporaneamente in un modulo. Di seguito sono riportati alcuni consigli per l’utilizzo di questi componenti:

**Blocco Acrobat Sign:** Puoi utilizzare il blocco Acrobat Sign per aggiungere campi Acrobat Sign in qualsiasi punto del modulo adattivo. Consente inoltre di assegnare campi specifici ai firmatari. Quando un modulo adattivo viene visualizzato in anteprima o pubblicato, il blocco Acrobat Sign non è visibile, per impostazione predefinita. Questi blocchi sono abilitati solo nel documento di firma. Nel documento di firma sono abilitati solo i campi assegnati a un firmatario. Il blocco Acrobat Sign può essere utilizzato con il primo e il successivo firmatario.

**Componente del passaggio firma:** È possibile utilizzare il componente del passaggio firma per creare un’esperienza di firma all’interno del modulo. Consente la firma solo del primo firmatario durante la compilazione del modulo. Quando si esegue il rendering della sezione contenente il componente Passaggio firma, viene visualizzata una versione PDF del modulo segnalabile. Si tratta generalmente dell’ultima o della penultima sezione seguita dal componente di riepilogo di un modulo.
