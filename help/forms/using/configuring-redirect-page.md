---
title: Configurazione della pagina di reindirizzamento
seo-title: Configurazione della pagina di reindirizzamento
description: Dopo aver compilato un modulo adattivo, gli utenti possono essere reindirizzati a una pagina web che gli autori del modulo possono configurare durante la creazione del modulo.
seo-description: Dopo aver compilato un modulo adattivo, gli utenti possono essere reindirizzati a una pagina web che gli autori del modulo possono configurare durante la creazione del modulo.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Moduli adattivi
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Configurazione della pagina di reindirizzamento {#configuring-redirect-page}

Gli autori dei moduli possono configurare una pagina per ciascun modulo, a cui verranno reindirizzati gli utenti dopo l’invio.

1. In modalità di modifica, seleziona un componente, quindi fai clic su ![livello campo](assets/field-level.png) > **Contenitore modulo adattivo**, quindi fai clic su ![cmppr](assets/cmppr.png).

1. Nella barra laterale fate clic su **Invio**.

1. Fornisci l’URL della pagina di reindirizzamento alla sezione Pagina di ringraziamento nella sezione Invio .
1. Facoltativamente, in Azione di invio per l’azione Invia a endpoint REST è possibile configurare il parametro da passare alla pagina di reindirizzamento.

![Reindirizza la ](assets/thank-you-setting-1.png)
**configurazione della paginaFigura:** *Reindirizza la configurazione della pagina*

Gli autori dei moduli possono utilizzare i seguenti parametri passati alla pagina di ringraziamento. Per tutte le azioni di invio disponibili, vengono passati i parametri `status` e `owner` . Oltre a questi due parametri, vengono passati alcuni parametri aggiuntivi per le seguenti azioni di invio:

* **Azione**  contenuto store (obsoleta) :  `contentPath`- viene passato il percorso del nodo nell&#39;archivio in cui sono archiviati i dati inviati.

* **Azione**  Store PDF (obsoleta) :  `contentPath`—dei dati inviati e del percorso del nodo che memorizza il file PDF nel repository—viene passato.

* **Invia al flusso di lavoro** Forms: I parametri di output restituiti dal flusso di lavoro dei moduli vengono trasmessi.

* **Invia all’endpoint** REST: I parametri aggiunti per la mappatura in-field ai parametri vengono passati. `status` e  `owner` i parametri non vengono passati in questa azione di invio. Per ulteriori informazioni, consulta [Configurazione dell’azione Invia all’endpoint REST](/help/forms/using/configuring-submit-actions.md).

