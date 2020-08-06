---
title: eCommerce
seo-title: eCommerce
description: 'AEM eCommerce consente ai professionisti del marketing di offrire esperienze di acquisto personalizzate e personalizzate su siti Web, dispositivi mobili e social network. '
seo-description: 'AEM eCommerce consente ai professionisti del marketing di offrire esperienze di acquisto personalizzate e personalizzate su siti Web, dispositivi mobili e social network. '
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
translation-type: tm+mt
source-git-commit: eb1ae2b4910e7adef48865996db4837175f588d9
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 3%

---


# eCommerce{#ecommerce}

* [Concetti ](/help/sites-administering/concepts.md)
* [Amministrazione (generica)](/help/sites-administering/generic.md)
* [Commerce Cloud SAP](/help/sites-administering/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

 Adobe fornisce due versioni di Commerce Integration Framework:

|  | CIF on-prem | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versioni di AEM supportate | AEM on prem o AMS 6.x | AEM AMS 6.4 e 6.5 |
| Back-end | - AEM, Java <br> - Integrazione monolitica, mappatura pre-build (modello)<br> - archivio JCR | - Magento <br>- Java e Javascript <br>- Nessun dato Commerce memorizzato nell&#39;archivio JCR |
| Front-end | AEM pagine sottoposte a rendering sul lato server | Applicazione a pagina mista (rendering ibrido) |
| Catalogo prodotti | - Importatore di prodotti, editor, cache in AEM <br>- Cataloghi regolari con AEM o pagine proxy | - Nessuna importazione di prodotti <br>- Modelli generici <br>- Dati on-demand tramite connettore |
| Scalabilità | - Può supportare fino a pochi milioni di prodotti (dipende dal caso d&#39;uso) <br> - Memorizzazione nella cache del Dispatcher | - Nessuna limitazione del volume <br>- Memorizzazione nella cache su Dispatcher o CDN |
| Modello dati standardizzato | No | Sì, schema Magento GraphQL |
| Disponibilità | Sì:<br> - Commerce Cloud SAP (estensione aggiornata per supportare AEM 6.4 e Hybris 5 (predefinita) e mantiene la compatibilità con Hybris 4 <br>- Salesforce Commerce Cloud (connettore open-source per supportare AEM 6.4) | Sì tramite open source tramite GitHub. <br> Magento Commerce (Supporta l&#39;Magento 2.3.2 (predefinito) e compatibile con Magento 2.3.1). |
| Quando utilizzare | Casi di utilizzo limitati: Per gli scenari in cui può essere necessario importare cataloghi statici di piccole dimensioni | Soluzione preferita nella maggior parte dei casi di utilizzo |

eCommerce, insieme a Product Information Management (PIM), gestisce le attività di un sito web incentrato sulla vendita di prodotti tramite un negozio online:

* Creazione, durata e obsolescenza di un prodotto
* Gestione dei prezzi
* Gestione delle transazioni
* Gestione di interi cataloghi
* Record di archiviazione live e centralizzati
* Interfacce Web

AEM eCommerce consente ai professionisti del marketing di offrire esperienze di acquisto personalizzate e personalizzate su siti Web, dispositivi mobili e social network. L’ambiente di authoring AEM consente di personalizzare pagine e componenti in base al contesto del visitatore e alle strategie di merchandising; ad esempio:

* Pagine prodotto
* Componenti per carrello acquisti
* Componenti di estrazione

L&#39;implementazione consente l&#39;accesso in tempo reale alle informazioni sui prodotti. Può essere utilizzato per applicare:

* Integrità delle informazioni sui prodotti
* Prezzi
* Scorte
* Variazioni nello stato di un carrello

>[!NOTE]
>
>Per utilizzare il framework di integrazione con i provider di eCommerce esterni, è innanzitutto necessario installare i pacchetti richiesti. Per ulteriori informazioni, vedere [Distribuzione di eCommerce](/help/sites-deploying/ecommerce.md).
>
>Per informazioni sull’estensione delle funzionalità eCommerce, consultate [Sviluppo di eCommerce](/help/sites-developing/ecommerce.md).

## Funzioni principali {#main-features}

AEM eCommerce fornisce:

* Una serie di componenti **AEM** out-of-the-box per illustrare quali risultati è possibile ottenere per il progetto:

   * Visualizzazione del prodotto
   * Carrello
   * Check-out
   * Prodotti visualizzati di recente
   * Voucher
   * e altri

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >Il framework di integrazione fornito da AEM consente inoltre di creare componenti AEM aggiuntivi per le funzionalità di eCommerce, indipendentemente dal motore specifico utilizzato.

* **Ricerca** - tramite:

   * ricerca AEM
   * la ricerca del sistema eCommerce
   * una ricerca di terze parti (ad esempio, Search&amp;Promote)
   * o una loro combinazione.

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Utilizza la capacità AEM di **presentare i contenuti su più canali**, indipendentemente dalla finestra completa del browser o dal dispositivo mobile. In questo modo, i contenuti vengono distribuiti nel formato richiesto dai visitatori.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* La capacità di **sviluppare la propria implementazione di integrazione sulla base del[AEM framework](#the-framework)**eCommerce.

   Le due implementazioni attualmente disponibili sono entrambe basate sulla stessa base, oltre all&#39;API generale (il framework). L&#39;implementazione di una nuova integrazione richiede solo l&#39;implementazione delle funzioni necessarie per l&#39;integrazione. I componenti front-end possono essere utilizzati da qualsiasi nuova implementazione utilizzando interfacce (in modo che siano indipendenti dall&#39;implementazione).

* La possibilità di sviluppare un&#39;attività commerciale basata sull&#39; **esperienza basata sui dati e sulle attività** dell&#39;acquirente. Questo consente di realizzare molti scenari:

   * Un esempio potrebbe consistere nel fornire riduzioni dei costi di spedizione quando l&#39;ordine totale supera un importo specifico.
   * Un altro potrebbe consentire di fornire offerte stagionali che utilizzano i dati del profilo (ad esempio la posizione). Questi possono quindi essere evidenziati, sempre in base ad altri fattori, se necessario.

   Nell’esempio di seguito, un teaser viene visualizzato in quanto il contenuto del carrello è inferiore a $75:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   Questo può essere modificato quando il contenuto del carrello supera i $75:

   ![chlimage_1-154](assets/chlimage_1-154.png)

* Altre caratteristiche, tra cui:

   * Contenuto del carrello acquisti conservato tra le sessioni
   * Cronologia ordine completo
   * Aggiornamento del catalogo espresso

## Il Quadro {#the-framework}

La sezione [Concetti](/help/sites-administering/concepts.md) descrive la struttura in modo più dettagliato, ma quanto segue fornisce una vista ad alto livello della struttura:

### Cosa? {#what}

* Il framework di integrazione fornisce l&#39;API, una serie di componenti per illustrare le funzionalità e diverse estensioni per fornire esempi di metodi di connessione.
* Il quadro fornisce la struttura di base necessaria per l&#39;implementazione di un progetto.
* Il framework è estensibile.
* Il framework non fornisce un sito pronto all&#39;uso e pronto all&#39;uso. Per adattare il framework alle proprie specifiche, è sempre necessario un certo lavoro di sviluppo.

### Perché? {#why}

* Fornire i meccanismi di base necessari per realizzare rapidamente un sito eCommerce personalizzato.
* Tp offre la flessibilità necessaria per sviluppare un sito eCommerce reale.
* Illustra le best practice.

