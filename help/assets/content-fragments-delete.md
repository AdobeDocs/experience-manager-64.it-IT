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
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Frammenti di contenuto
role: User
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 12%

---

# Frammenti di contenuto - Considerazioni sull’eliminazione {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

## Autorizzazioni - Elimina o Non Elimina {#permissions-delete-or-not-delete}

La possibilità di eliminare i contenuti è potente, ma potenzialmente sensibile, e molti settori devono limitare e controllare come questi privilegi vengono distribuiti.

Per quanto riguarda le autorizzazioni di eliminazione, i frammenti di contenuto devono essere considerati a due livelli:

1. **Il frammento di contenuto come singola entità.**

   * **Caso** di utilizzo: Utente che deve modificare/aggiornare un frammento di contenuto  **ed eliminare un intero frammento**.
   * **Autorizzazioni**: L’autorizzazione  [](/help/sites-administering/security.md#actions) Elimina può essere  [assegnata tramite Gestione utenti e/o gruppi](/help/sites-administering/security.md#managing-permissions).

1. **Le più sottoentità che compongono un frammento di contenuto; ad esempio, varianti, sotto-nodi.**

   Il funzionamento di base dell’editor dei frammenti di contenuto richiede che tali elementi secondari transitori possano essere eliminati. Ad esempio, quando si manipolano le variazioni; anche durante la modifica dei metadati o la gestione dei contenuti associati.

   * **Caso** di utilizzo: Utente che deve modificare/aggiornare un frammento di contenuto  **senza poter eliminare un intero frammento**.
   * **Autorizzazioni**: Consulta  [Autorizzazioni necessarie solo per la funzionalità dell’editor](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Se un utente non dispone di autorizzazioni [Elimina](/help/sites-administering/security.md#actions), l’editor dei frammenti di contenuto funziona in modalità *sola lettura*.

>[!NOTE]
>
>Vedere anche [Come verificare le operazioni di gestione degli utenti in AEM](/help/sites-administering/audit-user-management-operations.md).

## Autorizzazioni necessarie solo per la funzionalità dell’editor {#permissions-required-for-editor-functionality-only}

Dovrai assegnare autorizzazioni specifiche agli utenti che necessitano di modificare/aggiornare un frammento di contenuto, **ma a cui non vuoi consentire di eliminare un intero frammento**, poiché il funzionamento di base dell’Editor frammento di contenuto richiede l’eliminazione di elementi secondari transitori.

Ad esempio, quando si manipolano le variazioni; anche durante la modifica dei metadati o la gestione dei contenuti associati.

>[!NOTE]
>
>Le autorizzazioni di eliminazione, necessarie per modificare/aggiornare un frammento di contenuto, sono incluse nell’autorizzazione Elimina [assegnata tramite Gestione utente e/o gruppo](/help/sites-administering/security.md#managing-permissions).

Le autorizzazioni necessarie per modificare/aggiornare un frammento devono essere applicate al nodo contenente il frammento di contenuto o a un nodo principale appropriato (a qualsiasi livello in `/content/dam`). Quando vengono assegnate a tale nodo padre, le autorizzazioni vengono applicate a tutti i nodi all&#39;interno di tale ramo.

Ad esempio, una cartella contenente tutti i frammenti di contenuto, ad esempio:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>È inoltre possibile impostare le autorizzazioni su `/content/dam`, in quanto tutti i frammenti di contenuto sono memorizzati qui.
>
>Tuttavia, questa azione applica le stesse autorizzazioni di eliminazione anche ad *tutti* altri tipi di risorse.

I prerequisiti per le autorizzazioni per consentire a un utente e/o gruppo specifico di modificare/aggiornare un frammento di contenuto sono:

>[!NOTE]
>
>Questo elenco mostra tutti i privilegi richiesti, non solo quelli di eliminazione.

* Per i nodi o le cartelle dei frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Per il nodo `jcr:content` di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` e  `jcr:removeChildNodes`

* Per tutti i nodi sotto `jcr:content` di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` e  `jcr:removeChildNodes`,  `jcr:removeNode`

Questi privilegi `remove` devono essere [amministrati tramite gli elenchi di controllo accessi, all&#39;interno di CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

I privilegi `add` e `modify` possono essere amministrati anche in CRXDE Lite o utilizzando la console Gestione utente.

Ad esempio, la definizione dei privilegi `remove` per un gruppo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
