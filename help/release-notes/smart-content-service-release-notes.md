---
title: Note sulla versione di Smart Content Service
seo-title: Note sulla versione di Smart Content Service
description: Panoramica di Smart Content Service e problemi noti relativi al servizio.
seo-description: Panoramica di Smart Content Service e problemi noti relativi al servizio.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 7%

---


# Note sulla versione di Smart Content Service {#smart-content-service-release-notes}

Panoramica di Smart Content Service e problemi noti relativi al servizio.

Le organizzazioni richiedono che i tag delle proprie risorse digitali siano basati sulla tassonomia a cui dipendenti, partner e clienti fanno riferimento per cercare risorse digitali. Rispetto ai tag generici, le risorse con tag basati sulla tassonomia aziendale vengono identificate e recuperate più facilmente mediante ricerche basate sui tag.

Smart Content Service utilizza la tassonomia aziendale dei AEM Assets per assegnare automaticamente i tag alle risorse digitali, in modo che le risorse più rilevanti vengano visualizzate nelle ricerche.

È necessario formare Smart Content Service su un set specifico di risorse e tag AEM per riconoscere la tassonomia aziendale. Una volta eseguita la formazione, il servizio può applicare questi tag a un set di risorse simile.

Smart Content Service è basato sulla piattaforma Adobe Sensei , che consente di formare l&#39;algoritmo di riconoscimento delle immagini nella tassonomia aziendale. Questa funzione di content intelligence viene quindi utilizzata per applicare tag rilevanti a risorse simili.

## Miglioramenti principali {#key-improvements}

Smart Content Service include i seguenti miglioramenti principali:

* Ottimizzazioni degli algoritmi per migliorare ulteriormente la precisione del modello e i valori di richiamo
* Supporto per il ripristino della formazione del modello per tutti i tag a livello di tenant
* Supporto per spazi dei nomi avanzati per evitare conflitti
* Nuova politica di sostituzione del modello per evitare qualsiasi degrado dovuto alla riqualificazione
* Monitoraggio a livello di tenant per l&#39;utilizzo del servizio
* Correzioni per problemi relativi a clustering e connessione, che migliorano la robustezza del servizio

## Problemi risolti {#fixed-issues}

In questa versione sono stati risolti i seguenti problemi:

* Se non è possibile connettersi al server MySQL, i processi di lavoro per i flussi di lavoro di formazione e di tag si concludono. CQ-4242886

* Il punteggio parziale di precisione non viene calcolato correttamente. CQ-4241797

* Calcolo PR non corretto per il modello. CQ-4241381

* Nel flusso di lavoro di formazione mancano le risorse di esempio durante l’elaborazione dalla coda CQ-4240901

* Miglioramenti nel richiamo di precisione. CQ-4239895

* Criteri di sostituzione modello. CQ-4239886

* Le immagini per la camicia da uomo sono etichettate con la giacca donna etichetta. CQ-4239650

* Gli esempi di formazione non vengono visualizzati nella distribuzione dell&#39;area di visualizzazione. CQ-4239483

* La convalida nel processo di formazione deve avvenire su un set di risorse inviato per la formazione. CQ-4238834

* La creazione del modello non riesce per il foraggiamento negativo anche se per un tag sono presenti valori positivi/negativi minimi. CQ-4240741

* Voci fuorvianti per il foraggiamento negativo nei registri istruttori. CQ-4240738

* Problema con la formazione iniziale se i tag inviati per la formazione sono negativi casuali l’uno dell’altro. CQ-4240118

* Registri improvvisati per monitorare l&#39;utilizzo del servizio per tenant. CQ-4239781

## Lingue {#languages}

Smart Content Service è disponibile per le seguenti impostazioni internazionali:

* Inglese
* Tedesco
* Francese
* Spagnolo
* Italiano
* Portoghese
* Giapponese
* Cinese semplificato
* Coreano

## Collegamenti {#links}

* [Pagina prodotto  Adobe Experience Manager su adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentazione avanzata sui tag avanzati](/help/assets/enhanced-smart-tags.md)

## Product Access and Support (Restricted Sites) {#product-access-and-support-restricted-sites}

Questi siti sono disponibili solo per i clienti. Se siete un cliente e richiedete l&#39;accesso, contattate il vostro responsabile commerciale  Adobe.

* [Accesso al prodotto](https://login.marketing.adobe.com)
* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/).
* Aggiornamenti dei prodotti, patch e pacchetti per funzionalità aggiuntive sulla distribuzione [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)software.
* [Assistenza clienti tramite  Admin Console](https://adminconsole.adobe.com/). Per ulteriori informazioni, consulta [Nuova esperienza](https://docs.adobe.com/content/help/en/customer-one/using/home.html)di assistenza clienti  Adobe.
