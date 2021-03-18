---
title: Modifica del contenuto della pagina Zero in Designer
seo-title: Modifica del contenuto della pagina Zero in Designer
description: Sai come modificare il messaggio visualizzato sulla pagina Zero di un PDF XFA quando lo visualizzi in un visualizzatore non Adobe PDF?
seo-description: Sai come modificare il messaggio visualizzato sulla pagina Zero di un PDF XFA quando lo visualizzi in un visualizzatore non Adobe PDF?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Moduli adattivi
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---


# Modifica del contenuto di Page Zero in Designer {#changing-page-zero-content-in-designer}

Il contenuto della pagina Zero viene visualizzato per impostazione predefinita quando un visualizzatore non Adobe PDF, ad esempio il visualizzatore PDF predefinito in Chrome o Firefox, non è in grado di leggere il contenuto del modulo PDF/XFA. Il messaggio predefinito Zero pagina è mostrato di seguito.

![defaultpage0message](assets/defaultpage0message.png)

La versione di Designer Feature Pack 1 di AEM Forms consente di modificare il messaggio visualizzato sulla pagina Zero. Per modificare il messaggio Zero pagina, esegui le seguenti operazioni:

1. Verificare che sia installata la versione AEM Forms Feature Pack 1 di Designer. È possibile controllare la versione dalla schermata Informazioni su di designer.

1. Aprire il modulo per il quale si desidera modificare il contenuto Zero pagina.

1. Fare clic su **File > Proprietà modulo**.

1. Nella finestra di dialogo Proprietà modulo, fai clic su ![più](assets/plus.png) (icona Più) per aggiungere una proprietà personalizzata.

1. Specifica **_pagezerocontent** come nome della proprietà.
1. Aggiungi come valore il nuovo messaggio Zero pagina in formato RTF. Esempio:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Salvare il modulo come PDF.

1. Visualizza il modulo PDF nel browser per confermare l’aggiornamento del messaggio. Il valore di esempio sopra viene visualizzato come segue:

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>La proprietà personalizzata appena creata potrebbe non essere visualizzata correttamente nella finestra di dialogo Proprietà modulo quando si riapre il modulo. Tuttavia, funziona correttamente e nel modulo viene visualizzato il messaggio Zero pagina aggiornato.

