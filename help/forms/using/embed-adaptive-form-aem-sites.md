---
title: Incorporare un modulo adattivo o una comunicazione interattiva nella pagina AEM siti
seo-title: Embed an adaptive form or interactive communication in AEM sites page
description: È possibile incorporare moduli adattivi nelle pagine AEM siti. Gli utenti possono compilare e inviare i moduli senza uscire dalle pagine del sito.
seo-description: You can embed adaptive forms in AEM sites pages. Users can fill and submit forms without leaving the site pages.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications, author
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
exl-id: ba5d21a4-231c-4e1e-b172-4d700cb9696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# Incorporare un modulo adattivo o una comunicazione interattiva nella pagina AEM siti {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

AEM Forms consente agli sviluppatori di moduli di incorporare facilmente moduli adattivi e comunicazioni interattive in una pagina AEM Sites o in una pagina web ospitata all’esterno di AEM. Il modulo adattivo incorporato e la comunicazione interattiva sono completamente funzionanti e gli utenti possono compilare e inviare il modulo senza uscire dalla pagina. Consente all’utente di rimanere nel contesto di altri elementi della pagina web e di interagire contemporaneamente con il modulo o la comunicazione interattiva.

Per informazioni sull’incorporazione di un modulo adattivo in una pagina web esterna, consulta [Incorporare un modulo adattivo in una pagina web esterna](/help/forms/using/embed-adaptive-form-external-web-page.md).

Nella pagina AEM Sites puoi aggiungere un modulo adattivo o una comunicazione interattiva utilizzando:

