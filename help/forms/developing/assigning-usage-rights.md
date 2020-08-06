---
title: Assegnazione dei diritti di utilizzo
seo-title: Assegnazione dei diritti di utilizzo
description: 'null'
seo-description: 'null'
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
translation-type: tm+mt
source-git-commit: ba04fe705a91717f1d9658d436056ebddda6be3a
workflow-type: tm+mt
source-wordcount: '3895'
ht-degree: 0%

---


# Assegnazione dei diritti di utilizzo {#assigning-usage-rights}

## Informazioni su Acrobat Reader DC Extensions Service {#about-the-acrobat-reader-dc-extensions-service}

Il servizio di estensione Acrobat Reader DC consente alla vostra azienda di condividere facilmente documenti PDF interattivi estendendo le funzionalità di  Adobe Reader. Il servizio di estensione Acrobat Reader DC supporta completamente qualsiasi documento PDF, fino a PDF 1.7 incluso. Funziona con  Adobe Reader 7.0 e versioni successive. The service adds usage rights to a PDF document, activating features that are not usually available when a PDF document is opened using Adobe Reader. Gli utenti di terze parti non richiedono software o plug-in aggiuntivi per lavorare con i documenti abilitati per i diritti.

È possibile eseguire le seguenti attività utilizzando il servizio di estensione Acrobat Reader DC:

