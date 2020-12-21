---
title: Aggiungi Clientlibs
seo-title: Aggiungi Clientlibs
description: Aggiungi una ClientLibraryFolder
seo-description: Aggiungi una ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 805e4411930749ff4b6b05ea4a8b87b4f96d72fd
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 4%

---


# Aggiungi Clientlibs {#add-clientlibs}

## Aggiungere una ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Create una ClientLibraryFolder denominata `clientlibs`che conterrà i file JS e CSS utilizzati per il rendering delle pagine del sito.

Il valore della proprietà `categories`data a questa libreria client è l&#39;identificatore utilizzato per includere direttamente questa clientlib da una pagina di contenuto o per incorporarla in altri clientlibs.

1. Utilizzando **[!UICONTROL CRXDE Lite]**, espandere `/etc/designs`

1. Fare clic con il pulsante destro del mouse su `an-scf-sandbox` e selezionare `Create Node`

   * Nome: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Fai clic su **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Nella scheda **[!UICONTROL Proprietà]** per il nuovo nodo `clientlibs`, immettere la proprietà **`categories`**:

* Nome: **[!UICONTROL categorie]**
* Tipo: **[!UICONTROL String]**
* Valore: **[!UICONTROL apps.an-scf-sandbox]**
* Fate clic su **[!UICONTROL Aggiungi]**
* Fare clic su **[!UICONTROL Salva tutto]**

Nota: visualizzazione in anteprima del valore delle categorie con &#39;app&#39;. è una convenzione per identificare l&#39;applicazione proprietaria come nella cartella /apps, non /libs.  IMPORTANTE: Aggiungere file segnaposto `js.txt` e `css.txt`. (non è ufficialmente una cq:ClientLibraryFolder senza di esse.)


1. Fare clic con il pulsante destro del mouse su **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Selezionare **[!UICONTROL Crea file...]**
1. Immettere **[!UICONTROL Nome]**: `css.txt`

1. Selezionare **[!UICONTROL Crea file...]**
1. Immettere **[!UICONTROL Nome]**: `js.txt`

1. Fare clic su **[!UICONTROL Salva tutto]**

![chlimage_1-221](assets/chlimage_1-221.png)

La prima riga di css.txt e js.txt identifica la posizione di base dalla quale si trovano i seguenti elenchi di file.

Provate a impostare il contenuto di css.txt su:

```
#base=.
 style.css
```

Quindi create un file in clientlibs denominato style.css e impostate il contenuto su:

`body {`

`background-color: #b0c4de;`

`}`

## Incorpora client SCF {#embed-scf-clientlibs}

