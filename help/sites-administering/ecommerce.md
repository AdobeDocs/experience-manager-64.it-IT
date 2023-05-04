---
title: eCommerce
seo-title: eCommerce
description: AEM eCommerce aiuta gli esperti di marketing a fornire esperienze di acquisto personalizzate su diversi punti di contatto web, mobili e social.
seo-description: AEM eCommerce helps marketers deliver branded, personalized shopping experiences across web, mobile, and social touchpoints.
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: Commerce Integration Framework
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 3%

---

# eCommerce{#ecommerce}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

* [Concetti](/help/sites-administering/concepts.md)
* [Amministrazione (generico)](/help/sites-administering/generic.md)
* [Commerce Cloud SAP](/help/sites-administering/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

In Adobe sono disponibili due versioni di Commerce Integration Framework:

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versioni di AEM supportate | AEM on-premise o AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integrazione monolitica, mappatura pre-compilazione (modello)<br> - Archivio JCR | - Magento <br>- Java e JavaScript <br>- Nessun dato Commerce memorizzato nell&#39;archivio JCR |
| Front-end | AEM pagine di rendering lato server | Applicazione a pagina mista (rendering ibrido) |
| Catalogo dei prodotti | - Importazione prodotti, editor, memorizzazione in cache in AEM <br>- Cataloghi regolari con pagine AEM o proxy | - Nessuna importazione di prodotti <br>- Modelli generici <br>- Dati on-demand tramite connettore |
| Scalabilità | - Può supportare fino a pochi milioni di prodotti (dipende dal caso d&#39;uso) <br> - Memorizzazione in cache su Dispatcher | - Nessuna limitazione del volume <br>- Memorizzazione in cache su Dispatcher o CDN |
| Modello dati standardizzato | No | Sì, Magento schema GraphQL |
| Disponibilità | Sì:<br> - Commerce Cloud SAP (estensione aggiornata per supportare AEM 6.4 e Hybris 5 (impostazione predefinita) e mantenere la compatibilità con Hybris 4 <br>- Commerce Cloud Salesforce (connettore open source per supportare AEM 6.4) | Sì tramite open source tramite GitHub. <br> Magento Commerce (supporta Magento 2.3.2 (predefinito) e compatibile con Magento 2.3.1). |
| Quando utilizzare | Casi d’uso limitati: Per gli scenari in cui possono essere necessari l’importazione di cataloghi statici di piccole dimensioni | Soluzione preferita nella maggior parte dei casi d&#39;uso |

eCommerce, insieme a Product Information Management (PIM), gestisce le attività di un sito web incentrato sulla vendita di prodotti tramite un negozio online:

* Creazione, durata e obsolescenza di un prodotto
* Gestione dei prezzi
* Gestione delle transazioni
* Gestione di interi cataloghi
* Record di storage live e centralizzati
* Interfacce web

AEM eCommerce aiuta gli esperti di marketing a fornire esperienze di acquisto personalizzate su diversi punti di contatto web, mobili e social. L’ambiente di authoring AEM ti consente di personalizzare pagine e componenti in base al contesto del visitatore e alle strategie di merchandising di destinazione; ad esempio:

* Pagine prodotto
* Componenti del carrello
* Componenti di estrazione

L’implementazione consente l’accesso in tempo reale alle informazioni di prodotto. Può essere utilizzato per applicare:

* Integrità delle informazioni sul prodotto
* Prezzi
* Inventario delle scorte
* Variazioni nello stato di un carrello

>[!NOTE]
>
>Per utilizzare il framework di integrazione con provider di eCommerce esterni, devi prima installare i pacchetti richiesti. Per ulteriori informazioni, consulta [Distribuzione di eCommerce](/help/sites-deploying/ecommerce.md).
>
>Per informazioni sull’estensione delle funzionalità di eCommerce, consulta [Sviluppo di eCommerce](/help/sites-developing/ecommerce.md).

## Caratteristiche principali {#main-features}

AEM eCommerce fornisce:

* Un certo numero di **componenti AEM predefiniti** per illustrare i risultati ottenibili per il progetto:

   * Display del prodotto
   * Carrello
   * Check-out
   * Prodotti visualizzati di recente
   * Voucher
   * e altri

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >Il framework di integrazione fornito da AEM consente inoltre di creare componenti AEM aggiuntivi per le funzionalità commerce, indipendentemente dal motore di eCommerce specifico.

* **Ricerca** - utilizzando:

   * ricerca AEM
   * ricerca del sistema eCommerce
   * ricerca di terze parti
   * o una loro combinazione.

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Utilizza la capacità AEM di **presentare i contenuti su più canali**, sia la finestra del browser completa che il dispositivo mobile. In questo modo i contenuti vengono consegnati nel formato richiesto dai visitatori.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* La capacità di **Sviluppa la tua implementazione di integrazione basata su [Framework eCommerce AEM](#the-framework)**.

   Le due implementazioni attualmente disponibili sono entrambe basate sullo stesso criterio, oltre all’API generale (il framework). L’implementazione di una nuova integrazione comporta solo l’implementazione delle funzioni necessarie per l’integrazione. I componenti front-end possono essere utilizzati da qualsiasi nuova implementazione durante l’utilizzo delle interfacce (in modo che siano indipendenti dall’implementazione).

* La possibilità di sviluppare **e-commerce basato su esperienze basate su dati e attività dell’acquirente**. Questo consente di realizzare molti scenari:

   * Un esempio potrebbe essere la riduzione dei costi di spedizione quando l&#39;ordine totale supera un importo specifico.
   * Un altro potrebbe consentire di fornire offerte stagionali che utilizzano i dati del profilo (ad esempio la posizione). Questi possono quindi essere evidenziati, sempre a seconda di altri fattori quando necessario.

   Nell’esempio seguente viene mostrato un teaser con un contenuto inferiore a $75:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   Questo può essere modificato quando il contenuto del carrello supera i $75:

   ![chlimage_1-154](assets/chlimage_1-154.png)

* E altre caratteristiche, tra cui:

   * Contenuto del carrello conservato nelle sessioni
   * Storico ordini completo
   * Aggiornamento del catalogo Express

## Quadro {#the-framework}

La [Concetti](/help/sites-administering/concepts.md) la sezione descrive il framework in modo più dettagliato, ma quanto segue fornisce una vista ad alto livello del framework:

### Cosa? {#what}

* Il framework di integrazione fornisce l’API , una serie di componenti per illustrare funzionalità e diverse estensioni per fornire esempi di metodi di connessione.
* Il quadro fornisce la struttura di base necessaria per l’implementazione di un progetto.
* Il framework è estensibile.
* Il framework non fornisce un sito pronto all’uso pronto all’uso. Una certa quantità di lavoro di sviluppo è sempre necessaria per adattare il framework alle tue specifiche.

### Perché? {#why}

* Fornire i meccanismi di base necessari per realizzare rapidamente un sito eCommerce personalizzato.
* Tp offre la flessibilità necessaria per lo sviluppo di un sito e-commerce reale.
* Illustra le best practice.
