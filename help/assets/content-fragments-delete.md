---
title: Frammenti di contenuto - Considerazioni sull’eliminazione
seo-title: Frammenti di contenuto - Considerazioni sull’eliminazione
description: Frammenti di contenuto - Considerazioni sull’eliminazione
seo-description: Frammenti di contenuto - Considerazioni sull’eliminazione
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
translation-type: tm+mt
source-git-commit: 3fa80e73fb6e9400fbeba29d80aa57e080b6f333
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 12%

---


# Frammenti di contenuto - Considerazioni sull’eliminazione {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Alcune funzionalità per i frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

## Autorizzazioni - Elimina o Non Elimina {#permissions-delete-or-not-delete}

La possibilità di eliminare contenuti è potente, ma potenzialmente sensibile, e molti settori devono limitare e controllare la modalità di distribuzione di tali privilegi.

Per quanto riguarda l’eliminazione delle autorizzazioni, i frammenti di contenuto devono essere considerati a due livelli:

1. **Il frammento di contenuto come entità singola.**

   * **Caso** di utilizzo: Utente che deve modificare/aggiornare un frammento di contenuto **ed eliminare un intero frammento**.
   * **Autorizzazioni**: L&#39;autorizzazione [Elimina](/help/sites-administering/security.md#actions) può essere [assegnata tramite Gestione](/help/sites-administering/security.md#managing-permissions)utente e/o gruppo.

1. **Più sottoentità che costituiscono un frammento di contenuto; ad esempio, varianti, nodi secondari.**

   Il funzionamento di base dell’editor dei frammenti di contenuto richiede che tali sottoelementi transitori possano essere eliminati. Ad esempio, durante la manipolazione delle variazioni; anche durante la modifica dei metadati o la gestione del contenuto associato.

   * **Caso** di utilizzo: Un utente che deve modificare/aggiornare un frammento di contenuto, **senza la possibilità di eliminare un intero frammento**.
   * **Autorizzazioni**: Consultate [Autorizzazioni necessarie solo](content-fragments-delete.md#permissions-required-for-editor-functionality-only)per la funzionalità dell’editor.

>[!NOTE]
>
>When a user does not have any [Delete](/help/sites-administering/security.md#actions) permissions, the Content Fragment editor operates in *read-only* mode.

>[!NOTE]
>
>Vedere anche [Come controllare le operazioni di gestione degli utenti in AEM](/help/sites-administering/audit-user-management-operations.md).

## Autorizzazioni necessarie solo per la funzionalità Editor {#permissions-required-for-editor-functionality-only}

Dovrai assegnare autorizzazioni specifiche agli utenti che necessitano di modificare/aggiornare un frammento di contenuto, **ma a cui non vuoi consentire di eliminare un intero frammento**, poiché il funzionamento di base dell’Editor frammento di contenuto richiede l’eliminazione di elementi secondari transitori.

Ad esempio, durante la manipolazione delle variazioni; anche durante la modifica dei metadati o la gestione del contenuto associato.

>[!NOTE]
>
>Le autorizzazioni di eliminazione, necessarie per modificare/aggiornare un frammento di contenuto, sono incluse nell&#39;autorizzazione di eliminazione [assegnata tramite Gestione](/help/sites-administering/security.md#managing-permissions)utente e/o gruppo.

Le autorizzazioni necessarie per modificare/aggiornare un frammento devono essere applicate al nodo contenente il frammento di contenuto o a un nodo principale appropriato (a qualsiasi livello in `/content/dam`). Quando vengono assegnate a tale nodo padre, le autorizzazioni vengono applicate a tutti i nodi all&#39;interno di tale ramo.

Ad esempio, una cartella contenente tutti i frammenti di contenuto, come:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>È `/content/dam` inoltre possibile impostare le autorizzazioni in quanto tutti i frammenti di contenuto sono memorizzati in questa cartella.
>
>Tuttavia, questa azione applica le stesse autorizzazioni di eliminazione anche a *tutti* gli altri tipi di risorse.

I prerequisiti per consentire a un utente e/o gruppo specifico di modificare/aggiornare un frammento di contenuto sono:

>[!NOTE]
>
>Questo elenco mostra tutti i privilegi richiesti, non solo quelli di eliminazione.

* Per i nodi o le cartelle dei frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Per il `jcr:content` nodo di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`

* Per tutti i nodi sotto `jcr:content` di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`, `jcr:removeNode`

Tali `remove` privilegi devono essere [amministrati tramite elenchi di controllo di accesso, all&#39;interno di CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

I privilegi `add` e `modify` privilegi possono essere amministrati anche in CRXDE Lite o mediante la console Gestione utente.

Ad esempio, la definizione dei `remove` privilegi per un gruppo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)

