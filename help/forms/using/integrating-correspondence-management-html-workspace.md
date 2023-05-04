---
title: Integrazione di applicazioni di terze parti nell’area di lavoro di AEM Forms
seo-title: Integrating third-party applications in AEM Forms workspace
description: Come integrare app di terze parti come Gestione della corrispondenza nell’area di lavoro di AEM Forms.
seo-description: How-to integrate third-party apps like Correspondence Management in AEM Forms workspace.
uuid: 9649157c-fe28-43bf-a7d3-52ed55a0bf4f
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: f2bde2e8-da95-48ac-a652-85ead87f2cd3
exl-id: 4df9a16c-0853-4bbf-81bb-1856ab55c5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# Integrazione di applicazioni di terze parti nell’area di lavoro di AEM Forms {#integrating-third-party-applications-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Forms Workspace supporta la gestione delle attività di assegnazione e completamento delle attività per moduli e documenti. Questi moduli e documenti possono essere XDP Forms, Flex® o Guide (obsoleto) di cui è stato eseguito il rendering in formati XDP, PDF, HTML o Flex.

Queste funzionalità vengono ulteriormente migliorate. AEM Forms ora supporta la collaborazione con applicazioni di terze parti che supportano funzionalità simili all’area di lavoro di AEM Forms. Una parte comune di questa funzionalità è il flusso di lavoro dell&#39;assegnazione e della successiva approvazione di un&#39;attività. AEM Forms fornisce un’unica esperienza unificata per gli utenti aziendali AEM Forms in modo che tutte le assegnazioni o approvazioni di tali attività per le applicazioni supportate possano essere gestite tramite l’area di lavoro di AEM Forms.

Ad esempio, consideriamo Gestione Corrispondenza come esempio di candidato per l’integrazione con l’area di lavoro AEM Forms. Gestione della corrispondenza ha il concetto di &quot;Lettera&quot;, che può essere resa e consente azioni.

## Creare risorse di gestione della corrispondenza {#create-correspondence-management-assets}

Inizia creando un modello di esempio per la gestione della corrispondenza di cui viene eseguito il rendering nell’area di lavoro di AEM Forms. Per ulteriori dettagli, consulta [Creare un modello di lettera](/help/forms/using/create-letter.md).

Accedi al modello Gestione corrispondenza nel suo URL per verificare se è possibile eseguire il rendering del modello Gestione corrispondenza. L’URL ha un pattern simile a `https://[server]:[port]/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

dove `encodedLetterId` è l&#39;ID lettera con codifica URL. Specifica lo stesso ID lettera quando definisci il processo di rendering per l’attività dell’area di lavoro in Workbench.

## Creare un’attività per eseguire il rendering e inviare una lettera in AEM Workspace {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

Prima di eseguire questi passaggi, assicurati di essere membro dei seguenti gruppi:

* cm-agent-users
* Utenti di Workspace

Per ulteriori informazioni, consulta [Aggiungi e configura gli utenti](/help/forms/using/admin-help/adding-configuring-users.md).

Utilizza i seguenti passaggi per creare un’attività per eseguire il rendering e inviare una lettera in AEM Workspace:

1. Workbench di Launch. Accedi a localhost come amministratore.
1. Fare clic su File > Nuovo > Applicazione. Nel campo Nome applicazione immettere `CMDemoSample` quindi fare clic su Fine.
1. Seleziona `CMDemoSample/1.0` e fai clic con il pulsante destro del mouse `NewProcess`. Nel campo del nome, immetti `CMRenderer` quindi fare clic su Fine.
1. Trascina il selettore attività Punto iniziale e configuralo:

   1. In Dati presentazione, seleziona Usa una risorsa CRX.

      ![useacrxasset](assets/useacrxasset.png)

   1. Cerca una risorsa. Nella finestra di dialogo Seleziona risorsa modulo , nella scheda Lettere sono elencate tutte le lettere presenti sul server.

      ![scheda](assets/lettertab.png)

   1. Selezionare la lettera appropriata e fare clic su **OK**.

1. Fai clic su Gestisci profili azioni. Viene visualizzata la finestra di dialogo Gestisci profilo azione . Assicurati che il processo di rendering e il processo di invio siano selezionati in modo appropriato.
1. Per aprire la lettera con un file XML di dati, sfoglia e seleziona il file di dati appropriato nel processo di preparazione dei dati.
1. Fai clic su OK.
1. Definire le variabili per Output punto iniziale e Allegati attività. Le variabili definite conterranno i dati Output punto iniziale e Allegato attività.
1. (Facoltativo) Per aggiungere un altro utente al flusso di lavoro, trascina un selettore di attività, configuralo e assegnalo a un utente. Scrivere un wrapper personalizzato (esempio fornito di seguito) o scaricare e installare il DSC (dato di seguito) per estrarre il modello Lettera, l&#39;output del punto iniziale e l&#39;allegato dell&#39;attività.

   Di seguito è riportato un esempio di wrapper personalizzato:

   ```java
   public LetterInstanceInfo getLetterInstanceInfo(Document dataXML) throws Exception {
   try {
   if(dataXML == null)
   throw new Exception("dataXML is missing");
   
   CoreService coreService = getRemoteCoreService();
   if (coreService == null)
   throw new Exception("Unable to retrive service. Please verify connection details.");
   Map<String, Object> result = coreService.getLetterInstanceInfo(IOUtils.toString(dataXML.getInputStream(), "UTF-8"));
   LetterInstanceInfo letterInstanceInfo = new LetterInstanceInfo();
   
   List<Document> attachmentDocs = new ArrayList<Document>();
   List<byte[]> attachments = (List<byte[]>)result.get(CoreService.ATTACHMENT_KEY);
   if (attachments != null){
   for (byte[] attachment : attachments)
   { attachmentDocs.add(new Document(attachment)); }
   
   }
   letterInstanceInfo.setLetterAttachments(attachmentDocs);
   
   byte[] updateLayout = (byte[])result.get(CoreService.LAYOUT_TEMPLATE_KEY);
   if (updateLayout != null)
   { letterInstanceInfo.setLetterTemplate(new Document(updateLayout)); }
   
   else
   { throw new Exception("template bytes missing while getting Letter instance Info."); }
   
   return letterInstanceInfo;
   } catch (Exception e)
   { throw new Exception(e); }
   
   }
   ```

   [Ottieni file](assets/dscsample.zip)
Scarica DSC: Un esempio di DSC è disponibile nella sezione `DSCSample.zip` file allegato sopra. Scarica e decomprimi il file `DSCSample.zip` file. Prima di utilizzare il servizio DSC, è necessario configurarlo. Per informazioni, consulta [Configurare il servizio DSC](/help/forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p).

   Nella finestra di dialogo Definisci attività , seleziona l’attività appropriata, ad esempio getLetterInstanceInfo, e fai clic su **OK**.

1. Distribuisci l&#39;applicazione. Se richiesto, archivia e salva le risorse.
1. Accedere all’area di lavoro AEM forms all’indirizzo `https://[server]:[port]/lc/content/ws`.
1. Apri l&#39;attività che hai aggiunto, CMRenderer. Viene visualizzata la lettera Gestione corrispondenza.

   ![cminworkspace](assets/cminworkspace.png)

1. Compila i dati richiesti e invia la lettera. La finestra si chiude. In questo processo, l&#39;attività viene assegnata all&#39;utente specificato nel flusso di lavoro nel passaggio 9.

   >[!NOTE]
   >
   >Il pulsante Invia non viene attivato finché non vengono inserite tutte le variabili richieste nella lettera.
