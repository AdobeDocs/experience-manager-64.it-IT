---
title: Rendering del modello di modulo per i moduli HTML5
seo-title: Rendering del modello di modulo per i moduli HTML5
description: I profili dei moduli HTML5 sono associati ai rendering dei profili. I rendering dei profili sono pagine JSP responsabili della generazione della rappresentazione HTML del modulo mediante una chiamata al servizio Forms OSGi.
seo-description: I profili dei moduli HTML5 sono associati ai rendering dei profili. I rendering dei profili sono pagine JSP responsabili della generazione della rappresentazione HTML del modulo mediante una chiamata al servizio Forms OSGi.
uuid: 34daed78-0611-4355-9698-0d7f758e6b61
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 1%

---


# Rendering del modello di modulo per i moduli HTML5 {#rendering-form-template-for-html-forms}

## Endpoint di rendering {#render-endpoint}

I moduli HTML5 hanno la nozione di **Profili** esposti come endpoint REST per abilitare il rendering mobile dei modelli di modulo. Questi profili hanno associato **Renderer di profilo**. Sono pagine JSP responsabili della generazione della rappresentazione HTML del modulo chiamando il servizio Forms OSGi. Il percorso JCR del nodo Profilo determina l’URL del punto finale di rendering. Il punto finale di rendering predefinito del modulo che punta al profilo &quot;predefinito&quot; è simile al seguente:

https://&lt;*host*>:&lt;*port*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*percorso della cartella contenente xdp*>&amp;template=&lt;*nome dell&#39;xdp*>

Esempio, `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Per un profilo personalizzato, l’endpoint cambia di conseguenza. Ad esempio, il punto finale del profilo personalizzato con il nome di hrforms è:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Se il modello risiede nell&#39;archivio AEM in un&#39;applicazione denominata FormSubmission, l&#39;URI è:

```
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Parametri di rendering {#render-parameters}

I parametri di richiesta supportati durante il rendering del modulo come HTML sono:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Parametro </strong></th> 
   <th><strong>Descrizione</strong></th> 
  </tr> 
  <tr> 
   <td>template<br /> </td> 
   <td>Questo parametro specifica il nome del file modello.<br /> </td> 
  </tr> 
  <tr> 
   <td>contentRoot<br /> </td> 
   <td>Questo parametro specifica il percorso in cui si trovano il modello e le risorse associate. Questo percorso può essere il percorso del file system del server o un percorso del repository o http o un percorso ftp.<br /> </td> 
  </tr> 
  <tr> 
   <td>submitUrl<br /> </td> 
   <td>Questo parametro specifica l'url a cui viene inviato il file xml dei dati del modulo.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Unisci dati con modello di modulo {#merge-data-with-form-template}

| Parametro | Descrizione |
|---|---|
| dataRef | Questo parametro specifica **percorso assoluto** del file di dati unito al modello. Questo parametro può essere un URL di un servizio rest che restituisce i dati in formato xml. |
| data | Questo parametro specifica i byte di dati codificati UTF-8 uniti al modello. Se questo parametro viene specificato, il modulo HTML5 ignora il parametro dataRef. |

### Passaggio del parametro di rendering {#passing-the-render-parameter}

I moduli HTML5 supportano tre metodi per il passaggio dei parametri di rendering. Puoi trasmettere parametri tramite URL, coppie chiave-valore e nodo profilo. Nel parametro di rendering, la coppia chiave-valore ha la precedenza più alta seguita dal nodo del profilo. Il parametro URL Request ha la precedenza minore.

* **Parametri** di richiesta URL: Puoi specificare i parametri di rendering nell’URL. Nei parametri di richiesta URL, i parametri sono visibili all’utente finale. Ad esempio, il seguente URL di invio contiene il parametro di modello nell’URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **Parametri** di richiesta SetAttribute: Puoi specificare i parametri di rendering come coppia chiave-valore. Nei parametri di richiesta SetAttribute, i parametri non sono visibili all&#39;utente finale. Puoi inoltrare una richiesta da qualsiasi altro JSP a JSP per il rendering del profilo di modulo HTML5 e utilizzare *setAttribute* su richiesta per trasmettere tutti i parametri di rendering. Questo metodo ha la precedenza più alta.

* **Parametri di richiesta del nodo di profilo:** puoi specificare i parametri di rendering come proprietà del nodo di un nodo di profilo. Nei parametri di richiesta del nodo di profilo, i parametri non sono visibili all’utente finale. Il nodo del profilo è il nodo in cui viene inviata la richiesta. Per specificare parametri come proprietà del nodo, utilizza CRXDE lite.

### Parametri di invio {#submit-parameters}

I moduli HTML5 inviano dati; eseguire script e servizi Web lato server sui server AEM. Per informazioni dettagliate sui parametri utilizzati per eseguire script e servizi Web lato server sui server AEM, vedere [Proxy servizio moduli HTML5](/help/forms/using/service-proxy.md).
