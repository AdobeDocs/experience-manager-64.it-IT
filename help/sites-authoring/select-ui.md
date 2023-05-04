---
title: Selezione dell’interfaccia utente
seo-title: Selecting your UI
description: Configura l'interfaccia da utilizzare per lavorare in AEM
seo-description: Configure which interface you will use to work in AEM
uuid: af956219-178e-477b-a0cd-dd2341ed2ff0
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 9cadec1b-f435-4fd8-b4bc-1a23a0cf11f3
exl-id: 415efbe0-95f5-4c9e-ac33-c4a384a8271e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---

# Selezione dell’interfaccia utente{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Interfaccia utente

L’ambiente di authoring consente di:

* [Authoring](/help/sites-authoring/author.md) (tra cui [authoring delle pagine](/help/sites-authoring/author-environment-tools.md), [gestione delle risorse](/help/assets/home.md), [community](/help/communities/author-communities.md))

* [Amministrazione](/help/sites-administering/home.md) attività necessarie per generare e mantenere i contenuti del sito web

A questo scopo sono disponibili due interfacce grafiche. Questi sono accessibili tramite qualsiasi browser moderno.

1. Interfaccia touch

   * Questa è l’interfaccia AEM moderna e predefinita.
   * È prevalentemente di colore grigio, con interfaccia pulita e piatta.
   * Progettato per l&#39;utilizzo su dispositivi touch e desktop, l&#39;aspetto e la sensazione sono gli stessi su tutti i dispositivi, anche se [visualizzazione e selezione delle risorse](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) sono leggermente diverse (tocco o clic).

      * Desktop:

   ![screen_shot_2018-03-23at115248](assets/screen_shot_2018-03-23at115248.png)

   * Dispositivi tablet (o desktop con larghezza inferiore a 1024 pixel):

   ![screen_shot_2018-03-23at115505](assets/screen_shot_2018-03-23at115505.png)

1. Interfaccia classica

   * Questa è l’interfaccia utente legacy ed è disponibile in AEM da molti anni.
   * È prevalentemente verde.
   * È stato progettato per l&#39;uso su dispositivi desktop.
   * La seguente documentazione si concentra sull’interfaccia utente moderna. Per informazioni sull’authoring nell’interfaccia classica, consulta la [Documentazione sull’authoring per l’interfaccia classica](/help/sites-classic-ui-authoring/classicui.md).

   ![chlimage_1-232](assets/chlimage_1-232.png)

## Interfaccia di commutazione

L’interfaccia touch è ora l’interfaccia standard e [parità delle funzioni](../release-notes/touch-ui-features-status.md) è stato quasi raggiunto con l&#39;amministrazione e la modifica dei siti, ci possono essere momenti in cui l&#39;utente desidera passare al [interfaccia classica](/help/sites-classic-ui-authoring/classicui.md). Ci sono diverse opzioni per farlo.

>[!NOTE]
>
>Per informazioni sullo stato delle funzioni di parità con l’interfaccia classica, consulta la sezione [Parità delle funzioni dell’interfaccia touch](../release-notes/touch-ui-features-status.md) documento.

Puoi definire quale interfaccia utente usare in diverse aree:

