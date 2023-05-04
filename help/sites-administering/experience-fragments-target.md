---
title: Integrazione di Target con i frammenti esperienza
seo-title: Target Integration with Experience Fragments
description: Integrazione di Target con i frammenti esperienza
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 76%

---

# Integrazione di Target con i frammenti esperienza{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Questa funzionalità richiede l&#39;applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o successiva.

Puoi esportare [Frammenti esperienza](/help/sites-authoring/experience-fragments.md), creato in Adobe Experience Manager (AEM), in Adobe Target. Puoi quindi utilizzarli come offerte nelle attività di Target, per testare e personalizzare le esperienze su larga scala. Questo ti consente di combinare la facilità d’uso e la potenza di AEM, con le potenti funzionalità di intelligenza automatizzata (AI) e apprendimento automatico (ML) di Target.

## Prerequisiti {#prerequisites}

Sono necessarie diverse azioni:

1. Devi integrare AEM con Target. Vedi [Integrazione con Adobe Target](/help/sites-administering/target.md) per ulteriori informazioni.
1. I frammenti esperienza vengono esportati dall’istanza di authoring, per cui devi [Configurare l’esternalizzatore di collegamenti](/help/sites-developing/externalizer.md) nell’istanza di authoring, assicurati che tutti i collegamenti siano esternalizzati per l’istanza di pubblicazione.

## Aggiungere la configurazione cloud {#add-the-cloud-configuration}

Prima di esportare un frammento è necessario aggiungere la **Configurazione cloud** di **Adobe Target** al frammento o alla cartella:

1. Passa alla console **Frammenti di esperienza**.
1. Apri **Proprietà pagina** per la cartella o il frammento appropriato.

   >[!NOTE]
   >
   >Se aggiungi la configurazione cloud alla cartella principale Frammento di esperienza, questa viene ereditata da tutti gli elementi secondari.
   >
   >Se aggiungi la configurazione cloud al Frammento di esperienza stesso, questa viene ereditata da tutte le varianti.

1. Seleziona la scheda **Servizi cloud**.

1. Sotto **Configurazione Cloud Service**, seleziona **Adobe Target** dall’elenco a discesa.
1. Sotto **Adobe Target**, seleziona la configurazione appropriata.

1. **Salva e chiudi**.

## Esportazione di un frammento di esperienza in Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Per le risorse multimediali, come le immagini, viene esportato solo un riferimento in Target. La risorsa stessa rimane memorizzata in AEM Assets e viene distribuita dall’istanza di pubblicazione AEM.
>
>Per questo motivo è necessario pubblicare il frammento di esperienza con tutte le relative risorse prima di esportarlo in Target.

Per esportare un frammento di esperienza da AEM a Target (dopo aver specificato la configurazione cloud):

1. Passa alla console Frammenti di esperienza.
1. Seleziona il frammento di esperienza da esportare in Target.

   >[!NOTE]
   >
   >Deve essere una variante Web del frammento di esperienza.

1. Tocca o fai clic su **Esporta in Adobe Target**.

   >[!NOTE]
   >
   >Se il frammento di esperienza è già stato esportato, seleziona **Aggiorna in Adobe Target**.

1. Tocca o fai clic su **Esporta senza pubblicare** o **Pubblica** se necessario.

   >[!NOTE]
   >
   >Selezionando** Pubblica** il frammento di esperienza viene pubblicato immediatamente e inviato a Target.

1. Nella finestra di conferma tocca o fai clic su **OK**.

   Il frammento di esperienza deve ora essere in Target.

>[!NOTE]
>
>In alternativa, è possibile eseguire l’esportazione dall’editor di pagine utilizzando comandi comparabili nel menu [Informazioni pagina](/help/sites-authoring/author-environment-tools.md#page-information).

## Utilizzo dei frammenti di esperienza in Target {#using-your-experience-fragments-in-target}

Dopo aver eseguito le attività precedenti, il frammento di esperienza viene visualizzato nella pagina Offerte di Target. Dai un&#39;occhiata alla [documentazione specifica di Target](https://experiencecloud.adobe.com/resources/help/it_IT/target/target/aem-experience-fragments.html) per scoprire cosa puoi ottenere.

## Eliminazione di un frammento di esperienza già esportato in Target {#deleting-an-experience-fragment-already-exported-to-target}

L’eliminazione di un frammento di esperienza già esportato in Target potrebbe causare problemi se il frammento è già utilizzato in un’offerta in Target. L’eliminazione del frammento renderebbe l’offerta inutilizzabile mentre il contenuto del frammento è distribuito da AEM.

Per evitare tali situazioni:

* Se il frammento di esperienza non è attualmente utilizzato in un’attività, AEM consente all’utente di eliminarlo senza un messaggio di avviso.
* Se il frammento di esperienza è attualmente utilizzato da un’attività in Target, un messaggio di errore avvisa l’utente AEM delle possibili conseguenze che l’eliminazione del frammento avrà sull’attività.

   Il messaggio di errore in AEM non impedisce all’utente di (forzare) eliminare il frammento di esperienza. Se il frammento di esperienza viene eliminato:

   * L’offerta Target con il frammento di esperienza AEM può mostrare un comportamento indesiderato

      * L&#39;offerta sarà probabilmente ancora visualizzata, poiché l&#39;HTML del frammento di esperienza è stato inviato su Target
      * Eventuali riferimenti nel frammento di esperienza potrebbero non funzionare correttamente se le risorse di riferimento sono state eliminate anche in AEM.
   * Naturalmente, eventuali ulteriori modifiche al frammento di esperienza sono impossibili in quanto questo non esiste più in AEM.
