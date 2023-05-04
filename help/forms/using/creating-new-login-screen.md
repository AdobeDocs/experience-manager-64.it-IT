---
title: Creazione di una nuova schermata di accesso
seo-title: Creating a new login screen
description: Come modificare la pagina di accesso dei moduli di LiveCycle, ad esempio AEM Forms Workspace o Forms Manager.
seo-description: How-to modify the login page of LiveCycle modules, for example of AEM Forms workspace or Forms Manager.
uuid: c7643f87-4a08-4c63-b87c-f987dbe18ece
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: cfaa6b49-3fd0-4c08-84a2-e86c7e7e3532
exl-id: caa4f835-c353-49d5-b18c-4d0538c1136f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# Creazione di una nuova schermata di accesso {#creating-a-new-login-screen}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi modificare la schermata di accesso di tutti i moduli AEM Forms che utilizzano la schermata di accesso di AEM Forms. Ad esempio, le modifiche influiscono sulla schermata di accesso di, sia di Forms Manager che di AEM Forms workspace.

## Prerequisito {#prerequisite}

1. Accedi a `/lc/crx/de` con autorizzazioni di amministratore.
1. Esegui le seguenti operazioni:

   1. Replicare la struttura gerarchica: di `/libs/livecycle/core/content` a `/apps/livecycle/core/content`. Mantenere le stesse proprietà (nodo/cartella) e il controllo di accesso.
   1. Copia la cartella del contenuto: da `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimina il contenuto di `/apps/livecycle/core` cartella.

1. Esegui le seguenti operazioni:

   1. Replicare la struttura gerarchica: di `/libs/livecycle/core/components/login` a `/apps/livecycle/core/components/login`. Mantenere le stesse proprietà (nodo/cartella) e il controllo di accesso.
   1. Copia la cartella dei componenti: da `/libs/livecycle/core` a `/apps/livecycle/core`.
   1. Elimina il contenuto della cartella: `/apps/livecycle/core/components/login`.

## Aggiunta di una nuova impostazione internazionale {#adding-a-new-locale}

1. Copia il `i18n` cartella:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. Elimina tutte le cartelle all&#39;interno `i18n` tranne uno, dite `en`.
1. Sulla cartella `en`, esegui le seguenti operazioni:

   1. Rinomina la cartella con il nome delle impostazioni internazionali che desideri supportare. Esempio: `ar`.
   1. Modificare la proprietà `jcr:language` valore a `ar`(per `ar` cartella).

   >[!NOTE]
   >
   >Se le impostazioni internazionali sono una combinazione di codice paese lingua, ad esempio `ar-DZ`, quindi modifica il nome della cartella e il valore della proprietà in `ar-DZ`.

1. Copia `login.jsp`:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. Modifica il seguente frammento di codice per `/apps/livecycle/core/components/login/login.jsp`:

   ***Le impostazioni internazionali sono codici della lingua***

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

   ***L’impostazione internazionale è un codice del paese della lingua***

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

1. Copia `i18n` cartella:

   * da `/libs/livecycle/core/components/login`
   * a `/apps/livecycle/core/components/login`

1. Ora modifica il valore della proprietà `sling:message` del nodo (nella cartella del codice locale desiderata) per il quale si desidera modificare il testo. La traduzione viene effettuata tramite la chiave menzionata nel valore di `sling:key` proprietà del nodo.
1. Per aggiungere una nuova coppia chiave-valore, esegui le seguenti operazioni. Controlla un esempio nella schermata seguente.

   1. Crea un nodo di tipo `sling:MessageEntry`oppure copia un nodo esistente e rinominalo, in tutte le cartelle locali.
   1. Copia `login.jsp` :

      * da `/libs/livecycle/core/components/login`
      * a `/apps/livecycle/core/components/login`
   1. Modifica `/apps/livecycle/core/components/login/login.jsp` incorporare il testo appena aggiunto.

   ![catturare](assets/capture.png)

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

## Aggiunta di un nuovo stile o modifica di uno stile esistente {#adding-new-style-or-modifying-existing-style}

1. Copia `login` nodo:

   * da `/libs/livecycle/core/content`
   * a `/apps/livecycle/core/content`

1. Elimina file `login.js` e `jquery-1.8.0.min.js`, dal nodo `/apps/livecycle/core/content/login.`
1. Modifica gli stili nel file CSS.
1. Per aggiungere nuovi stili:

   1. Aggiungi nuovi stili a `/apps/livecycle/core/content/login/login.css`
   1. Copia `login.jsp`

      * da `/libs/livecycle/core/components/login`
      * a `/apps/livecycle/core/components/login`
   1. Modifica `/apps/livecycle/core/components/login/login.jsp` per incorporare gli stili appena aggiunti.


1. Ad esempio:

   * Aggiungi quanto segue a `/apps/livecycle/core/content/login/login.css`.

   ```css
   .newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
   ```

   * Modifica quanto segue in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContentArea">
   
   To
   
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Se le immagini esistenti in `/apps/livecycle/core/content/login` (copiato da `/libs/livecycle/core/content/login`) vengono rimossi, quindi rimuovi i riferimenti corrispondenti in CSS.

## Aggiungi nuove immagini {#add-new-images}

1. Segui i passaggi descritti in precedenza per aggiungere un nuovo stile o modificare lo stile esistente.
1. Aggiungi nuove immagini in `/apps/livecycle/core/content/login`. Per aggiungere un&#39;immagine:

   1. Installa il client WebDAV.
   1. Passa a `/apps/livecycle/core/content/login` cartella, utilizzando il client webDAV. Per ulteriori informazioni, consulta: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).
   1. Aggiungi nuove immagini.

1. Aggiungi nuovi stili in `/apps/livecycle/core/content/login/login.css,` corrispondente alle nuove immagini aggiunte in `/apps/livecycle/core/content/login`.
1. Utilizzare i nuovi stili in `login.jsp` a `/apps/livecycle/core/components`.
1. Ad esempio:

   * Aggiungi quanto segue a `/apps/livecycle/core/content/login/login.css`

   ```css
   .newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
   ```

   * Modifica quanto segue in /apps/livecycle/core/components/login.jsp.

   ```
   <div class="loginContainerBkg">
   
   To
   
   <div class="newLginContainerBkg">
   ```
