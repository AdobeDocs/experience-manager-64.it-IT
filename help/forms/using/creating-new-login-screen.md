---
title: Creazione di una nuova schermata di login
seo-title: Creazione di una nuova schermata di login
description: Come modificare la pagina di accesso dei moduli di LiveCycle, ad esempio 'area di lavoro AEM Forms o Forms Manager.
seo-description: Come modificare la pagina di accesso dei moduli di LiveCycle, ad esempio 'area di lavoro AEM Forms o Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 4%

---


# Creazione di una nuova schermata di login {#creating-a-new-login-screen}

È possibile modificare la schermata di accesso di tutti  moduli AEM Forms che utilizzano la schermata di login  AEM Forms. Ad esempio, le modifiche influiscono sulla schermata di accesso dell’area di lavoro di Forms Manager e  AEM Forms.

## Prerequisito {#prerequisite}

1. Effettuate l&#39;accesso in `/lc/crx/de` con le autorizzazioni di amministratore.
1. Effettuare le seguenti operazioni:

   1. Replicare la struttura gerarchica: di `/libs/livecycle/core/content` in `/apps/livecycle/core/content`. Mantenere le stesse proprietà (nodo/cartella) e il controllo di accesso.
   1. Copiate la cartella del contenuto: da `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Eliminate il contenuto della cartella `/apps/livecycle/core`.

1. Effettuare le seguenti operazioni:

   1. Replicare la struttura gerarchica: di `/libs/livecycle/core/components/login` in `/apps/livecycle/core/components/login`. Mantenere le stesse proprietà (nodo/cartella) e il controllo di accesso.
   1. Copiate la cartella dei componenti: da `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Eliminate il contenuto della cartella: `/apps/livecycle/core/components/login`.

## Aggiunta di una nuova impostazione internazionale {#adding-a-new-locale}

1. Copiate la cartella `i18n`:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. Eliminate tutte le cartelle all&#39;interno `i18n` tranne una, ad esempio `en`.
1. Nella cartella `en`, eseguire le azioni seguenti:

   1. Rinominare la cartella con il nome delle impostazioni internazionali che si desidera supportare. Esempio, `ar`.
   1. Modificate il valore della proprietà `jcr:language` in `ar`(per la cartella `ar`).

   >[!NOTE]
   >
   >Se l&#39;impostazione internazionale è una combinazione di codice paese lingua, ad esempio `ar-DZ`, modificare il nome della cartella e il valore della proprietà in `ar-DZ`.

1. Copia `login.jsp`:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. Modificate il frammento di codice seguente per `/apps/livecycle/core/components/login/login.jsp`:

   ***Lingua è il codice della lingua***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Lingua è il codice del paese della lingua***

   ```
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   
   To
   
   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
   ```

   ***Per modificare le impostazioni internazionali predefinite***

   ```
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)
   
   To
   
   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
   ```

## Aggiunta di nuovo testo o modifica di testo esistente {#adding-new-text-or-modifying-existing-text}

1. Copia cartella `i18n`:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. A questo punto, modificate il valore della proprietà `sling:message` del nodo (nella cartella del codice lingua desiderata) per il quale desiderate modificare il testo. La conversione viene eseguita tramite la chiave indicata nel valore della proprietà `sling:key` del nodo.
1. Per aggiungere una nuova coppia chiave-valore, effettuare le seguenti operazioni. Controllate un esempio nello screenshot che segue.

   1. Create un nodo di tipo `sling:MessageEntry`, oppure copiate un nodo esistente e rinominatelo in tutte le cartelle delle impostazioni internazionali.
   1. Copia `login.jsp` :

      * da `/libs/livecycle/core/components/login`
      * a `/apps/livecycle/core/components/login`
   1. Modificare `/apps/livecycle/core/components/login/login.jsp` per incorporare il testo appena aggiunto.

   ![capture](assets/capture.png)

   ```
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   
   To
   
   div class="loginContent">
                       <span class="loginFlow"></span>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></span>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></span>
                       <span class="loginTitle"><%= i18n.get("Login") %></span>
                       <% if (loginFailed) {%>
   ```

## Aggiunta di nuovo stile o modifica dello stile esistente {#adding-new-style-or-modifying-existing-style}

1. Copia nodo `login`:

   * da `/libs/livecycle/core/content`
   * a `/apps/livecycle/core/content`

1. Eliminare i file `login.js` e `jquery-1.8.0.min.js` dal nodo `/apps/livecycle/core/content/login.`
1. Modificate gli stili nel file CSS.
1. Per aggiungere nuovi stili:

   1. Aggiungere nuovi stili a `/apps/livecycle/core/content/login/login.css`
   1. Copia `login.jsp`

      * da `/libs/livecycle/core/components/login`
      * a `/apps/livecycle/core/components/login`
   1. Modificare `/apps/livecycle/core/components/login/login.jsp` per incorporare i nuovi stili aggiunti.


1. Esempio:

   * Aggiungete quanto segue a `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Modificate quanto segue in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Se le immagini esistenti in `/apps/livecycle/core/content/login` (copiate da `/libs/livecycle/core/content/login`) vengono rimosse, rimuovere i riferimenti corrispondenti in CSS.

## Aggiungere nuove immagini {#add-new-images}

1. Seguire i passaggi per aggiungere nuovo stile o modificare lo stile esistente (documentato sopra).
1. Aggiungere nuove immagini in `/apps/livecycle/core/content/login`. Per aggiungere un&#39;immagine:

   1. Installare il client WebDAV.
   1. Andate alla cartella `/apps/livecycle/core/content/login` utilizzando il client webDAV. Per ulteriori informazioni, vedi: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Aggiungete nuove immagini.

1. Aggiungete nuovi stili in `/apps/livecycle/core/content/login/login.css,` corrispondenti alle nuove immagini aggiunte in `/apps/livecycle/core/content/login`.
1. Utilizzate i nuovi stili in `login.jsp` in `/apps/livecycle/core/components`.
1. Ad Esempio:

   * Aggiungi quanto segue a `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Modificate quanto segue in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
