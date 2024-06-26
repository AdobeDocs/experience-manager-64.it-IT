---
title: Conversione tra formati di file e PDF
seo-title: Converting Between File Formatsand PDF
description: Utilizzare il servizio Generate PDF per convertire i formati di file nativi in PDF. Generate PDF service converte anche PDF in altri formati di file e ottimizza le dimensioni dei documenti PDF.
seo-description: Use the Generate PDF service to convert native file formats to PDF. Generate PDF service also converts PDF to other file formats and optimizes the size of PDF documents.
uuid: f72ad603-c996-4d48-9bfc-bed7bf776af6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 180cac3f-6378-42bc-9a47-60f9f08a7103
role: Developer
exl-id: 79091a75-2669-453f-9560-e58bfffa3487
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '7908'
ht-degree: 0%

---

# Conversione tra formati di file e PDF {#converting-between-file-formatsand-pdf}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

**Informazioni sul servizio Generate PDF**

Il servizio Generate PDF converte i formati di file nativi in PDF. Converte anche PDF in altri formati di file e ottimizza le dimensioni dei documenti PDF.

Il servizio Generate PDF utilizza applicazioni native per convertire i seguenti formati di file in PDF. Salvo diversa indicazione, sono supportate solo le versioni tedesca, francese, inglese e giapponese di queste applicazioni. *Solo Windows* indica il supporto solo per Windows Server® 2003 e Windows Server 2008.

* Microsoft Office 2003 e 2007 per convertire DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS e PUB (solo Windows)

   >[!NOTE]
   >
   >Per convertire il formato Microsoft XPS in PDF è necessario Acrobat® 9.2 o versione successiva.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 e 2009 per convertire DWF, DWG e DXW (solo in lingua inglese)
* Corel WordPerfect 12 e X4 per convertire WPD, QPW, SHW (solo inglese)
* OpenOffice 2.0, 2.4, 3.0.1 e 3.1 per convertire ODT, ODS, ODP, ODG, ODF, ODF, SXW, SXC, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX e PUB

   >[!NOTE]
   >
   >Il servizio Generate PDF non supporta le versioni a 64 bit di OpenOffice.

* Adobe Photoshop® CS2 per convertire PSD (solo Windows)

   >[!NOTE]
   >
   >Photoshop CS3 e CS4 non sono supportati perché non supportano Windows Server 2003 o Windows Server 2008.

* Adobe FrameMaker® 7.2 e 8 per convertire FM (solo Windows)
* Adobe PageMaker® 7.0 per la conversione di PMD, PM6, P65 e PM (solo Windows)
* Formati nativi supportati da applicazioni di terze parti (richiede lo sviluppo di file di installazione specifici per l&#39;applicazione) (solo Windows)

Il servizio Generate PDF converte i seguenti formati di file basati sugli standard in PDF.

* Formati video: SWF, FLV (solo Windows)
* Formati immagine: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ e Linux®)

Il servizio Generate PDF converte PDF nei seguenti formati di file (solo Windows):

* PostScript incapsulato (EPS)
* HTML3.2
* HTML 4.01 con CSS 1.0
* DOC (formato Microsoft Word)
* RTF
* Testo (accessibile e semplice)
* XML
* PDF/A-1a che utilizza solo lo spazio colore DeviceRGB
* PDF/A-1b che utilizza solo lo spazio colore DeviceRGB

Il servizio Generate PDF richiede l&#39;esecuzione delle seguenti attività amministrative:

* Installare le applicazioni native necessarie sul computer che ospita AEM Forms
* Installare Adobe Acrobat Professional o Acrobat Pro Extended 9.2 sul computer che ospita AEM Forms
* Eseguire operazioni di configurazione post-installazione

Queste attività sono descritte in Installazione e distribuzione di moduli AEM utilizzando JBoss Turnkey.

Puoi eseguire queste attività utilizzando il servizio Genera PDF:

* Converti da formati di file nativi in PDF.
* Conversione di documenti HTML in documenti PDF.
* Convertire i documenti PDF in formati file.