* Apply usage rights to PDF documents. Per ulteriori informazioni, vedere [Applicazione dei diritti di utilizzo ai documenti](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)PDF.
* Rimuovere i diritti di utilizzo dai documenti PDF. For information, see [Removing Usage Rights from PDF Documents](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Recuperare i dettagli delle credenziali. Per ulteriori informazioni, vedere [Recupero di informazioni](assigning-usage-rights.md#retrieving-credential-information)sulle credenziali.

>[!NOTE]
>
>For more information about the Acrobat Reader DC extensions service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Applicazione dei diritti di utilizzo ai documenti PDF {#applying-usage-rights-to-pdf-documents}

You can apply usage rights to PDF documents using the Acrobat Reader DC extensions Java Client API and web service. Usage rights pertain to functionality that is available by default in Acrobat but not in Adobe Reader, such as the ability to add comments to a form or to fill in form fields and save the form. I documenti PDF a cui sono stati applicati diritti di utilizzo sono denominati documenti abilitati per i diritti. Un utente che apre un documento con diritti in  Adobe Reader può eseguire operazioni abilitate per tale documento specifico.

>[!NOTE]
>
>When applying usage rights to PDF documents using the `applyUsageRights` method, which is part of the Java API, you can set the `isModeFinal` parameter of the `ReaderExtensionsOptionSpec` object to `false`. This results in the forms processed counter not being updated and an improvement in performance. Se non si desidera aggiornare il contatore dei moduli elaborati, è consigliabile impostare il `isModeFinal` parametro su `false`.

>[!NOTE]
>
>Per ulteriori informazioni sul servizio di estensione Acrobat Reader DC, vedere [Servizi di riferimento per  AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary-of-steps}

Per applicare diritti di utilizzo a un documento PDF, effettuare le seguenti operazioni:

1. Includere i file di progetto.
1. Creare un oggetto client con estensioni Acrobat Reader DC.
1. Recuperare un documento PDF.
1. Specificate i diritti di utilizzo da applicare.
1. Applicare i diritti di utilizzo al documento PDF.
1. Salvare il documento PDF con diritti.

**Includi file di progetto**

Includete i file necessari nel progetto di sviluppo. Se state creando un&#39;applicazione client utilizzando Java, includete i file JAR necessari. Se utilizzate servizi Web, accertatevi di includere i file proxy.

**Create a Acrobat Reader DC extensions Client object**

Per eseguire un&#39;operazione di Acrobat Reader DC Extension Service a livello di programmazione, è necessario creare un oggetto client del servizio di estensione Acrobat Reader DC. Se utilizzate l&#39;API Java delle estensioni Acrobat Reader DC, create un `ReaderExtensionsServiceClient` oggetto. If you are using the Acrobat Reader DC extensions web service API, create a `ReaderExtensionsServiceService` object.

**Recupero di un documento PDF**

È necessario recuperare un documento PDF per applicare i diritti di utilizzo. I documenti PDF con diritti di utilizzo contengono un dizionario dei diritti di utilizzo. Quando  Adobe Reader apre un documento contenente tale dizionario, attiva i diritti di utilizzo specificati nel dizionario solo per tale documento. Se il documento non contiene un dizionario dei diritti di utilizzo, il servizio di estensione Acrobat Reader DC ne crea uno. Se contiene già un dizionario, il servizio di estensione Acrobat Reader DC sovrascrive i diritti di utilizzo esistenti con quelli specificati. The dictionary specifies which usage rights are enabled. When a user opens the document in Adobe Reader, only the usage rights specified in the dictionary are permitted.

**Specificare i diritti di utilizzo da applicare**

I diritti di utilizzo che è possibile impostare sono determinati da una credenziale acquistata da Adobe Systems Incorporated. Le credenziali forniscono in genere l&#39;autorizzazione per impostare un gruppo di diritti di utilizzo correlati, ad esempio quelli relativi ai moduli interattivi. Ciascuna credenziale consente di creare un certo numero di documenti PDF abilitati per i diritti. Una credenziale di valutazione dà il diritto di creare un numero illimitato di bozze di documenti.

>[!NOTE]
>
>Se si tenta di assegnare un diritto di utilizzo non consentito dalla credenziale, si causerà un&#39;eccezione.

**Applicazione dei diritti di utilizzo al documento PDF**

Per applicare diritti di utilizzo a un documento PDF, è necessario fare riferimento all&#39;alias della credenziale utilizzata per applicare diritti di utilizzo (una credenziale viene in genere installata durante l&#39;installazione di  AEM Forms). È inoltre necessario specificare il documento PDF a cui vengono applicati i diritti di utilizzo. Per informazioni sulla configurazione di una credenziale, consultate la guida all&#39;installazione e alla distribuzione per il server delle applicazioni.

**Salvare il documento PDF con diritti**

Dopo che il servizio di estensione Acrobat Reader DC applica i diritti di utilizzo a un documento PDF, è possibile salvare il documento PDF con diritti abilitati come file PDF.

**Consulta anche**

[Applicazione dei diritti di utilizzo tramite l&#39;API Java](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Applicazione dei diritti di utilizzo tramite l&#39;API del servizio Web](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Avvio rapido di Acrobat Reader DC Extensions Service API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Applicazione dei diritti di utilizzo tramite l&#39;API Java {#apply-usage-rights-using-the-java-api}

Applicazione dei diritti di utilizzo a un documento PDF tramite l&#39;API Acrobat Reader DC Extensions (Java):

1. Includi file di progetto

   Includete file JAR client, ad esempio adobe-reader-extensions-client.jar, nel percorso di classe del progetto Java.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   * Creare un `ServiceClientFactory` oggetto che contenga proprietà di connessione.
   * Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore e passando l&#39; `ServiceClientFactory` oggetto.

1. Recuperare un documento PDF.

   * Creare un oggetto `java.io.FileInputStream` che rappresenti il documento PDF utilizzando il relativo costruttore e passando un valore di stringa che specifica la posizione del documento PDF.
   * Creare un `com.adobe.idp.Document` oggetto utilizzando il relativo costruttore e passando l&#39; `java.io.FileInputStream` oggetto.

1. Specificate i diritti di utilizzo da applicare.

   * Creare un `UsageRights` oggetto che rappresenti i diritti di utilizzo utilizzando il relativo costruttore.
   * Per ogni diritto di utilizzo da applicare, richiamare un metodo corrispondente che appartiene all&#39; `UsageRights` oggetto. Ad esempio, per aggiungere il diritto di `enableFormFillIn` utilizzo, richiamare il metodo dell&#39; `UsageRights` oggetto `enableFormFillIn` e passare `true`. Ripetete questo passaggio per ogni diritto di utilizzo da applicare.

1. Applicare i diritti di utilizzo al documento PDF.

   * Creare un `ReaderExtensionsOptionSpec` oggetto utilizzando il relativo costruttore. Questo oggetto contiene le opzioni di esecuzione richieste dal servizio di estensione Acrobat Reader DC. Quando si richiama questo costruttore, è necessario specificare i seguenti valori:

      * L&#39; `UsageRights` oggetto che contiene i diritti di utilizzo da applicare al documento.
      * Valore stringa che specifica un messaggio visualizzato dall&#39;utente all&#39;apertura in  Adobe Reader 7.x del documento PDF con diritti. Questo messaggio non viene visualizzato in  Adobe Reader 8.0.
   * Per applicare i diritti di utilizzo al documento PDF, richiamare il metodo dell&#39; `ReaderExtensionsServiceClient` oggetto `applyUsageRights` e passare i seguenti valori:

      * L&#39; `com.adobe.idp.Document` oggetto che contiene il documento PDF a cui sono applicati i diritti di utilizzo.
      * Valore stringa che specifica l&#39;alias della credenziale che consente di applicare diritti di utilizzo.
      * Un valore di stringa che specifica il valore della password corrispondente. (Attualmente questo parametro viene ignorato. Potete passare `null`.)
   * L&#39; `ReaderExtensionsOptionSpec` oggetto che contiene le opzioni di esecuzione.

   Il `applyUsageRights` metodo restituisce un `com.adobe.idp.Document` oggetto che contiene il documento PDF abilitato per i diritti.

1. Salvare il documento PDF con diritti.

   * Create un `java.io.File` oggetto e accertatevi che l&#39;estensione del file sia .pdf.
   * Richiamare il metodo `com.adobe.idp.Document` dell&#39;oggetto `copyToFile` per copiare il contenuto dell&#39; `com.adobe.idp.Document` oggetto nel file (assicurarsi di utilizzare l&#39; `com.adobe.idp.Document` oggetto restituito dal `applyUsageRights` metodo).

**Consulta anche**

[Applicazione dei diritti di utilizzo ai documenti PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Avvio rapido (modalità SOAP):applicazione dei diritti di utilizzo tramite l&#39;API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Applicazione dei diritti di utilizzo tramite l&#39;API del servizio Web {#apply-usage-rights-using-the-web-service-api}

Applicazione dei diritti di utilizzo a un documento PDF tramite l&#39;API delle estensioni Acrobat Reader DC (servizio Web):

1. Includere i file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurarsi di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituire `localhost` con l&#39;indirizzo IP del server che ospita  AEM Forms.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   * Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore predefinito.
   * Creare un `ReaderExtensionsServiceClient.Endpoint.Address` oggetto utilizzando il `System.ServiceModel.EndpointAddress` costruttore. Passate un valore di stringa che specifica il WSDL al servizio AEM Forms  (ad esempio, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Accertatevi di specificare `?blob=mtom`.)
   * Creare un `System.ServiceModel.BasicHttpBinding` oggetto ottenendo il valore del `ReaderExtensionsServiceClient.Endpoint.Binding` campo. Inserite il valore restituito in `BasicHttpBinding`.
   * Impostare il campo `System.ServiceModel.BasicHttpBinding` dell&#39; `MessageEncoding` oggetto su `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilitate l&#39;autenticazione HTTP di base eseguendo le seguenti operazioni:

      * Assegnare al campo il nome utente del modulo AEM `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Assegnare il valore della password corrispondente al campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Assegnare il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegnare il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recuperare un documento PDF.

   * Creare un `BLOB` oggetto utilizzando il relativo costruttore. The `BLOB` object is used to store a PDF document to which a usage rights is applied.
   * Creare un `System.IO.FileStream` oggetto richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF e la modalità di apertura del file.
   * Creare un array di byte che memorizza il contenuto dell&#39; `System.IO.FileStream` oggetto. È possibile determinare la dimensione dell&#39;array di byte ottenendo la proprietà dell&#39; `System.IO.FileStream` oggetto `Length` .
   * Compilare l&#39;array di byte con i dati del flusso richiamando il metodo dell&#39; `System.IO.FileStream` oggetto `Read` . Passare l&#39;array di byte, la posizione iniziale e la lunghezza del flusso da leggere.
   * Compilare l&#39; `BLOB` oggetto assegnandone `MTOM` la proprietà con il contenuto dell&#39;array di byte.

1. Specify usage rights to apply.

   * Creare un `UsageRights` oggetto che rappresenti i diritti di utilizzo utilizzando il relativo costruttore.
   * Per ogni diritto di utilizzo da applicare, assegnare il valore `true` al membro di dati corrispondente che appartiene all&#39; `UsageRights` oggetto. For example, to add the `enableFormFillIn` usage right, assign `true` to the `UsageRights` object’s `enableFormFillIn` data member. Ripetete questo passaggio per ogni diritto di utilizzo da applicare.

1. Applicare i diritti di utilizzo al documento PDF.

   * Creare un `ReaderExtensionsOptionSpec` oggetto utilizzando il relativo costruttore. Questo oggetto contiene le opzioni di esecuzione richieste dal servizio di estensione Acrobat Reader DC.
   * Assign the `UsageRights` object to the `ReaderExtensionsOptionSpec` object’s `usageRights` data member.
   * Assign a string value that specifies the message that a user sees when the rights-enabled PDF document is opened in Adobe Reader to the `ReaderExtensionsOptionSpec` object’s `message` data member.
   * Apply usage rights to the PDF document by invoking the `ReaderExtensionsServiceClient` object’s `applyUsageRights` method and passing the following values:

      * L&#39; `BLOB` oggetto che contiene il documento PDF a cui sono applicati i diritti di utilizzo.
      * Valore stringa che specifica l&#39;alias della credenziale che consente di applicare diritti di utilizzo.
      * Un valore di stringa che specifica il valore della password corrispondente. (Attualmente questo parametro viene ignorato. Potete passare `null`.)
   * L&#39; `ReaderExtensionsOptionSpec` oggetto che contiene le opzioni di esecuzione.

   Il `applyUsageRights` metodo restituisce un `BLOB` oggetto che contiene il documento PDF abilitato per i diritti.

1. Salvare il documento PDF con diritti.

   * Creare un `System.IO.FileStream` oggetto richiamandone il costruttore. Passa un valore di stringa che rappresenta la posizione del file del documento PDF abilitato per i diritti.
   * Creare un array di byte che memorizza il contenuto dei dati dell&#39; `BLOB` oggetto restituito dal `applyUsageRights` metodo. Compilare l&#39;array di byte ottenendo il valore del membro `BLOB` dati dell&#39; `MTOM` oggetto.
   * Creare un `System.IO.BinaryWriter` oggetto richiamando il relativo costruttore e passando l&#39; `System.IO.FileStream` oggetto.
   * Scrivere il contenuto dell&#39;array di byte in un file PDF richiamando il metodo dell&#39; `System.IO.BinaryWriter` oggetto `Write` e passando l&#39;array di byte.

**Consulta anche**

[Applicazione dei diritti di utilizzo ai documenti PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Chiamata  AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chiamata  AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Rimozione dei diritti di utilizzo dai documenti PDF {#removing-usage-rights-from-pdf-documents}

Potete rimuovere i diritti di utilizzo da un documento con diritti. Removing usage-rights from a rights-enabled PDF document is also necessary in order to perform other AEM Forms operations on it. Ad esempio, è necessario firmare (o certificare) digitalmente un documento PDF prima di impostare i diritti di utilizzo. Pertanto, se si desidera eseguire operazioni su un documento con diritti, è necessario rimuovere i diritti di utilizzo dal documento PDF, eseguire altre operazioni, ad esempio firmare digitalmente il documento e quindi riapplicare i diritti di utilizzo al documento.

>[!NOTE]
>
>For more information about the Acrobat Reader DC extensions service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary_of_steps-1}

Per rimuovere i diritti di utilizzo da un documento PDF abilitato per i diritti, effettuare le seguenti operazioni:

1. Includere i file di progetto.
1. Creare un oggetto client con estensioni Acrobat Reader DC.
1. Recuperare un documento PDF abilitato per diritti.
1. Rimuovere i diritti di utilizzo dal documento PDF.
1. Salvare il documento PDF.

**Includi file di progetto**

Includete i file necessari nel progetto di sviluppo. Se state creando un&#39;applicazione client utilizzando Java, includete i file JAR necessari. Se utilizzate servizi Web, accertatevi di includere i file proxy.

**Create a Acrobat Reader DC extensions Client object**

Before you can programmatically perform a Acrobat Reader DC extensions service operation, you must create a Acrobat Reader DC extensions service client object. Se utilizzate l&#39;API Java, create un `ReaderExtensionsServiceClient` oggetto. If you are using the Acrobat Reader DC extensions web service API, create a `ReaderExtensionsServiceService` object.

**Retrieve a rights-enabled PDF document**

Retrieve a rights-enabled PDF document in order to remove usage rights.

**Remove usage rights from the PDF document**

After you retrieve a rights-enabled PDF document, you can remove usage rights. Dopo aver rimosso i diritti di utilizzo, il documento PDF non disporrà di alcuna funzionalità aggiuntiva durante la visualizzazione in  Adobe Reader.

**Salvare il documento PDF**

You can save the PDF document that no longer contains usage-rights as a PDF file. Once saved as a PDF file, the PDF document can be viewed in Adobe Reader or Acrobat.

**Consulta anche**

[Remove usage rights using the Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Rimozione dei diritti di utilizzo tramite l&#39;API del servizio Web](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Avvio rapido di Acrobat Reader DC Extensions Service API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Applicazione dei diritti di utilizzo ai documenti PDF](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Rimuovere i diritti di utilizzo mediante l&#39;API Java {#remove-usage-rights-using-the-java-api}

Per rimuovere i diritti di utilizzo da un documento PDF abilitato per i diritti, utilizzate l&#39;API delle estensioni Acrobat Reader DC (Java):

1. Includere i file di progetto.

   Includete file JAR client, ad esempio adobe-reader-extensions-client.jar, nel percorso di classe del progetto Java.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore e passando un `ServiceClientFactory` oggetto che contiene le proprietà di connessione.

1. Recuperare un documento PDF.

   * Create a `java.io.FileInputStream` object that represent the rights-enabled PDF document by using its constructor and passing a string value that specifies the location of the PDF document.
   * Creare un `com.adobe.idp.Document` oggetto utilizzando il relativo costruttore e passando l&#39; `java.io.FileInputStream` oggetto.

1. Rimuovere i diritti di utilizzo dal documento PDF.

   Rimuovere i diritti di utilizzo dal documento PDF richiamando il `ReaderExtensionsServiceClient` metodo dell&#39; `removeUsageRights` oggetto e passando l&#39; `com.adobe.idp.Document` oggetto che contiene il documento PDF abilitato per i diritti. This method returns a `com.adobe.idp.Document` object that contains a PDF document that does not have usage rights.

1. Applicare i diritti di utilizzo al documento PDF.

   * Create a `java.io.File` object and ensure that the file extension is .PDF.
   * Richiamare il metodo `Document` dell&#39;oggetto `copyToFile` per copiare il contenuto dell&#39; `Document` oggetto nel file (assicurarsi di utilizzare l&#39; `Document` oggetto restituito dal `removeUsageRights` metodo).

**Consulta anche**

[Rimozione dei diritti di utilizzo dai documenti PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Quick Start (SOAP mode): Removing usage rights from a PDF document using the Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Remove usage rights using the web service API {#remove-usage-rights-using-the-web-service-api}

Remove usage rights from a rights-enabled PDF document by using the Acrobat Reader DC extensions API (web service):

1. Includere i file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurarsi di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituire `localhost` con l&#39;indirizzo IP del server che ospita  AEM Forms.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   * Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore predefinito.
   * Creare un `ReaderExtensionsServiceClient.Endpoint.Address` oggetto utilizzando il `System.ServiceModel.EndpointAddress` costruttore. Passate un valore di stringa che specifica il WSDL al servizio AEM Forms  (ad esempio, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Accertatevi di specificare `?blob=mtom`.)
   * Creare un `System.ServiceModel.BasicHttpBinding` oggetto ottenendo il valore del `ReaderExtensionsServiceClient.Endpoint.Binding` campo. Inserite il valore restituito in `BasicHttpBinding`.
   * Impostare il campo `System.ServiceModel.BasicHttpBinding` dell&#39; `MessageEncoding` oggetto su `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilitate l&#39;autenticazione HTTP di base eseguendo le seguenti operazioni:

      * Assegnare al campo il nome utente del modulo AEM `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Assegnare il valore della password corrispondente al campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Assegnare il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegnare il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recuperare un documento PDF.

   * Creare un `BLOB` oggetto utilizzando il relativo costruttore. L&#39; `BLOB` oggetto viene utilizzato per memorizzare il documento PDF con diritti abilitati dal quale vengono rimossi i diritti di utilizzo.
   * Creare un `System.IO.FileStream` oggetto richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF e la modalità di apertura del file.
   * Creare un array di byte che memorizza il contenuto dell&#39; `System.IO.FileStream` oggetto. È possibile determinare la dimensione dell&#39;array di byte ottenendo la proprietà dell&#39; `System.IO.FileStream` oggetto `Length` .
   * Compilare l&#39;array di byte con i dati del flusso richiamando il `System.IO.FileStream` `Read` metodo dell&#39;oggetto e passando l&#39;array di byte, la posizione iniziale e la lunghezza del flusso da leggere.
   * Compilare l&#39; `BLOB` oggetto assegnandone `MTOM` la proprietà con il contenuto dell&#39;array di byte.

1. Rimuovere i diritti di utilizzo dal documento PDF.

   Remove usage rights from the PDF document by invoking the `ReaderExtensionsServiceClient` object’s `removeUsageRights` method and passing the `BLOB` object that contains the rights-enabled PDF document. This method returns a `BLOB` object that contains a PDF document that does not have usage rights.

1. Applicare i diritti di utilizzo al documento PDF.

   * Create a `System.IO.FileStream` object by invoking its constructor and passing a string value that represents the PDF file location.
   * Creare un array di byte che memorizza il contenuto dei dati dell&#39; `BLOB` oggetto restituito dal `removeUsageRights` metodo. Compilare l&#39;array di byte ottenendo il valore del membro `BLOB` dati dell&#39; `MTOM` oggetto.
   * Creare un `System.IO.BinaryWriter` oggetto richiamando il relativo costruttore e passando l&#39; `System.IO.FileStream` oggetto.

**Consulta anche**

[Rimozione dei diritti di utilizzo dai documenti PDF](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Chiamata  AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chiamata  AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Retrieving Credential Information {#retrieving-credential-information}

You can retrieve information about the credential that was used to apply usage rights to a rights-enabled PDF document. Recuperando informazioni su una credenziale, è possibile ottenere informazioni quali la data dopo la quale il certificato non è più valido.

>[!NOTE]
>
>For more information about the Acrobat Reader DC extensions service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Riepilogo dei passaggi {#summary_of_steps-2}

To retrieve information about the credential that was used to apply usage rights to a PDF document, perform the following steps:

1. Includere i file di progetto.
1. Creare un oggetto client con estensioni Acrobat Reader DC.
1. Recuperare un documento PDF abilitato per diritti.
1. Retrieve information about the credential.

**Includi file di progetto**

Includete i file necessari nel progetto di sviluppo. Se state creando un&#39;applicazione client utilizzando Java, includete i file JAR necessari. Se utilizzate servizi Web, accertatevi di includere i file proxy.

**Creare un oggetto client con estensioni Acrobat Reader DC**

Before you can programmatically perform a Acrobat Reader DC extensions service operation, you must create a Acrobat Reader DC extensions service client object. Se utilizzate l&#39;API Java, create un `ReaderExtensionsServiceClient` oggetto. If you are using the Acrobat Reader DC extensions web service API, create a `ReaderExtensionsServiceService` object.

**Recuperare un documento PDF con diritti**

You must retrieve a rights-enabled PDF document in order to retrieve information about the credential. È inoltre possibile recuperare informazioni su una credenziale specificandone l&#39;alias; tuttavia, se si desidera recuperare informazioni su una credenziale utilizzata per applicare diritti di utilizzo a un documento PDF con diritti specifici, è necessario recuperare il documento.

**Recupero di informazioni sulla credenziale**

After you retrieve a rights-enabled PDF document, you can obtain information about the credential that was used to apply usage rights to it. You can obtain the following information about the credential:

* The message that is displayed within Adobe Reader when the rights-enabled PDF document is opened.
* The date after which the credential is no longer valid.
* Data prima della quale la credenziale non è valida.
* I diritti di utilizzo impostati per questo documento PDF con diritti.
* Il numero di volte in cui è stata utilizzata la credenziale.

**Consulta anche**

[Remove usage rights using the Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Remove usage rights using the web service API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Avvio rapido di Acrobat Reader DC Extensions Service API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Recupero delle informazioni sulle credenziali tramite l&#39;API Java {#retrieve-credential-information-using-the-java-api}

Recuperate le informazioni sulle credenziali utilizzando l&#39;API delle estensioni Acrobat Reader DC (Java):

1. Includere i file di progetto.

   Includete file JAR client, ad esempio adobe-reader-extensions-client.jar, nel percorso di classe del progetto Java.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore e passando un `ServiceClientFactory` oggetto che contiene le proprietà di connessione.

1. Recuperare un documento PDF.

   * Creare un oggetto `java.io.FileInputStream` che rappresenti il documento PDF abilitato per i diritti utilizzando il relativo costruttore e passando un valore di stringa che specifica la posizione del documento PDF abilitato per i diritti.
   * Creare un `com.adobe.idp.Document` oggetto utilizzando il relativo costruttore e passando l&#39; `java.io.FileInputStream` oggetto.

1. Rimuovere i diritti di utilizzo dal documento PDF.

   * Recuperare informazioni sulle credenziali utilizzate per applicare diritti di utilizzo al documento PDF richiamando il metodo dell&#39; `ReaderExtensionsServiceClient` oggetto `getDocumentUsageRights` e passando l&#39; `com.adobe.idp.Document` oggetto che contiene il documento PDF abilitato per i diritti. Questo metodo restituisce un `GetUsageRightsResult` oggetto che contiene informazioni sulle credenziali.
   * Recuperare la data dopo la quale la credenziale non è più valida richiamando il `GetUsageRightsResult` metodo dell&#39;oggetto `getNotAfter` . Questo metodo restituisce un oggetto `java.util.Date` che rappresenta la data dopo la quale la credenziale non è più valida.
   * Recuperare il messaggio visualizzato in  Adobe Reader quando il documento PDF con diritti viene aperto richiamando il `GetUsageRightsResult` metodo dell&#39; `getMessage` oggetto. Questo metodo restituisce un valore di stringa che rappresenta il messaggio.

**Consulta anche**

[Recupero delle informazioni sulle credenziali](assigning-usage-rights.md#retrieving-credential-information)

[Avvio rapido (modalità SOAP): Recupero delle informazioni sulle credenziali tramite l&#39;API Java](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusione  file libreria Java AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Recupero delle informazioni sulle credenziali tramite l&#39;API del servizio Web {#retrieve-credential-information-using-the-web-service-api}

Recuperate le informazioni sulle credenziali utilizzando l&#39;API delle estensioni Acrobat Reader DC (servizio Web):

1. Includere i file di progetto.

   Creare un progetto Microsoft .NET che utilizza MTOM. Assicurarsi di utilizzare la seguente definizione WSDL: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Sostituire `localhost` con l&#39;indirizzo IP del server che ospita  AEM Forms.

1. Creare un oggetto client con estensioni Acrobat Reader DC.

   * Creare un `ReaderExtensionsServiceClient` oggetto utilizzando il relativo costruttore predefinito.
   * Creare un `ReaderExtensionsServiceClient.Endpoint.Address` oggetto utilizzando il `System.ServiceModel.EndpointAddress` costruttore. Passate un valore di stringa che specifica il WSDL al servizio AEM Forms  (ad esempio, `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Accertatevi di specificare `?blob=mtom`.)
   * Creare un `System.ServiceModel.BasicHttpBinding` oggetto ottenendo il valore del `ReaderExtensionsServiceClient.Endpoint.Binding` campo. Inserite il valore restituito in `BasicHttpBinding`.
   * Impostare il campo `System.ServiceModel.BasicHttpBinding` dell&#39; `MessageEncoding` oggetto su `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
   * Abilitate l&#39;autenticazione HTTP di base eseguendo le seguenti operazioni:

      * Assegnare al campo il nome utente del modulo AEM `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Assegnare il valore della password corrispondente al campo `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Assegnare il valore costante `HttpClientCredentialType.Basic` al campo `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Assegnare il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al campo `BasicHttpBindingSecurity.Security.Mode`.

1. Recuperare un documento PDF.

   * Creare un `BLOB` oggetto utilizzando il relativo costruttore. L&#39; `BLOB` oggetto viene utilizzato per memorizzare un documento PDF abilitato per i diritti.
   * Creare un `System.IO.FileStream` oggetto richiamando il relativo costruttore e passando un valore di stringa che rappresenta la posizione del file del documento PDF abilitato per i diritti e la modalità di apertura del file.
   * Creare un array di byte che memorizza il contenuto dell&#39; `System.IO.FileStream` oggetto. È possibile determinare la dimensione dell&#39;array di byte ottenendo la proprietà dell&#39; `System.IO.FileStream` oggetto `Length` .
   * Compilare l&#39;array di byte con i dati del flusso richiamando il `System.IO.FileStream` `Read` metodo dell&#39;oggetto e passando l&#39;array di byte, la posizione iniziale e la lunghezza del flusso da leggere.
   * Compilare l&#39; `BLOB` oggetto assegnandone `MTOM` la proprietà con il contenuto dell&#39;array di byte.

1. Rimuovere i diritti di utilizzo dal documento PDF.

   * Recuperare informazioni sulle credenziali utilizzate per applicare diritti di utilizzo al documento PDF richiamando il metodo dell&#39; `ReaderExtensionsServiceClient` oggetto `getDocumentUsageRights` e passando l&#39; `com.adobe.idp.Document` oggetto che contiene il documento PDF abilitato per i diritti. Questo metodo restituisce un `GetUsageRightsResult` oggetto che contiene informazioni sulle credenziali.
   * Recuperare la data dopo la quale la credenziale non è più valida ottenendo il valore del membro `GetUsageRightsResult` dati dell&#39; `notAfter` oggetto. Il tipo di dati di questo membro è `System.DateTime`.
   * Recuperare il messaggio visualizzato quando il documento PDF con diritti viene aperto in  Adobe Reader ottenendo il valore del membro `GetUsageRightsResult` dati `message` dell&#39;oggetto. Il tipo di dati di questo membro è una stringa.
   * Recuperare il numero di volte in cui la credenziale viene utilizzata ottenendo il valore del membro `GetUsageRightsResult` dati dell&#39; `useCount` oggetto. Il tipo di dati di questo membro dati è un numero intero.

**Consulta anche**

[Recupero delle informazioni sulle credenziali](assigning-usage-rights.md#retrieving-credential-information)

[Chiamata  AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Chiamata  AEM Forms tramite SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
