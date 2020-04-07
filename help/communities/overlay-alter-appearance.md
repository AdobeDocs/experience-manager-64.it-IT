---
title: Modifica dell'aspetto
seo-title: Modifica dell'aspetto
description: Modificare lo script
seo-description: Modificare lo script
uuid: 6930381b-74c1-4e63-9621-621dbedbc25e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: da3891d3-fa07-4c88-b4ac-077926b3a674
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# Modifica dell&#39;aspetto {#alter-the-appearance}

## Modificare lo script {#modify-the-script}

Lo script comment.hbs è responsabile della creazione dell&#39;HTML complessivo per ciascun commento.

Per non visualizzare l&#39;avatar accanto a ciascun commento pubblicato:

1. Copia `comment.hbs`da `libs`a `apps`
   1. Seleziona `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Seleziona **[!UICONTROL copia]**
   1. Seleziona `/apps/social/commons/components/hbs/comments/comment`
   1. Seleziona **[!UICONTROL Incolla]**
1. Aprire la sovrapposizione `comment.hbs`
   * Fare doppio clic sul nodo `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`
1. Trovate le righe seguenti ed eliminatele o aggiungetele un commento:

```xml
<aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Eliminare le righe o circondarle con &#39;&lt;!—&#39; e &#39;—>&#39; per commentare. Inoltre, i caratteri &#39;xxx&#39; vengono aggiunti come indicatore visivo del punto in cui l&#39;avatar sarebbe stato.

```xml
<!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

## Replica della sovrapposizione {#replicate-the-overlay}

Inviate il componente dei commenti sovrapposti all’istanza di pubblicazione utilizzando lo strumento di replica.

>[!NOTE]
>
>Una replica più affidabile consiste nel creare un pacchetto in Gestione pacchetti e [attivarlo](../../help/sites-administering/package-manager.md#replicating-packages) . Un pacchetto può essere esportato e archiviato.

Dalla navigazione globale, selezionare **[!UICONTROL Strumenti > Distribuzione > Replica]** , quindi **[!UICONTROL Attiva albero]**.

Per Percorso iniziale immettere `/apps/social/commons` e selezionare **[!UICONTROL Attiva]**.

![chlimage_1-42](assets/chlimage_1-42.png)

## Visualizza risultati {#view-results}

Se accedete all’istanza di pubblicazione come amministratore, ad esempio http://localhost:4503/crx/de come amministratore/amministratore, potete verificare che i componenti sovrapposti siano presenti.

Se effettuate il logout e accedete nuovamente come `aaron.mcdonald@mailinator.com/password` e aggiornate la pagina, il commento pubblicato non viene più visualizzato con un avatar, ma viene visualizzato un semplice &#39;xxx&#39;.

![chlimage_1-43](assets/chlimage_1-43.png)