>[!NOTE]
>
>Per ulteriori informazioni sul servizio Generate PDF, consulta [Riferimento servizi per AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Conversione di documenti Word in documenti PDF {#converting-word-documents-to-pdf-documents}

In questa sezione viene descritto come utilizzare l’API Generate PDF per convertire programmaticamente un documento Microsoft Word in un documento PDF.

>[!NOTE]
>
>Per ulteriori informazioni su formati di file aggiuntivi, consulta [Aggiunta del supporto per formati di file nativi aggiuntivi](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats).

>[!NOTE]
>
>Per ulteriori informazioni sul servizio Generate PDF, consulta [Riferimento servizi per AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary-of-steps}

Per convertire un documento Microsoft Word in un documento PDF, eseguire le operazioni seguenti:

1. Includi file di progetto.
1. Crea un client Generate PDF.
1. Recupera il file da convertire in un documento PDF.
1. Converti il file in un documento PDF.
1. Recupera i risultati.

**Includi file di progetto**

Includi i file necessari nel progetto di sviluppo. Se stai creando un&#39;applicazione client utilizzando Java, includi i file JAR necessari. Se utilizzi i servizi web, assicurati di includere i file proxy.

**Creare un client Generate PDF**

Prima di eseguire un’operazione Generate PDF a livello di programmazione, creare un client di servizio Generate PDF. Se utilizzi l’API Java, crea un `GeneratePdfServiceClient` oggetto. Se utilizzi l’API del servizio Web, crea un `GeneratePDFServiceService` oggetto.

**Recupera il file da convertire in un documento PDF**

Recuperare il documento Microsoft Word per la conversione in un documento PDF.

**Convertire il file in un documento PDF**

Dopo aver creato il client di servizio Generate PDF, è possibile richiamare l’ `createPDF2` metodo . Questo metodo richiede informazioni sul documento da convertire, inclusa l&#39;estensione del file.

**Recupera i risultati**

Dopo la conversione del file in un documento PDF, è possibile recuperare i risultati. Ad esempio, dopo aver convertito un file Word in un documento PDF, è possibile recuperare e salvare il documento PDF.

**Consulta anche**

[Conversione di documenti Word in documenti PDF tramite API Java](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Conversione di documenti Word in documenti PDF tramite API del servizio Web](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generare gli avvii rapidi dell’API di PDF Service](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Conversione di documenti Word in documenti PDF tramite API Java {#convert-word-documents-to-pdf-documents-using-the-java-api}

Convertire un documento Microsoft Word in un documento PDF utilizzando l’API Generate PDF (Java):

1. Includi file di progetto.

   Includi file JAR client, come adobe-generatepdf-client.jar, nel percorso di classe del progetto Java.

1. Crea un client Generate PDF.

   * Crea un `ServiceClientFactory` oggetto contenente le proprietà di connessione.
   * Crea un `GeneratePdfServiceClient` utilizzando il relativo costruttore e passando `ServiceClientFactory` oggetto.

1. Recupera il file da convertire in un documento PDF.

   * Crea un `java.io.FileInputStream` oggetto che rappresenta il file Word da convertire utilizzando il relativo costruttore. Passa un valore stringa che specifica la posizione del file.
   * Crea un `com.adobe.idp.Document` utilizzando il relativo costruttore e passando `java.io.FileInputStream` oggetto.

1. Converti il file in un documento PDF.

   Converti il file in un documento PDF richiamando il `GeneratePdfServiceClient` dell’oggetto `createPDF2` e passando i seguenti valori:

   * A `com.adobe.idp.Document` oggetto che rappresenta il file da convertire.
   * A `java.lang.String` oggetto che contiene l&#39;estensione file.
   * A `java.lang.String` oggetto contenente le impostazioni del tipo di file da utilizzare nella conversione. Le impostazioni del tipo di file forniscono impostazioni di conversione per diversi tipi di file, ad esempio .doc o .xls.
   * A `java.lang.String` oggetto contenente il nome delle impostazioni PDF da utilizzare. Ad esempio, puoi specificare `Standard`.
   * A `java.lang.String` oggetto contenente il nome delle impostazioni di protezione da utilizzare.
   * Facoltativo `com.adobe.idp.Document` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF.
   * Facoltativo `com.adobe.idp.Document` oggetto contenente informazioni sui metadati da applicare al documento PDF.

   La `createPDF2` restituisce un `CreatePDFResult` oggetto contenente il nuovo documento PDF e le informazioni di registro. Il file di registro in genere contiene messaggi di errore o di avviso generati dalla richiesta di conversione.

1. Recupera i risultati.

   Per ottenere il documento PDF, eseguire le operazioni seguenti:

   * Richiama il `CreatePDFResult` dell’oggetto `getCreatedDocument` che restituisce un `com.adobe.idp.Document` oggetto.
   * Richiama il `com.adobe.idp.Document` dell’oggetto `copyToFile` per estrarre il documento PDF dall&#39;oggetto creato nel passaggio precedente.

   Se hai utilizzato la `createPDF2` per ottenere il documento di registro (non applicabile alle conversioni di HTML), esegui le seguenti operazioni:

   * Richiama il `CreatePDFResult` dell’oggetto `getLogDocument` metodo . Questo restituisce un `com.adobe.idp.Document` oggetto.
   * Richiama il `com.adobe.idp.Document` dell’oggetto `copyToFile` metodo per estrarre il documento di registro.


**Consulta anche**

[Riepilogo dei passaggi](converting-file-formats-pdf.md#summary-of-steps)

[Avvio rapido (modalità SOAP): Conversione di un documento Microsoft Word in un documento PDF tramite API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Conversione di documenti Word in documenti PDF tramite API del servizio Web {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

Convertire un documento Microsoft Word in un documento PDF utilizzando l’API Generate PDF (servizio Web):

1. Includi file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurati di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituisci `localhost` con l’indirizzo IP del server che ospita AEM Forms.

1. Crea un client Generate PDF.

   * Crea un `GeneratePDFServiceClient` utilizzando il relativo costruttore predefinito.
   * Crea un `GeneratePDFServiceClient.Endpoint.Address` utilizzando `System.ServiceModel.EndpointAddress` costruttore. Passa un valore stringa che specifica il WSDL al servizio AEM Forms (ad esempio, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Non è necessario utilizzare il `lc_version` attributo. Tuttavia, specifica `?blob=mtom`.
   * Crea un `System.ServiceModel.BasicHttpBinding` ottenendo il valore del `GeneratePDFServiceClient.Endpoint.Binding` campo . Imposta il valore restituito su `BasicHttpBinding`.
   * Imposta la `System.ServiceModel.BasicHttpBinding` dell’oggetto `MessageEncoding` campo a `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilita l’autenticazione HTTP di base eseguendo le seguenti attività:

      * Assegnare il nome utente del modulo di AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Assegna il valore della password corrispondente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Assegna il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegna il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupera il file da convertire in un documento PDF.

   * Crea un `BLOB` utilizzando il relativo costruttore. La `BLOB` viene utilizzato per memorizzare il file che si desidera convertire in un documento PDF.
   * Crea un `System.IO.FileStream` richiamando il relativo costruttore. Passa un valore stringa che rappresenta la posizione del file da convertire e la modalità di apertura del file.
   * Creare un array di byte che memorizza il contenuto del `System.IO.FileStream` oggetto. È possibile determinare le dimensioni dell&#39;array di byte ottenendo il `System.IO.FileStream` dell’oggetto `Length` proprietà.
   * Compilare l&#39;array di byte con i dati del flusso richiamando il `System.IO.FileStream` dell’oggetto `Read` e passare l&#39;array di byte, la posizione iniziale e la lunghezza del flusso da leggere.
   * Popolare `BLOB` oggetto assegnando al relativo `MTOM` proprietà il contenuto dell&#39;array di byte.

1. Converti il file in un documento PDF.

   Converti il file in un documento PDF richiamando il `GeneratePDFServiceService` dell’oggetto `CreatePDF2` e passando i seguenti valori:

   * A `BLOB` oggetto che rappresenta il file da convertire.
   * Una stringa che contiene l&#39;estensione del file.
   * A `java.lang.String` oggetto contenente le impostazioni del tipo di file da utilizzare nella conversione. Le impostazioni del tipo di file forniscono impostazioni di conversione per diversi tipi di file, ad esempio .doc o .xls.
   * Oggetto string contenente le impostazioni PDF da utilizzare. Puoi specificare `Standard`.
   * Oggetto string contenente le impostazioni di protezione da utilizzare. Puoi specificare `No Security`.
   * Facoltativo `BLOB` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF.
   * Facoltativo `BLOB` oggetto contenente informazioni sui metadati da applicare al documento PDF.
   * Un parametro di output di tipo `BLOB` che viene popolato da `CreatePDF2` metodo . La `CreatePDF2` popola questo oggetto con il documento convertito. (Questo valore di parametro è richiesto solo per la chiamata al servizio Web).
   * Un parametro di output di tipo `BLOB` che viene popolato da `CreatePDF2` metodo . La `CreatePDF2` popola questo oggetto con il documento di registro. (Questo valore di parametro è richiesto solo per la chiamata al servizio Web).

1. Recupera i risultati.

   * Recupera il documento PDF convertito assegnando il `BLOB` dell’oggetto `MTOM` su un array di byte. L&#39;array di byte rappresenta il documento PDF convertito. Assicurati di utilizzare `BLOB` viene utilizzato come parametro di output per `createPDF2` metodo .
   * Crea un `System.IO.FileStream` richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF convertito.
   * Crea un `System.IO.BinaryWriter` richiamando il relativo costruttore e passando `System.IO.FileStream` oggetto.
   * Scrivi il contenuto dell’array di byte in un file PDF richiamando il `System.IO.BinaryWriter` dell’oggetto `Write` e passare l&#39;array di byte.

**Consulta anche**

[Riepilogo dei passaggi](converting-file-formats-pdf.md#summary-of-steps)

[Richiamo di AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Richiamo di AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversione di documenti HTML in documenti PDF {#converting-html-documents-to-pdf-documents}

Questa sezione descrive come utilizzare l’API Generate PDF per convertire programmaticamente i documenti HTML in documenti PDF.

>[!NOTE]
>
>Per ulteriori informazioni sul servizio Generate PDF, consulta [Riferimento servizi per AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary_of_steps-1}

Per convertire un documento HTML in un documento PDF, eseguire le operazioni seguenti:

1. Includi file di progetto.
1. Crea un client Generate PDF.
1. Recupera il contenuto HTML da convertire in un documento PDF.
1. Convertire il contenuto di HTML in un documento di PDF.
1. Recupera i risultati.

**Includi file di progetto**

Includi i file necessari nel progetto di sviluppo. Se stai creando un&#39;applicazione client utilizzando Java, includi i file JAR necessari. Se utilizzi i servizi web, assicurati di includere i file proxy.

**Creare un client Generate PDF**

Prima di poter eseguire un’operazione Generate PDF a livello di programmazione, è necessario creare un client di servizio Generate PDF. Se utilizzi l’API Java, crea un `GeneratePdfServiceClient` oggetto. Se utilizzi l’API del servizio Web, crea un `GeneratePDFServiceService`.

**Recupera il contenuto HTML da convertire in un documento PDF**

Fare riferimento al contenuto HTML che si desidera convertire in un documento PDF. È possibile fare riferimento al contenuto di HTML, ad esempio un file HTML o un contenuto HTML accessibile tramite un URL.

**Convertire il contenuto di HTML in un documento PDF**

Dopo aver creato il client di servizio, è possibile richiamare l’operazione di creazione di PDF appropriata. Questa operazione richiede informazioni sul documento da convertire, incluso il percorso del documento di destinazione.

**Recupera i risultati**

Una volta convertito il contenuto di HTML in un documento PDF, è possibile recuperare i risultati e salvare il documento PDF.

**Consulta anche**

[Convertire il contenuto HTML in un documento PDF utilizzando l’API Java](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[Convertire il contenuto HTML in un documento PDF utilizzando l’API del servizio Web](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generare gli avvii rapidi dell’API di PDF Service](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Convertire il contenuto HTML in un documento PDF utilizzando l’API Java {#convert-html-content-to-a-pdf-document-using-the-java-api}

Convertire un documento HTML in un documento PDF utilizzando l’API Generate PDF (Java):

1. Includi file di progetto.

   Includi file JAR client, come adobe-generatepdf-client.jar, nel percorso di classe del progetto Java.

1. Crea un client Generate PDF.

   Crea un `GeneratePdfServiceClient` utilizzando il relativo costruttore e passando un `ServiceClientFactory` oggetto contenente le proprietà di connessione.

1. Recupera il contenuto HTML da convertire in un documento PDF.

   Recupera il contenuto di HTML creando una variabile stringa e assegnando un URL che punta al contenuto di HTML.

1. Convertire il contenuto di HTML in un documento di PDF.

   Richiama il `GeneratePdfServiceClient` dell’oggetto `htmlToPDF2` e passare i seguenti valori:

   * A `java.lang.String` oggetto contenente l’URL del file HTML da convertire.
   * A `java.lang.String` oggetto contenente le impostazioni del tipo di file da utilizzare nella conversione. Le impostazioni del tipo di file possono includere livelli di ragnatela.
   * A `java.lang.String` oggetto contenente il nome delle impostazioni di protezione da utilizzare.
   * Facoltativo `com.adobe.idp.Document` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF. Se queste informazioni non vengono fornite, le impostazioni vengono scelte automaticamente in base ai tre parametri precedenti.
   * Facoltativo `com.adobe.idp.Document` oggetto contenente informazioni sui metadati da applicare al documento PDF.

1. Recupera i risultati.

   La `htmlToPDF2` restituisce un `HtmlToPdfResult` che contiene il nuovo documento PDF generato. Per ottenere il documento PDF appena creato, eseguire le operazioni seguenti:

   * Richiama il `HtmlToPdfResult` dell’oggetto `getCreatedDocument` metodo . Questo restituisce un `com.adobe.idp.Document` oggetto.
   * Richiama il `com.adobe.idp.Document` dell’oggetto `copyToFile` per estrarre il documento PDF dall&#39;oggetto creato nel passaggio precedente.

**Consulta anche**

[Conversione di documenti HTML in documenti PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Avvio rapido (modalità SOAP): Conversione del contenuto HTML in un documento PDF tramite l’API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Avvio rapido (modalità SOAP): Conversione del contenuto HTML in un documento PDF tramite l’API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertire il contenuto HTML in un documento PDF utilizzando l’API del servizio Web {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

Convertire il contenuto HTML in un documento PDF utilizzando l’API Generate PDF (servizio Web):

1. Includi file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurati di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituisci `localhost` con l’indirizzo IP del server che ospita AEM Forms.

1. Crea un client Generate PDF.

   * Crea un `GeneratePDFServiceClient` utilizzando il relativo costruttore predefinito.
   * Crea un `GeneratePDFServiceClient.Endpoint.Address` utilizzando `System.ServiceModel.EndpointAddress` costruttore. Passa un valore stringa che specifica il WSDL al servizio AEM Forms (ad esempio, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Non è necessario utilizzare il `lc_version` attributo. Tuttavia, specifica `?blob=mtom`.
   * Crea un `System.ServiceModel.BasicHttpBinding` ottenendo il valore del `GeneratePDFServiceClient.Endpoint.Binding` campo . Imposta il valore restituito su `BasicHttpBinding`.
   * Imposta la `System.ServiceModel.BasicHttpBinding` dell’oggetto `MessageEncoding` campo a `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilita l’autenticazione HTTP di base eseguendo le seguenti attività:

      * Assegnare il nome utente del modulo di AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Assegna il valore della password corrispondente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Assegna il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegna il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupera il contenuto HTML da convertire in un documento PDF.

   Recupera il contenuto di HTML creando una variabile stringa e assegnando un URL che punta al contenuto di HTML.

1. Convertire il contenuto di HTML in un documento di PDF.

   Convertire il contenuto di HTML in un documento PDF richiamando il `GeneratePDFServiceService` dell’oggetto `HtmlToPDF2` e passare i seguenti valori:

   * Una stringa che contiene il contenuto HTML da convertire.
   * A `java.lang.String` oggetto contenente le impostazioni del tipo di file da utilizzare nella conversione.
   * Oggetto string contenente le impostazioni di protezione da utilizzare.
   * Facoltativo `BLOB` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF.
   * Facoltativo `BLOB` oggetto contenente informazioni sui metadati da applicare al documento PDF.
   * Un parametro di output di tipo `BLOB` che viene popolato da `CreatePDF2` metodo . La `CreatePDF2` popola questo oggetto con il documento convertito. (Questo valore di parametro è richiesto solo per la chiamata al servizio Web).

1. Recupera i risultati.

   * Recupera il documento PDF convertito assegnando il `BLOB` dell’oggetto `MTOM` su un array di byte. L&#39;array di byte rappresenta il documento PDF convertito. Assicurati di utilizzare `BLOB` viene utilizzato come parametro di output per `HtmlToPDF2` metodo .
   * Crea un `System.IO.FileStream` richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF convertito.
   * Crea un `System.IO.BinaryWriter` richiamando il relativo costruttore e passando `System.IO.FileStream` oggetto.
   * Scrivi il contenuto dell’array di byte in un file PDF richiamando il `System.IO.BinaryWriter` dell’oggetto `Write` e passare l&#39;array di byte.

**Consulta anche**

[Conversione di documenti HTML in documenti PDF](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Richiamo di AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Richiamo di AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Conversione di documenti PDF in formati non immagine {#converting-pdf-documents-to-non-image-formats}

Questa sezione descrive come utilizzare l’API Generate PDF Java API e l’API del servizio Web per convertire programmaticamente un documento PDF in un file RTF, che è un esempio di un formato non immagine. Altri formati non immagine includono HTML, testo, DOC e EPS. Durante la conversione di un documento PDF in formato RTF, assicurati che il documento PDF non contenga elementi modulo, ad esempio un pulsante di invio. Gli elementi modulo non vengono convertiti.

>[!NOTE]
>
>Per ulteriori informazioni sul servizio Generate PDF, consulta [Riferimento servizi per AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary_of_steps-2}

Per convertire un documento PDF in uno qualsiasi dei tipi supportati, eseguire le operazioni seguenti:

1. Includi file di progetto.
1. Crea un client Generate PDF.
1. Recupera il documento PDF da convertire.
1. Converti il documento PDF.
1. Salva il file convertito.

**Includi file di progetto**

Includi i file necessari nel progetto di sviluppo. Se stai creando un&#39;applicazione client utilizzando Java, includi i file JAR necessari. Se utilizzi i servizi web, assicurati di includere i file proxy.

**Creare un client Generate PDF**

Prima di poter eseguire un’operazione Generate PDF a livello di programmazione, è necessario creare un client di servizio Generate PDF. Se utilizzi l’API Java, crea un `GeneratePdfServiceClient` oggetto. Se utilizzi l’API del servizio Web, crea un `GeneratePDFServiceService` oggetto.

**Recupera il documento PDF da convertire**

Recupera il documento PDF da convertire in un formato non immagine.

**Conversione del documento PDF**

Dopo aver creato il client di servizio, è possibile richiamare l’operazione di esportazione di PDF. Questa operazione richiede informazioni sul documento da convertire, incluso il percorso del documento di destinazione.

**Salva il file convertito**

Salva il file convertito. Ad esempio, se converti un documento PDF in un file RTF, salva il documento convertito in un file RTF.

**Consulta anche**

[Convertire un documento PDF in un file RTF utilizzando l’API Java](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Convertire un documento PDF in un file RTF utilizzando l’API del servizio Web](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generare gli avvii rapidi dell’API di PDF Service](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Convertire un documento PDF in un file RTF utilizzando l’API Java {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

Converti un documento PDF in un file RTF utilizzando l’API Generate PDF (Java):

1. Includi file di progetto.

   Includi file JAR client, come adobe-generatepdf-client.jar, nel percorso di classe del progetto Java.

1. Crea un client Generate PDF.

   Crea un `GeneratePdfServiceClient` utilizzando il relativo costruttore e passando un `ServiceClientFactory` oggetto contenente le proprietà di connessione.

1. Recupera il documento PDF da convertire.

   * Crea un `java.io.FileInputStream` oggetto che rappresenta il documento PDF da convertire utilizzando il relativo costruttore. Passa un valore stringa che specifica la posizione del documento PDF.
   * Crea un `com.adobe.idp.Document` utilizzando il relativo costruttore e passando `java.io.FileInputStream` oggetto.

1. Converti il documento PDF.

   Richiama il `GeneratePdfServiceClient` dell’oggetto `exportPDF2` e passare i seguenti valori:

   * A `com.adobe.idp.Document` oggetto che rappresenta il file PDF da convertire.
   * A `java.lang.String` oggetto che contiene il nome del file da convertire.
   * A `java.lang.String` oggetto che contiene il nome delle impostazioni di Adobe PDF.
   * A `ConvertPDFFormatType` oggetto che specifica il tipo di file di destinazione per la conversione.
   * Facoltativo `com.adobe.idp.Document` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF.

   La `exportPDF2` restituisce un `ExportPDFResult` oggetto contenente il file convertito.

1. Converti il documento PDF.

   Per ottenere il file appena creato, esegui le seguenti operazioni:

   * Richiama il `ExportPDFResult` dell’oggetto `getConvertedDocument` metodo . Questo restituisce un `com.adobe.idp.Document` oggetto.
   * Richiama il `com.adobe.idp.Document` dell’oggetto `copyToFile` per estrarre il nuovo documento.

**Consulta anche**

[Riepilogo dei passaggi](converting-file-formats-pdf.md#summary-of-steps)

[Avvio rapido (modalità SOAP): Conversione del contenuto HTML in un documento PDF tramite l’API Java](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Convertire un documento PDF in un file RTF utilizzando l’API del servizio Web {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Converti un documento PDF in un file RTF utilizzando l’API Generate PDF (servizio Web):

1. Includi file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurati di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituisci `localhost` con l’indirizzo IP del server che ospita AEM Forms.

1. Creare un client Generate PDf.

   * Crea un `GeneratePDFServiceClient` utilizzando il relativo costruttore predefinito.
   * Crea un `GeneratePDFServiceClient.Endpoint.Address` utilizzando `System.ServiceModel.EndpointAddress` costruttore. Passa un valore stringa che specifica il WSDL al servizio AEM Forms (ad esempio, `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) Non è necessario utilizzare il `lc_version` attributo. Tuttavia, specifica `?blob=mtom`.
   * Crea un `System.ServiceModel.BasicHttpBinding` ottenendo il valore del `GeneratePDFServiceClient.Endpoint.Binding` campo . Imposta il valore restituito su `BasicHttpBinding`.
   * Imposta la `System.ServiceModel.BasicHttpBinding` dell’oggetto `MessageEncoding` campo a `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilita l’autenticazione HTTP di base eseguendo le seguenti attività:

      * Assegnare il nome utente del modulo di AEM al campo `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Assegna il valore della password corrispondente al campo `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Assegna il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegna il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recupera il documento PDF da convertire.

   * Crea un `BLOB` utilizzando il relativo costruttore. La `BLOB` viene utilizzato per memorizzare un documento PDF convertito.
   * Crea un `System.IO.FileStream` richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF e la modalità di apertura del file.
   * Creare un array di byte che memorizza il contenuto del `System.IO.FileStream` oggetto. È possibile determinare le dimensioni dell&#39;array di byte ottenendo il `System.IO.FileStream` dell’oggetto `Length` proprietà.
   * Compilare l&#39;array di byte con i dati del flusso richiamando il `System.IO.FileStream` dell’oggetto `Read` e passare l&#39;array di byte, la posizione iniziale e la lunghezza del flusso da leggere.
   * Popolare `BLOB` oggetto assegnando al relativo `MTOM` proprietà il contenuto dell&#39;array di byte.

1. Converti il documento PDF.

   Richiama il `GeneratePDFServiceServiceWse` dell’oggetto `ExportPDF2` e passare i seguenti valori:

   * A `BLOB` oggetto che rappresenta il file PDF da convertire.
   * Una stringa che contiene il nome del percorso del file da convertire.
   * A `java.lang.String` oggetto che specifica la posizione del file.
   * Oggetto string che specifica il tipo di file di destinazione per la conversione. Specifica `RTF`.
   * Facoltativo `BLOB` oggetto contenente le impostazioni da applicare durante la generazione del documento PDF.
   * Un parametro di output di tipo `BLOB` che viene popolato da `ExportPDF2` metodo . La `ExportPDF2` popola questo oggetto con il documento convertito. (Questo valore di parametro è richiesto solo per la chiamata al servizio Web).

1. Salva il file convertito.

   * Recupera il documento RTF convertito assegnando il `BLOB` dell’oggetto `MTOM` su un array di byte. L&#39;array di byte rappresenta il documento RTF convertito. Assicurati di utilizzare `BLOB` viene utilizzato come parametro di output per `ExportPDF2` metodo .
   * Crea un `System.IO.FileStream` richiamando il relativo costruttore. Passa un valore stringa che rappresenta la posizione del file RTF.
   * Crea un `System.IO.BinaryWriter` richiamando il relativo costruttore e passando `System.IO.FileStream` oggetto.
   * Scrivi il contenuto dell&#39;array di byte in un file RTF richiamando il `System.IO.BinaryWriter` dell’oggetto `Write` e passare l&#39;array di byte.

**Consulta anche**

[Riepilogo dei passaggi](converting-file-formats-pdf.md#summary-of-steps)

[Richiamo di AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Richiamo di AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Aggiunta del supporto per formati di file nativi aggiuntivi {#adding-support-for-additional-native-file-formats}

Questa sezione spiega come aggiungere il supporto per ulteriori formati di file nativi. Fornisce una panoramica delle interazioni tra il servizio Generate PDF e le applicazioni native utilizzate da questo servizio per convertire i formati di file nativi in PDF.

Questa sezione spiega anche quanto segue:

* Come modificare la risposta fornita dal servizio Generate PDF alle applicazioni native utilizzate da questo prodotto per convertire i formati di file nativi in PDF
* Interazioni tra il servizio Generate PDF, il componente Generate PDF service Application Monitor (AppMon) e le applicazioni native, come Microsoft Word
* I ruoli che le grammatiche XML svolgono in queste interazioni

### Interazioni dei componenti {#component-interactions}

Il servizio Generate PDF converte i formati di file nativi richiamando l&#39;applicazione associata al formato di file e quindi interagendo con l&#39;applicazione per stampare il documento utilizzando la stampante predefinita. La stampante predefinita deve essere impostata come stampante Adobe PDF.

Questa illustrazione mostra i componenti e i driver coinvolti nel supporto nativo delle applicazioni. Cita anche le grammatiche XML che influenzano le interazioni.

Interazioni dei componenti per la conversione dei file nativi

Questo documento utilizza il termine *applicazione nativa* per indicare l&#39;applicazione utilizzata per produrre un formato di file nativo, ad esempio Microsoft Word.

*AppMon* è un componente enterprise che interagisce con un&#39;applicazione nativa nello stesso modo in cui un utente naviga attraverso le finestre di dialogo presentate da tale applicazione. Le grammatiche XML utilizzate da AppMon per istruire un&#39;applicazione, come Microsoft Word, ad aprire e stampare un file richiedono le seguenti attività sequenziali:

1. Per aprire il file, selezionare File > Apri
1. Assicurarsi che venga visualizzata la finestra di dialogo Apri; in caso contrario, gestire l&#39;errore
1. Specificare il nome del file nel campo Nome file e quindi fare clic sul pulsante Apri
1. Assicurati che il file si apra effettivamente
1. Per aprire la finestra di dialogo Stampa, selezionare File > Stampa
1. Visualizzazione della finestra di dialogo Stampa

AppMon utilizza le API Win32 standard per interagire con applicazioni di terze parti al fine di trasferire gli eventi dell&#39;interfaccia utente, come i tasti e i clic del mouse, il che è utile per controllare queste applicazioni per produrre file PDF da esse.

A causa di una limitazione con queste API Win32, AppMon non è in grado di inviare questi eventi dell&#39;interfaccia utente ad alcuni tipi specifici di finestre, come barre dei menu mobili (presenti in alcune applicazioni come TextPad) e determinati tipi di finestre di dialogo il cui contenuto non può essere recuperato utilizzando le API Win32.

È facile identificare visivamente una barra di menu mobile; tuttavia, potrebbe non essere possibile identificare i tipi speciali di dialoghi solo attraverso l&#39;ispezione visiva. È necessario un&#39;applicazione di terze parti come Microsoft Spy++ (parte dell&#39;ambiente di sviluppo di Microsoft Visual C++) o il relativo WinID equivalente (che può essere scaricato gratuitamente da [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)) per esaminare una finestra di dialogo per determinare se AppMon è in grado di interagire con essa utilizzando le API Win32 standard.

Se WinID è in grado di estrarre il contenuto della finestra di dialogo, ad esempio il testo, le finestre secondarie, l’ID della classe della finestra e così via, AppMon sarà in grado di fare lo stesso.

In questa tabella sono elencati i tipi di informazioni utilizzati per la stampa dei formati di file nativi.

<table> 
 <thead> 
  <tr> 
   <th><p>Tipo di informazione</p></th> 
   <th><p>Descrizione</p></th> 
   <th><p>Modifica/creazione di voci relative a file nativi </p></th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td><p>Impostazioni amministrative </p></td> 
   <td><p>Include le impostazioni PDF, le impostazioni di protezione e le impostazioni del tipo di file. </p><p>Le impostazioni del tipo di file associano le estensioni del nome file alle applicazioni native corrispondenti. Le impostazioni del tipo di file specificano anche le impostazioni dell'applicazione nativa utilizzate per stampare file nativi. </p></td> 
   <td><p>Per modificare le impostazioni di un'applicazione nativa già supportata, l'amministratore di sistema imposta le impostazioni Tipo file nella console di amministrazione. </p><p>Per aggiungere il supporto per un nuovo formato di file nativo, è necessario modificare manualmente il file. (Vedi <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">Aggiunta o modifica del supporto per un formato di file nativo</a>.) </p></td> 
  </tr> 
  <tr> 
   <td><p>Script </p></td> 
   <td><p>Specifica le interazioni tra il servizio Generate PDF e un'applicazione nativa. Tali interazioni solitamente indirizzano l'applicazione a stampare un file sul driver Adobe PDF. </p><p>Lo script contiene istruzioni che indirizzano l'applicazione nativa ad aprire finestre di dialogo specifiche e che forniscono risposte specifiche ai campi e ai pulsanti di tali finestre di dialogo. </p></td> 
   <td><p>Il servizio Generate PDF include file di script per tutte le applicazioni native supportate. È possibile modificare questi file utilizzando un'applicazione di modifica XML.</p><p>Per aggiungere il supporto per una nuova applicazione nativa, è necessario creare un nuovo file di script. (Vedi <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Creazione o modifica di un file XML di dialogo aggiuntivo per un'applicazione nativa</a>.) </p></td> 
  </tr> 
  <tr> 
   <td><p>Istruzioni per la finestra di dialogo Generico </p></td> 
   <td><p>Specifica come rispondere alle finestre di dialogo comuni a più applicazioni. Tali finestre di dialogo sono generate da sistemi operativi, applicazioni helper (come PDFMaker) e driver. </p><p>Il file che contiene queste informazioni è appmon.global.en_US.xml.</p></td> 
   <td><p>Non modificare il file. </p></td> 
  </tr> 
  <tr> 
   <td><p>Istruzioni per la finestra di dialogo specifica dell’applicazione</p></td> 
   <td><p>Specifica come rispondere alle finestre di dialogo specifiche dell'applicazione. </p><p>Il file che contiene queste informazioni è appmon.<i>[nomeapp]</i>.dialog.<i>[locale]</i>.xml (ad esempio, appmon.word.en_US.xml).</p></td> 
   <td><p>Non modificare il file. </p><p>Per aggiungere le istruzioni della finestra di dialogo per una nuova applicazione nativa, vedere <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Creazione o modifica di un file XML di dialogo aggiuntivo per un'applicazione nativa</a>.</p></td> 
  </tr> 
  <tr> 
   <td><p>Istruzioni aggiuntive per la finestra di dialogo specifica per l'applicazione </p></td> 
   <td><p>Specifica sostituzioni e aggiunte alle istruzioni della finestra di dialogo specifica per l'applicazione. La sezione presenta un esempio di tali informazioni. </p><p>Il file che contiene queste informazioni è appmon.<i>[nomeapp]</i>.addizione.<i>[locale]</i>.xml. Un esempio è appmon.addizione.en_US.xml.</p></td> 
   <td><p>I file di questo tipo possono essere creati e modificati utilizzando un'applicazione di modifica XML. (Vedi <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Creazione o modifica di un file XML di dialogo aggiuntivo per un'applicazione nativa</a>.) </p><p><strong>Importante</strong>: È necessario creare ulteriori istruzioni per la finestra di dialogo specifiche per le applicazioni per ogni applicazione nativa supportata dal server. </p></td> 
  </tr> 
 </tbody> 
</table>

### Informazioni sullo script e sui file XML di dialogo {#about-the-script-and-dialog-xml-files}

I file XML di script indirizzano il servizio Generate PDF per navigare tra le finestre di dialogo delle applicazioni nello stesso modo in cui un utente naviga attraverso le finestre di dialogo delle applicazioni. I file XML di script inoltre indirizzano il servizio Generate PDF per rispondere alle finestre di dialogo eseguendo azioni quali la pressione dei pulsanti, la selezione o la deselezione delle caselle di controllo o la selezione delle voci di menu.

Al contrario, i file XML di dialogo rispondono semplicemente a finestre di dialogo con gli stessi tipi di azioni utilizzati nei file XML di script.

#### Terminologia della finestra di dialogo e degli elementi della finestra {#dialog-box-and-window-element-terminology}

Questa sezione e la sezione successiva utilizzano una terminologia diversa per le finestre di dialogo e i componenti che contengono, a seconda della prospettiva descritta. I componenti della finestra di dialogo sono elementi quali pulsanti, campi e caselle combinate.

Quando questa sezione e la sezione successiva descrivono le finestre di dialogo e i relativi componenti dal punto di vista di un utente, termini come *finestra di dialogo*, *pulsante*, *field* e *casella combinata* sono utilizzati.

Quando questa sezione e la sezione successiva descrivono le finestre di dialogo e i relativi componenti dal punto di vista della loro rappresentazione interna, il termine *elemento finestra* viene utilizzato. La rappresentazione interna degli elementi della finestra è una gerarchia, in cui ogni istanza dell’elemento della finestra è identificata dalle etichette. L&#39;istanza dell&#39;elemento window descrive anche le sue caratteristiche fisiche e il suo comportamento.

Dal punto di vista di un utente, le finestre di dialogo e i relativi componenti mostrano comportamenti diversi, in cui alcuni elementi della finestra di dialogo sono nascosti fino all’attivazione. Dal punto di vista della rappresentazione interna, non esiste un problema del genere. Ad esempio, la rappresentazione interna di una finestra di dialogo è simile a quella dei componenti che contiene, con l’eccezione che i componenti sono nidificati all’interno della finestra di dialogo.

Questa sezione descrive gli elementi XML che forniscono istruzioni ad AppMon. Questi elementi hanno nomi come `dialog` e `window` elemento. In questo documento viene utilizzato un font monospitato per distinguere gli elementi XML. La `*dialog*` l&#39;elemento identifica una finestra di dialogo che un file di script XML può causare la visualizzazione intenzionale o non intenzionale. La `*window*` l’elemento identifica un elemento finestra (finestra di dialogo o i componenti di una finestra di dialogo).

#### Gerarchia {#hierarchy}

Questo diagramma mostra la gerarchia di script e finestra di dialogo XML. Un file XML di script è conforme allo schema script.xsd, che include (in senso XML) lo schema window.xsd. Analogamente, un file XML della finestra di dialogo è conforme allo schema dialogs.xsd, che include anche lo schema window.xsd.

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

Gerarchia dello script e della finestra di dialogo XML

#### File XML script {#script-xml-files}

A *file XML script* specifica una serie di passaggi che indirizzano l&#39;applicazione nativa a spostarsi su determinati elementi della finestra e quindi a fornire risposte a tali elementi. La maggior parte delle risposte è composta da testo o tasti che corrispondono all’input che un utente immette a un campo, a una casella combinata o a un pulsante nella finestra di dialogo corrispondente.

Lo scopo del supporto del servizio Generate PDF per i file XML di script è quello di indirizzare un&#39;applicazione nativa alla stampa di un file nativo. Tuttavia, i file XML di script possono essere utilizzati per eseguire qualsiasi attività che un utente può eseguire durante l&#39;interazione con le finestre di dialogo dell&#39;applicazione nativa.

I passaggi in un file XML di script vengono eseguiti in ordine, senza alcuna possibilità di diramazione. L’unico test condizionale supportato è per timeout/tentativi, il che causa la chiusura di uno script se un passaggio non viene completato correttamente entro un periodo di tempo specifico e dopo un numero specifico di tentativi.

Oltre ai passaggi sequenziali, le istruzioni all’interno di un passaggio vengono eseguite in ordine. È necessario assicurarsi che i passaggi e le istruzioni rispecchino l&#39;ordine in cui un utente eseguirà gli stessi passaggi.

Ogni passaggio in un file XML di script identifica l&#39;elemento finestra che deve essere visualizzato se le istruzioni del passaggio vengono eseguite correttamente. Se durante l’esecuzione di un passaggio di script viene visualizzata una finestra di dialogo imprevista, il servizio Generate PDF cerca i file XML della finestra di dialogo come descritto nella sezione successiva.

#### File XML della finestra di dialogo {#dialog-xml-files}

L&#39;esecuzione di applicazioni native visualizza diverse finestre di dialogo, che vengono visualizzate indipendentemente dal fatto che le applicazioni native siano in modalità visibile o invisibile. Le finestre di dialogo possono essere generate dal sistema operativo o dall&#39;applicazione stessa. Quando le applicazioni native sono in esecuzione sotto il controllo del servizio Generate PDF, le finestre di dialogo del sistema e dell’applicazione nativa vengono visualizzate in una finestra invisibile.

A *file XML di dialogo* specifica il modo in cui il servizio Generate PDF risponde alle finestre di dialogo del sistema o dell&#39;applicazione nativa. I file XML della finestra di dialogo consentono al servizio Generate PDF di rispondere alle finestre di dialogo non richieste in modo da facilitare il processo di conversione.

Quando nel sistema o nell’applicazione nativa viene visualizzata una finestra di dialogo non gestita dal file XML di script attualmente in esecuzione, il servizio Generate PDF cerca i file XML di dialogo in questo ordine, arrestandosi quando trova una corrispondenza:

* appmon.*[nomeapp]*.aggiuntivo.*[locale]*.xml
* appmon.*[nomeapp].[locale]*.xml (non modificare il file).
* appmon.global.*[locale]*.xml (non modificare il file).

Se il servizio Genera PDF trova una corrispondenza per la finestra di dialogo, la ignora inviando il tasto o un’altra azione specificata per la finestra di dialogo. Se le istruzioni per la finestra di dialogo specificano un messaggio di interruzione, il servizio Generate PDF interrompe il processo attualmente in esecuzione e genera un messaggio di errore. Tale messaggio di interruzione sarebbe specificato nel `abortMessage` elemento nella grammatica XML dello script.

Se il servizio Genera PDF rileva una finestra di dialogo non descritta in nessuno dei file precedentemente elencati, il servizio Genera PDF incorpora la didascalia della finestra di dialogo nella voce del file di registro. Il processo attualmente in esecuzione alla fine si interrompe. È quindi possibile utilizzare le informazioni contenute nel file di registro per comporre nuove istruzioni nel file XML della finestra di dialogo aggiuntivo per l&#39;applicazione nativa.

### Aggiunta o modifica del supporto per un formato di file nativo {#adding-or-modifying-support-for-a-native-file-format}

Questa sezione descrive le attività da eseguire per supportare altri formati di file nativi o per modificare il supporto di un formato di file nativo già supportato.

Prima di poter aggiungere o modificare il supporto, è necessario completare le seguenti attività.

#### Scelta di uno strumento per identificare gli elementi della finestra {#choosing-a-tool-for-identifying-window-elements}

I file XML di dialogo e script richiedono l’identificazione dell’elemento finestra (finestra di dialogo, campo o altro componente di dialogo) a cui risponde l’elemento di dialogo o script. Ad esempio, dopo che uno script richiama un menu per un&#39;applicazione nativa, lo script deve identificare l&#39;elemento della finestra in quel menu a cui devono essere applicati i tasti o un&#39;azione.

È possibile identificare facilmente una finestra di dialogo in base alla didascalia visualizzata nella relativa barra del titolo. Tuttavia, è necessario utilizzare uno strumento come Microsoft Spy++ per identificare gli elementi della finestra di livello inferiore. Gli elementi della finestra di livello inferiore possono essere identificati attraverso una varietà di attributi, che non sono ovvi. Inoltre, ogni applicazione nativa può identificare il proprio elemento finestra in modo diverso. Di conseguenza, esistono diversi modi per identificare un elemento finestra. Di seguito è riportato l’ordine consigliato per considerare l’identificazione degli elementi della finestra:

1. Didascalia se è univoca
1. ID controllo, che può essere univoco o meno per una determinata finestra di dialogo
1. Nome della classe, che può essere univoco o meno

È possibile utilizzare uno o più di questi tre attributi per identificare una finestra.

Se gli attributi non identificano una didascalia, è invece possibile identificare un elemento finestra utilizzando il relativo indice rispetto al relativo elemento padre. Un *index* specifica la posizione dell&#39;elemento finestra rispetto agli elementi della finestra di pari livello. Spesso, gli indici sono l&#39;unico modo per identificare le caselle combinate.

Tieni presente i seguenti problemi:

* Microsoft Spy++ visualizza i sottotitoli utilizzando una e commerciale (&amp;) per identificare l’hot key della didascalia. Ad esempio, Spy++ mostra la didascalia di una finestra di dialogo Stampa come `Pri&nt`, che indica che il tasto di scelta rapida è *n*. I titoli delle didascalie negli script e nei file XML della finestra di dialogo devono omettere le e commerciali.
* Alcune didascalie includono interruzioni di riga. il servizio Generate PDF non è in grado di identificare le interruzioni di riga. Se una didascalia include un&#39;interruzione di riga, includerne una quantità sufficiente per distinguerla dalle altre voci di menu, quindi utilizzare espressioni regolari per la parte omessa. Un esempio è ( `^Long caption title$`). (Vedi [Utilizzo di espressioni regolari negli attributi della didascalia](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes).)
* Utilizzare entità carattere (o sequenze di escape) per caratteri XML riservati. Ad esempio, utilizza `&` e commerciali, `<` e `>` per simboli inferiori e maggiori di, `&apos;` per gli apostrofi, e `&quot;` tra virgolette.

Se si prevede di lavorare su file XML di dialogo o script, è necessario installare l&#39;applicazione Microsoft Spy++.

#### Estrazione della finestra di dialogo e dei file di script {#unpackaging-the-dialog-and-script-files}

I file di dialogo e script si trovano nel file appmondata.jar . Prima di poter modificare uno qualsiasi di questi file o aggiungere nuovi file di script o di dialogo, devi rimuovere il pacchetto da questo file JAR. Ad esempio, si supponga di voler aggiungere il supporto per l&#39;applicazione EditPlus. Si creano due file XML denominati appmon.editplus.script.en_US.xml e appmon.editplus.script.addizione.en_US.xml. Questi script XML devono essere aggiunti al file adobe-appmondata.jar in due posizioni, come specificato di seguito:

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. Il file adobe-livecycle-native-jboss-x86_win32.ear si trova nella cartella di esportazione in *[Directory di installazione dei moduli AEM]\*configurationManager. (se AEM Forms è implementato su un altro server applicativo J2EE, sostituisci il file adobe-livecycle-native-jboss-x86_win32.ear con il file EAR corrispondente al server dell&#39;applicazione J2EE.)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (il file adobe-appmondata.jar si trova nel file adobe-generatepdf-dsc.jar ). Il file adobe-generatepdf-dsc.jar si trova nel *[Directory di installazione dei moduli AEM]*\deploy.

Dopo aver aggiunto questi file XML al file adobe-appmondata.jar, devi ridistribuire il componente GeneratePDF. Per aggiungere file XML di dialogo e script al file adobe-appmondata.jar, esegui le seguenti operazioni:

1. Utilizzando uno strumento come WinZip o WinRAR, apri adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar file.
1. Aggiungi la finestra di dialogo e i file XML di script al file appmondata.jar o modifica i file XML esistenti in questo file. (Vedi [Creazione o modifica di un file XML di script per un&#39;applicazione nativa](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)e [Creazione o modifica di un file XML di dialogo aggiuntivo per un&#39;applicazione nativa](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).)
1. Utilizzando uno strumento come WinZip o WinRAR, apri adobe-generatepdf-dsc.jar > adobe-appmondata.jar.
1. Aggiungi la finestra di dialogo e i file XML di script al file appmondata.jar o modifica i file XML esistenti in questo file. (Vedi [Creazione o modifica di un file XML di script per un&#39;applicazione nativa](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)e [Creazione o modifica di un file XML di dialogo aggiuntivo per un&#39;applicazione nativa](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).) Dopo aver aggiunto i file XML al file adobe-appmondata.jar, inserisci il nuovo file adobe-appmondata.jar nel file adobe-generatepdf-dsc.jar .
1. Se è stato aggiunto il supporto per un formato di file nativo aggiuntivo, creare una variabile di ambiente di sistema che fornisca il percorso dell&#39;applicazione (Vedere [Creazione di una variabile di ambiente per individuare l&#39;applicazione nativa](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application).)

**Per ridistribuire il componente GeneratePDF**

1. Accedi a Workbench.
1. Seleziona **Finestra** > **Mostra visualizzazioni** > **Componenti**. Questa azione aggiunge la vista Componenti a Workbench.
1. Fare clic con il pulsante destro del mouse sul componente GeneratePDF, quindi selezionare **Interrompi componente**.
1. Quando il componente è stato arrestato, fare clic con il pulsante destro del mouse e selezionare Disinstalla componente per rimuoverlo.
1. Fai clic con il pulsante destro del mouse sul pulsante **Componenti** e seleziona **Installazione componente**.
1. Cerca e seleziona il file adobe-generatepdf-dsc.jar modificato, quindi fai clic su Apri. Accanto al componente GeneratePDF viene visualizzato un quadrato rosso.
1. Espandere il componente GeneratePDF, selezionare Service Descriptor, quindi fare clic con il pulsante destro del mouse su GeneratePDFService e selezionare Activate Service.
1. Nella finestra di dialogo di configurazione visualizzata, immetti i valori di configurazione applicabili. Se si lasciano vuoti questi valori, vengono utilizzati i valori di configurazione predefiniti.
1. Fare clic con il pulsante destro del mouse su Genera PDF e selezionare Avvia componente.
1. Espandi Servizi attivi. Se è in esecuzione, accanto al nome del servizio viene visualizzata una freccia verde. In caso contrario, il servizio si trova in uno stato di arresto.
1. Se il servizio è in stato di arresto, fare clic con il pulsante destro del mouse sul nome del servizio e selezionare Avvia servizio.

### Creazione o modifica di un file XML di script per un&#39;applicazione nativa {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Se si desidera indirizzare i file a una nuova applicazione nativa, è necessario creare un file XML di script per tale applicazione. Se si desidera modificare il modo in cui il servizio Generate PDF interagisce con un&#39;applicazione nativa già supportata, è necessario modificare lo script per tale applicazione.

Lo script contiene istruzioni che navigano tra gli elementi della finestra dell’applicazione nativa e che forniscono risposte specifiche a tali elementi. Il file che contiene queste informazioni è appmon.*[nomeapp]*.script.*[locale]*.xml. Un esempio è appmon.blocco note.script.en_US.xml.

#### Identificazione dei passaggi che lo script deve eseguire {#identifying-steps-the-script-must-execute}

Utilizzando l&#39;applicazione nativa, determinare gli elementi della finestra da navigare e ogni risposta da eseguire per stampare il documento. Osserva le finestre di dialogo risultanti da qualsiasi risposta. I passaggi saranno simili ai seguenti:

1. Selezionare File > Apri.
1. Specificare il percorso, quindi fare clic su Apri.
1. Selezionare File > Stampa nella barra dei menu.
1. Specificare le proprietà richieste per la stampante.
1. Selezionare Stampa e attendere che venga visualizzata la finestra di dialogo Salva con nome. Per specificare la destinazione del file PDF, è necessaria la finestra di dialogo Salva con nome per il servizio Genera PDF.

#### Identificazione delle finestre di dialogo specificate negli attributi della didascalia {#identifying-the-dialogs-specified-in-caption-attributes}

Utilizza Microsoft Spy++ per ottenere le identità delle proprietà degli elementi finestra nell&#39;applicazione nativa. Per scrivere script è necessario disporre di queste identità.

#### Utilizzo di espressioni regolari negli attributi della didascalia {#using-regular-expressions-in-caption-attributes}

È possibile utilizzare espressioni regolari nelle specifiche delle didascalie. Il servizio Generate PDF utilizza la variabile `java.util.regex.Matcher` per supportare espressioni regolari. Questa utility supporta le espressioni regolari descritte in `java.util.regex.Pattern`.

**Espressione regolare che gestisce il nome del file aggiunto al Blocco note nel banner Blocco note**

```as3
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. --> 
 <step> 
     <expectedWindow> 
         <window caption=".*Notepad"/> 
     </expectedWindow> 
 </step>
```

**Espressione regolare che distingue Stampa da Imposta di stampa**

```as3
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. --> 
 <windowList> 
     <window controlID="0x01" caption="^Print$" action="press"/> 
 </windowList>
```

#### Ordinamento degli elementi windowList e windowList {#ordering-the-window-and-windowlist-elements}

Devi ordinare `window` e `windowList` elementi come segue:

* Quando sono multipli `window` gli elementi vengono visualizzati come elementi secondari in un `windowList` o `dialog` elemento, ordinali `window` elementi in ordine decrescente, con le lunghezze dei `caption` nomi che indicano la posizione nell&#39;ordine.
* Quando sono multipli `windowList` gli elementi vengono visualizzati in un `window` elemento, ordinali `windowList` elementi in ordine decrescente, con le lunghezze dei `caption` attributi del primo `indexes/`che indica la posizione nell’ordine.

**Ordinamento degli elementi della finestra in un file di dialogo**

```as3
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <window caption="Unexpected Failure in DebugActiveProcess"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Adobe Acrobat - License Agreement"> 
     <…> 
 </window> 
  
 <!-- Caption length is 33 characters. --> 
 <window caption="Microsoft Visual.*Runtime Library"> 
     <…> 
 </window> 
  
 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. --> 
 <window caption="Adobe Acrobat - Registration"> 
     <…> 
 </window>
```

**Ordinamento degli elementi della finestra all&#39;interno di un elemento windowList**

```as3
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. --> 
 <windowList> 
     <window caption="Can&apos;t exit design mode because.* cannot be created"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="Do you want to continue loading the project?"/> 
     <window className="Button" caption="No" action="press"/> 
 </windowList> 
 <windowList> 
     <window caption="The macros in this project are disabled"/> 
     <window className="Button" caption="OK" action="press"/> 
 </windowList>
```

### Creazione o modifica di un file XML di dialogo aggiuntivo per un&#39;applicazione nativa {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Se si crea uno script per un&#39;applicazione nativa non supportata in precedenza, è necessario creare anche un file XML di dialogo aggiuntivo per tale applicazione. Ogni applicazione nativa utilizzata da AppMon deve disporre di un solo file XML di dialogo aggiuntivo. Il file XML della finestra di dialogo aggiuntivo è necessario anche se non sono previste finestre di dialogo non richieste. La finestra di dialogo aggiuntiva deve avere almeno un `window` anche se `window` è semplicemente un segnaposto.

>[!NOTE]
>
>In questo contesto, il termine aggiuntivo indica il contenuto dell&#39;appello.[application name].addizione.[locale]file .xml. Tale file specifica le sostituzioni e le aggiunte al file XML della finestra di dialogo.

È inoltre possibile modificare il file XML della finestra di dialogo aggiuntivo per un&#39;applicazione nativa per i seguenti scopi:

* Per ignorare il file XML della finestra di dialogo per un&#39;applicazione con una risposta diversa
* Per aggiungere una risposta a una finestra di dialogo non indirizzata nel file XML della finestra di dialogo per l&#39;applicazione

Il nome file che identifica un file dialogXML aggiuntivo è appmon.*[nomeapp]*.addizione.*[locale]*.xml. Un esempio è appmon.excel.addizione.en_US.xml.

Il nome del file XML della finestra di dialogo aggiuntivo deve utilizzare l&#39;oggetto format.*[application name]*.addizione.*[locale]*.xml, dove *application name* deve corrispondere esattamente al nome dell&#39;applicazione utilizzato nel file di configurazione XML e nello script.

>[!NOTE]
>
>Nessuna delle applicazioni generiche specificate nel file di configurazione native2pdfconfig.xml dispone di un file XML di dialogo primario. La sezione [Aggiunta o modifica del supporto per un formato di file nativo](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) descrive tali specifiche.

Devi ordinare `windowList` elementi che vengono visualizzati come elementi secondari in un `window` elemento. (Vedi [Ordinamento degli elementi windowList e windowList](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements).)

### Modifica del file XML della finestra di dialogo generale {#modifying-the-general-dialog-xml-file}

È possibile modificare il file XML della finestra di dialogo generale per rispondere alle finestre di dialogo generate dal sistema o per rispondere alle finestre di dialogo comuni a più applicazioni.

#### Aggiunta di una voce filetype nel file di configurazione XML {#adding-a-filetype-entry-in-the-xml-configuration-file}

Questa procedura spiega come aggiornare il file di configurazione del servizio Generate PDF per associare i tipi di file alle applicazioni native. Per aggiornare questo file di configurazione, è necessario utilizzare la console di amministrazione per esportare i dati di configurazione in un file. Il nome file predefinito per i dati di configurazione è native2pdfconfig.xml.

**Aggiornare il file di configurazione del servizio Generate PDF**

1. Seleziona **Pagina principale** > **Servizi** > **Generatore Adobe PDF** > **File di configurazione**, quindi seleziona **Configurazione esportazione**.
1. Modifica la `filetype-settings` nel file native2pdfconfig.xml, se necessario.
1. Seleziona **Pagina principale** > **Servizi** > **Generatore Adobe PDF** >**File di configurazione**, quindi seleziona **Importa configurazione**. I dati di configurazione vengono importati nel servizio Generate PDF, sostituendo le impostazioni precedenti.

>[!NOTE]
>
>Il nome dell&#39;applicazione è specificato come valore del `GenericApp` dell’elemento `name` attributo. Questo valore deve corrispondere esattamente al nome corrispondente specificato nello script sviluppato per quell&#39;applicazione. Allo stesso modo, il `GenericApp` dell’elemento `displayName` l’attributo deve corrispondere esattamente a quello dello script corrispondente `expectedWindow` didascalia della finestra. Tale equivalenza viene valutata dopo la risoluzione di eventuali espressioni regolari visualizzate nella `displayName` o `caption` attributi.

In questo esempio, i dati di configurazione predefiniti forniti con il servizio Generate PDF sono stati modificati per specificare che Notepad (non Microsoft Word) deve essere utilizzato per elaborare i file con estensione .txt. Prima di questa modifica, Microsoft Word è stato specificato come applicazione nativa che deve elaborare tali file.

**Modifiche per l&#39;indirizzamento dei file di testo a Notepad (native2pdfconfig.xml)**

```as3
 <filetype-settings> 
  
 <!-- Some native app file types were omitted for brevity. --> 
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. --> 
             <GenericApp 
                 extensions="txt" 
                 name="Notepad" displayName=".*Notepad"/> 
             <GenericApp  
                 extensions="wpd"  
                 name="WordPerfect" displayName="Corel WordPerfect"/> 
             <GenericApp extensions="pmd,pm6,p65,pm"  
                 name="PageMaker" displayName="Adobe PageMaker"/> 
             <GenericApp extensions="fm"  
                 name="FrameMaker" displayName="Adobe FrameMaker"/> 
             <GenericApp extensions="psd"  
                 name="Photoshop" displayName="Adobe Photoshop"/> 
         </settings> 
     </filetype-settings>
```

#### Creazione di una variabile di ambiente per individuare l&#39;applicazione nativa {#creating-an-environment-variable-to-locate-the-native-application}

Creare una variabile di ambiente che specifica la posizione dell&#39;eseguibile dell&#39;applicazione nativa. La variabile deve utilizzare il formato *[application name]*_PATH, dove *application name* deve corrispondere esattamente al nome dell&#39;applicazione utilizzato nel file di configurazione XML e nello script e dove il percorso contiene il percorso dell&#39;eseguibile tra virgolette doppie. Un esempio di tale variabile di ambiente è `Photoshop_PATH`.

Dopo aver creato la nuova variabile di ambiente, è necessario riavviare il server in cui viene distribuito il servizio Generate PDF.

**Creare una variabile di sistema nell&#39;ambiente Windows XP**

1. Seleziona **Pannello di controllo Campaign > Sistema**.
1. Nella finestra di dialogo Proprietà sistema, fai clic su **Avanzate** , quindi fai clic su **Variabili di ambiente**.
1. Nella finestra di dialogo Variabili di sistema della finestra di dialogo Variabili di ambiente fare clic su **Nuovo**.
1. Nella finestra di dialogo Nuova variabile di sistema, **Nome della variabile** digitare un nome che utilizzi il formato *[application name]*_PERCORSO.
1. In **Valore variabile** digitare il percorso completo e il nome file del file eseguibile dell&#39;applicazione, quindi fare clic su **OK**. Ad esempio, digitare: `c:\windows\Notepad.exe`
1. Nella finestra di dialogo Variabili di ambiente, fai clic su **OK**.

**Crea una variabile di sistema dalla riga di comando**

1. In una finestra della riga di comando, digitare la definizione della variabile utilizzando il seguente formato:

   ```as3
            [applicationname]_PATH=[Full path name]
   ```

   Ad esempio, digitare: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Avvia un nuovo prompt della riga di comando per rendere effettiva la variabile di sistema.

#### File XML {#xml-files}

AEM Forms include file XML di esempio che fanno sì che il servizio Generate PDF utilizzi Notepad per elaborare qualsiasi file con estensione .txt. Questo codice è incluso in questa sezione. Inoltre, devi apportare le altre modifiche descritte in questa sezione.

#### File XML della finestra di dialogo aggiuntivo {#additional-dialog-xml-file}

Questo esempio contiene le finestre di dialogo aggiuntive per l&#39;applicazione Notepad. Queste finestre di dialogo possono essere in aggiunta a quelle specificate dal servizio Genera PDF.

**Finestra di dialogo Blocco note(appmon.blocco note.addizione.en_US.xml)**

```as3
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd"> 
     <window caption="Caption Title"> 
         <windowList> 
             <window className="Button" caption="OK" action="press"/> 
         </windowList> 
     </window> 
 </dialogs>
```

#### File XML script {#script-xml-file}

Questo esempio specifica come il servizio Generate PDF deve interagire con Notepad per stampare i file utilizzando la stampante Adobe PDF.

**File XML script del Blocco note (appmon.blocco note.script.en_US.xml)**

```as3
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<!-- 
* 
* ADOBE CONFIDENTIAL 
* ___________________ 
* Copyright 2004 - 2005 Adobe Systems Incorporated 
* All Rights Reserved. 
* 
* NOTICE:  All information contained herein is, and remains 
* the property of Adobe Systems Incorporated and its suppliers, 
* if any.  The intellectual and technical concepts contained 
* herein are proprietary to Adobe Systems Incorporated and its 
* suppliers and may be covered by U.S. and Foreign Patents, 
* patents in process, and are protected by trade secret or copyright law. 
* Dissemination of this information or reproduction of this material 
* is strictly forbidden unless prior written permission is obtained 
* from Adobe Systems Incorporated. 
*--> 
 
<!-- This file automates printing of text files via notepad to Adobe PDF printer. In order to see the complete hierarchy we recommend using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps--> 
 
<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd"> 
 
    <!-- In this step we wait for the application window to appear --> 
    <step> 
        <expectedWindow> 
            <window caption=".*Notepad"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->         
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Open...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear --> 
    <step> 
        <acquiredWindow> 
            <window caption="Open"> 
                <windowList> 
                    <window className="ComboBoxEx32"> 
                        <windowList> 
                            <window className="ComboBox"> 
                                <windowList> 
                                <window className="Edit" action="inputSourcePath"/> 
                                </windowList> 
                            </window> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Open" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Open" action="disappear"/> 
        </expectedWindow> 
        <pause value="30"/> 
    </step> 
     
    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog--> 
    <step> 
        <acquiredWindow> 
            <window caption=".*Notepad"> 
                <virtualInput> 
                    <menuBar> 
                        <selection> 
                            <name>File</name> 
                        </selection> 
                        <selection> 
                            <name>Print...</name> 
                        </selection> 
                    </menuBar> 
                </virtualInput> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print"> 
        </window> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the Print dialog and click on the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"> 
                        <windowList> 
                            <window className="Button" caption="Preferences" action="press"/> 
                        </windowList> 
                    </window> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which  has the caption '"View Adobe PDF results' and we click on the button OK. The expectation is that 'Printing Preferences' dialog disappears. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Printing Preferences"> 
                <windowList> 
                    <window caption="Adobe PDF Settings"> 
                        <windowList> 
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/> 
                        </windowList> 
                        <windowList> 
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/> 
                        </windowList> 
                    </window> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="OK" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Printing Preferences" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- In this step, we acquire the 'Print' dialog and click on the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. --> 
    <step> 
        <acquiredWindow> 
            <window caption="Print"> 
                <windowList> 
                    <window caption="General"/> 
                    <window className="Button" caption="^Print$" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Print" action="disappear"/> 
        </expectedWindow> 
    </step> 
    <step> 
        <expectedWindow> 
            <window caption="Save PDF File As"/> 
        </expectedWindow> 
    </step> 
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click on the Save button. The expectation is that the dialog disappears--> 
    <step> 
        <acquiredWindow> 
            <window caption="Save PDF File As"> 
                <windowList> 
                    <window className="Edit" action="inputDestinationPath"/> 
                </windowList> 
                <windowList> 
                    <window className="Button" caption="Save" action="press"/> 
                </windowList> 
            </window> 
        </acquiredWindow> 
        <expectedWindow> 
            <window caption="Save PDF File As" action="disappear"/> 
        </expectedWindow> 
    </step> 
     
    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. --> 
    <abortMessage msg="15078"/> 
</application>
```
