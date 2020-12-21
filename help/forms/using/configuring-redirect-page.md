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
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Configurazione della pagina di reindirizzamento {#configuring-redirect-page}

Gli autori dei moduli possono configurare una pagina per ciascun modulo, alla quale verranno reindirizzati gli utenti dopo l&#39;invio del modulo.

1. In modalità di modifica, selezionare un componente, quindi fare clic su ![livello campo](assets/field-level.png) > **Contenitore modulo adattivo**, quindi fare clic su ![cmppr](assets/cmppr.png).

1. Nella barra laterale, fare clic su **Invio**.

1. Fornite l’URL della pagina di reindirizzamento nella sezione Pagina di ringraziamento della sezione Invio.
1. Facoltativamente, in Invia azione, per l’azione Invia a endpoint REST è possibile configurare il parametro da passare alla pagina di reindirizzamento.

![Reindirizza ](assets/thank-you-setting-1.png)
**configurazione paginaFigura:** *Reindirizza configurazione pagina*

Gli autori dei moduli possono utilizzare i seguenti parametri passati alla pagina di ringraziamento. Per tutte le azioni di invio disponibili, vengono passati i parametri `status` e `owner`. Oltre a questi due parametri, alcuni parametri aggiuntivi vengono passati per le seguenti azioni di invio:

* **Azione**  contenuto store (obsoleto):  `contentPath`— il percorso del nodo nell&#39;archivio in cui sono memorizzati i dati inviati.

* **Azione**  Store PDF (obsoleto):  `contentPath`—dei dati inviati e del percorso del nodo in cui è memorizzato il file PDF nella directory archivio—viene passato.

* **Invia al flusso di lavoro** Forms: I parametri di output restituiti dal flusso di lavoro dei moduli vengono passati.

* **Invia a endpoint** REST: I parametri aggiunti per la mappatura in-field ai parametri vengono passati. `status` e  `owner` i parametri non vengono passati in questa azione di invio. Per ulteriori informazioni, vedere [Configurazione dell&#39;azione Invia a endpoint REST](/help/forms/using/configuring-submit-actions.md).

