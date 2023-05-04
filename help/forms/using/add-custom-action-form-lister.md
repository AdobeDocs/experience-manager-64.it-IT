---
title: Aggiunta di un’azione personalizzata agli elementi dell’elenco moduli
seo-title: Adding custom action on form lister items
description: Gli sviluppatori di moduli possono aggiungere ulteriori azioni all’elenco dei moduli nella pagina del portale dei moduli. Per impostazione predefinita, l’elenco dei moduli consente di accedere al modulo, compilarlo e inviarlo.
seo-description: Form developers can add more actions to the listing of forms on the forms portal page. By default, the form listing allows you to access the form, fill it, and submit it.
uuid: 02c64f7d-f726-4a5b-a303-ec96934e9c01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 0e0a9b6b-fd2f-4cec-b233-500c940ee4d5
exl-id: d8f60be3-474a-4dd1-aaa5-7b6a97e1a9bd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 2%

---

# Aggiunta di un’azione personalizzata agli elementi dell’elenco moduli {#adding-custom-action-on-form-lister-items}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In AEM Forms è possibile creare una pagina del portale in cui sono elencati i moduli disponibili. Per impostazione predefinita, è possibile cercare ed elencare i moduli in una pagina del portale. È possibile aprire i moduli per la compilazione e inviare le informazioni. Solo le azioni di rendering vengono fornite come predefinite per i moduli elencati in una pagina del portale. Per ulteriori informazioni sulle azioni disponibili in una pagina del portale, consulta [Creazione di una pagina del portale moduli](/help/forms/using/creating-form-portal-page.md).

È possibile aggiungere altre opzioni alla pagina del portale. Queste opzioni o azioni possono essere personalizzate personalizzando il modello del portale dei moduli.

Questo articolo illustra come creare un pulsante per inviare il collegamento di un modulo direttamente da una pagina del portale dei moduli. Questa personalizzazione richiede l’aggiornamento del modello per il componente Ricerca e filtro .

Il codice necessario per aggiungere l’azione al modello è disponibile di seguito. La `onclick` nello snippet di codice è presente uno script per inviare un collegamento di un modulo tramite e-mail.

```mxml
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

Puoi aggiungere azioni simili nel modello personalizzato. Per definire una funzione JavaScript, aggiungi la funzione in uno script a livello di pagina e collegala all’elemento HTML richiesto. Nell’esempio precedente, la `onclick` espressione è la funzione collegata.

Dopo aver apportato le modifiche al modello, la pagina del portale di esempio contiene un pulsante per inviare il collegamento del modulo tramite e-mail, come illustrato di seguito.

![email](assets/email.png)
