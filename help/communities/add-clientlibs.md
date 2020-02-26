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
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc

---


# Aggiungi Clientlibs {#add-clientlibs}

## Aggiungere una ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Create una ClientLibraryFolder denominata `clientlibs`che conterrà i file JS e CSS utilizzati per il rendering delle pagine del sito.

Il valore della `categories`proprietà dato a questa libreria client è l&#39;identificatore utilizzato per includere direttamente questa clientlib da una pagina di contenuto o per incorporarla in altri clientlibs.

1. Utilizzando **[!UICONTROL CRXDE Lite]**, espandete `/etc/designs`

1. Fare clic con il pulsante destro del mouse `an-scf-sandbox` e selezionare `Create Node`

   * Nome: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Fai clic su **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Nella scheda **[!UICONTROL Proprietà]** del nuovo `clientlibs` nodo, immettere la **`categories`** proprietà:

* Nome: **[!UICONTROL categorie]**
* Tipo: **[!UICONTROL Stringa]**
* Valore: **[!UICONTROL apps.an-scf-sandbox]**
* Fate clic su **[!UICONTROL Aggiungi]**
* Fate clic su **[!UICONTROL Salva tutto]**

Nota: anteprima del valore delle categorie con &#39;app&#39;. è una convenzione per identificare l&#39;applicazione proprietaria come nella cartella /apps, non /libs.  IMPORTANTE: Aggiungere segnaposto `js.txt` e `css.txt` file. (non è ufficialmente una cq:ClientLibraryFolder senza di esse.)


1. Clic destro **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Seleziona **[!UICONTROL Crea file...]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. Seleziona **[!UICONTROL Crea file...]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. Fate clic su **[!UICONTROL Salva tutto]**

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

Nella scheda **[!UICONTROL Proprietà]** del `clientlibs` nodo, immettere la proprietà String **[!UICONTROL embed]** con più valori. In questo modo verranno incorporate le librerie lato [client (clientlibs) necessarie per i componenti](client-customize.md#clientlibs-for-scf)SCF. Per questa esercitazione verranno aggiunti molti dei clientlibs necessari per i componenti Community.

**Notate** che questo potrebbe essere l&#39;approccio desiderato per un sito di produzione, in quanto vi sono considerazioni di convenienza rispetto alla dimensione/velocità dei clientlibs scaricati per ogni pagina.

Se si utilizza una sola funzione su una pagina, è possibile includere direttamente sulla pagina la clientlib completa della funzionalità, ad esempio &lt;% ui:includeClientLib category=cq.social.hbs.forum&quot; %>

In questo caso, li includiamo tutti, e quindi preferiremmo i più basilari clientlibs SCF che sono gli autori clientlibs:

* Nome: **`embed`**
* Tipo: **`String`**

* Clic **`Multi`**
* Valore: **`cq.social.scf`**

   *&lt;enter> apre una finestra di dialogo*

   *Fate clic **[+]**dopo ogni voce per aggiungere le seguenti categorie clientlib:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Fai clic su **[!UICONTROL OK]**

* Fate clic su **[!UICONTROL Salva tutto]**

![chlimage_1-222](assets/chlimage_1-222.png)

Questo è il modo in cui `/etc/designs/an-scf-sandbox/clientlibs` dovrebbe essere visualizzato nella directory archivio:

![chlimage_1-223](assets/chlimage_1-223.png)

## Includi Clientlibs nel modello PlayPage {#include-clientlibs-in-playpage-template}

Senza includere la categoria `apps.an-scf-sandbox` ClientLibraryFolder nella pagina, i componenti SCF non funzioneranno né saranno formattati in quanto non saranno disponibili i JavaScript e gli stili necessari.

Ad esempio, senza includere i clientlibs, il componente Commenti SCF appare privo di stile:

![chlimage_1-224](assets/chlimage_1-224.png)

Una volta inclusi i clientlibs apps.an-scf-sandbox, il componente dei commenti SCF appare formattato:

![chlimage_1-225](assets/chlimage_1-225.png)

L&#39;istruzione include appartiene alla variabile <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> della sezione <html> script. L&#39;impostazione predefinita **`foundation head.jsp`** include uno script che può essere sovrapposto: **`headlibs.jsp`**.

**Copiate headlibs.jsp e includete clientlibs:**

1. Utilizzando **[!UICONTROL CRXDE Lite]**, selezionare **`/libs/foundation/components/page/headlibs.jsp`**
1. Fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Copia]** (oppure selezionate Copia dalla barra degli strumenti)
1. Seleziona **`/apps/an-scf-sandbox/components/playpage`**
1. Fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL Incolla]** (oppure selezionate Incolla dalla barra degli strumenti)
1. Fare doppio clic **`headlibs.jsp`** per aprirlo
1. Aggiungi la riga seguente alla fine del file

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Fate clic su **[!UICONTROL Salva tutto]**


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

Questo pacchetto è disponibile nell’esercitazione [Crea una pagina](create-sample-page.md) di esempio per coloro che non vedono l’ora di iniziare a riprodurre il pacchetto...

Per creare un pacchetto:


* Da **[!UICONTROL CRXDE Lite]**, fate clic sull&#39;icona [Pacchetto](http://localhost:4502/crx/packmgr/)
* Fate clic su **[!UICONTROL Crea pacchetto]**

   * Nome pacchetto: `an-scf-sandbox-minimal-pkg`
   * Versione: `0.1`
   * Gruppo: &lt;lasciare come predefinito>
   * Fai clic su **[!UICONTROL OK]**

* Fai clic su **[!UICONTROL Modifica]**

   * Seleziona **[!UICONTROL filtri]** , scheda

      * Fate clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;Browse to `/apps/an-scf-sandbox`>
      * Fate clic su **[!UICONTROL Fine]**
      * Fate clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;Browse to `/etc/designs/an-scf-sandbox`>
      * Fate clic su **[!UICONTROL Fine]**
      * Fate clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso directory principale: &lt;Browse to `/content/an-scf-sandbox`>
      * Fate clic su **[!UICONTROL Fine]**
   * Fai clic su **[!UICONTROL Salva]**


* Fate clic su **[!UICONTROL Genera]**

Ora potete selezionare **[!UICONTROL Scarica]** per salvarlo su disco e **[!UICONTROL caricare il pacchetto]** altrove, nonché **[!UICONTROL Altro > Replica]** per inviare la sandbox a un&#39;istanza di pubblicazione localhost per espandere il realm della sandbox.
