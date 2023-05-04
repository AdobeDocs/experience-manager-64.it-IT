---
title: Configurazione della pagina di reindirizzamento
seo-title: Configuring redirect page
description: Dopo aver compilato un modulo adattivo, gli utenti possono essere reindirizzati a una pagina web che gli autori del modulo possono configurare durante la creazione del modulo.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# Configurazione della pagina di reindirizzamento {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Gli autori dei moduli possono configurare una pagina per ciascun modulo, a cui verranno reindirizzati gli utenti dopo l’invio.

1. In modalità di modifica, seleziona un componente, quindi fai clic su ![a livello di campo](assets/field-level.png) > **Contenitore di moduli adattivi**, quindi fai clic su ![cmppr](assets/cmppr.png).

1. Nella barra laterale, fai clic su **Invio**.

1. Fornisci l’URL della pagina di reindirizzamento alla sezione Pagina di ringraziamento nella sezione Invio .
1. Facoltativamente, in Azione di invio per l’azione Invia a endpoint REST è possibile configurare il parametro da passare alla pagina di reindirizzamento.

![Reindirizza la configurazione della pagina](assets/thank-you-setting-1.png)
**Figura:** *Reindirizza la configurazione della pagina*

Gli autori dei moduli possono utilizzare i seguenti parametri passati alla pagina di ringraziamento. Per tutte le azioni di invio disponibili, `status` e `owner` vengono passati i parametri . Oltre a questi due parametri, vengono passati alcuni parametri aggiuntivi per le seguenti azioni di invio:

* **Azione di archiviazione contenuti** (obsoleto) : `contentPath`- viene passato il percorso del nodo nell&#39;archivio in cui sono archiviati i dati inviati.

* **Azione Store PDF** (obsoleto) : `contentPath`- dei dati inviati e del percorso del nodo che memorizza il file PDF nel repository.

* **Invio al flusso di lavoro Forms**: I parametri di output restituiti dal flusso di lavoro dei moduli vengono trasmessi.

* **Invia all’endpoint REST**: I parametri aggiunti per la mappatura in-field ai parametri vengono passati. `status` e `owner` i parametri non vengono passati in questa azione di invio. Per ulteriori informazioni, consulta [Configurazione dell’azione di invio dell’endpoint Submit to REST](/help/forms/using/configuring-submit-actions.md).
