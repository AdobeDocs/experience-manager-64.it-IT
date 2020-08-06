---
title: Integrazione delle pagine di destinazione con  Adobe Analytics
seo-title: Integrazione delle pagine di destinazione con  Adobe Analytics
description: Scoprite come integrare le pagine di destinazione con  Adobe Analytics.
seo-description: Scoprite come integrare le pagine di destinazione con  Adobe Analytics.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 20%

---


# Integrazione delle pagine di destinazione con  Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM ha integrato la soluzione per pagine di destinazione con [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) utilizzando i seguenti componenti di invito all’azione (CTA, Call To Action):

1. Componente Collegamento ClickThrough
1. Componente Collegamento grafico

Questi componenti espongono alcuni attributi che possono essere mappati tramite  variabili Adobe Analytics (Traffic, conversion variables) ed eventi di successo per inviare informazioni a  Adobe Analytics.

## Prerequisiti {#prerequisites}

 Adobe consiglia di esaminare l&#39;integrazione [Adobe Analytics AEM-](/help/sites-administering/adobeanalytics.md) esistente per comprendere come funziona questa integrazione.

## Componenti disponibili per la mappatura {#components-available-for-mapping}

In AEM, i componenti **Invito all’azione** - **ClickThroughLink** e **GraphicalLink** - visualizzati qui nella barra laterale, possono essere mappati su  variabili Adobe Analytics.

![chlimage_1-21](assets/chlimage_1-21.jpeg)

### Mappatura dei componenti della pagina di destinazione  Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

Per mappare i componenti della pagina di destinazione su  Adobe Analytics:

1. Dopo aver creato la configurazione Adobe Analytics  e aver creato un nuovo framework, selezionate la suite di rapporti appropriata dal menu a discesa. Ciò comporta il recupero delle variabili Adobe Analytics  e la relativa visualizzazione in Content Finder.
1. Trascinate i componenti Invito all’azione (CTA) dalla barra laterale all’area di mappatura al centro della pagina.

<table> 
 <tbody>
  <tr>
   <td><strong>Nome componente</strong></td> 
   <td><strong>Attributi disponibili</strong></td> 
   <td><strong>Significato dell’attributo</strong></td> 
  </tr>
  <tr>
   <td><strong>Collegamento ClickThrough CTA</strong></td> 
   <td><i>eventdata.clickthroughLinkLabel</i> <br /> </td> 
   <td>Etichetta o testo del collegamento </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td> 
   <td>Destinazione a cui si accede quando si fa clic sul collegamento </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clickthroughLinkClick</i> <br /> </td> 
   <td>Evento clic </td> 
  </tr>
  <tr>
   <td><strong>Collegamento grafico CTA</strong></td> 
   <td><i>eventdata.clickthroughImageLabel</i> <br /> </td> 
   <td>Titolo dell’immagine CTA </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughImageTarget</i> <br /> </td> 
   <td>Destinazione a cui si passa quando si fa clic sull’immagine del collegamento</td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughImageAsset</i> <br /> </td> 
   <td>Percorso della risorsa immagine nell’archivio </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clickthroughImageClick</i> <br /> </td> 
   <td>Evento clic</td> 
  </tr>
 </tbody>
</table>

1. Mappate questi attributi esposti con qualsiasi  variabile Adobe Analytics da Content Finder. Il framework è ora pronto per essere utilizzato.
1. È ora possibile creare una nuova pagina di destinazione o aprire una pagina di destinazione esistente con componenti CTA e fare clic sulla scheda **Cloud Services** nella barra laterale Proprietà **** pagina (nell’interfaccia touch, selezionate **Apri proprietà** e fate clic su **Cloud Services**) e configurate il framework da utilizzare con la pagina di destinazione. Selezionate il framework dall’elenco a comparsa.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Dopo aver configurato il framework con la pagina di destinazione, ora potete utilizzare i componenti strumentati e tutti i clic su CTA vengono registrati in  Adobe Analytics.

