---
title: Nozioni di base sull’editor Rich Text
seo-title: Rich Text Editor Essentials
description: Panoramica delle funzioni dell’editor Rich Text
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: d236a8d3-20ad-4568-a7c2-87d146aa0532
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 6%

---

# Nozioni di base sull’editor Rich Text {#rich-text-editor-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Un editor Rich Text consente di immettere testo con tag.

Per i componenti Community, mentre è simile al [editor Rich Text nell’ambiente di authoring](../../help/sites-authoring/rich-text-editor.md), influisce sul testo immesso nell’ambiente di pubblicazione.

![chlimage_1-410](assets/chlimage_1-410.png)

## Abilitazione dell’editor Rich Text {#enabling-rich-text-editor}

I componenti community che consentono l’editor Rich Text possono essere abilitati per i contenuti generati dall’utente (UGC). A seconda che il componente sia stato aggiunto a una pagina o incluso in un [Funzione](functions.md), l’editor Rich Text può essere abilitato o meno per impostazione predefinita.

Se non è abilitato, è sufficiente immettere [modalità modifica autore](sites-console.md#authoring-site-content), seleziona il componente da modificare e seleziona il `Rich Text Editor` casella di controllo.

L’editor Rich Text è disponibile per i seguenti componenti di Communities:

* [Blog](blog-feature.md)
* [Calendario](calendar.md)
* [Commenti](comments.md)
* [Filelibrio](file-library.md)
* [Forum](forum.md)
* [Messaggi](configure-messaging.md)
* [D/R](working-with-qna.md)
* [Recensioni](reviews.md)

## Personalizzazione {#customization}

È possibile personalizzare l’editor Rich Text in quanto l’implementazione si basa su [CKEditor](https://www.ckeditor.com/).

La configurazione corrente per i componenti di Communities si trova nel `cq.social.  scf   clientlib`, situato nell’archivio all’indirizzo

`/libs/clientlibs/social/commons/scf/ckrte.js`

La modifica di cq.social.scf clientlib non è consigliata in quanto gli aggiornamenti futuri potrebbero sostituire qualsiasi modifica.

### Esempio di personalizzazione: Collegamenti in linea {#example-customization-inline-links}

Per motivi di sicurezza, le opzioni dei collegamenti ipertestuali non sono incluse nel set di icone RTF presentate ai membri per impostazione predefinita. La capacità di errore è ampia quando gli hrefs sono ammessi in UGC.

Per aggiungere le opzioni per i collegamenti ipertestuali alla barra degli strumenti:

* Aggiungi una barra degli strumenti denominata &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Seleziona **[!UICONTROL Salva tutto]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items: [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
