---
title: NON PUBBLICARE Crea il tuo primo documento adattivo
seo-title: DO NOT PUBLISH Create your first adaptive document
description: NON PUBBLICARE
seo-description: DO NOT PUBLISH
page-status-flag: de-activated
uuid: 2cb2bf82-130f-4d6b-a711-df0b97cb0504
discoiquuid: f3ca177f-7c0d-4b8b-ab4b-bf04668d634c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---


# NON PUBBLICARE Crea il tuo primo documento adattivo {#do-not-publish-create-your-first-adaptive-document}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Caso d’uso  {#use-case}

We Finance è un&#39;organizzazione leader nel settore dei servizi finanziari che offre soluzioni finanziarie complete e personalizzate per soddisfare le esigenze dei diversi profili dei clienti.

Una delle polizze di assicurazione auto dei loro clienti sta scadendo e le stanno inviando un promemoria, che è interattivo e include un PDF, con il preventivo di rinnovo. La comunicazione contiene anche altre informazioni, come i premi fedeltà e le offerte di sconti.

Il portale viene eseguito su Adobe AEM. L&#39;output del canale di benvenuto per il web e la stampa viene creato utilizzando le funzionalità multicanale di Adaptive Document.

Alla fine dell’esercitazione sarà disponibile un documento adattivo simile al seguente:
[ ![ad-1](assets/ad-1.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Mobile.pdf)    [ ![ad-2](assets/ad-2.png)](https://blogs.adobe.com/contentcorner/files/2017/07/PAF_Desktop.pdf)La creazione della prima esercitazione per documenti adattivi è suddivisa in passaggi. Ogni passaggio è un articolo completo in sé.

<table> 
 <tbody>
  <tr>
   <th>Imparerà</th> 
   <th>
    <ul> 
     <li>Creazione di un modello di documento e dati modulo adattivo.</li> 
     <li>Creazione di modelli e temi per documenti adattivi.</li> 
     <li>Utilizzo dell'editor di regole per creare regole di business.<br /> </li> 
     <li>Pubblicazione di un documento adattivo. <br /> </li> 
    </ul> </th> 
  </tr>
  <tr>
   <td>Prerequisito</td> 
   <td>
    <ul> 
     <li>Imposta AEM'istanza di authoring. </li> 
     <li>Installare il componente aggiuntivo per AEM Forms. Per informazioni dettagliate, consulta <a href="/help/forms/using/installing-configuring-aem-forms-osgi.md" target="_blank">Installare e configurare AEM Forms</a>.</li> 
     <li>Ottenere il driver del database JDBC (file JAR) dal provider del database. Gli esempi nell'esercitazione sono basati sul database MySQL e utilizzano il driver di database MySQL JDBC di Oracle. </li> 
     <li>Imposta un database contenente i dati del cliente. Un database è essenziale per creare un documento adattivo. Questa esercitazione utilizza un database per visualizzare il modello dati del modulo e le funzionalità di persistenza di AEM Forms. </li> 
     <li>Crea/importa e abilita <a href="/help/forms/using/web-channel-print-channel.md">Modelli per stampa e canale web</a>.</li> 
     <li>Assicurati che la <a href="/help/forms/using/document-fragments.md">Frammenti di documenti basati su FDM</a>.</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## Passaggio 1: Crea modello dati modulo {#step-create-form-data-model}

Un modello di dati modulo consente di collegare un documento adattivo a più origini dati. Ad esempio, AEM profilo utente, servizi web RESTful, servizi web basati su SOAP, servizi OData e database relazionali. Un modello dati Modulo è uno schema di rappresentazione dei dati unificato delle entità e dei servizi aziendali disponibili nelle origini dati connesse. È possibile utilizzare il modello dati del modulo con un documento adattivo per recuperare i dati dalle origini dati connesse. Per ulteriori informazioni sul modello dati modulo, vedere [Integrazione dei dati di AEM Forms](/help/forms/using/data-integration.md).

Obiettivi:

* Configurare l’istanza di database (Microsoft Dynamics) come origine dati
* Creare il modello dati del modulo utilizzando Microsoft Dynamics come origine dati
* Aggiunta di oggetti del modello dati al modello dati del modulo
* Configurare i servizi di lettura e scrittura per il modello dati del modulo
* Verificare il modello dati del modulo e i servizi configurati con i dati di prova

## Passaggio 2: Creare un documento adattivo {#step-create-an-adaptive-document}

Le comunicazioni con la clientela centralizzano e gestiscono la creazione, l&#39;assemblaggio e la distribuzione di corrispondenze sicure, personalizzate e interattive quali corrispondenza aziendale, lettere, documenti, dichiarazioni, note sui benefit, prospetto di gestione patrimoniale, e-mail di marketing, fatture e kit di benvenuto.

Utilizzando documenti adattivi, puoi creare comunicazioni con i clienti di natura coinvolgente, reattiva, dinamica e adattiva. AEM Forms fornisce un editor WYSIWYG con trascinamento per creare documenti adattivi.

<!--`For more information about adaptive documents, see [Introduction to authoring adaptive documents](/forms/using/introduction-ad-authoring.md).`-->

Obiettivi:

* Creazione di output di stampa e Web di un documento adattivo basato sul modello di dati del modulo.
* Campi di layout di un modulo adattivo per visualizzare le informazioni al cliente
* Creare regole per recuperare e visualizzare informazioni dal modello dati del modulo al documento adattivo.

<!--![see-the-guide-sm](assets/see-the-guide-sm.png)-->

## Passaggio 3: Applicare regole ai campi del documento adattivo (solo per il canale Web) {#step-apply-rules-to-adaptive-document-fields-web-channel-only}

Il documento adattivo fornisce un editor per la scrittura di regole sugli oggetti del documento adattivo. Queste regole definiscono le azioni da attivare sugli oggetti del documento in base a condizioni preimpostate e alle azioni dell&#39;utente sul documento. Consente di garantire precisione e velocizzare l&#39;esperienza utente nella versione web del documento adattivo. Per ulteriori informazioni sull&#39;editor di regole e regole per i documenti adattivi, consulta [editor di regole](/help/forms/using/rule-editor.md).

Obiettivi:

* Creare e applicare regole ai campi del canale web del documento adattivo
* Utilizzare le regole per attivare i servizi del modello dati documento nel canale Web

## Passaggio 4: Personalizzare lo stile del documento adattivo (solo per il canale web) {#step-style-the-adaptive-document-web-channel-only}

I documenti adattivi forniscono un editor per creare temi per i documenti adattivi e lo stile in linea. Un tema contiene dettagli di stile per componenti e pannelli e puoi riutilizzare un tema sui canali web di diversi documenti. Gli stili includono proprietà quali colori di sfondo, colori dello stato, trasparenza, allineamento e dimensioni. Quando si applica il tema al documento, lo stile specificato si riflette sui componenti corrispondenti del documento. Per ulteriori informazioni, consulta [Temi](/help/forms/using/themes.md).

Obiettivi:

* Crea un tema per il canale web del documento adattivo
* Applica tema al canale web del documento adattivo
* Convalidare l’aspetto del canale web del documento adattivo su dispositivi mobili e desktop

## Passaggio 5: Pubblicare il documento adattivo {#step-publish-the-adaptive-document}

Dopo aver creato il documento adattivo, devi pubblicarlo affinché sia disponibile nell’istanza di pubblicazione, dove gli agenti possono utilizzare il documento adattivo per creare le istanze di comunicazione basate su di esso.

Per pubblicare il documento adattivo, gli autori del documento devono disporre delle autorizzazioni necessarie.
