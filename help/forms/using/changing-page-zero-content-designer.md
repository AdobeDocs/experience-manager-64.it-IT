---
title: Modifica del contenuto Page Zero in Designer
seo-title: Modifica del contenuto Page Zero in Designer
description: Sapete come modificare il messaggio visualizzato sulla pagina Zero di un PDF XFA quando lo visualizzate in un visualizzatore PDF non Adobe?
seo-description: Sapete come modificare il messaggio visualizzato sulla pagina Zero di un PDF XFA quando lo visualizzate in un visualizzatore PDF non Adobe?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Modifica del contenuto Page Zero in Designer {#changing-page-zero-content-in-designer}

Il contenuto della pagina Zero è visualizzato per impostazione predefinita quando un visualizzatore PDF non Adobe, ad esempio il visualizzatore PDF predefinito in Chrome o Firefox, non è in grado di leggere il contenuto del modulo PDF/XFA. Il messaggio predefinito Page Zero è riportato di seguito.

![defaultpage0message](assets/defaultpage0message.png)

La versione di Designer di AEM Forms Feature Pack 1 consente di modificare il messaggio visualizzato sulla pagina Zero. Per modificare il messaggio Page Zero, effettuare le seguenti operazioni:

1. Verificare che sia installata la versione AEM Forms Feature Pack 1 di Designer. È possibile controllare la versione dalla schermata Informazioni su di Designer.

1. Aprire il modulo per il quale si desidera modificare il contenuto Page Zero.

1. Click **File > Form Properties**.

1. Nella finestra di dialogo Proprietà modulo, fare clic su ![più](assets/plus.png) (icona più) per aggiungere una proprietà personalizzata.

1. Specificate **_pagezerocontent** come nome della proprietà.
1. Aggiungi il nuovo messaggio Page Zero, in formato RTF, come valore. Ad esempio:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Salvare il modulo come PDF.

1. Visualizzare il modulo PDF nel browser per confermare l&#39;aggiornamento del messaggio. Il valore di esempio sopra viene visualizzato come segue:

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>La proprietà personalizzata appena creata potrebbe non essere visualizzata correttamente nella finestra di dialogo Proprietà modulo quando si riapre il modulo. Tuttavia, funziona correttamente e il modulo visualizza il messaggio Page Zero aggiornato.

