---
title: Personalizzazione dei modelli per i componenti del portale dei moduli
seo-title: Personalizzazione dei modelli per i componenti del portale dei moduli
description: Visualizzazione dei metadati personalizzati nell’elenco dei moduli
seo-description: Visualizzazione dei metadati personalizzati nell’elenco dei moduli
uuid: 746aeece-a6d1-417b-8065-05cd54bd66d6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 842d3a5a-8e09-4a21-b9a2-a8f4f5b699bd
feature: Forms Portal
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---


# Personalizzazione dei modelli per i componenti del portale dei moduli {#customizing-templates-for-forms-portal-components}

## Prerequisiti {#prerequisites}

[Gestione dei metadati dei moduli](/help/forms/using/manage-form-metadata.md)

Conoscenza del funzionamento di HTML e CSS

## Panoramica {#overview}

L’interfaccia utente di AEM Forms consente di aggiungere metadati a qualsiasi modulo. I metadati personalizzati possono migliorare l’esperienza utente durante l’elenco e la ricerca di moduli dell’organizzazione.

Forms Portal consente di utilizzare metadati personalizzati negli elenchi dei moduli. Durante la creazione di modelli personalizzati per le risorse, puoi modificarne il layout e utilizzare metadati personalizzati con il set di stili CSS.

Esegui i seguenti passaggi per creare un modello personalizzato per vari componenti del portale Forms.

## Creazione di un modello personalizzato {#creating-a-nbsp-custom-template}

1. Crea un nodo sling:Folder sotto */apps *

   Aggiungi una proprietà &quot;fpContentType&quot;. Specifica i valori appropriati per la proprietà a seconda del componente per il quale stai definendo il modello personalizzato.

   * Componente Ricerca e filtro: &quot;/libs/fd/fp/formTemplate&quot;
   * Componente Bozze e invii:

      * Sezione Bozze: /libs/fd/fp/draftTemplate
      * Sezione invii: /libs/fd/fp/submitTemplate
   * Componente collegamento: /libs/fd/fp/linkTemplate

   Aggiungere un titolo da visualizzare durante la selezione dei modelli di layout.

   *Nota: Il titolo può essere diverso dal nome del nodo di sling:Folder creato. *
   *L’immagine seguente illustra la configurazione del componente Ricerca e filtro .* ![Creazione di una sling:Folder](assets/1-3.png)

1. Crea un file template.html in questa cartella da usare come modello personalizzato.
1. Scrivi il modello personalizzato e utilizza i metadati personalizzati come descritto di seguito.

## Esempio di lavoro {#working-example}

Di seguito è riportato un esempio di implementazione di un modello personalizzato in cui Forms Portal acquisisce un layout personalizzato della scheda Gov per il componente Ricerca e filtro.

```mxml
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
 <div class="__FP_boxes-thumbnail">
     <img src ="${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png"/>
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">${localize-Apply}</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">${localize-Download}</a>
            </div>
        </div>
    </div>
</div>
```

## Specifiche tecniche per i modelli personalizzati {#technical-specifications-for-custom-templates}

Un modello personalizzato per qualsiasi componente di Forms Portal include voci ripetibili e non ripetibili. Le voci ripetibili sono entità di base per l’inserimento nell’elenco. Esempi di voci ripetibili sono i componenti Search &amp; Lister, Drafts &amp; Submission e Link.

Forms Portal fornisce una sintassi per i segnaposto per la visualizzazione dei metadati personalizzati/OOTB. I segnaposto vengono compilati dopo la visualizzazione dei risultati di moduli, bozze o invii.

Per includere una voce ripetibile, configura il valore dell&#39;attributo **ripetibile ai dati** in **true**.

*Nell&#39;esempio illustrato, due elementi Div sono presenti nella parte superiore del modello personalizzato. Il primo, con la classe CSS &quot;__FP_boxes-container&quot;, funziona come un elemento contenitore per i moduli elencati. Il secondo, con la classe CSS &quot;__FP_boxes&quot;, è un modello per le entità di base, in questo caso un modulo. L’attributo **ripetibile per i dati** presente nell’elemento Div ha il valore **true**.

