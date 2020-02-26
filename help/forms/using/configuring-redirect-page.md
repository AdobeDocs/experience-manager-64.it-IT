---
title: Configurazione della pagina di reindirizzamento
seo-title: Configurazione della pagina di reindirizzamento
description: Dopo aver compilato un modulo adattivo, gli utenti possono essere reindirizzati a una pagina Web che gli autori del modulo possono configurare durante la creazione del modulo.
seo-description: Dopo aver compilato un modulo adattivo, gli utenti possono essere reindirizzati a una pagina Web che gli autori del modulo possono configurare durante la creazione del modulo.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d

---


# Configurazione della pagina di reindirizzamento {#configuring-redirect-page}

Gli autori dei moduli possono configurare una pagina per ciascun modulo, alla quale verranno reindirizzati gli utenti dopo l&#39;invio del modulo.

1. In modalità di modifica, selezionare un componente, fare clic su ![campo](assets/field-level.png) > Contenitore **modulo** adattivo, quindi fare clic su ![cmppr](assets/cmppr.png).

1. Nella barra laterale, fate clic su **Invia**.

1. Fornite l’URL della pagina di reindirizzamento nella sezione Pagina di ringraziamento della sezione Invio.
1. Facoltativamente, in Invia azione, per l’azione Invia a endpoint REST è possibile configurare il parametro da passare alla pagina di reindirizzamento.

![](assets/thank-you-setting-1.png) Reindirizza configurazione **** pagina Figura: Configurazione *di reindirizzamento della pagina*

Gli autori dei moduli possono utilizzare i seguenti parametri passati alla pagina di ringraziamento. Per tutte le azioni di invio disponibili `status` e per `owner` i parametri vengono passati. Oltre a questi due parametri, alcuni parametri aggiuntivi vengono passati per le seguenti azioni di invio:

* **Azione** contenuto store (obsoleto): `contentPath`(percorso del nodo nell&#39;archivio in cui sono memorizzati i dati inviati) viene passato.

* **Azione** Store PDF (obsoleto): Viene passato `contentPath`—dei dati inviati e del percorso al nodo in cui è memorizzato il file PDF nella directory archivio—.

* **Flusso di lavoro** di invio a Forms: I parametri di output restituiti dal flusso di lavoro dei moduli vengono passati.

* **Invia a endpoint** REST: I parametri aggiunti per la mappatura in-field ai parametri vengono passati. `status` e `owner` i parametri non vengono passati in questa azione di invio. Per ulteriori informazioni, vedere [Configurazione dell&#39;azione](/help/forms/using/configuring-submit-actions.md)di invio dell&#39;endpoint Invia a REST.

