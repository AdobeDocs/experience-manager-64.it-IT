---
title: Frammenti di contenuto - Considerazioni sull’eliminazione
seo-title: Content Fragments - Delete Considerations
description: Frammenti di contenuto - Considerazioni sull’eliminazione
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 75%

---

# Frammenti di contenuto - Considerazioni sull’eliminazione {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

## Autorizzazioni - Elimina o Non Eliminare {#permissions-delete-or-not-delete}

La possibilità di eliminare i contenuti è straordinaria, ma potenzialmente delicata, e in molti settori è necessario limitare e controllare come questi privilegi vengono distribuiti.

Per quanto riguarda le autorizzazioni di eliminazione, i frammenti di contenuto devono essere considerati a due livelli:

1. **Il frammento di contenuto come singola entità.**

   * **Caso d’uso**: utente che deve modificare o aggiornare un frammento di contenuto **ed eliminare un intero frammento**.
   * **Autorizzazioni**[](/help/sites-administering/security.md#actions)[: l’autorizzazione Elimina può essere assegnata tramite la gestione degli utenti e/o dei gruppi](/help/sites-administering/security.md#managing-permissions).

1. **Le numerose sottoentità che compongono un frammento di contenuto, come varianti e sotto-nodi.**

   Il funzionamento di base dell’editor di frammenti di contenuto prevede che tali elementi secondari transitori possano essere eliminati. Ad esempio, quando si manipolano le varianti, ma anche durante la modifica dei metadati o la gestione dei contenuti associati.

   * **Caso d’uso**: utente che deve modificare o aggiornare un frammento di contenuto **senza la possibilità di eliminare un intero frammento**.
   * **Autorizzazioni**: vedi [Autorizzazioni necessarie solo per la funzionalità dell’editor](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Quando un utente non dispone di [Elimina](/help/sites-administering/security.md#actions) autorizzazioni, l’editor Frammento di contenuto funziona in *sola lettura* modalità.

>[!NOTE]
>
>Vedi anche [Controllare le operazioni di gestione degli utenti in AEM](/help/sites-administering/audit-user-management-operations.md).

## Autorizzazioni necessarie solo per la funzionalità dell’editor {#permissions-required-for-editor-functionality-only}

Dovrai assegnare autorizzazioni specifiche agli utenti che necessitano di modificare/aggiornare un frammento di contenuto, **ma a cui non vuoi consentire di eliminare un intero frammento**, poiché il funzionamento di base dell’Editor frammento di contenuto richiede l’eliminazione di elementi secondari transitori.

Ad esempio, quando si manipolano le varianti, ma anche durante la modifica dei metadati o la gestione dei contenuti associati.

>[!NOTE]
>
>Le autorizzazioni di eliminazione, necessarie per modificare/aggiornare un frammento di contenuto, sono incluse nell’autorizzazione Elimina [assegnato tramite Gestione utenti e/o gruppi](/help/sites-administering/security.md#managing-permissions).

Le autorizzazioni necessarie per modificare o aggiornare un frammento devono essere applicate al nodo contenente il frammento di contenuto o a un nodo principale appropriato (a qualsiasi livello in `/content/dam`). Le autorizzazioni assegnate a un nodo principale vengono applicate a tutti i nodi al suo interno.

Ad esempio, una cartella contenente tutti i frammenti di contenuto, come:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>È anche possibile impostare le autorizzazioni su `/content/dam`, in quanto tutti i frammenti di contenuto sono memorizzati qui.
>
>Tuttavia, questa azione applica le stesse autorizzazioni di eliminazione anche a *tutti* gli altri tipi di risorse.

I prerequisiti di autorizzazione per consentire a un utente e/o gruppo specifico di modificare/aggiornare un frammento di contenuto sono:

>[!NOTE]
>
>Questo elenco mostra tutti i privilegi richiesti, non solo quelli di eliminazione.

* Per i nodi o le cartelle dei frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Per il `jcr:content` nodo di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`

* Per tutti i nodi sottostanti `jcr:content` di tutti i frammenti di contenuto:

   * `jcr:addChildNodes`, `jcr:modifyProperties` e `jcr:removeChildNodes`, `jcr:removeNode`

Tali `remove` i privilegi devono essere [amministrato tramite elenchi di controllo di accesso, in CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

La `add` e `modify` è inoltre possibile amministrare i privilegi in CRXDE Lite o utilizzare la console Gestione utente.

Ad esempio, la definizione di `remove` privilegi per un gruppo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
