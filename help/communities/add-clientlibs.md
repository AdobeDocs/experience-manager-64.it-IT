---
title: Aggiungi clientlibs
seo-title: Add Clientlibs
description: Aggiungi una ClientLibraryFolder
seo-description: Add a ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
exl-id: 9b8c3d1c-a9b1-4dde-9044-46c8f2b22c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 5%

---

# Aggiungi clientlibs {#add-clientlibs}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Aggiungi una ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Crea una ClientLibraryFolder denominata `clientlibs`che conterrà i JS e CSS utilizzati per il rendering delle pagine del sito.

La `categories`il valore della proprietà dato a questa libreria client è l&#39;identificatore utilizzato per includere direttamente questa clientlib da una pagina di contenuto o per incorporarla in altre clientlibs.

1. Utilizzo **[!UICONTROL CRXDE Lite]**, espandi `/etc/designs`

1. Fai clic con il pulsante destro del mouse `an-scf-sandbox` e seleziona `Create Node`

   * Nome: `clientlibs`
   * Tipo: `cq:ClientLibraryFolder`

1. Fai clic su **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

In **[!UICONTROL Proprietà]** scheda per il nuovo `clientlibs` , immetti **`categories`** proprietà:

* Nome: **[!UICONTROL categorie]**
* Tipo: **[!UICONTROL Stringa]**
* Valore: **[!UICONTROL apps.an-scf-sandbox]**
* Fai clic su **[!UICONTROL Aggiungi]**
* Fai clic su **[!UICONTROL Salva tutto]**

Nota: aggiunta in anteprima del valore delle categorie con &#39;apps&#39;. è una convenzione per identificare l&#39;applicazione proprietaria come presente nella cartella /apps, non /libs.  IMPORTANTE: Aggiungi segnaposto `js.txt` e `css.txt` file. (Non è ufficialmente un cq:ClientLibraryFolder senza di loro.)


1. Fai clic con il pulsante destro del mouse **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Seleziona **[!UICONTROL Crea file...]**
1. Invio **[!UICONTROL Nome]**: `css.txt`

1. Seleziona **[!UICONTROL Crea file...]**
1. Invio **[!UICONTROL Nome]**: `js.txt`

1. Fai clic su **[!UICONTROL Salva tutto]**

![chlimage_1-221](assets/chlimage_1-221.png)

La prima riga di css.txt e js.txt identifica la posizione di base da cui devono essere trovati i seguenti elenchi di file.

Prova a impostare il contenuto di css.txt su:

```
#base=.
 style.css
```

Quindi crea un file sotto clientlibs denominato style.css e imposta il contenuto su:

`body {`

`background-color: #b0c4de;`

`}`

## Incorpora Clientlibs SCF {#embed-scf-clientlibs}