Ogni segnaposto ha un set di metadati OOTB esclusivo. Per visualizzare i metadati personalizzati in una posizione specifica del modulo, aggiungere la proprietà **$metadata_prop** nella posizione desiderata.

*Nell&#39;esempio, la proprietà metadati viene utilizzata in più istanze. Ad esempio, viene utilizzato in **description**,**name**,**formUrl**,**htmlStyle**,**pdfUrl**,**pdfStyle**e **percorso**nel modo prescritto.*

## Metadati predefiniti {#out-of-the-box-metadata}

Diversi componenti del portale Forms forniscono set esclusivi di metadati OOTB utilizzabili per l’inserimento nell’elenco.

### Componente Ricerca e filtro {#search-amp-lister-component}

* **Titolo:** titolo del modulo
* **nome**: Nome del modulo (in genere corrisponde al titolo)
* **descrizione**: Descrizione del modulo
* **formUrl**: URL per eseguire il rendering del modulo come HTML
* **pdfUrl**: URL per eseguire il rendering del modulo come PDF
* **assetType**: Tipo di risorsa. I valori validi includono **Modulo**, **Modulo PDF**, **Modulo di stampa** e **Modulo adattivo**
* **htmlStyle**  e  **pdfStyle**: Stile di visualizzazione per le icone HTML e PDF utilizzate rispettivamente per il rendering. I valori validi sono &quot;**__FP_display_none**&quot; o **blank**

   *Nota: Ricordare di utilizzare la classe __FP_display_none nel foglio di stile personalizzato*

* **downloadUrl**: URL per scaricare una risorsa.

Supporto per la localizzazione, l&#39;ordinamento e l&#39;utilizzo delle proprietà di configurazione nell&#39;interfaccia utente (solo ricerca e filtro):

1. **Supporto** per la localizzazione: Per localizzare un testo statico, utilizza l’attributo  **${localize-***YOUR_TEXT***}**  e rende disponibile il valore localizzato, se non esiste già.

   *Nell&#39;esempio illustrato, gli attributi ${localize-Apply} e ${localize-Download} vengono utilizzati per localizzare il testo Applica e Scarica.*

1. **Supporto per l’ordinamento**: Fai clic sull’elemento HTML per ordinare i risultati della ricerca. Per implementare l’ordinamento in un layout sottoposto, aggiungi l’attributo &quot;data-sortKey&quot; nella particolare intestazione della tabella. Inoltre, aggiungi il relativo valore come metadati per i quali desideri eseguire l’ordinamento.

   Ad esempio, per l’intestazione &quot;Titolo&quot; nella vista griglia, il valore dell’intestazione &quot;data-sortKey&quot; è &quot;title&quot;. Fai clic sull’intestazione per ordinare i valori in una particolare colonna.

1. **Utilizzo delle proprietà** di configurazione: Il componente Ricerca e filtro dispone di diverse configurazioni che è possibile utilizzare nell’interfaccia utente. Ad esempio, per visualizzare il testo HTML della descrizione comandi salvato tramite la finestra di dialogo di modifica, utilizza l&#39;attributo **${config-htmlLinkText} .** Analogamente, per il testo della descrizione comandi PDF, utilizzare l’attributo **${config-pdfLinkText}** .

### Componente collegamento {#link-component}

* **Titolo:** titolo del modulo
* **formUrl**: URL per eseguire il rendering del modulo come HTML
* **target**: Attributo di destinazione del collegamento. I valori validi sono &quot;_blank&quot; e &quot;_self&quot;.
* **linkText**: Didascalia collegamento

### Componente Bozze e invii {#drafts-amp-submissions-component}