* [Configurazione dell’interfaccia utente predefinita per l’istanza](#configuring-the-default-ui-for-your-instance) - Questa opzione consente di impostare l’interfaccia utente predefinita da visualizzare all’accesso dell’utente, anche se l’utente può selezionare una diversa interfaccia per il proprio account o la sessione corrente.

* [Impostazione dell’authoring dell’interfaccia classica per il tuo account](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account) - Questa opzione consente di impostare l’interfaccia utente predefinita per la modifica delle pagine, anche se l’utente può selezionare una diversa interfaccia per il proprio account o la sessione corrente.

* [Passaggio all’interfaccia classica per la sessione corrente](#switching-to-classic-ui-for-the-current-session) - Consente di passare all’interfaccia classica per la sessione corrente.

* Per quanto riguarda [l’authoring delle pagine nel sistema implementa alcune impostazioni locali in relazione all’interfaccia utente](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Le varie opzioni per passare all’interfaccia classica non sono immediatamente disponibili e devono essere configurate in modo specifico per l’istanza in uso.
>
>Vedi [Abilitazione dell’accesso all’interfaccia classica](/help/sites-administering/enable-classic-ui.md) per ulteriori informazioni.

>[!NOTE]
>
>Le istanze aggiornate da una versione precedente manterranno l’interfaccia classica per la creazione delle pagine.
>
>Dopo l’aggiornamento, l’authoring delle pagine non passa automaticamente all’interfaccia touch, ma puoi configurarlo utilizzando l’ [Configurazione OSGi](/help/sites-deploying/configuring-osgi.md) del **Servizio modalità interfaccia utente di authoring WCM** ( `AuthoringUIMode` servizio). Vedi [Ignorare le impostazioni dell’interfaccia per l’editor](#ui-overrides-for-the-editor).

## Configurazione dell’interfaccia utente predefinita per la tua istanza {#configuring-the-default-ui-for-your-instance}

Un amministratore di sistema può configurare l’interfaccia utente visualizzata all’avvio e all’accesso utilizzando [Mappatura radice](/help/sites-deploying/osgi-configuration-settings.md).

Questo valore può essere ignorato dalle impostazioni predefinite dell’utente o dalle impostazioni della sessione.

## Impostazione dell’authoring dell’interfaccia classica per il tuo account {#setting-classic-ui-authoring-for-your-account}

Ogni utente può accedere alle proprie [preferenze utente](/help/sites-authoring/user-properties.md) per definire se utilizzare l’interfaccia classica per la creazione delle pagine (anziché l’interfaccia predefinita).

Questo può essere ignorato dalle impostazioni della sessione.

## Passaggio all’interfaccia classica per la sessione corrente {#switching-to-classic-ui-for-the-current-session}

Gli utenti desktop possono passare dall’interfaccia touch all’interfaccia classica (solo per desktop). Esistono diversi metodi per passare all’interfaccia classica per la sessione corrente:

* **Collegamenti di navigazione**

   >[!CAUTION]
   >
   >Questa opzione per passare all’interfaccia classica non è immediatamente disponibile, ma deve essere configurata in modo specifico per la tua istanza.
   >
   >
   >Vedi [Abilitazione dell’accesso all’interfaccia classica](/help/sites-administering/enable-classic-ui.md) per ulteriori informazioni.

   Se questa opzione è abilitata, ogni volta che passi il mouse su una console applicabile viene visualizzata un’icona (simbolo di un monitor); toccando o facendo clic su di essa si aprirà la posizione appropriata nell’interfaccia classica.

   Ad esempio, i collegamenti da **Sites** a **siteadmin**:

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

* **URL**

   È possibile accedere all’interfaccia classica tramite l’URL della schermata di benvenuto all’indirizzo `welcome.html`. Ad esempio:

   `http://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >L’interfaccia touch è accessibile tramite `sites.html`. Ad esempio:
   >
   >
   >`http://localhost:4502/sites.html`

### Passaggio all’interfaccia classica durante la modifica di una pagina {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Questa opzione per passare all’interfaccia classica non è immediatamente disponibile, ma deve essere configurata in modo specifico per la tua istanza.
>
>Vedi [Abilitazione dell’accesso all’interfaccia classica](/help/sites-administering/enable-classic-ui.md) per ulteriori informazioni.

Se attivato, **Apri l’interfaccia classica** è disponibile dal **Informazioni pagina** finestra di dialogo:

![chlimage_1-49](assets/chlimage_1-49.png)

### Ignorare le impostazioni dell’interfaccia per l’editor {#ui-overrides-for-the-editor}

Le impostazioni definite da un utente o amministratore di sistema possono essere ignorate dal sistema nel caso di authoring delle pagine.

* Durante l’authoring delle pagine:

   * Viene forzato l’utilizzo dell’editor classico quando si accede alla pagina utilizzando `cf#` nell’URL. Ad esempio:

      `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Viene forzato l’utilizzo dell’editor touch quando si utilizza `/editor.html` nell’URL o quando si utilizza un dispositivo touch. Ad esempio:

      `http://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Qualsiasi forzatura è temporanea e valida solo per la sessione del browser

   * Viene impostato un cookie a seconda che sia abilitato o meno il tocco ( `editor.html`) o classica ( `cf#`).

* Quando si aprono le pagine attraverso `siteadmin`, si verificherà l&#39;esistenza di:

   * Il cookie
   * Una preferenza utente
   * Se non esistono, verrà utilizzata per impostazione predefinita le definizioni impostate in [Configurazione OSGi](/help/sites-deploying/configuring-osgi.md) del **Servizio modalità interfaccia utente di authoring WCM** ( `AuthoringUIMode` servizio).

>[!NOTE]
>
>Se [un utente ha già definito una preferenza per l’authoring delle pagine](#setting-classic-ui-authoring-for-your-account), che non verrà ignorato modificando la proprietà OSGi.

>[!CAUTION]
>
>A causa dell’uso dei cookie, come già descritto, si sconsiglia di:
>
>* Modifica manuale dell’URL: un URL non standard potrebbe causare una situazione sconosciuta e la mancanza di funzionalità.
>* NON tenere entrambi gli editor aperti allo stesso tempo, ad esempio in due diverse finestre.
>

