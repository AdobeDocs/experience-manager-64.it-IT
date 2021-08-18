---
title: Sviluppa applicazione sandbox
seo-title: Sviluppa applicazione sandbox
description: Sviluppare applicazioni utilizzando gli script di foundation
seo-description: Sviluppare applicazioni utilizzando gli script di foundation
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: cd036e4a-0884-4ba0-83e9-7013583bbbae
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 5%

---

# Sviluppa applicazione sandbox {#develop-sandbox-application}

In questa sezione, ora che il modello è stato configurato nella sezione [applicazione iniziale](initial-app.md) e nelle pagine iniziali stabilite nella sezione [contenuto iniziale](initial-content.md), l’applicazione può essere sviluppata utilizzando script di base, tra cui la possibilità di abilitare l’authoring con i componenti di Communities. Al termine di questa sezione, il sito web funzionerà.

## Utilizzo degli script di pagina di Foundation {#using-foundation-page-scripts}

Lo script predefinito, creato quando è stato aggiunto il componente che esegue il rendering del modello di playpage, viene modificato per includere il head.jsp della pagina di base e un body.jsp locale.

### Super tipo di risorsa {#super-resource-type}

Il primo passo è quello di aggiungere una proprietà super type di risorsa al nodo `/apps/an-scf-sandbox/components/playpage` in modo che erediti gli script e le proprietà del super-type.

Utilizzo di CRXDE Lite:

<!--Resolve steps below-->

* Nome: `sling:resourceSuperType`
* Tipo: `String`
* Valore: `foundation/components/page`

1. Fai clic sul verde **[!UICONTROL [+] Aggiungi]**
1. Fai clic su **[!UICONTROL Salva tutto]**

![chlimage_1-231](assets/chlimage_1-231.png)

### Script testa e corpo {#head-and-body-scripts}

1. In **CRXDE Lite** riquadro Esplora risorse, passare a `/apps/an-scf-sandbox/components/playpage` e fare doppio clic sul file `playpage.jsp` per aprirlo nel riquadro di modifica.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp}

```xml
<%--

  An SCF Sandbox Play Component component.

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %><%
%><%
 // TODO add your code here
%>
```

1. Essendo a conoscenza dei tag script aperti/chiusi, sostituire &quot; // TODO ...&quot; con include di script per le parti testa e corpo di &lt;html>.

   Con un super tipo di `foundation/components/page`, qualsiasi script non definito nella stessa cartella verrà risolto in uno script nella cartella `/apps/foundation/components/page` (se presente), in uno script nella cartella `/libs/foundation/components/page`.

#### /apps/an-scf-sandbox/components/playpage/playpage.jsp {#apps-an-scf-sandbox-components-playpage-playpage-jsp-1}

```xml
<%--

    An SCF Sandbox Play Component component: playpage.jsp

  This is the component which renders content for An SCF Sandbox page.

--%><%
%><%@include file="/libs/foundation/global.jsp"%><%
%><%@page session="false" %>
<html>
  <cq:include script="head.jsp"/>
  <cq:include script="body.jsp"/>
</html>
```

1. Lo script di base `head.jsp` non deve essere sovrapposto, ma lo script di base `body.jsp` è vuoto.

   Per impostare l’authoring, sovrapponi `body.jsp` con uno script locale e includi un sistema di paragrafi (parsys) nel corpo:

   1. passa a `/apps/an-scf-sandbox/components`
   1. seleziona il nodo `playpage`.
   1. fai clic con il pulsante destro del mouse e seleziona `Create > Create File...`

      * Nome: **body.jsp**
   1. Fai clic su **[!UICONTROL Salva tutto]**

   Apri `/apps/an-scf-sandbox/components/playpage/body.jsp` e incolla il seguente testo:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Fai clic su **[!UICONTROL Salva tutto]**

**Visualizzare la pagina in un browser in modalità di modifica:**

* Interfaccia standard: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

È consigliabile non solo visualizzare l&#39;intestazione **Community Play**, ma anche l&#39;interfaccia utente per la modifica del contenuto della pagina.

Il pannello laterale Risorse/Componente viene visualizzato quando il pannello laterale è disattivato e la finestra è sufficientemente ampia da consentire la visualizzazione del contenuto laterale e della pagina.

![chlimage_1-232](assets/chlimage_1-232.png)

* Interfaccia classica: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Di seguito viene illustrata l’aspetto della pagina di riproduzione nell’interfaccia classica, incluso con Content Finder (cf):

![chlimage_1-233](assets/chlimage_1-233.png)

## Componenti di Communities {#communities-components}

Per abilitare i componenti per l’authoring di Communities, segui queste istruzioni:

* [Accesso ai componenti di Communities](basics.md#accessing-communities-components)

Ai fini di questa sandbox, inizia con i seguenti componenti **Communities** (attiva selezionando la casella ):

* Commenti
* Forum
* Valutazione
* Recensioni
* Riepilogo recensioni (visualizzazione)
* Votazione

Inoltre, scegli i componenti **[!UICONTROL Generale]**, ad esempio

* Immagine
* Tabella
* Testo
* Titolo (Foundation)

>[!NOTE]
>
>I componenti abilitati per la pagina par vengono memorizzati nell’archivio come valore della proprietà `components` del\
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` nodo.

## Pagina di destinazione {#landing-page}

In un ambiente multilingue, la pagina principale includerebbe uno script che analizzerebbe la richiesta del client per determinare la lingua preferita.

In questo semplice esempio, la pagina principale viene impostata statisticamente per reindirizzare alla pagina inglese, che in futuro potrebbe essere la pagina di destinazione principale con un collegamento alla pagina di riproduzione.

Modifica l’URL del browser nella pagina principale: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Seleziona l’icona Informazioni pagina
* Seleziona **[!UICONTROL Apri proprietà]**
* Nella scheda AVANZATE

   * Per la voce Reindirizza, vai a **[!UICONTROL Siti web > Sito Sandbox SCF > SCF Sandbox]**
   * Fai clic su **[!UICONTROL OK]**

* Fai clic su **[!UICONTROL OK]**

Una volta pubblicato il sito, l’esplorazione della pagina principale in un’istanza di pubblicazione reindirizzerà alla pagina inglese.

L’ultimo passaggio prima di giocare con i componenti SCF di Communities consiste nell’aggiungere una cartella della libreria client (clientlibs) .... **[⇒](add-clientlibs.md)**