* **Percorso**: Percorso del nodo di metadati bozza/invio. Utilizzalo con l&#39;estensione HTML come URL per aprire una bozza o un invio.
* **contextPath**: Percorso contestuale dell&#39;istanza AEM
* **firstLetter**: Prima lettera (maiuscola) del titolo del modulo adattivo, salvata come bozza o inviata.
* **formName**: Titolo del modulo adattivo, salvato come Bozza o inviato.
* **DraftID**: ID per la bozza elencata (da utilizzare solo nel modello per la sezione Bozza).
* **submitID**: ID per l’invio elencato (da utilizzare solo nel modello per la sezione Invio).
* **stato**: Stato del modulo inviato. (Utilizzare solo nel modello per la sezione Invio).
* **descrizione**: Descrizione del modulo adattivo associato alla bozza o all’invio.
* **diffTime**: Differenza tra l&#39;ora corrente e l&#39;ultima azione di salvataggio per la bozza. In alternativa, la differenza tra l’ora corrente e l’ultima azione di invio per l’invio.
* **iconClass**: Classe CSS utilizzata per visualizzare la prima lettera della bozza/invio. Forms Portal include le seguenti classi, che forniscono sfondi colorati diversi.
* **proprietario**: Utente che ha creato la bozza/invio.
* **Oggi**: Data di creazione della bozza o della presentazione in formato GG:MM:AAAA.
* **TimeNow**: Ora di creazione della bozza o della presentazione in formato HH:MM:SS 24 ore

*Nota:*

1. Per l’opzione Elimina nella sezione Bozze del componente Bozze e invii , denomina la classe CSS &quot;__FP_deleteDraft&quot;. Inoltre, includi l&#39;attributo &quot;DraftID&quot; con il valore **${draftID}**, che è l&#39;ID bozza della bozza corrispondente.

1. Durante la creazione di collegamenti per aprire bozze e invii, è possibile specificare **$path.html** come valore dell&#39;attributo **href** per il tag di ancoraggio.

![Nodo Bozze e invio](assets/raw-image-with-index.png)

**A**. Elemento contenitore

**Metadati B.**  &quot;path&quot; con una gerarchia fissa per ottenere la miniatura memorizzata per ciascun modulo.

**C.** Attributo ripetibile ai dati utilizzato per la sezione del modello per ciascun modulo

**D.** Per localizzare la stringa &quot;Applica&quot;

**E.** Utilizzo della proprietà di configurazione pdfLinkText

**F.** Utilizzo dei metadati &quot;pdfUrl&quot;

## Suggerimenti, trucchi e problemi noti {#tips-tricks-and-known-issues}

1. Non utilizzare virgolette singole (&#39;) in alcun modello personalizzato.
1. Per i metadati personalizzati, memorizza questa proprietà solo sul nodo **jcr:content/metadata** . Se lo archivi in qualsiasi altro luogo, Forms Portal non può visualizzare i metadati.
1. Assicurati che il nome di eventuali metadati personalizzati o metadati esistenti non includa due punti (:). In questo caso, non è possibile visualizzarlo nell’interfaccia utente.
1. **data-** repeat non ha alcun significato per un  **** componente Linkcomponent. Adobe consiglia di evitare di utilizzare questa proprietà nel modello per un componente Collegamento.

## Articoli correlati

* [Abilitare i componenti del portale moduli](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina del portale dei moduli](/help/forms/using/creating-form-portal-page.md)
* [Elencare moduli in una pagina web utilizzando le API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Usa componente Bozze e invii](/help/forms/using/draft-submission-component.md)
* [Personalizzare l’archiviazione delle bozze e dei moduli inviati](/help/forms/using/draft-submission-component.md)
* [Esempio per l&#39;integrazione del componente bozze e invii con il database](/help/forms/using/integrate-draft-submission-database.md)
* [Personalizzazione dei modelli per i componenti del portale dei moduli](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Introduzione alla pubblicazione di moduli su un portale](/help/forms/using/introduction-publishing-forms.md)