Nella scheda **[!UICONTROL Proprietà]** del nodo `clientlibs`, immettere la proprietà String multi-valore **[!UICONTROL embed]**. In questo modo verranno incorporate le [librerie lato client (clientlibs) necessarie per i componenti SCF](client-customize.md#clientlibs-for-scf). Per questa esercitazione verranno aggiunti molti dei clientlibs necessari per i componenti Community.

**Si** noti che questo potrebbe essere o meno l&#39;approccio desiderato da utilizzare per un sito di produzione, in quanto vi sono considerazioni di convenienza rispetto alla dimensione/velocità dei clientlibs scaricati per ogni pagina.

Se si utilizza una sola funzione su una pagina, è possibile includere direttamente sulla pagina la clientlib completa di tale funzione, ad esempio, &lt;% ui:includeClientLib category=cq.social.hbs.forum&quot; %>

In questo caso, li includiamo tutti, e quindi preferiremmo i più basilari clientlibs SCF che sono gli autori clientlibs:

* Nome: **`embed`**
* Tipo: **`String`**

* Clic **`Multi`**
* Valore: **`cq.social.scf`**

   *&lt;enter> verrà visualizzata una finestra di dialogo*

   *Fate clic **[+]**dopo ogni voce per aggiungere le seguenti categorie clientlib:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Fai clic su **[!UICONTROL OK]**

* Fare clic su **[!UICONTROL Salva tutto]**

![chlimage_1-222](assets/chlimage_1-222.png)

Questo è il modo in cui `/etc/designs/an-scf-sandbox/clientlibs` dovrebbe ora apparire nella directory archivio:

![chlimage_1-223](assets/chlimage_1-223.png)

## Includi Clientlibs nel modello PlayPage {#include-clientlibs-in-playpage-template}

Senza includere la categoria `apps.an-scf-sandbox` ClientLibraryFolder nella pagina, i componenti SCF non funzioneranno né saranno formattati in quanto non saranno disponibili i JavaScript e gli stili necessari.

Ad esempio, senza includere i clientlibs, il componente Commenti SCF appare privo di stile:

![chlimage_1-224](assets/chlimage_1-224.png)

Una volta inclusi i clientlibs apps.an-scf-sandbox, il componente dei commenti SCF appare formattato:

![chlimage_1-225](assets/chlimage_1-225.png)

L&#39;istruzione include appartiene alla sezione `<head>` dello script `<html>`. L&#39;elemento **`foundation head.jsp`** predefinito include uno script che può essere sovrapposto: **`headlibs.jsp`**.

**Copiate headlibs.jsp e includete clientlibs:**

1. Utilizzando **[!UICONTROL CRXDE Lite]**, selezionare **`/libs/foundation/components/page/headlibs.jsp`**
1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Copia]** (oppure selezionare Copia dalla barra degli strumenti)
1. Seleziona **`/apps/an-scf-sandbox/components/playpage`**
1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Incolla]** (oppure selezionare Incolla dalla barra degli strumenti)
1. Fare doppio clic su **`headlibs.jsp`** per aprirlo
1. Aggiungi la riga seguente alla fine del file

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Fare clic su **[!UICONTROL Salva tutto]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Caricate il sito Web nel browser e verificate se lo sfondo non è blu.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Salvataggio del lavoro fino ad ora {#saving-your-work-so-far}

A questo punto, esiste una sandbox minimalista, e potrebbe essere utile salvarla come pacchetto in modo che, durante la riproduzione, se il repository diventa danneggiato e si desidera ricominciare, è possibile spegnere il server, rinominare o eliminare la cartella crx-quickstart/, attivare il server, caricare e installare questo pacchetto salvato, e non dover ripetere questi passaggi fondamentali.

Questo pacchetto è disponibile nell&#39;esercitazione [Create a Sample Page](create-sample-page.md) per coloro che non possono aspettare di passare a un&#39;azione e iniziare la riproduzione!...

Per creare un pacchetto:


* Da **[!UICONTROL CRXDE Lite]**, fare clic sull&#39;icona [Pacchetto](http://localhost:4502/crx/packmgr/)
* Fare clic su **[!UICONTROL Crea pacchetto]**

   * Nome pacchetto: `an-scf-sandbox-minimal-pkg`
   * Versione: `0.1`
   * Gruppo: &lt;lasciare come predefinito>
   * Fai clic su **[!UICONTROL OK]**

* Fai clic su **[!UICONTROL Modifica]**

   * Selezionare la scheda **[!UICONTROL Filtri]**

      * Fare clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;individuare `/apps/an-scf-sandbox`
      * Fare clic su **[!UICONTROL Fine]**
      * Fare clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;individuare `/etc/designs/an-scf-sandbox`
      * Fare clic su **[!UICONTROL Fine]**
      * Fare clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;individuare `/content/an-scf-sandbox`
      * Fare clic su **[!UICONTROL Fine]**
   * Fai clic su **[!UICONTROL Salva]**


* Fare clic su **[!UICONTROL Build]**

Ora potete selezionare **[!UICONTROL Scarica]** per salvarlo su disco e **[!UICONTROL Carica pacchetto]** altrove, nonché selezionare **[!UICONTROL Altro > Replica]** per inviare la sandbox a un&#39;istanza di pubblicazione localhost per espandere l&#39;area di autenticazione della sandbox.
