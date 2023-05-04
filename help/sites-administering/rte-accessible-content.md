---
title: Configurazione dell’editor Rich Text per la produzione di siti accessibili
seo-title: Configuring RTE for Producing Accessible Sites
description: Scopri come configurare l’editor Rich Text AEM per generare siti accessibili.
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 2%

---

# Configurazione dell’editor Rich Text per la produzione di siti accessibili {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM supporta entrambi:

* funzioni di accessibilità standard, compreso il testo alternativo per le immagini
* nonché funzioni aggiuntive accessibili durante la creazione di contenuti con componenti che utilizzano l’editor Rich Text

>[!NOTE]
>
>* [Guida rapida alle linee guida WCAG 2.0](/help/managing/qg-wcag.md)
>* [Creazione di contenuto accessibile (conformità WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)


Gli autori di contenuti possono utilizzare le funzioni dell’editor Rich Text per fornire informazioni di accesso facilitato durante l’aggiunta di contenuti a una pagina. Ciò può includere l’aggiunta di informazioni strutturali tramite intestazioni ed elementi di paragrafo.

È possibile [configurare e personalizzare queste funzioni configurando i plug-in RTE](#configuring-the-plugin-features) per il componente. Ad esempio, il `paraformat` il plug-in consente di aggiungere ulteriori elementi semantici a livello di blocco, tra cui l’estensione del numero di livelli di intestazione supportati oltre la base `H1`, `H2` e `H3` fornito per impostazione predefinita.

L’editor Rich Text è disponibile in diversi componenti sia dall’interfaccia touch che classica. Tuttavia, il componente principale per l’utilizzo dell’editor Rich Text è **Testo** componente.

La **Testo** in AEM è disponibile sia per le interfacce touch che per quelle classica. Le immagini seguenti mostrano l’editor Rich Text con una serie di plug-in abilitati, tra cui `paraformat`:

* La **Testo** nell’interfaccia touch:

   ![Componente testo (Editor Rich Text) in modalità a schermo intero nell’interfaccia touch.](assets/chlimage_1-206.png)

* La **Testo** nell’interfaccia classica:

   ![Finestra di dialogo Modifica (RTE) del componente testo nell’interfaccia classica.](assets/chlimage_1-207.png)

>[!NOTE]
>
>Esistono differenze tra le funzioni dell’editor Rich Text disponibili nell’interfaccia classica e l’interfaccia touch. Per ulteriori dettagli vedi
>
>* [Plug-in e relative funzioni](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Plug-in e relative funzioni - Interfaccia touch](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## Configurazione delle funzionalità plug-in {#configuring-the-plugin-features}

Le istruzioni complete sulla configurazione dell’editor Rich Text sono disponibili nella sezione [Configurazione dell’editor Rich Text](/help/sites-administering/rich-text-editor.md) pagina. Vengono trattati tutti i problemi, compresi i passaggi chiave:

* [Plug-in e relative funzioni](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Posizioni di configurazione](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Attivare un plug-in e configurare la proprietà feature](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Configurazione di altre funzionalità dell’editor Rich Text](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Configurando un plug-in all’interno del `rtePlugins` in CRXDE Lite (immagine seguente), puoi attivare tutte le funzioni o specifiche del plug-in.

![CRXDE Lite mostra un esempio rtePlugin.](assets/chlimage_1-208.png)

### Esempio - Specifica dei formati di paragrafo disponibili nel campo di selezione dell’editor Rich Text {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Nuovi formati di blocchi semantici possono essere messi a disposizione per la selezione:

1. A seconda dell’editor Rich Text, determina e naviga fino al [percorso di configurazione](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Attiva il campo di selezione Paragrafi](/help/sites-administering/rich-text-editor.md); da [attivazione del plug-in](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Specificare i formati che si desidera rendere disponibili nel campo di selezione Paragrafi](/help/sites-administering/rich-text-editor.md).
1. I formati di paragrafo sono quindi disponibili per l’autore del contenuto dai campi di selezione nell’editor Rich Text. Sono accessibili:

   * Utilizzando il paragrafo ([corvo](https://en.wikipedia.org/wiki/Pilcrow)) nell’interfaccia touch:

   ![Icona Paragrafo (pilcrow).](do-not-localize/chlimage_1-7.png)

   * Utilizzo della **Formato** (selettore a discesa) nell’interfaccia classica.


Con gli elementi strutturali disponibili nell’editor Rich Text tramite le opzioni del formato paragrafo, AEM fornisce una buona base per lo sviluppo di contenuti accessibili. Gli autori di contenuti non possono utilizzare l’editor Rich Text per formattare la dimensione del font o i colori o altri attributi correlati, impedendo la creazione di formattazione in linea. Devono invece selezionare gli elementi strutturali appropriati, ad esempio i titoli, e utilizzare gli stili globali selezionati dall’opzione Stili. In questo modo si garantisce un markup pulito, opzioni più ampie per gli utenti che navigano con i propri fogli di stile e contenuti strutturati correttamente.

## Utilizzo della funzione di modifica sorgente {#use-of-the-source-edit-feature}

In alcuni casi, gli autori di contenuti dovranno esaminare e regolare il codice sorgente HTML creato utilizzando l’editor Rich Text. Ad esempio, per garantire la conformità alle linee guida WCAG 2.0, un contenuto creato all’interno dell’editor Rich Text può richiedere tag aggiuntivi. Questo può essere fatto con [modifica sorgente](/help/sites-administering/rich-text-editor.md#aboutplugins) opzione dell’editor Rich Text. Puoi specificare la [ `sourceedit` sulla `misctools` plugin](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Utilizza la `sourceedit` con attenzione. La digitazione di errori e/o funzioni non supportate può causare altri problemi.

## Aggiunta di supporto per elementi e attributi di HTML aggiuntivi {#adding-support-for-additional-html-elements-and-attributes}

Per estendere ulteriormente le funzioni di accessibilità di AEM, è possibile estendere i componenti esistenti in base all’editor Rich Text (come **Testo** e **Tabella** componenti) con elementi e attributi aggiuntivi.

La procedura seguente illustra come estendere il **Tabella** componente con un **Didascalia** elemento che fornisce informazioni su una tabella di dati agli utenti di tecnologie per l’accessibilità:

### Esempio: aggiunta della didascalia alla finestra di dialogo Proprietà tabella {#example-adding-the-caption-to-the-table-properties-dialog}

Nel costruttore del `TablePropertiesDialog`, aggiungi un campo di immissione testo aggiuntivo utilizzato per modificare la didascalia. Tieni presente che `itemId` deve essere impostato su `caption` (ovvero il nome dell’attributo DOM) per gestire automaticamente il contenuto.

In **Tabella** devi impostare o rimuovere esplicitamente l’attributo a/dall’elemento DOM. Il valore viene passato dalla finestra di dialogo nel `config` oggetto. Gli attributi DOM devono essere impostati/rimossi utilizzando il corrispondente `CQ.form.rte.Common` metodi ( `com` è una scorciatoia per `CQ.form.rte.Common`) per evitare problematiche comuni con le implementazioni del browser.

>[!NOTE]
>
>Questa procedura è adatta solo all’interfaccia classica.

### Istruzioni dettagliate {#step-by-step-instructions}

1. Avvia CRXDE Lite. Ad esempio: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Copia:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   a:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Potrebbe essere necessario creare cartelle intermedie se non esistono già.

1. Copia:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   a:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Apri il file seguente per la modifica (apri con doppio clic):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. In `constructor` prima della lettura della riga:

   ```
   var dialogRef = this;
   ```

   Aggiungi il codice seguente:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Apri il file seguente:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Aggiungi il seguente codice alla fine del `transferConfigToTable` metodo:

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Salva le modifiche utilizzando **Salva tutto**

>[!NOTE]
>
>Un campo di testo normale non è l’unico tipo di input consentito per il valore dell’elemento didascalia. Qualsiasi widget ExtJS che fornisce il valore della didascalia attraverso il relativo `getValue()` potrebbe essere utilizzato.
>
>Per aggiungere funzionalità di modifica per altri elementi e attributi, assicurati che:
>
>* La `itemId` per ogni campo corrispondente viene impostata sul nome dell&#39;attributo DOM appropriato (`TablePropertiesDialog`).
>* L’attributo viene impostato e/o rimosso esplicitamente sull’elemento DOM (`Table`).

