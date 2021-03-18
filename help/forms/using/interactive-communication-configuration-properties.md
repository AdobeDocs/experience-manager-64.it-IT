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
feature: Comunicazione interattiva
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 8%

---


# Proprietà di configurazione delle comunicazioni interattive {#interactive-communications-configuration-properties}

Modifica delle proprietà di configurazione predefinite per le comunicazioni interattive

Le comunicazioni interattive includono proprietà configurate automaticamente dopo l&#39;installazione del pacchetto aggiuntivo [AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Gli autori di comunicazioni interattive possono modificare queste proprietà di configurazione predefinite utilizzando la pagina **Configurazione della console Web Adobe Experience Manager** .

Apri la pagina **Configurazione console Web Adobe Experience Manager** utilizzando il seguente URL:

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

Le proprietà di configurazione includono:

* [Configurazione dei frammenti di documento](#document-fragments-configuration)
* [Creare la configurazione della corrispondenza](#create-correspondence-configuration)
* [Configurazione del canale web per moduli adattivi e comunicazioni interattive](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configurazione del tema del canale web di comunicazione e modulo adattivo](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configurazione dei frammenti di documento {#document-fragments-configuration}

Toccare **Configurazione frammenti di documento** nella pagina **Configurazione console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione dei frammenti di documento.

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
   <td>Formato di visualizzazione specifico per le impostazioni internazionali per campi, variabili ed elementi del modello dati del modulo disponibili durante la creazione di una comunicazione interattiva per i canali Stampa e Web.</td> 
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
   <td>Larghezza della singola unità di rientro applicata al testo nei frammenti di documento elenco.</td> 
   <td>12,7 mm</td> 
   <td>Numero</td> 
  </tr> 
  <tr> 
   <td>Larghezza minima numeri romani</td> 
   <td>Larghezza minima da applicare al campo punto elenco o numero quando si utilizzano numeri romani nei frammenti di documento elenco. </td> 
   <td>12,7 mm</td> 
   <td>Numero</td> 
  </tr> 
  <tr> 
   <td>Larghezza minima</td> 
   <td>Larghezza minima da applicare al campo punto elenco o numero quando si utilizzano elenchi numerati diversi dai numeri romani nei frammenti di documento elenco.</td> 
   <td>8,0 mm</td> 
   <td>Numero</td> 
  </tr> 
 </tbody> 
</table>

## Creare la configurazione della corrispondenza {#create-correspondence-configuration}

Tocca **Crea configurazione corrispondenza** nella pagina **Configurazione console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per l&#39;interfaccia utente agente.

| Proprietà | Descrizione | Predefiniti | Valori accettabili |
|---|---|---|---|
| Mostra contenuto risolto per la modifica | Selezionare la casella di controllo per visualizzare il contenuto risolto (valori effettivi anziché segnaposto) durante la modifica del modulo di testo nell&#39;interfaccia utente dell&#39;agente. | Non selezionato | Non applicabile |
| Applica filigrana durante l&#39;anteprima | Selezionare la casella di controllo per applicare la filigrana al canale Stampa di comunicazione interattiva in modalità Anteprima. | Non selezionato | Non applicabile |

## Configurazione del canale web per moduli adattivi e comunicazioni interattive {#adaptive-form-and-interactive-communication-web-channel-configuration}

Tocca **Configurazione canale web per moduli adattivi e comunicazioni interattive** nella pagina **Configurazione console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per il canale web per Forms adattivo e comunicazioni interattive. La tabella seguente descrive le proprietà relative alle comunicazioni interattive:

| Proprietà | Descrizione | Predefiniti | Valori accettabili |
|---|---|---|---|
| Mostra segnaposto | Seleziona la casella di controllo per abilitare la visualizzazione dei segnaposto per i campi inclusi nei moduli adattivi e nelle comunicazioni interattive. | Selezionato | Non applicabile |
| Numero massimo di voci della cache | Imposta il numero massimo di moduli adattivi e comunicazioni interattive recuperabili utilizzando la memoria cache. | 100 | Numero |
| Rendi univoco il nome del file | Seleziona la casella di controllo per assegnare nomi univoci ai file inclusi come allegati in Adaptive Forms e Interactive Communications. | Non selezionato | Non applicabile |

## Configurazione del tema del canale web per moduli adattivi e comunicazioni interattive {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Tocca **Configurazione del tema del canale web per moduli adattivi e comunicazioni interattive** nella pagina **Configurazione della console Web Adobe Experience Manager** per visualizzare le proprietà di configurazione per i temi del canale web per Forms adattivo e comunicazioni interattive.

<table> 
 <tbody> 
  <tr> 
   <td>Proprietà</td> 
   <td>Descrizione</td> 
   <td>Predefiniti</td> 
   <td>Valori accettabili</td> 
  </tr> 
  <tr> 
   <td>Nome elenco caratteri</td> 
   <td>Elenco dei font disponibili per la creazione di Adattivo Forms e comunicazioni interattive.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Impatto</p> <p>Palatino Linotype</p> </td> 
   <td>Tutti i font validi del server di Adobe</td> 
  </tr> 
 </tbody> 
</table>

