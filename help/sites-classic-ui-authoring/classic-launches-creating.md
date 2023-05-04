---
title: Creazione dei lanci
seo-title: Creating Launches
description: Crea un lancio per abilitare l’aggiornamento di una nuova versione di pagine web esistenti da attivare in futuro. Per creare un lancio, è necessario specificare un titolo e la pagina di origine.
seo-description: Create a launch to enable the updating of a new version of existing web pages for future activation. When you create a Launch, you specify a title and the source page.
uuid: e67608a9-e6c9-42f3-bd1d-63a5fa87ae18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 48826f03-6731-49c5-a6c5-6e2fb718f912
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 2f5c022e-bd98-4912-9409-d08137a1caf1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 29%

---

# Creazione dei lanci{#creating-launches}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Crea un lancio per abilitare l’aggiornamento di una nuova versione di pagine web esistenti da attivare in futuro. Per creare un lancio, è necessario specificare un titolo e la pagina di origine:

* Il titolo viene visualizzato nel **Barra laterale**, da cui gli autori possono accedervi per lavorare su di loro.
* Per impostazione predefinita, nel lancio sono incluse le pagine figlie della pagina sorgente. Puoi utilizzare solo la pagina sorgente, se lo desideri.
* Per impostazione predefinita, [Live Copy](/help/sites-administering/msm.md) aggiorna automaticamente le pagine di lancio mano a mano che cambiano le pagine di origine. È possibile specificare la creazione di una copia statica per evitare modifiche automatiche.

Facoltativamente, puoi specificare la **Data lancio** (e l’ora) per definire quando promuovere e attivare le pagine del lancio. Tuttavia, la **Data lancio** funziona solo in combinazione con il flag **Production Ready** (vedi la sezione [Modifica di una configurazione di lancio](/help/sites-classic-ui-authoring/classic-launches-editing.md#editing-a-launch-configuration)). Affinché le azioni vengano effettivamente eseguite in automatico, è necessario impostare entrambe.

## Creazione di un lancio {#creating-a-launch}

La procedura seguente crea un lancio.

1. Apri la pagina di amministrazione del sito web ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)).
1. Fai clic su **Nuovo...** then **Nuovo lancio...**.
1. In **Creare un lancio** specificare i valori per le seguenti proprietà:

   * **Titolo lancio**: Nome del lancio. Il nome deve essere significativo per gli autori.
   * **Pagina di origine**: Percorso della pagina per la quale creare il lancio. Per impostazione predefinita, sono incluse tutte le pagine figlie.
   * **Escludi sottopagine**: Seleziona questa opzione per creare il lancio solo per la pagina sorgente e non per le pagine figlie. Per impostazione predefinita, questa opzione non è selezionata.
   * **Mantieni in sincronia**: Seleziona questa opzione per aggiornare automaticamente il contenuto delle pagine del lancio quando vengono modificate le pagine di origine. Ciò si ottiene con il lancio di un [Live Copy](/help/sites-administering/msm.md).
   * **Data lancio**: la data e l&#39;ora in cui la copia del lancio deve essere attivata (in base alla segnalazione **Produzione pronta**; consulta [Lanci: l&#39;ordine degli eventi](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Fai clic su **Crea**.

## Eliminazione di un lancio {#deleting-a-launch}

Puoi anche eliminare un lancio.

1. In [console lanci](/help/sites-classic-ui-authoring/classic-launches.md), seleziona il lancio richiesto.
1. Fai clic su **Elimina** - è richiesta la conferma:

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!CAUTION]
   >
   >Quando si eliminano i lanci nidificati, è necessario eliminare prima i livelli inferiori.
