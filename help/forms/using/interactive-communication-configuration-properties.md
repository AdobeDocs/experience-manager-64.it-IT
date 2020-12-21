---
title: Proprietà di configurazione di Interactive Communications
seo-title: Proprietà di configurazione della comunicazione interattiva
description: Modifica delle proprietà di configurazione predefinite per le comunicazioni interattive
seo-description: Modifica delle proprietà di configurazione predefinite per le comunicazioni interattive
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 7%

---


# Proprietà di configurazione delle comunicazioni interattive {#interactive-communications-configuration-properties}

Modifica delle proprietà di configurazione predefinite per le comunicazioni interattive

Le comunicazioni interattive includono proprietà configurate automaticamente dopo l&#39;installazione del pacchetto [ componente aggiuntivo AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Gli autori delle comunicazioni interattive possono modificare queste proprietà di configurazione predefinite utilizzando la pagina **Configurazione della console Web di Adobe Experience Manager**.

Aprite la pagina **Configurazione console Web Adobe Experience Manager** utilizzando il seguente URL:

https://&lt;server>:&lt;porta>/&lt;percorsoContesto>/system/console/configMgr

Le proprietà di configurazione includono:

* [Configurazione frammenti di documento](#document-fragments-configuration)
* [Crea configurazione corrispondenza](#create-correspondence-configuration)
* [Configurazione canale Web per moduli adattivi e comunicazioni interattive](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configurazione del tema del canale del canale Web per moduli adattivi e comunicazioni interattive](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configurazione frammenti di documento {#document-fragments-configuration}

Toccate **Configurazione frammenti di documento** nella pagina **Configurazione console Web di Adobe Experience Manager** per visualizzare le proprietà di configurazione per i frammenti di documento.

<table> 
 <tbody> 
  <tr> 
   <td>Proprietà</td> 
   <td>Descrizione</td> 
   <td>Predefiniti</td> 
   <td>Valori accettabili</td> 
  </tr> 
  <tr> 
   <td>Formati di visualizzazione dei dati</td> 
   <td>Formato di visualizzazione specifico per le impostazioni internazionali per campi, variabili ed elementi del modello di dati del modulo disponibili durante la creazione di una comunicazione interattiva per i canali Stampa e Web.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR e ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Rientro</td> 
   <td>Larghezza di una singola unità di rientro applicata al testo nei frammenti di documento elenco.</td> 
   <td>12,7 mm</td> 
   <td>Numero</td> 
  </tr> 
  <tr> 
   <td>Larghezza minima numeri romani</td> 
   <td>Larghezza minima da applicare al campo punto elenco o numero quando si utilizzano numeri romani nei frammenti del documento elenco. </td> 
   <td>12,7 mm</td> 
   <td>Numero</td> 
  </tr> 
  <tr> 
   <td>Larghezza minima</td> 
   <td>Larghezza minima da applicare al campo punto elenco o numero quando si utilizzano elenchi numerati, ad eccezione dei numeri romani, nei frammenti di documento elenco.</td> 
   <td>8,0 mm</td> 
   <td>Numero</td> 
  </tr> 
 </tbody> 
</table>

## Crea configurazione corrispondenza {#create-correspondence-configuration}

Toccate **Crea configurazione corrispondenza** nella pagina **Configurazione console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per l&#39;interfaccia utente dell&#39;agente.

| Proprietà | Descrizione | Predefiniti | Valori accettabili |
|---|---|---|---|
| Mostra contenuto risolto per la modifica | Selezionate la casella di controllo per visualizzare il contenuto risolto (valori effettivi invece dei segnaposto) durante la modifica del modulo di testo nell’interfaccia utente dell’agente. | Non selezionato | Non applicabile |
| Applica filigrana durante l&#39;anteprima | Selezionate la casella di controllo per applicare una filigrana al canale di stampa della comunicazione interattiva in modalità Anteprima. | Non selezionato | Non applicabile |

## Configurazione canale Web per moduli adattivi e comunicazioni interattive {#adaptive-form-and-interactive-communication-web-channel-configuration}

Toccate **Configurazione canale Web per moduli adattivi e comunicazioni interattive** nella pagina **Configurazione console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per il canale Web per Forms adattivo e per le comunicazioni interattive. La tabella seguente descrive le proprietà relative alle comunicazioni interattive:

| Proprietà | Descrizione | Predefiniti | Valori accettabili |
|---|---|---|---|
| Mostra segnaposto | Selezionate la casella di controllo per attivare la visualizzazione dei segnaposto per i campi inclusi nei moduli adattivi e nelle comunicazioni interattive. | Selezionato | Non applicabile |
| Numero massimo di voci della cache | Impostare il numero massimo di moduli adattivi e comunicazioni interattive che è possibile recuperare utilizzando la memoria cache. | 100 | Numero |
| Rendi univoco il nome del file | Selezionate la casella di controllo per avere nomi univoci per i file inclusi come allegati in Forms adattivo e nelle comunicazioni interattive. | Non selezionato | Non applicabile |

## Configurazione del tema del canale Web per moduli adattivi e comunicazioni interattive {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Toccate **Configurazione del tema del canale Web per moduli adattivi e comunicazioni interattive** nella pagina **Configurazione della console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per i temi del canale Web per Forms adattivo e per le comunicazioni interattive.

<table> 
 <tbody> 
  <tr> 
   <td>Proprietà</td> 
   <td>Descrizione</td> 
   <td>Predefiniti</td> 
   <td>Valori accettabili</td> 
  </tr> 
  <tr> 
   <td>Nome elenco font</td> 
   <td>Elenco dei font disponibili per la creazione di Forms adattivo e comunicazioni interattive.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impatto</p> <p>Palatino Linotype</p> </td> 
   <td>Tutti i font del server di  validi</td> 
  </tr> 
 </tbody> 
</table>

