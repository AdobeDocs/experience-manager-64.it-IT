---
title: Integrazione dell’interfaccia utente Crea corrispondenza con il portale personalizzato
seo-title: Integrating Create Correspondence UI with your custom portal
description: Scopri come integrare l’interfaccia utente per la corrispondenza con il tuo portale personalizzato
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 5%

---

# Integrazione dell’interfaccia utente Crea corrispondenza con il portale personalizzato {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Questo articolo descrive come integrare Crea soluzione di corrispondenza con il tuo ambiente.

## Chiamata basata su URL {#url-based-invocation}

Un modo per chiamare l’applicazione Crea corrispondenza da un portale personalizzato è quello di preparare l’URL con i seguenti parametri di richiesta:

* l’identificatore del modello di lettera (utilizzando il parametro cmLetterId ) o il nome del modello di lettera (utilizzando il parametro cmLetterName )

* l&#39;URL dei dati XML recuperati dall&#39;origine dati desiderata (utilizzando il parametro cmDataUrl ).

Ad esempio, il portale personalizzato prepara l’URL come\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, che potrebbe essere il href da un collegamento sul portale.\
Se il portale contiene il nome del modello Lettera , l’URL potrebbe essere\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Le chiamate in questo modo non sono sicure in quanto i parametri necessari vengono trasmessi come richiesta di GET, esponendo gli stessi (chiaramente visibili) nell&#39;URL.

>[!NOTE]
>
>Prima di chiamare l’applicazione Create Correspondence, salva e carica i dati per chiamare l’interfaccia utente Create Correspondence in corrispondenza del dataURL specificato. Questo può essere fatto dal portale personalizzato stesso o attraverso un altro processo back-end.

## Chiamata in linea basata su dati {#inline-data-based-invocation}

Un altro modo (e più sicuro) per chiamare l&#39;applicazione Create Correspondence potrebbe essere quello di colpire semplicemente l&#39;URL in `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, durante l’invio dei parametri e dei dati per chiamare l’applicazione Create Correspondence come richiesta di POST (nasconderli dall’utente finale). Ciò significa anche che ora è possibile trasmettere i dati XML per l&#39;applicazione Create Correspondence in linea (come parte della stessa richiesta, utilizzando il parametro cmData), che non era possibile/ideale nell&#39;approccio precedente.

### Parametri per la specifica della lettera {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Stringa</td> 
   <td>Identificatore per l'istanza della lettera.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Stringa</td> 
   <td><p>Identificatore del modello di lettera. </p> <p>Se su un server sono presenti più lettere CM con lo stesso nome, l'utilizzo del parametro cmLetterName nell'URL genera un errore "Esistono più lettere con lo stesso nome". In questo caso, utilizza il parametro cmLetterId nell’URL invece di cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Stringa</td> 
   <td>Nome del modello Lettera.</td> 
  </tr>
 </tbody>
</table>

L’ordine dei parametri nella tabella specifica la preferenza dei parametri utilizzati per caricare la lettera.

### Parametri per la specifica dell&#39;origine dati XML {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Dati XML da un file di origine utilizzando protocolli di base come cq, ftp, http o file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Stringa</td> 
   <td>Utilizzo dei dati xml disponibili in Letter Instance.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Per riutilizzare i dati di test allegati nel dizionario dati.</td> 
  </tr>
 </tbody>
</table>

L’ordine dei parametri nella tabella specifica la preferenza dei parametri utilizzati per caricare i dati XML.

### Altri parametri {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>Nome</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booleano</td> 
   <td>True per aprire la lettera in modalità anteprima<br /> </td> 
  </tr>
  <tr>
   <td>Casuale</td> 
   <td>Timestamp</td> 
   <td>Per risolvere i problemi di memorizzazione in cache del browser.</td> 
  </tr>
 </tbody>
</table>

Se utilizzi il protocollo http o cq per cmDataURL, l&#39;URL di http/cq dovrebbe essere accessibile in modo anonimo.
