---
title: Richiamo dei processi a lunga durata incentrati sull'uomo
seo-title: Invoking Human-Centric Long-Lived Processes
description: È possibile richiamare a livello di codice i processi a lunga durata incentrati sull'uomo creati in Workbench utilizzando un'applicazione client basata sul Web Java che utilizza l'API di vocazione, un'applicazione ASP.NET che utilizza i servizi Web e un'applicazione client creata con Flex che utilizza la funzione Remoting.
seo-description: Programmatically invoke human-centric long-lived processes created in Workbench using a Java web-based client application that uses the Invocation API, an ASP.NET application that uses web services, and a client application built with Flex that uses Remoting.
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
role: Developer
exl-id: 4f581af8-9c1a-4e80-b459-a83a1dab3b01
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3748'
ht-degree: 0%

---

# Richiamo dei processi a lunga durata incentrati sull&#39;uomo {#invoking-human-centric-long-lived-processes}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile richiamare programmaticamente i processi a lunga vita incentrati sulle persone creati in Workbench utilizzando le seguenti applicazioni client:

* Applicazione client basata su Web Java che utilizza l&#39;API di vocazione. (Vedi [Richiamo di AEM Forms tramite l’API Java](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).
* Applicazione ASP.NET che utilizza servizi Web. (Vedi [Richiamo di AEM Forms tramite servizi web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Applicazione client integrata con Flex che utilizza Remoting. (Vedi [Richiamo di AEM Forms utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Il processo a lungo termine richiamato viene denominato *FirstAppSolution/PreLoanProcess*. Puoi creare questo processo seguendo l’esercitazione specificata in [Creazione della prima applicazione AEM Forms](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).

Un processo incentrato sulle persone comporta un’attività a cui un utente può rispondere utilizzando Workspace. Ad esempio, utilizzando Workbench, è possibile creare un processo che consenta a un responsabile bancario di approvare o negare un&#39;applicazione di prestito. La figura seguente illustra il processo *FirstAppSolution/PreLoanProcess*.

Il processo* FirstAppSolution/PreLoanProcess* accetta un parametro di input denominato* formData* il cui tipo di dati è XML. I dati XML vengono uniti con una struttura del modulo denominata *PreLoanForm.xdp*. Nell&#39;illustrazione seguente viene illustrato un modulo che rappresenta un&#39;attività assegnata a un utente per approvare o negare una richiesta di prestito. L’utente approva o nega l’applicazione utilizzando Workspace. L’utente di Workspace può approvare la richiesta di prestito facendo clic sul pulsante Approva mostrato nella figura seguente. Allo stesso modo, l&#39;utente può negare la richiesta di prestito facendo clic sul pulsante nega.

Un processo longevo viene richiamato in modo asincrono e non può essere richiamato in modo sincrono a causa dei seguenti fattori:

* Un processo può avere un periodo di tempo significativo.
* Un processo può superare i limiti organizzativi.
* Per completare un processo, è necessario un input esterno. Ad esempio, si consideri una situazione in cui un modulo viene inviato a un responsabile che non è in ufficio. In questa situazione, il processo non viene completato finché il responsabile non restituisce e compila il modulo.

Quando si richiama un processo di lunga durata, AEM Forms crea un valore di identificatore di chiamata come parte della creazione di un record. Il record tiene traccia dello stato del processo di lunga durata e viene memorizzato nel database AEM Forms. Utilizzando il valore dell&#39;identificatore di chiamata, puoi tenere traccia dello stato del processo di lunga durata. Inoltre, è possibile utilizzare il valore dell&#39;identificatore di chiamata del processo per eseguire operazioni di Process Manager, ad esempio la terminazione di un&#39;istanza di processo in esecuzione.

>[!NOTE]
>
>AEM Forms non crea un valore di identificatore di chiamata o un record quando si richiama un processo di breve durata.

La `FirstAppSolution/PreLoanProcess` Il processo viene richiamato quando un richiedente invia una domanda, rappresentata come dati XML. Il nome della variabile del processo di input è `formData` e il relativo tipo di dati è XML. Ai fini della presente discussione, si presuppone che i seguenti dati XML siano utilizzati come input per la `FirstAppSolution/PreLoanProcess` processo.

```as3
 <?xml version="1.0" encoding="UTF-8"?> 
 <LoanApp> 
 <Name>Sam White</Name> 
 <LoanAmount>250000</LoanAmount> 
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail> 
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
 </LoanApp>
```

I dati XML trasmessi a un processo devono corrispondere ai campi presenti nel modulo utilizzato nel processo. In caso contrario, i dati non vengono visualizzati all’interno del modulo. Tutte le applicazioni che richiamano il `FirstAppSolution/PreLoanProcess` Il processo deve passare questa origine dati XML. Le applicazioni create in *Richiamo dei processi a lunga durata incentrati sull&#39;uomo* creare dinamicamente l&#39;origine dati XML dai valori immessi da un utente in un client web.

Utilizzando un&#39;applicazione client, puoi inviare *FirstAppSolution/PreLoanProcess *elabora i dati XML richiesti. Un processo di lunga durata restituisce come valore restituito un valore di identificatore di chiamata. La figura seguente mostra le applicazioni client che richiamano* PrimoAppSolution/PreLoanProcess *processo a lungo termine. Le applicazioni client inviano dati XML e restituiscono un valore stringa che rappresenta il valore dell&#39;identificatore di chiamata.

**Consulta anche**

[Creazione di un&#39;applicazione web Java che richiama un processo longevo incentrato sull&#39;uomo](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Creazione di un&#39;applicazione Web ASP.NET che richiama un processo di lunga durata incentrato sull&#39;uomo](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Creazione di un&#39;applicazione client creata con Flex che richiama un processo longevo incentrato sull&#39;uomo](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Creazione di un&#39;applicazione web Java che richiama un processo longevo incentrato sull&#39;uomo {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

Puoi creare un&#39;applicazione basata sul Web che utilizza un servlet Java per richiamare l&#39; `FirstAppSolution/PreLoanProcess` processo. Per richiamare questo processo da un servlet Java, utilizza l’API di chiamata all’interno del servlet Java. (Vedi [Richiamo di AEM Forms tramite l’API Java](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

L&#39;illustrazione seguente mostra un&#39;applicazione client basata su Web che pubblica nome, telefono (o e-mail) e valori di importo. Questi valori vengono inviati al servlet Java quando l’utente fa clic sul pulsante Invia applicazione.

Il servlet Java esegue le seguenti attività:

* Recupera i valori inviati dalla pagina HTML al servlet Java.
* Crea in modo dinamico un&#39;origine dati XML da passare al processo* FirstAppSolution/PreLoanProcess *. Il nome, il telefono (o l&#39;e-mail) e i valori di quantità sono specificati nell&#39;origine dati XML.
* Richiama il *FirstAppSolution/PreLoanProcess* mediante l’API di esortazione di AEM Forms.
* Restituisce il valore dell&#39;identificatore di chiamata al browser Web client.

### Riepilogo dei passaggi {#summary-of-steps}

Per creare un&#39;applicazione Java basata sul Web che richiama il `FirstAppSolution/PreLoanProcess` esegui le seguenti operazioni:

1. [Creare un progetto web](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Creare una logica di applicazione Java per il servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [Creare la pagina Web per l&#39;applicazione Web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Creare un pacchetto dell&#39;applicazione Web in un file WAR](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Distribuire il file WAR al server applicazioni J2EE che ospita AEM Forms](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms).
1. [Test dell&#39;applicazione web](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Alcuni di questi passaggi dipendono dall’applicazione J2EE da cui viene distribuito AEM Forms. Ad esempio, il metodo utilizzato per distribuire un file WAR dipende dal server applicativo J2EE in uso. Si presume che AEM Forms sia implementato su JBoss®.

### Creare un progetto web {#create-a-web-project}

Il primo passo per creare un&#39;applicazione web è quello di creare un progetto web. L&#39;IDE Java su cui si basa questo documento è Eclipse 3.3. Utilizzando l&#39;IDE Eclipse, crea un progetto web e aggiungi i file JAR richiesti al progetto. Aggiungi al tuo progetto una pagina HTML denominata *index.html *e un servlet Java.

L’elenco seguente specifica i file JAR da includere nel progetto Web:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Per la posizione di questi file JAR, vedi [Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>Il file J2EE.jar definisce i tipi di dati utilizzati da un servlet Java. Puoi ottenere questo file JAR dal server dell&#39;applicazione J2EE in cui viene distribuito AEM Forms.

**Creare un progetto web**

1. Avvia Eclipse e fai clic su **File** >  **Nuovo progetto**.
1. In **Nuovo progetto** finestra di dialogo, seleziona **Web** > **Progetto web dinamico**.
1. Tipo `InvokePreLoanProcess` per il nome del progetto, quindi fai clic su **Fine**.

**Aggiungi i file JAR richiesti al progetto**

1. Nella finestra Esplora progetti fare clic con il pulsante destro del mouse sul pulsante `InvokePreLoanProcess` progetto e seleziona **Proprietà**.
1. Fai clic su **Percorso build Java** quindi fai clic sul pulsante **Librerie** scheda .
1. Fai clic sul pulsante **Aggiungi JAR esterni** e naviga ai file JAR da includere.

**Aggiungere un servlet Java al progetto**

1. Nella finestra Esplora progetti fare clic con il pulsante destro del mouse sul pulsante `InvokePreLoanProcess` progetto e seleziona **Nuovo** >  **Altro**.
1. Espandi la **Web** cartella, seleziona **Servlet**, quindi fai clic su **Successivo**.
1. Nella finestra di dialogo Crea servlet digitare `SubmitXML` per il nome del servlet, quindi fai clic su **Fine**.

**Aggiungere una pagina HTML al progetto**

1. Nella finestra Esplora progetti fare clic con il pulsante destro del mouse sul pulsante `InvokePreLoanProcess` progetto e seleziona **Nuovo** > **Altro**.
1. Espandi la **Web** cartella, seleziona **HTML** e fai clic su **Successivo**.
1. Nella finestra di dialogo Nuovo HTML, digitare `index.html` per il nome del file, quindi fai clic su **Fine**.

>[!NOTE]
>
>Per informazioni sulla creazione di contenuto HTML che richiama il servlet Java SubmitXML, consulta [Creare la pagina Web per l&#39;applicazione Web](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application).

### Creare una logica di applicazione Java per il servlet {#create-java-application-logic-for-the-servlet}

Creare una logica di applicazione Java che richiama l’ `FirstAppSolution/PreLoanProcess` dall’interno del servlet Java. Il codice seguente mostra la sintassi della `SubmitXML` Servlet Java:

```as3
     public class SubmitXML extends HttpServlet implements Servlet { 
         public void doGet(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
         doPost(req,resp); 
          
         } 
         public void doPost(HttpServletRequest req, HttpServletResponse resp 
         throws ServletException, IOException { 
             //Add code here to invoke the FirstAppSolution/PreLoanProcess process 
             }
```

Normalmente, non inserisci il codice client all&#39;interno di un servlet Java `doGet` o `doPost` metodo . Una migliore pratica di programmazione consiste nel collocare questo codice all&#39;interno di una classe separata. Quindi crea un&#39;istanza della classe all&#39;interno della `doPost` metodo (o `doGet` e chiamare i metodi appropriati. Tuttavia, per la brevità del codice, gli esempi di codice sono limitati al minimo e vengono inseriti nel `doPost` metodo .

Per richiamare `FirstAppSolution/PreLoanProcess` Procedi utilizzando l&#39;API di vocazione ed esegui le seguenti attività:

1. Includi file JAR client, come adobe-livecycle-client.jar, nel percorso di classe del progetto Java. Per informazioni sulla posizione di questi file, vedi [Inclusione dei file libreria Java di AEM Forms](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Recupera il nome, il telefono e i valori di quantità inviati dalla pagina HTML. Utilizzare questi valori per creare in modo dinamico un&#39;origine dati XML inviata al `FirstAppSolution/PreLoanProcess` processo. È possibile utilizzare `org.w3c.dom` classi per creare l&#39;origine dati XML (questa logica di applicazione viene mostrata nell&#39;esempio di codice seguente).
1. Crea un `ServiceClientFactory` oggetto contenente le proprietà di connessione. (Vedi [Impostazione delle proprietà di connessione](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Crea un `ServiceClient` utilizzando il relativo costruttore e passando `ServiceClientFactory` oggetto. A `ServiceClient` consente di richiamare un&#39;operazione del servizio. Gestisce attività quali l&#39;individuazione, l&#39;invio e l&#39;indirizzamento delle richieste di chiamata.
1. Crea un `java.util.HashMap` utilizzando il relativo costruttore.
1. Richiama il `java.util.HashMap` dell’oggetto `put` metodo per ogni parametro di input da passare al processo longevo. Assicurati di specificare il nome dei parametri di input del processo. Perché `FirstAppSolution/PreLoanProcess` il processo richiede un parametro di input di tipo `XML` (denominato `formData`), è sufficiente richiamare `put` metodo una volta.

   ```as3
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process 
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                 
    //Create a Map object to store the parameter value 
    Map params = new HashMap(); 
    params.put("formData", inXML);
   ```

1. Crea un `InvocationRequest` richiamando l&#39;oggetto `ServiceClientFactory` dell’oggetto `createInvocationRequest` e passando i seguenti valori:

   * Valore stringa che specifica il nome del processo a lunga durata da richiamare. Per richiamare `FirstAppSolution/PreLoanProcess` processo, specificare `FirstAppSolution/PreLoanProcess`.
   * Valore stringa che rappresenta il nome dell&#39;operazione di processo. Il nome dell&#39;operazione di processo a lungo termine è `invoke`.
   * La `java.util.HashMap` oggetto contenente i valori dei parametri richiesti dall&#39;operazione del servizio.
   * Un valore booleano che specifica `false`, che crea una richiesta asincrona (questo valore è applicabile per richiamare un processo longevo).

   >[!NOTE]
   >
   >*Un processo di breve durata può essere invocato passando il valore true come quarto parametro del metodo createInvocationRequest. Passando il valore true si crea una richiesta sincrona.*

1. Invia la richiesta di chiamata ad AEM Forms richiamando il `ServiceClient` dell’oggetto `invoke` e passare `InvocationRequest` oggetto. La `invoke` restituisce un `InvocationReponse` oggetto.
1. Un processo longevo restituisce un valore stringa che rappresenta un valore di identificazione di chiamata. Recupera questo valore richiamando il `InvocationReponse` dell’oggetto `getInvocationId` metodo .

   ```as3
    //Send the invocation request to the long-lived process and  
    //get back an invocation response object 
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
    String invocationId = lcResponse.getInvocationId();
   ```

1. Scrivi il valore di identificazione della chiamata al browser Web del client. Puoi utilizzare un `java.io.PrintWriter` istanza per scrivere questo valore nel browser Web client.

### Avvio rapido: Richiamare un processo di lunga durata utilizzando l’API di richiamo {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

Il seguente esempio di codice Java rappresenta il servlet Java che richiama il `FirstAppSolution/PreLoanProcess` processo.

```as3
 /* 
     * This Java Quick Start uses the following JAR files 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
     * 
     * (Because this  quick start is implemented as a Java servlet, it is  
     * not necessary to include J2EE specific JAR files - the Java project 
     * that contains this quick start is exported as a WAR file which 
     * is deployed to the J2EE application server) 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * For complete details about the location of these JAR files,  
     * see "Including AEM Forms library files" in Programming with AEM forms 
     * */ 
 import java.io.ByteArrayOutputStream; 
 import java.io.File; 
 import java.io.IOException; 
 import java.io.PrintWriter; 
  
 import javax.servlet.ServletException; 
 import javax.servlet.http.HttpServletRequest; 
 import javax.servlet.http.HttpServletResponse; 
 import java.util.*; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
 import javax.xml.parsers.DocumentBuilder; 
 import javax.xml.parsers.DocumentBuilderFactory; 
 import javax.xml.transform.Transformer; 
 import javax.xml.transform.TransformerFactory; 
 import javax.xml.transform.dom.DOMSource; 
 import javax.xml.transform.stream.StreamResult; 
  
 import com.adobe.idp.dsc.InvocationRequest; 
 import com.adobe.idp.dsc.InvocationResponse; 
 import com.adobe.idp.dsc.clientsdk.ServiceClient; 
 import org.w3c.dom.Element; 
  
     public class SubmitXML extends javax.servlet.http.HttpServlet implements javax.servlet.Servlet { 
       static final long serialVersionUID = 1L; 
      
        public SubmitXML() { 
         super(); 
     }        
      
      
     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
         // TODO Auto-generated method stub 
         doPost(request,response); 
     }       
      
     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
                  
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Create a ServiceClient object 
             ServiceClient myServiceClient = myFactory.getServiceClient(); 
              
             //Get the values that are passed from the Loan HTML page 
             String name = (String)request.getParameter("name"); 
             String phone = (String)request.getParameter("phone"); 
             String amount = (String)request.getParameter("amount"); 
                  
             //Create XML to pass to the FirstAppSolution/PreLoanProcess process 
             org.w3c.dom.Document inXML = GetDataSource(name,phone,amount); 
                                  
             //Create a Map object to store the XML input parameter value 
             Map params = new HashMap(); 
             params.put("formData", inXML);  
              
             //Create an InvocationRequest object 
             InvocationRequest lcRequest =  myFactory.createInvocationRequest( 
                 "FirstAppSolution/PreLoanProcess", //Specify the long-lived process name 
                     "invoke",           //Specify the operation name     
                     params,               //Specify input values 
                     false);               //Create an asynchronous request  
              
             //Send the invocation request to the long-lived process and  
             //get back an invocation response object 
             InvocationResponse lcResponse = myServiceClient.invoke(lcRequest); 
             String invocationId = lcResponse.getInvocationId(); 
  
             //Create a PrintWriter instance 
             PrintWriter pp = response.getWriter();      
              
             //Write the invocation identifier value back to the client web browser 
             pp.println("The job status identifier value is: " +invocationId); 
              
         }catch (Exception e) { 
              System.out.println("The following exception occurred: "+e.getMessage()); 
       } 
     } 
      
      
      //Create XML data to pass to the long-lived process 
      private static org.w3c.dom.Document GetDataSource(String name, String phone, String amount) 
      { 
             org.w3c.dom.Document document = null; 
              
             try 
             { 
                 //Create DocumentBuilderFactory and DocumentBuilder objects 
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance(); 
                 DocumentBuilder builder = factory.newDocumentBuilder(); 
  
                 //Create a new Document object 
                 document = builder.newDocument();  
  
                 //Create MortgageApp - the root element in the XML  
                 Element root = (Element)document.createElement("LoanApp"); 
                 document.appendChild(root); 
                                              
                 //Create an XML element for Name 
                 Element nameElement = (Element)document.createElement("Name"); 
                 nameElement.appendChild(document.createTextNode(name)); 
                 root.appendChild(nameElement); 
                  
                 //Create an XML element for Phone 
                 Element phoneElement = (Element)document.createElement("PhoneOrEmail"); 
                 phoneElement.appendChild(document.createTextNode(phone)); 
                 root.appendChild(phoneElement); 
                  
                 //Create an XML element for amount 
                 Element loanElement = (Element)document.createElement("LoanAmount"); 
                 loanElement.appendChild(document.createTextNode(amount)); 
                 root.appendChild(loanElement); 
  
                 //Create an XML element for ApprovalStatus 
                 Element approveElement = (Element)document.createElement("ApprovalStatus"); 
                 approveElement.appendChild(document.createTextNode("PENDING APPROVAL")); 
                 root.appendChild(approveElement); 
                                  
               } 
          catch (Exception e) { 
                   System.out.println("The following exception occurred: "+e.getMessage()); 
                } 
         return document; 
          } 
         }
```

### Creare la pagina Web per l&#39;applicazione Web {#create-the-web-page-for-the-web-application}

La pagina web* index.html *fornisce un punto di ingresso al servlet Java che richiama il `FirstAppSolution/PreLoanProcess` processo. Questa pagina web è un modulo HTML di base contenente un modulo HTML e un pulsante di invio. Quando l’utente fa clic sul pulsante di invio, i dati del modulo vengono inviati al `SubmitXML` Servlet Java.

Il servlet Java acquisisce i dati inviati dalla pagina HTML utilizzando il seguente codice Java:

```as3
 //Get the values that are passed from the Loan HTML page 
 String name = request.getParameter("name"); 
 String phone = request.getParameter("phone"); 
 String amount = request.getParameter("amount");
```

Il seguente codice HTML rappresenta il file index.html creato durante l&#39;installazione dell&#39;ambiente di sviluppo. (Vedi [Creare un progetto web](invoking-human-centric-long-lived.md#create-a-web-project).)

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "https://www.w3.org/TR/html4/loose.dtd"> 
 <html> 
 <head> 
 <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1"> 
 <title>Insert title here</title> 
 </head> 
 <body> 
 <table> 
     <TBODY> 
         <TR> 
             <td><img src="financeCorpLogo.jpg" width="172" height="62"></TD> 
             <td><FONT size="+2"><strong>Java Loan Application Page</strong></FONT></TD> 
             <td> </TD> 
             <td> </TD> 
         </TR> 
          
     </TBODY> 
 </TABLE> 
     <FORM action="https://hiro-xp:8080/PreLoanProcess/SubmitXML" method="post"> 
        <table> 
          <TBODY> 
                <TR> 
                      <td><LABEL for="name">Name: </LABEL></TD> 
                  <td><INPUT type="text" name="name"></TD> 
                  <td><input type="submit" value="Submit Application"></TD> 
                  </TR> 
            <TR> 
                  <td> <LABEL for="phone">Phone/Email: </LABEL></TD> 
              <td><INPUT type="text" name="phone"></TD> 
                  <td></TD> 
              </TR> 
  
            <TR> 
                  <td><LABEL for="amount">Amount: </LABEL></TD> 
              <td><INPUT type="text" name="amount"></TD> 
                 <td></TD> 
             </TR> 
          </TBODY> 
 </TABLE> 
       </FORM> 
 </body> 
 </html>
```

### Creare un pacchetto dell&#39;applicazione Web in un file WAR {#package-the-web-application-to-a-war-file}

Per distribuire il servlet Java che richiama il `FirstAppSolution/PreLoanProcess` elaborare, creare un pacchetto dell&#39;applicazione Web in un file WAR. Assicurati che nel file WAR siano inclusi anche i file JAR esterni da cui dipende la logica di business del componente, come adobe-livecycle-client.jar e adobe-usermanager-client.jar.

L’illustrazione seguente mostra il contenuto del progetto Eclipse, che viene assemblato in un file WAR.

>[!NOTE]
>
>Nell’illustrazione precedente, il file JPG può essere sostituito da qualsiasi file immagine di JPG.

**Creare un pacchetto di un&#39;applicazione web in un file WAR:**

1. Da **Esplora progetti** fare clic con il pulsante destro del mouse sulla finestra `InvokePreLoanProcess` progetto e seleziona **Esporta** > **File WAR**.
1. In **Modulo web** casella di testo, tipo `InvokePreLoanProcess` nome del progetto Java.
1. In **Destinazione** casella di testo, tipo `PreLoanProcess.war`**per** nome file, specificare il percorso del file WAR, quindi fare clic su Fine.

### Distribuire il file WAR al server applicazioni J2EE che ospita AEM Forms {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Distribuisci il file WAR al server dell&#39;applicazione J2EE in cui viene distribuito AEM Forms. Per distribuire il file WAR al server applicazioni J2EE, copia il file WAR dal percorso di esportazione in *[Installazione AEM Forms]*\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy.

>[!NOTE]
>
>se AEM Forms non è implementato su JBoss, è necessario distribuire il file WAR in conformità con il server applicazioni J2EE che ospita AEM Forms.

### Test dell&#39;applicazione web {#test-your-web-application}

Dopo aver distribuito l&#39;applicazione web, puoi testarla utilizzando un browser web. Supponendo di utilizzare lo stesso computer che ospita AEM Forms, puoi specificare il seguente URL:

* http://localhost:8080/PreLoanProcess/index.html

   Immettere i valori nei campi del modulo HTML e fare clic sul pulsante Invia applicazione. Se si verificano dei problemi, vedere il file di registro dell&#39;application server J2EE.

   >[!NOTE]
   >
   >Per confermare che l&#39;applicazione Java ha richiamato il processo, avviare Workspace e accettare il prestito.

## Creazione di un&#39;applicazione Web ASP.NET che richiama un processo di lunga durata incentrato sull&#39;uomo {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

È possibile creare un&#39;applicazione ASP.NET che richiama `FirstAppSolution/PreLoanProcess` processo. Per richiamare questo processo da un&#39;applicazione ASP.NET, utilizzare i servizi Web. (Vedi [Richiamo di AEM Forms tramite i servizi web](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

Nell&#39;illustrazione seguente viene illustrato un&#39;applicazione client ASP.NET che ottiene dati da un utente finale. I dati vengono inseriti in un’origine dati XML e inviati al `FirstAppSolution/PreLoanProcess` quando l&#39;utente fa clic sul pulsante Invia applicazione.

Dopo aver richiamato il processo, viene visualizzato un valore di identificatore di chiamata . Il valore di un identificatore di chiamata viene creato come parte di un record che tiene traccia dello stato del processo di lunga durata.

L&#39;applicazione ASP.NET esegue le seguenti attività:

* Recupera i valori immessi dall’utente nella pagina web.
* Crea in modo dinamico un&#39;origine dati XML passata al processo* FirstAppSolution/PreLoanProcess *. I tre valori sono specificati nell&#39;origine dati XML.
* Richiama il processo* FirstAppSolution/PreLoanProcess *utilizzando i servizi web.
* Restituisce il valore dell&#39;identificatore di chiamata e lo stato dell&#39;operazione a lungo termine al browser Web del client.

### Riepilogo dei passaggi {#summary_of_steps-1}

Per creare un&#39;applicazione ASP.NET in grado di richiamare il processo FirstAppSolution/PreLoanProcess, eseguire le operazioni seguenti:

1. [Creare un&#39;applicazione Web ASP.NET](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Creare una pagina ASP che richiama FirstAppSolution/PreLoanProcess](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess).
1. [Eseguire l&#39;applicazione ASP.NET](invoking-human-centric-long-lived.md#run-the-asp-net-application).

### Creare un&#39;applicazione Web ASP.NET {#create-an-asp-net-web-application}

Creare un&#39;applicazione Web Microsoft .NET C# ASP.NET. Nell&#39;illustrazione seguente viene illustrato il contenuto del progetto ASP.NET denominato *InvokePreLoanProcess*.

In Riferimenti al servizio sono presenti due elementi. Il primo elemento è denominato* JobManager*. Questo riferimento consente all&#39;applicazione ASP.NET di richiamare il servizio Job Manager. Questo servizio restituisce informazioni sullo stato di un processo di lunga durata. Ad esempio, se il processo è in esecuzione, questo servizio restituisce un valore numerico che specifica il processo attualmente in esecuzione. Il secondo riferimento è denominato *PreLoanProcess*. Questo riferimento al servizio rappresenta il riferimento al processo* FirstAppSolution/PreLoanProcess *. Dopo aver creato un riferimento a un servizio, i tipi di dati associati al servizio AEM Forms sono disponibili per l&#39;utilizzo all&#39;interno del progetto .NET.

**Creare un progetto ASP.NET:**

1. Avviare Microsoft Visual Studio 2008.
1. Da **File** menu, seleziona **Nuovo**, **Sito Web**.
1. In **Modelli** elenco, selezionare **Sito Web ASP.NET**.
1. In **Posizione** seleziona una posizione per il progetto. Assegnare un nome al progetto *InvokePreLoanProcess*.
1. In **Lingua** selezionare Visual C#
1. Fai clic su OK.

**Aggiungi riferimenti al servizio:**

1. Nel menu Progetto, seleziona **Aggiungi riferimento al servizio**.
1. In **Indirizzo** specificare il WSDL nel servizio Job Manager.

   ```as3
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Nel campo Namespace, digita `JobManager`.
1. Fai clic su **Vai** quindi fai clic su **OK**.
1. In **Progetto** menu, seleziona **Aggiungi riferimento al servizio**.
1. In **Indirizzo** specificare il processo WSDL al processo FirstAppSolution/PreLoanProcess.

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Nel campo Namespace, digita `PreLoanProcess`.
1. Fai clic su **Vai** quindi fai clic su **OK**.

>[!NOTE]
>
>Sostituisci `hiro-xp` con l’indirizzo IP del server dell’applicazione J2EE che ospita AEM Forms. La `lc_version` assicura la disponibilità della funzionalità AEM Forms, ad esempio MTOM. Senza specificare la `lc_version`non è possibile richiamare AEM Forms utilizzando MTOM. (Vedi [Richiamo di AEM Forms tramite MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

### Creare una pagina ASP che richiama FirstAppSolution/PreLoanProcess {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

All&#39;interno del progetto ASP.NET, aggiungere un modulo Web (un file ASPX) responsabile della visualizzazione di una pagina HTML al richiedente del prestito. Il modulo web si basa su una classe derivata da `System.Web.UI.Page`. Logica dell&#39;applicazione C# che richiama `FirstAppSolution/PreLoanProcess` si trova in `Button1_Click` (questo pulsante rappresenta il pulsante Invia applicazione).

Nell&#39;illustrazione seguente viene mostrata l&#39;applicazione ASP.NET

Nella tabella seguente sono elencati i controlli che fanno parte di questa applicazione ASP.NET.

<table> 
 <thead> 
  <tr> 
   <th><p>Nome del controllo</p></th> 
   <th><p>Descrizione</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>NomeCasellaTesto</p></td> 
   <td><p>Specifica il nome e il cognome del cliente. </p></td> 
  </tr> 
  <tr> 
   <td><p>TelefonoCasellaTesto</p></td> 
   <td><p>Specifica l’indirizzo di telefono o e-mail del cliente. </p></td> 
  </tr> 
  <tr> 
   <td><p>ValoreCasellaTesto</p></td> 
   <td><p>Specifica l'importo del prestito.</p></td> 
  </tr> 
  <tr> 
   <td><p>Button1</p></td> 
   <td><p>Rappresenta il pulsante Invia applicazione.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelJobID</p></td> 
   <td><p>Controllo Label che specifica il valore dell'identificatore di chiamata.</p></td> 
  </tr> 
  <tr> 
   <td><p>LabelStatus</p></td> 
   <td><p>Controllo Label che specifica il valore dello stato del processo. Questo valore viene recuperato richiamando il servizio Job Manager. </p></td> 
  </tr> 
 </tbody> 
</table>

La logica dell&#39;applicazione che fa parte dell&#39;applicazione ASP.NET deve creare in modo dinamico un&#39;origine dati XML da passare al `FirstAppSolution/PreLoanProcess` processo. I valori immessi dal richiedente nella pagina HTML devono essere specificati all&#39;interno dell&#39;origine dati XML. Questi valori dati vengono uniti nel modulo quando il modulo viene visualizzato in Workspace. Le classi situate nel `System.Xml` Lo spazio dei nomi viene utilizzato per creare l&#39;origine dati XML.

Quando si richiama un processo che richiede dati XML da un&#39;applicazione ASP.NET, è disponibile un tipo di dati XML da utilizzare. Cioè, non puoi passare un `System.Xml.XmlDocument` istanza al processo. Il nome completo di questa istanza XML da passare al processo è `InvokePreLoanProcess.PreLoanProcess.XML`. Converti `System.Xml.XmlDocument` istanza a `InvokePreLoanProcess.PreLoanProcess.XML`. È possibile eseguire questa attività utilizzando il seguente codice.

```as3
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
 XmlDocument myXML = CreateXML(userName, phone, amount); 
      
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance 
 StringWriter sw = new StringWriter(); 
 XmlTextWriter xw = new XmlTextWriter(sw); 
 myXML.WriteTo(xw); 
  
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
 inXML.document = sw.ToString();
```

Per creare una pagina ASP che richiama il `FirstAppSolution/PreLoanProcess` eseguire le seguenti operazioni nel `Button1_Click` metodo:

1. Crea un `FirstAppSolution_PreLoanProcessClient` utilizzando il relativo costruttore predefinito.
1. Crea un `FirstAppSolution_PreLoanProcessClient.Endpoint.Address` utilizzando `System.ServiceModel.EndpointAddress` costruttore. Passa un valore stringa che specifica il WSDL al servizio AEM Forms e il tipo di codifica:

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   Non è necessario utilizzare il `lc_version` attributo. Questo attributo viene utilizzato quando si crea un riferimento a un servizio. Tuttavia, assicurati di specificare `?blob=mtom`.

   >[!NOTE]
   >
   >Sostituisci `hiro-xp`* con l&#39;indirizzo IP del server applicativo J2EE che ospita AEM Forms. *

1. Crea un `System.ServiceModel.BasicHttpBinding` ottenendo il valore del `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` membro dati. Imposta il valore restituito su `BasicHttpBinding`.
1. Imposta la `System.ServiceModel.BasicHttpBinding` dell’oggetto `MessageEncoding` membro dei dati `WSMessageEncoding.Mtom`. Questo valore assicura che venga utilizzato MTOM.
1. Abilita l’autenticazione HTTP di base eseguendo le seguenti attività:

   * Assegnare il nome utente del modulo di AEM al membro dati `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName`.
   * Assegna il valore della password corrispondente al membro dati `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password`.
   * Assegna il valore costante `HttpClientCredentialType.Basic` al membro interessato `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Assegna il valore costante `BasicHttpSecurityMode.TransportCredentialOnly` al membro interessato `BasicHttpBindingSecurity.Security.Mode`.

   L&#39;esempio di codice seguente mostra queste attività.

   ```as3
    //Enable BASIC HTTP authentication 
    BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
    b.MessageEncoding = WSMessageEncoding.Mtom; 
    mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
    mortgageClient.ClientCredentials.UserName.Password = "password"; 
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
    b.MaxReceivedMessageSize = 2000000; 
    b.MaxBufferSize = 2000000; 
    b.ReaderQuotas.MaxArrayLength = 2000000;
   ```

1. Recupera il nome, il telefono e i valori di quantità immessi dall’utente nella pagina web. Utilizzare questi valori per creare in modo dinamico un&#39;origine dati XML inviata al `FirstAppSolution/PreLoanProcess` processo. Crea un `System.Xml.XmlDocument` che rappresenta l&#39;origine dati XML da passare al processo (questa logica di applicazione è mostrata nell&#39;esempio di codice seguente).
1. Converti `System.Xml.XmlDocument` istanza a `InvokePreLoanProcess.PreLoanProcess.XML` (questa logica di applicazione viene mostrata nell&#39;esempio di codice seguente).
1. Richiama il `FirstAppSolution/PreLoanProcess` richiamando il `FirstAppSolution_PreLoanProcessClient` dell’oggetto `invoke_Async` metodo . Questo metodo restituisce un valore di stringa che rappresenta il valore dell&#39;identificatore di chiamata del processo longevo.
1. Crea un `JobManagerClient` utilizzando il costruttore . Assicurati di aver impostato un riferimento al servizio nel servizio Job Manager.
1. Ripetere i passaggi da 1 a 5. Specifica il seguente URL per il passaggio 2: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Crea un `JobId` utilizzando il relativo costruttore.
1. Imposta la `JobId` dell&#39;oggetto `id` membro con il valore restituito del `FirstAppSolution_PreLoanProcessClient` dell’oggetto `invoke_Async` metodo .
1. Assegna `value` true `JobId` dell&#39;oggetto `persistent` membro dati.
1. Crea un `JobStatus` richiamando l&#39;oggetto `JobManagerService` dell&#39;oggetto `getStatus` e passare `JobId` oggetto.
1. Ottieni il valore di stato recuperando il valore del `JobStatus` dell&#39;oggetto `statusCode` membro dati.
1. Assegna il valore dell&#39;identificatore di chiamata al `LabelJobID.Text` campo .
1. Assegna il valore di stato al `LabelStatus.Text` campo .

### Avvio rapido: Richiamare un processo di lunga durata utilizzando l’API del servizio Web {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

Il seguente esempio di codice C# richiama il `FirstAppSolution/PreLoanProcess`processo.

```as3
 ???/** 
     * Ensure that you create a .NET project that uses  
     * MS Visual Studio 2008 and version 3.5 of the .NET 
     * framework. This is required to invoke a  
     * AEM Forms service using MTOM. 
      
  
 using System; 
 using System.Collections; 
 using System.Configuration; 
 using System.Data; 
 using System.Linq; 
 using System.Web; 
 using System.ServiceModel; 
 using System.Web.Security; 
 using System.Web.UI; 
 using System.Web.UI.HtmlControls; 
 using System.Web.UI.WebControls; 
 using System.Web.UI.WebControls.WebParts; 
 using System.Xml.Linq; 
 using System.Xml; 
 using System.IO; 
  
 //A reference to FirstAppSolution/PreLoanProcess 
 using InvokePreLoanProcess.PreLoanProcess; 
  
 //A reference to JobManager service 
 using InvokePreLoanProcess.JobManager; 
  
  
 namespace InvokePreLoanProcess 
 { 
        public partial class _Default : System.Web.UI.Page 
        { 
            //This method is called when the Submit Application button is  
            //Clicked 
            protected void Button1_Click(object sender, EventArgs e) 
            { 
                //Create a FirstAppSolution_PreLoanProcessClient object 
                FirstAppSolution_PreLoanProcessClient mortgageClient = new FirstAppSolution_PreLoanProcessClient(); 
                mortgageClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding; 
                b.MessageEncoding = WSMessageEncoding.Mtom; 
                mortgageClient.ClientCredentials.UserName.UserName = "administrator"; 
                mortgageClient.ClientCredentials.UserName.Password = "password"; 
                b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b.MaxReceivedMessageSize = 2000000; 
                b.MaxBufferSize = 2000000; 
                b.ReaderQuotas.MaxArrayLength = 2000000; 
      
                //Retrieve values that user entered into the web page 
                String userName = TextBoxName.Text; 
                String phone = TextBoxPhone.Text; 
                String amount = TextBoxAmount.Text; 
  
                //Create the XML to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument myXML = CreateXML(userName, phone, amount); 
      
                StringWriter sw = new StringWriter(); 
                XmlTextWriter xw = new XmlTextWriter(sw); 
                myXML.WriteTo(xw); 
  
                InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML(); 
                inXML.document = sw.ToString();  
  
                //INvoke the FirstAppSolution/PreLoanProcess process 
                String invocationID =  mortgageClient.invoke_Async(inXML); 
  
                //Create a JobManagerClient object to obtain the status of the long-lived operation 
                JobManagerClient jobManager = new JobManagerClient(); 
                jobManager.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/JobManager?blob=mtom"); 
  
                //Enable BASIC HTTP authentication 
                BasicHttpBinding b1 = (BasicHttpBinding)jobManager.Endpoint.Binding; 
                b1.MessageEncoding = WSMessageEncoding.Mtom; 
                jobManager.ClientCredentials.UserName.UserName = "administrator"; 
                jobManager.ClientCredentials.UserName.Password = "password"; 
                b1.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic; 
                b1.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly; 
                b1.MaxReceivedMessageSize = 2000000; 
                b1.MaxBufferSize = 2000000; 
                b1.ReaderQuotas.MaxArrayLength = 2000000; 
  
  
                //Create a JobID object that represents the status of the  
                //long-lived operation 
                JobId jobId = new JobId(); 
                jobId.id = invocationID; 
                jobId.persistent = true; 
                JobStatus jobStatus = jobManager.getStatus(jobId); 
                System.Int16 val2 = jobStatus.statusCode; 
                LabelJobID.Text = "The job status identifier value is " + invocationID;   
                LabelStatus.Text = "The status of the long-lived operation is " + getJobDescription(val2);  
      
            } 
  
            private static XmlDocument CreateXML(String name, String phone, String amount) 
            { 
                //This method dynamically creates a DDX document  
                //to pass to the FirstAppSolution/PreLoanProcess process 
                XmlDocument xmlDoc = new XmlDocument(); 
  
                //Create the root element and append it to the XML DOM         
                System.Xml.XmlElement root = xmlDoc.CreateElement("LoanApp"); 
                xmlDoc.AppendChild(root); 
  
                //Create the Name element 
                XmlElement nameElement = xmlDoc.CreateElement("Name"); 
                nameElement.AppendChild(xmlDoc.CreateTextNode(name)); 
                root.AppendChild(nameElement); 
  
                //Create the LoanAmount element 
                XmlElement LoanAmount = xmlDoc.CreateElement("LoanAmount"); 
                LoanAmount.AppendChild(xmlDoc.CreateTextNode(amount)); 
                root.AppendChild(LoanAmount); 
  
                //Create the PhoneOrEmail element 
                XmlElement PhoneOrEmail = xmlDoc.CreateElement("PhoneOrEmail"); 
                PhoneOrEmail.AppendChild(xmlDoc.CreateTextNode(phone)); 
                root.AppendChild(PhoneOrEmail); 
  
                //Create the ApprovalStatus element 
                XmlElement ApprovalStatus = xmlDoc.CreateElement("ApprovalStatus"); 
                ApprovalStatus.AppendChild(xmlDoc.CreateTextNode("PENDING APPROVAL")); 
                root.AppendChild(ApprovalStatus); 
  
                //Return the XmlElement instance 
                return xmlDoc; 
            } 
  
  
            //Returns the String value of the Job Manager status code 
            private String getJobDescription(int val) 
            { 
                switch(val) 
                { 
                    case 0: 
                        return "JOB_STATUS_UNKNOWN"; 
      
                    case 1:  
                        return "JOB_STATUS_QUEUED"; 
  
                    case 2:  
                        return "JOB_STATUS_RUNNING"; 
  
                    case 3:  
                        return "JOB_STATUS_COMPLETED";   
      
                    case 4:  
                        return "JOB_STATUS_FAILED";  
  
                     case 5:  
                        return "JOB_STATUS_COMPLETED";  
      
                    case 6:  
                        return "JOB_STATUS_SUSPENDED"; 
      
                    case 7:  
                        return "JOB_STATUS_COMPLETE_REQUESTED"; 
      
                    case 8:  
                        return "JOB_STATUS_TERMINATE_REQUESTED"; 
  
                     case 9:  
                        return "JOB_STATUS_SUSPEND_REQUESTED"; 
  
                       case 10:  
                        return "JOB_STATUS_RESUME_REQUESTED"; 
                } 
  
                return ""; 
            } 
       } 
 } 
 
```

>[!NOTE]
>
>I valori che si trovano nel metodo definito dall&#39;utente getJobDescription corrispondono ai valori restituiti dal servizio Job Manager.

### Eseguire l&#39;applicazione ASP.NET {#run-the-asp-net-application}

Dopo aver compilato e distribuito l&#39;applicazione ASP.NET, è possibile eseguirla utilizzando un browser Web. Presupponendo che il nome del progetto ASP.NET sia *InvokePreLoanProcess*, specifica l’URL seguente all’interno di un browser web:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

dove localhost è il nome del server web che ospita il progetto ASP.NET e 1629 è il numero di porta. Quando si compila e si crea l&#39;applicazione ASP.NET, Microsoft Visual Studio la distribuisce automaticamente.

>[!NOTE]
>
>Per confermare che l&#39;applicazione ASP.NET ha richiamato il processo, avviare Workspace e accettare il prestito.

## Creazione di un&#39;applicazione client creata con Flex che richiama un processo longevo incentrato sull&#39;uomo {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

Puoi creare un’applicazione client creata con Flex per richiamare l’ *FirstAppSolution/PreLoanProcess* processo. Questa applicazione utilizza Remoting per richiamare *FirstAppSolution/PreLoanProcess* processo. (Vedi [Richiamo di AEM Forms utilizzando (obsoleto per i moduli AEM) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

L&#39;illustrazione seguente mostra un&#39;applicazione client creata con Flex che raccoglie dati da un utente finale. I dati vengono inseriti in un’origine dati XML e inviati al processo.

Dopo aver richiamato il processo, viene visualizzato un valore di identificatore di chiamata . Il valore di un identificatore di chiamata viene creato come parte di un record che tiene traccia dello stato del processo di lunga durata.

L’applicazione client creata con Flex esegue le seguenti attività:

* Recupera i valori immessi dall’utente nella pagina web.
* Crea in modo dinamico un&#39;origine dati XML passata a *FirstAppSolution/PreLoanProcess* processo. I tre valori sono specificati nell&#39;origine dati XML.
* Richiama il *FirstAppSolution/PreLoanProcess* utilizzando Remoting.
* Restituisce il valore dell&#39;identificatore di chiamata del processo longevo.

### Riepilogo dei passaggi {#summary_of_steps-2}

Per creare un&#39;applicazione client creata con Flex in grado di richiamare il processo FirstAppSolution/PreLoanProcess, esegui i seguenti passaggi:

1. Avvia un nuovo progetto Flex.
1. Includi il file adobe-remoting-provider.swc nel percorso di classe del progetto. (Vedi [Inclusione del file della libreria AEM Forms Flex](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Crea un `mx:RemoteObject` tramite ActionScript o MXML. (Vedi [Creazione di un&#39;istanza mx:RemoteObject](/help/forms/developing/invoking-aem-forms-using-remoting.md))
1. Imposta un `ChannelSet` istanza per comunicare con AEM Forms e associarla al `mx:RemoteObject` istanza. (Vedi [Creare un canale su AEM Forms](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Chiamare il `login` metodo o del servizio `setCredentials` per specificare il valore dell&#39;identificatore utente e la password. (Vedi [Utilizzo del single sign-on](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Crea l&#39;origine dati XML da passare al `FirstAppSolution/PreLoanProcess` mediante la creazione di un&#39;istanza XML. (Questa logica di applicazione viene mostrata nell&#39;esempio di codice seguente.)
1. Creare un oggetto di tipo Object utilizzando il relativo costruttore. Assegna il codice XML all’oggetto specificando il nome del parametro di input del processo, come illustrato nel codice seguente:

   ```as3
    //Get the XML data to pass to the AEM Forms process 
    var xml:XML = createXML(); 
    var params:Object = new Object(); 
    params["formData"]=xml;
   ```

1. Richiama il `FirstAppSolution/PreLoanProcess` chiamando il `mx:RemoteObject` dell’istanza `invoke_Async` metodo . Passa la `Object` che contiene il parametro di input. (Vedi [Trasferimento dei valori di ingresso](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Recupera il valore di identificazione della chiamata restituito da un processo longevo, come mostrato nel codice seguente:

   ```as3
    // Handles async call that invokes the long-lived process 
    private function resultHandler(event:ResultEvent):void 
    { 
    ji = event.result as JobId; 
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
    }
   ```

### Richiamo di un processo di lunga durata tramite Remoting {#invoking-a-long-lived-process-using-remoting}

Il seguente esempio di codice Flex richiama il `FirstAppSolution/PreLoanProcess` processo.

```as3
 <?xml version="1.0" encoding="utf-8"?> 
  
 <mx:Application  xmlns="*" backgroundColor="#FFFFFF"  
      creationComplete="initializeChannelSet();"> 
  
 <mx:Script> 
          <![CDATA[ 
  
             import mx.controls.Alert; 
             import mx.rpc.events.FaultEvent; 
             import mx.rpc.events.ResultEvent; 
             import flash.net.navigateToURL; 
             import mx.messaging.ChannelSet; 
             import mx.messaging.channels.AMFChannel; 
             import mx.collections.ArrayCollection; 
             import mx.rpc.livecycle.JobId; 
             import mx.rpc.livecycle.JobStatus; 
             import mx.rpc.livecycle.DocumentReference; 
             import mx.formatters.NumberFormatter; 
      
             // Holds the job ID returned by LC.JobManager 
             private var ji:JobId;   
      
             private function initializeChannelSet():void  
              { 
              var cs:ChannelSet= new ChannelSet();  
         cs.addChannel(new AMFChannel("remoting-amf", "https://hiro-xp:8080/remoting/messagebroker/amf"));  
         LC_MortgageApp.setCredentials("tblue", "password"); 
         LC_MortgageApp.channelSet = cs; 
              } 
  
            private function submitApplication():void 
             { 
             //Get the XML data to pass to the AEM Forms process 
             var xml:XML = createXML(); 
             var params:Object = new Object(); 
             params["formData"]=xml; 
             LC_MortgageApp.invoke_Async(params); 
             } 
  
             // Handles async call that invokes the long-lived process 
             private function resultHandler(event:ResultEvent):void 
             { 
                ji = event.result as JobId; 
                jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;  
             } 
  
             private function createXML():XML 
             { 
                //Calculate the Mortgage value to place in the XML data 
                var propertyPrice:String = txtAmount.text ;  
                var name:String = txtName.text ; 
                var phone:String = txtPhone.text ;;  
      
                var model:XML =  
  
                  <LoanApp> 
                           <Name>{name}</Name> 
                           <LoanAmount>{propertyPrice}</LoanAmount> 
                           <PhoneOrEmail>{phone}</PhoneOrEmail>  
                           <ApprovalStatus>PENDING APPROVAL</ApprovalStatus> 
                  </LoanApp> 
      
              return model; 
             } 
      
      
          ]]> 
       </mx:Script> 
      
       <!-- Declare the RemoteObject and set its destination to the mortgage-app remoting endpoint defined in AEM Forms. --> 
       <mx:RemoteObject id="LC_MortgageApp" destination="FirstAppSolution/PreLoanProcess" result="resultHandler(event);"> 
          <mx:method name="invoke_Async" result="resultHandler(event)"/> 
      </mx:RemoteObject> 
  
  
     <mx:Grid x="229" y="186"> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Image> 
                     <mx:source>file:///D|/LiveCycle_9/FirstApp/financeCorpLogo.jpg</mx:source> 
                 </mx:Image> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Flex Loan Application Page" fontSize="20"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Name:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtName"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Button label="Submit Application" click="submitApplication()"/> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Phone/Email:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtPhone"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Amount:" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:TextInput id="txtAmount"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
         <mx:GridRow width="100%" height="100%"> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
                 <mx:Label text="Label" id="jobStatusDisplay" enabled="true" fontSize="12" fontWeight="bold"/> 
             </mx:GridItem> 
             <mx:GridItem width="100%" height="100%"> 
             </mx:GridItem> 
         </mx:GridRow> 
     </mx:Grid> 
      
 </mx:Application> 
 
```
