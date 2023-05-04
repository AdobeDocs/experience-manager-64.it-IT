---
title: Utilizzo di set di regole per la trasformazione degli URL
description: Puoi distribuire i set di regole in Dynamic Media per trasformare gli URL. I set di regole sono insiemi di istruzioni scritte in un linguaggio di script (ad esempio JavaScript) che valutano i dati XML e eseguono determinate azioni se tali dati soddisfano determinate condizioni.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: f0cd3a75-03ed-40a9-b336-8a782f3cfe69
feature: Rulesets
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 6%

---

# Utilizzo dei set di regole per la trasformazione degli URL {#using-rulesets-to-transform-urls}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi distribuire i set di regole in Dynamic Media per trasformare gli URL. I set di regole sono insiemi di istruzioni scritte in un linguaggio di script (ad esempio JavaScript) che valutano i dati XML e eseguono determinate azioni se tali dati soddisfano determinate condizioni. Ogni regola consiste di almeno una condizione e almeno un&#39;azione. Una regola valuta i dati XML in base alle condizioni e, se una condizione viene soddisfatta, esegue l&#39;azione appropriata. Esempi di set di regole includono:

* Aggiunta di un suffisso di tipo MIME. Molti servizi e siti web richiedono suffissi di immagini, ad esempio l&#39;aggiunta di `.jpg` a un URL.
* Creazione di un percorso di cartella per l’URL a scopo di ottimizzazione SEO (Search Engine Optimization).

   Vedi [Come Adobe Dynamic Media Classic supporta il SEO](/help/assets/assets/s7_seo.pdf).

* Aggiunta di metadati all’URL per scopi SEO (Search Engine Optimization).

   Vedi [Come Adobe Dynamic Media Classic supporta il SEO](/help/assets/assets/s7_seo.pdf).

* Impostazione della disposizione dei contenuti per attivare un download.
* Semplificare gli URL dei modelli di Image Server per la personalizzazione. Ad esempio, girare `rgb{XX,YY,ZZ}` in RTF-ready `\redXX\greenYY\blueZZ`

* Richiedere la codifica di alcuni caratteri, ad esempio `$`, `{`e `}`, e alcuni caratteri da decodificare verso ImageServer. Ad esempio, Facebook non funziona bene con gli URL contenenti caratteri speciali.

   Vedi [Rimozione di caratteri speciali dagli URL](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

Nel contesto di Dynamic Media, i siti web che utilizzano un sistema basato su XML per gestire le informazioni sulle risorse possono caricare file XML in Dynamic Media. Puoi designare uno di questi file come file del set di regole di pre-elaborazione per il serving della risorsa Dynamic Media. Questo file ristruttura il formato del protocollo URL standard per soddisfare la logica di business dei sistemi che vengono integrati con Dynamic Media. È possibile specificare un file XML da utilizzare come percorso del file delle definizioni del set di regole.

>[!CAUTION]
>
>Prestare attenzione quando si utilizzano i set di regole; possono impedire la visualizzazione del contenuto Dynamic Media sul sito web.

Sono disponibili set di regole di esempio che possono essere utili per creare un set di regole personalizzato.\
Vedi [Riferimento set di regole](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference.html).

Come per la creazione di tutti i set di regole, assicurati che il file XML sia valido prima di caricarlo utilizzando un programma di convalida XML come xmlvalid.\
Vedi anche [Risoluzione dei problemi dei set di regole](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Inoltre, verifica prima il set di regole in un ambiente di staging che non influisce sull’ambiente di produzione live.\
Gli ambienti di produzione e gli ambienti di staging in genere richiedono accessi diversi.

Consulta la sezione [Applicazione desktop Adobe Dynamic Media Classic per l&#39;accesso alle informazioni](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app).

<!-- * **NA staging environment** login page: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA staging environment** login page: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC staging environment** login page: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/) -->

Vedi anche [Utilizzo dell&#39;immagine &quot;asset&quot; invece di &quot;is&quot; in un set di regole](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**Per distribuire i set di regole XML:**

1. Accedi al tuo [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#sign-in-dmc-app).

   Le credenziali e l&#39;accesso sono stati forniti da Adobe al momento del provisioning. Se non si dispone di tali informazioni, contattare il supporto tecnico.

1. Carica il file del set di regole facendo quanto segue:

   * Nella barra di navigazione globale, fai clic su **[!UICONTROL Carica]**.
   * Sulla **[!UICONTROL Carica]** , nell’angolo in alto a sinistra, fai clic su **[!UICONTROL Sfoglia]**.
   * In **[!UICONTROL Apri]** aprire il file del set di regole (XML).
   * Seleziona il file, quindi fai clic su **[!UICONTROL Apri]**.
   * Sul lato destro del **[!UICONTROL Carica]** selezionare una cartella di destinazione per il file del set di regole.
   * Vicino alla parte inferiore della pagina, assicurati **[!UICONTROL Pubblica dopo il caricamento]** è controllata.
   * Nell’angolo in basso a destra della pagina, fai clic su **[!UICONTROL Invia caricamento]**.
   * Nella barra di navigazione globale, fai clic su **[!UICONTROL Processi]** per controllare lo stato del processo di caricamento. Quando il **[!UICONTROL Stato]** nella colonna **[!UICONTROL Processo]** In questa pagina viene visualizzato Carica completato e continua con i passaggi successivi.

1. Nella barra di navigazione vicino alla parte superiore della pagina, fai clic su **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni pubblicazione > Image Server]**.
1. Nella pagina **[!UICONTROL Pubblica su Image Server]**, seleziona il gruppo **[!UICONTROL Gestione catalogo]** e individua il **[!UICONTROL Percorso file definizione set regole]**, quindi fai clic su **[!UICONTROL Seleziona]**.
1. Nella pagina **[!UICONTROL Seleziona file definizione set regole (XML)]**, individua il file del set regole, quindi fai clic su **[!UICONTROL Seleziona]** nell’angolo inferiore destro della pagina.
1. Nell’angolo inferiore destro della pagina Configurazione, fai clic su **[!UICONTROL Chiudi]**.
1. Esegui un processo di pubblicazione su Image Server.

   Le condizioni del set di regole vengono applicate alle richieste ai server di immagini Dynamic Media live.

   Se apporti modifiche al file del set di regole, le modifiche vengono applicate immediatamente quando ricarichi e ripubblichi il file del set di regole aggiornato.
