---
title: Note sulla versione del Servizio di contenuti avanzati
seo-title: Note sulla versione del Servizio di contenuti avanzati
description: Panoramica del Servizio di contenuti avanzati e problemi noti relativi al servizio.
seo-description: Panoramica del Servizio di contenuti avanzati e problemi noti relativi al servizio.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
exl-id: 6e7ac9d2-7181-48bb-82c4-61a90e594ff5
source-git-commit: a842c45f0a0597f4c7f143974a550874258e5382
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 7%

---

# Note sulla versione del servizio di contenuti avanzati {#smart-content-service-release-notes}

Panoramica del Servizio di contenuti avanzati e problemi noti relativi al servizio.

Le organizzazioni richiedono l’assegnazione di tag alle risorse digitali in base alla tassonomia utilizzata da dipendenti, partner e clienti per fare riferimento alle risorse digitali e per effettuare ricerche in esse. Rispetto ai tag generici, le risorse con tag basati sulla tassonomia aziendale vengono identificate e recuperate più facilmente tramite ricerche basate sui tag.

Il Servizio di contenuti avanzati utilizza la tassonomia aziendale di AEM Assets per assegnare automaticamente i tag alle risorse digitali, in modo che le risorse più rilevanti vengano visualizzate nelle ricerche.

È necessario addestrare il Servizio di contenuti avanzati su un set specifico di risorse e tag AEM per riconoscere la tassonomia aziendale. Una volta effettuata la formazione, il servizio può applicare questi tag a un set di risorse simile.

Il Servizio di contenuti avanzati è basato sulla piattaforma Adobe Sensei, che consente di addestrare l’algoritmo di riconoscimento delle immagini sulla tassonomia aziendale. Questa intelligenza dei contenuti viene quindi utilizzata per applicare tag rilevanti a risorse simili.

## Miglioramenti principali {#key-improvements}

Il Servizio di contenuti avanzati include i seguenti miglioramenti chiave:

* Ottimizzazioni dell&#39;algoritmo per migliorare ulteriormente la precisione del modello e i valori di richiamo
* Supporto per la reimpostazione della formazione sul modello per tutti i tag a livello di tenant
* Supporto per spazi dei nomi dei tag avanzati migliorati per evitare conflitti
* Nuova politica di sostituzione del modello per evitare qualsiasi degrado dovuto alla riqualificazione
* Monitoraggio in base al tenant per l’utilizzo del servizio
* Correzioni dei problemi relativi al clustering e alla connessione, che aumentano la robustezza del servizio

## Problemi risolti {#fixed-issues}

In questa versione sono stati risolti i seguenti problemi:

* Se non è possibile connettersi al server MySQL, i processi di lavoro per l&#39;assegnazione di tag e i flussi di lavoro di formazione verranno interrotti. CQ-4242886

* Il punteggio di precisione non viene calcolato correttamente. CQ-4241797

* Calcolo PR non corretto per il modello. CQ-4241381

* Nel flusso di lavoro di formazione mancano le risorse di esempio durante l’elaborazione dalla coda CQ-4240901

* Miglioramenti nel richiamo di precisione. CQ-4239895

* Criterio di sostituzione del modello. CQ-4239886

* Le immagini per la maglietta degli uomini sono contrassegnate con l&#39;etichetta della giacca delle donne. CQ-4239650

* Gli esempi di formazione non vengono distribuiti sullo stage. CQ-4239483

* La convalida in un processo di formazione dovrebbe avvenire su un insieme di risorse presentate per la formazione. CQ-4238834

* La creazione del modello non riesce per il foraggio negativo anche se per un tag sono presenti positivi/negativi minimi. CQ-4240741

* Voci fuorvianti per il foraggiamento negativo nei registri del formatore. CQ-4240738

* Problema relativo alla formazione iniziale se i tag inviati per la formazione sono negativi casuali l’uno dell’altro. CQ-4240118

* Improvvisa i registri per monitorare l’utilizzo del servizio per tenant. CQ-4239781

## Lingue {#languages}

Il Servizio di contenuti avanzati è disponibile per le seguenti impostazioni internazionali:

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

* [Pagina del prodotto Adobe Experience Manager su adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentazione avanzata sui tag avanzati](/help/assets/enhanced-smart-tags.md)

## Accesso e supporto ai prodotti (siti con restrizioni) {#product-access-and-support-restricted-sites}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedervi, contatta il tuo account manager Adobe.

* [Accesso al prodotto](https://login.experiencecloud.adobe.com/exc-content/login.html)
* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/).
* Aggiornamenti dei prodotti, patch e pacchetti per funzionalità aggiuntive su [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Assistenza clienti tramite Admin Console](https://adminconsole.adobe.com/). Per ulteriori informazioni, consulta [Nuovo Adobe sull’esperienza di accesso all’Assistenza clienti](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