In **[!UICONTROL Proprietà]** scheda per `clientlibs` node, immettere la proprietà String con più valori **[!UICONTROL incorporare]**. Ciò incorporerà le [librerie lato client (clientlibs) per componenti SCF](client-customize.md#clientlibs-for-scf). Per questa esercitazione verranno aggiunte molte delle clientlibs necessarie per i componenti di Communities.

**Nota** che questo potrebbe essere o meno l&#39;approccio desiderato da utilizzare per un sito di produzione in quanto ci sono considerazioni di convenienza rispetto a dimensione/velocità dei clientlibs scaricati per ogni pagina.

Se utilizzi una sola funzione su una pagina, puoi includere direttamente sulla pagina la clientlib completa della funzione, ad esempio &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

In questo caso, li includiamo tutti, e quindi preferiremmo le clientlibs SCF più basilari che sono le clientlibs degli autori:

* Nome: **`embed`**
* Tipo: **`String`**

* Clic **`Multi`**
* Valore: **`cq.social.scf`**

   *&lt;enter> apre una finestra di dialogo*

   *Fai clic su **[+]**dopo ogni voce per aggiungere le seguenti categorie clientlib:*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Fai clic su **[!UICONTROL OK]**

* Fai clic su **[!UICONTROL Salva tutto]**

![chlimage_1-222](assets/chlimage_1-222.png)

Questo è come `/etc/designs/an-scf-sandbox/clientlibs` dovrebbe ora essere visualizzato nell’archivio:

![chlimage_1-223](assets/chlimage_1-223.png)

## Includi clientlibs nel modello PlayPage {#include-clientlibs-in-playpage-template}

Senza includere `apps.an-scf-sandbox` Categoria ClientLibraryFolder nella pagina, i componenti SCF non saranno funzionali né formattati in quanto i JavaScript e gli stili necessari non saranno disponibili.

Ad esempio, senza includere le clientlibs, il componente commenti SCF appare senza stile:

![chlimage_1-224](assets/chlimage_1-224.png)

Una volta incluse le clientlibs di apps.an-scf-sandbox, il componente dei commenti SCF appare formattato:

![chlimage_1-225](assets/chlimage_1-225.png)

L’istruzione &quot;include&quot; appartiene alla `<head>` della sezione `<html>` script. Il valore predefinito **`foundation head.jsp`** include uno script che può essere sovrapposto: **`headlibs.jsp`**.

**Copia headlibs.jsp e includi clientlibs:**

1. Utilizzo **[!UICONTROL CRXDE Lite]**, seleziona **`/libs/foundation/components/page/headlibs.jsp`**
1. Fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Copia]** (o selezionate Copia dalla barra degli strumenti)
1. Seleziona **`/apps/an-scf-sandbox/components/playpage`**
1. Fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Incolla]** (oppure seleziona Incolla dalla barra degli strumenti)
1. Fai doppio clic su **`headlibs.jsp`** per aprirlo
1. Aggiungi la riga seguente alla fine del file

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Fai clic su **[!UICONTROL Salva tutto]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Carica il tuo sito web nel browser e controlla se lo sfondo non è un&#39;ombra di blu.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Salvataggio del lavoro finora eseguito {#saving-your-work-so-far}

A questo punto, esiste una sandbox minimalista, e potrebbe essere utile salvarla come pacchetto in modo che, durante la riproduzione, se il tuo archivio diventa danneggiato e desideri ricominciare da capo, puoi spegnere il tuo server, rinominare o eliminare la cartella crx-quickstart/, accendere il tuo server, caricare e installare questo pacchetto salvato, e non dover ripetere questi passaggi fondamentali.

Questo pacchetto esiste nel [Creare una pagina di esempio](create-sample-page.md) tutorial per coloro che non vedono l&#39;ora di saltare e iniziare a giocare!..

Per creare un pacchetto:


* Da **[!UICONTROL CRXDE Lite]**, fai clic su [Icona del pacchetto](http://localhost:4502/crx/packmgr/)
* Fai clic su **[!UICONTROL Crea pacchetto]**

   * Nome pacchetto: `an-scf-sandbox-minimal-pkg`
   * Versione: `0.1`
   * Gruppo: &lt;leave as=&quot;&quot; default=&quot;&quot;>
   * Fai clic su **[!UICONTROL OK]**

* Fai clic su **[!UICONTROL Modifica]**

   * Seleziona **[!UICONTROL Filtri]** scheda

      * Fai clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso principale: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/apps/an-scf-sandbox`
      * Fai clic su **[!UICONTROL Fine]**
      * Fai clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso principale: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/etc/designs/an-scf-sandbox`
      * Fai clic su **[!UICONTROL Fine]**
      * Fai clic su **[!UICONTROL Aggiungi filtro]**
      * Percorso principale: &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/content/an-scf-sandbox`
      * Fai clic su **[!UICONTROL Fine]**
   * Fai clic su **[!UICONTROL Salva]**


* Fai clic su **[!UICONTROL Crea]**

Ora è possibile selezionare **[!UICONTROL Scarica]** per salvarlo su disco e **[!UICONTROL Carica pacchetto]** altrove, e selezionare **[!UICONTROL Altro > Replica]** per spingere la sandbox a un&#39;istanza di pubblicazione localhost per espandere il regno della sandbox.
