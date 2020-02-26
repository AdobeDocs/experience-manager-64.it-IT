---
title: Integrazione con Target con i frammenti esperienza
seo-title: Integrazione con Target con i frammenti esperienza
description: Integrazione con Target con i frammenti esperienza
seo-description: Integrazione con Target con i frammenti esperienza
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb

---


# Integrazione con Target con i frammenti esperienza{#target-integration-with-experience-fragments}

>[!NOTE]
>
>Questa funzionalità richiede l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o successivo.

Puoi esportare frammenti [](/help/sites-authoring/experience-fragments.md)esperienza creati in Adobe Experience Manager (AEM) in Adobe Target. Possono quindi essere utilizzati come offerte nelle attività Target, per sottoporre a test e personalizzare le esperienze su scala. Questo consente di combinare la facilità di utilizzo e la potenza di AEM con le potenti funzionalità di Automated Intelligence (AI) e di machine Learning (ML) di Target.

## Prerequisiti {#prerequisites}

Sono necessarie diverse azioni:

1. Devi integrare AEM con Target. See [Integrating with Adobe Target](/help/sites-administering/target.md) for more information.
1. I frammenti esperienza vengono esportati dall’istanza di creazione, pertanto è necessario [configurare Link Externalizer](/help/sites-developing/externalizer.md) sull’istanza di creazione per garantire che eventuali collegamenti siano esternalizzati per l’istanza di pubblicazione.

## Aggiungi configurazione cloud {#add-the-cloud-configuration}

Prima di esportare un frammento è necessario aggiungere la configurazione **** Cloud per **Adobe Target** al frammento o alla cartella:

1. Andate alla console **Frammenti** esperienza.
1. Aprire Proprietà **** pagina per la cartella o il frammento appropriato.

   >[!NOTE]
   >
   >Se aggiungi la configurazione cloud alla cartella padre del frammento esperienza, la configurazione viene ereditata da tutti gli elementi figlio.
   >
   >Se aggiungi la configurazione cloud allo stesso frammento esperienza, la configurazione viene ereditata da tutte le varianti.

1. Selezionate la scheda Servizi **** cloud.

1. In Configurazione **servizio** Cloud, seleziona **Adobe Target** dall&#39;elenco a discesa.
1. In **Adobe Target**, seleziona la configurazione appropriata.

1. **Salva e chiudi**.

## Esportazione di un frammento esperienza in Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Per le risorse multimediali, come le immagini, viene esportato solo un riferimento a Target. La risorsa stessa rimane memorizzata in Risorse AEM e viene distribuita dall’istanza di pubblicazione AEM.
>
>Per questo motivo, il frammento esperienza, con tutte le risorse correlate, deve essere pubblicato prima di esportare in Target.

Per esportare un frammento esperienza da AEM a Target (dopo aver specificato la configurazione cloud):

1. Passate alla console Frammenti esperienza.
1. Selezionate il frammento esperienza da esportare come destinazione.

   >[!NOTE]
   >
   >Deve essere una variante Web del frammento esperienza.

1. Toccate o fate clic su **Esporta in Adobe Target**.

   >[!NOTE]
   >
   >Se il frammento esperienza è già stato esportato, selezionate **Aggiorna in Adobe Target**.

1. Toccate/fate clic su **Esporta senza pubblicare** o **pubblicare** come necessario.

   >[!NOTE]
   >
   >Se selezionate** Publish**, il frammento esperienza verrà pubblicato immediatamente e inviato a Target.

1. Toccate o fate clic su **OK** nella finestra di dialogo di conferma.

   Il frammento esperienza deve ora essere in Target.

>[!NOTE]
>
>In alternativa, potete eseguire l’esportazione dall’editor pagina utilizzando comandi comparabili nel menu Informazioni [](/help/sites-authoring/author-environment-tools.md#page-information) pagina.

## Utilizzo dei frammenti esperienza in Target {#using-your-experience-fragments-in-target}

Dopo aver eseguito le attività precedenti, il frammento esperienza viene visualizzato nella pagina Offerte in Target. Consulta la documentazione [](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) specifica di Target per saperne di più sui risultati ottenuti.

## Eliminazione di un frammento esperienza già esportato in Target {#deleting-an-experience-fragment-already-exported-to-target}

L&#39;eliminazione di un frammento esperienza già esportato in Target potrebbe causare problemi se il frammento è già utilizzato in un&#39;offerta in Target. L’eliminazione del frammento renderebbe l’offerta inutilizzabile mentre il contenuto del frammento viene distribuito da AEM.

Per evitare tali situazioni:

* Se il frammento esperienza non è attualmente utilizzato in un&#39;attività, AEM consente all&#39;utente di eliminare il frammento senza ricevere un messaggio di avviso.
* Se il frammento esperienza è attualmente utilizzato da un&#39;attività in Target, un messaggio di errore avvisa l&#39;utente AEM delle possibili conseguenze che l&#39;eliminazione del frammento avrà sull&#39;attività.

   Il messaggio di errore in AEM non impedisce all’utente di (forzare-)eliminare il frammento esperienza. Se il frammento esperienza viene eliminato:

   * L&#39;offerta Target con il frammento esperienza AEM può mostrare un comportamento indesiderato

      * Il rendering dell&#39;offerta continuerà probabilmente, in quanto l&#39;HTML del frammento esperienza è stato inviato a Target
      * Eventuali riferimenti nel frammento esperienza potrebbero non funzionare correttamente se anche le risorse di riferimento venivano eliminate in AEM.
   * Ovviamente, non è possibile apportare ulteriori modifiche al frammento esperienza, in quanto il frammento esperienza non esiste più in AEM.


