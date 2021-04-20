---
title: Integrazione dell’interfaccia utente Crea corrispondenza con il portale personalizzato
seo-title: Integrazione dell’interfaccia utente Crea corrispondenza con il portale personalizzato
description: Scopri come integrare l’interfaccia utente per la corrispondenza con il tuo portale personalizzato
seo-description: Scopri come integrare l’interfaccia utente per la corrispondenza con il tuo portale personalizzato
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 4%

---


# Integrazione dell’interfaccia utente Crea corrispondenza con il portale personalizzato {#integrating-create-correspondence-ui-with-your-custom-portal}

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

Un altro modo (e più sicuro) per chiamare l&#39;applicazione Create Correspondence potrebbe essere quello di colpire semplicemente l&#39;URL a `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, mentre inviando i parametri e i dati per chiamare l&#39;applicazione Create Correspondence come richiesta di POST (nascondendoli dall&#39;utente finale). Ciò significa anche che ora è possibile trasmettere i dati XML per l&#39;applicazione Create Correspondence in linea (come parte della stessa richiesta, utilizzando il parametro cmData), che non era possibile/ideale nell&#39;approccio precedente.

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

### Parametri per specificare l&#39;origine dati XML {#parameters-for-specifying-the-xml-data-source}

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
   <td>Dati XML da un file di origine che utilizzano protocolli di base come cq, ftp, http o file.<br /> </td> 
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