* **[Componente Contenitore di AEM Forms](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms fornisce un componente che è possibile aggiungere alle pagine del sito. Il componente Contenitore di AEM Forms consente di incorporare un modulo adattivo e una comunicazione interattiva.

* **[Browser risorse](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Tutti i moduli e le comunicazioni interattive create sono disponibili in Risorse. È possibile trascinare il modulo come risorsa sulla pagina.

## Prerequisiti {#prerequisites}

Per incorporare un modulo adattivo o una comunicazione interattiva in una pagina AEM siti che utilizza un modello modificabile, assicurati che il componente Modulo AEM sia configurato come componente consentito nel modello associato. Per ulteriori informazioni, consulta **Criteri e proprietà (contenitore di layout)** sezione [Creazione di modelli di pagina](/help/sites-authoring/templates.md).

Nel caso di una pagina Sites che utilizza un modello statico, devi configurarla nel sistema di paragrafi della pagina del sito. Vedi [Configurazione dei componenti in modalità Progettazione](/help/sites-authoring/default-components-designmode.md) per ulteriori informazioni.

## Incorporazione di un modulo adattivo o comunicazione interattiva {#af-component}

Per incorporare un modulo adattivo o una comunicazione interattiva utilizzando il componente Contenitore di AEM Forms:

1. Apri la pagina AEM siti in modalità di modifica in cui desideri incorporare un modulo adattivo o una comunicazione interattiva.
1. Dal pannello del browser Componenti , trascina sulla pagina il componente Contenitore di AEM Forms .

   In alternativa, puoi cercare un modulo adattivo o una comunicazione interattiva nel browser Risorse e trascinarlo nella pagina Sites . Incorpora il modulo in un contenitore AEM Forms.

   >[!NOTE]
   >
   >Non sono supportati più componenti contenitore AEM Forms in una pagina.

1. Tocca il componente contenitore AEM Forms incorporato nella pagina Sites , quindi tocca ![settings_icon](assets/settings_icon.png) sulla barra delle azioni. La **[!UICONTROL Modifica contenitore AEM Forms]** viene visualizzata la finestra di dialogo .
1. Nella finestra di dialogo Modifica contenitore AEM Forms , specifica quanto segue.

   * **Tipo risorsa:** Seleziona il tipo di risorsa da incorporare. Le opzioni sono moduli adattivi e comunicazione interattiva
   * **Percorso risorsa**: Sfoglia e seleziona il modulo adattivo o la comunicazione interattiva da incorporare. Viene compilato automaticamente se viene rilasciato dal browser Risorse.
   * (Solo modulo adattivo) **Invia invio**: Selezionare l’azione da attivare all’invio del modulo. Puoi scegliere di mostrare un messaggio di ringraziamento o una pagina di ringraziamento.

      * **Messaggio di ringraziamento**: Scrivere un messaggio utilizzando l’editor Rich Text da visualizzare durante l’invio del modulo. Questa opzione è disponibile solo quando scegli di mostrare un messaggio di ringraziamento.
      * **Pagina di ringraziamento**: Individuare e selezionare la pagina da visualizzare durante l’invio del modulo. Questa opzione è disponibile solo quando scegli di mostrare una pagina di ringraziamento.
      * **Aggiorna pagina all’invio**: Abilita per aggiornare la pagina contenente il modulo adattivo incorporato per visualizzare la pagina di ringraziamento. In caso contrario, la pagina di ringraziamento sostituisce il modulo adattivo nel contenitore AEM Forms, senza aggiornare la pagina. Questa opzione è disponibile solo quando scegli di mostrare una pagina di ringraziamento.
   * **Tema**: Seleziona un tema che definisce lo stile dei componenti del modulo adattivo o della comunicazione interattiva. Lo stile include proprietà di aspetto quali stile font, colore di sfondo, dimensioni e allineamento.
   * **Altezza**: Specifica l’altezza del contenitore. Lascia vuoto per ridimensionare automaticamente il contenitore.
   * **Libreria client CSS**: Specifica il percorso di una libreria client CSS.


1. Salva le impostazioni. Il modulo adattivo o la comunicazione interattiva è ora incorporato nella pagina .

## Pubblicazione di moduli adattivi incorporati e comunicazione interattiva {#publishing-embedded-adaptive-form-and-interactive-communication}

Consideriamo i seguenti scenari per la pubblicazione di una risorsa incorporata (modulo adattivo o comunicazione interattiva) nella pagina AEM siti:

* Se pubblichi la pagina dei siti di AEM per la prima volta e include un modulo adattivo incorporato o una comunicazione interattiva, pubblica la pagina dei siti e la risorsa incorporata.
* Se hai modificato solo il modulo adattivo incorporato o la comunicazione interattiva in una pagina del sito pubblicata, pubblica la risorsa originale e le modifiche si riflettono nella pagina del sito pubblicata. La pagina del sito pubblicata include un riferimento alla risorsa e non richiede la ripubblicazione della pagina.
* Se hai modificato la pagina Sites e il modulo adattivo incorporato o la comunicazione interattiva, ripubblica la pagina Sites e la risorsa incorporata.

## Modifica di moduli adattivi incorporati e comunicazione interattiva {#modifying-embedded-adaptive-form-and-interactive-communication}

AEM pagina Sites conserva un riferimento al modulo adattivo e alla comunicazione interattiva nel contenitore AEM Forms. Pertanto, tutte le configurazioni e proprietà, come il tema, gli stili e l’azione di invio, configurate nel modulo adattivo originale e la comunicazione interattiva vengono mantenute nel modulo adattivo incorporato e nella comunicazione interattiva.

Per modificare qualsiasi configurazione o proprietà del modulo adattivo incorporato e la comunicazione interattiva, eseguire una delle operazioni seguenti.

* Apri il modulo originale in moduli adattivi o comunicazioni interattive nei rispettivi editor e modificalo.
* Tocca il modulo adattivo o la comunicazione interattiva all’interno della pagina del sito in modalità di modifica, quindi tocca **[!UICONTROL Modifica in una nuova finestra]**. Il modulo originale viene aperto in modalità di modifica che è possibile modificare.

>[!NOTE]
>
>Le modifiche apportate al modulo adattivo originale o alla comunicazione interattiva si riflettono automaticamente nel modulo incorporato. Tuttavia, ripubblica il modulo adattivo, la comunicazione interattiva o la pagina del sito per riflettere le modifiche nella pagina pubblicata.

## Considerazioni e best practice {#considerations-and-best-practices}

Quando incorpori moduli adattivi nelle pagine dei siti AEM tenere a mente quanto segue:

* Le intestazioni e i piè di pagina nel modulo originale non sono inclusi nel modulo incorporato.
* Le bozze degli utenti e gli invii dei moduli incorporati sono supportati e visibili nelle schede Bozze e Inviate Forms sul portale dei moduli.
* L’azione di invio configurata sul modulo originale viene mantenuta nel modulo incorporato.
* Il targeting delle esperienze e i test A/B configurati sul modulo originale non funzionano nel modulo incorporato. Tuttavia, puoi utilizzare il targeting delle esperienze nella pagina Sites per presentare moduli diversi basati sui profili utente.
* Se Adobe Analytics è stato configurato per il modulo originale, i dati analitici del modulo incorporato vengono acquisiti in Adobe Analytics. Tuttavia, non è disponibile nel rapporto di analisi dei moduli.
