---
title: Modificare l’aspetto
seo-title: Alter the Appearance
description: Modificare lo script
seo-description: Modify the script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
exl-id: 01a20578-56c3-41b3-8a0e-281104af2481
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 4%

---

# Modificare l’aspetto {#alter-the-appearance}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Modificare lo script {#modify-the-script}

Lo script comment.hbs è responsabile della creazione del HTML generale per ogni commento.

Per non visualizzare l&#39;avatar accanto a ciascun commento pubblicato:

1. Copia `comment.hbs`da `libs`a `apps`
   1. Seleziona `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Seleziona **[!UICONTROL Copia]**
   1. Seleziona `/apps/social/commons/components/hbs/comments/comment`
   1. Seleziona **[!UICONTROL Incolla]**
1. Apri la sovrapposizione `comment.hbs`
   * Fare doppio clic sul nodo  `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. Trova le seguenti righe ed eliminale o commenta:

   ```xml
   <aside class="scf-comment-author">
           <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
   ```

Elimina le linee o circondale con &#39;&lt;!>—&quot; e &quot;—>&quot; per commentarli. Inoltre, i caratteri &#39;xxx&#39; vengono aggiunti come indicatore visivo di dove sarebbe stato l&#39;avatar.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Replicare la sovrapposizione {#replicate-the-overlay}

Invia il componente commenti sovrapposti all’istanza di pubblicazione utilizzando lo strumento di replica.

>[!NOTE]
>
>Una forma di replica più solida sarebbe quella di creare un pacchetto in Gestione pacchetti e [attivare](../../help/sites-administering/package-manager.md#replicating-packages) . Un pacchetto può essere esportato e archiviato.

Dalla navigazione globale, seleziona **[!UICONTROL Strumenti > Implementazione > Replica]** e poi **[!UICONTROL Attiva albero]**.

Per Percorso iniziale immetti `/apps/social/commons` e seleziona **[!UICONTROL Attiva]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Visualizza risultati {#view-results}

Se accedi all’istanza di pubblicazione come amministratore, ad esempio http://localhost:4503/crx/de come amministratore/amministratore, puoi verificare che i componenti sovrapposti siano presenti.

Se disconnetti e riaccedi come `aaron.mcdonald@mailinator.com/password` e aggiorna la pagina, noterai che il commento pubblicato non viene più visualizzato con un avatar, ma viene visualizzato un semplice &#39;xxx&#39;.

![chlimage_1-43](assets/chlimage_1-43.png)
