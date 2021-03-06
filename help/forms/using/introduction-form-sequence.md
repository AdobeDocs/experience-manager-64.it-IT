---
title: Introduzione alla sequenza di moduli a più passaggi
seo-title: Introduzione alla sequenza di moduli a più passaggi
description: Con AEM Forms è possibile definire una sequenza di pannelli di moduli in cui gli utenti devono navigare e compilare un modulo adattivo.
seo-description: Con AEM Forms è possibile definire una sequenza di pannelli di moduli in cui gli utenti devono navigare e compilare un modulo adattivo.
uuid: b2b94e4c-0c28-47ba-8e23-fd8742baf71c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 4a51ebc4-e019-4fc5-93a1-d97f695126f5
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Introduzione alla sequenza di più passaggi di un modulo {#introduction-to-multi-step-form-sequence}

I moduli adattivi consentono agli autori dei moduli di creare con grande facilità un’esperienza di acquisizione dati in più passaggi. Offre supporto integrato per la creazione di più pannelli e l’associazione di ciascun pannello a diversi pattern di navigazione. Gli autori dei moduli possono raggruppare i campi modulo in sezioni logiche e rappresentare un gruppo come pannello. La navigazione tra i pannelli viene controllata mediante il layout del pannello. Gli autori possono scegliere di disporre i pannelli in layout diversi, ad esempio per posizionarli in sequenza utilizzando il layout della procedura guidata o in modo ad hoc utilizzando il layout a schede. Per informazioni sui layout dei pannelli, vedere [Funzionalità di layout dei moduli adattivi](/help/forms/using/layout-capabilities-adaptive-forms.md).

In una tipica esperienza di compilazione dei moduli, sono necessari più passaggi rispetto all’acquisizione dei dati. L’invio completo di un modulo può comprendere altri passaggi, ad esempio la firma digitale del modulo, la verifica delle informazioni inserite nel modulo, l’elaborazione dei pagamenti e così via. Si differenzia da caso a caso.

Se il tuo caso d’uso richiede una serie di passaggi per l’acquisizione dei dati o se sono previste normative che richiedono l’esecuzione di determinati passaggi, AEM Forms offre un modo per applicare tale struttura comune nei diversi moduli. L’implementazione premeditata della struttura del modulo definisce la sequenza di passaggi per un modulo. ![Esempio di sequenza di moduli a più passaggi](assets/formpipeline.png)

Prendiamo un caso d’uso in cui è necessario creare una sequenza per compilare, verificare, firmare e confermare i passaggi di un modulo. La procedura per creare una sequenza di questo tipo è la seguente:

1. Definire un modello di modulo e aggiungergli il pannello richiesto. Tieni presente che per ogni passaggio della sequenza deve essere presente un pannello. Tuttavia, puoi includere pannelli secondari all’interno di un pannello.

   In questo esempio, possiamo aggiungere i seguenti pannelli:

   * **Riempimento**: Contiene campi dei moduli per l’acquisizione dei dati. In questo caso puoi includere pannelli secondari nidificati per creare sezioni per diversi tipi di informazioni, ad esempio personali, familiari, finanziarie e così via.
   * **Verifica**: Contiene il componente  **** Verifycomponent che può essere utilizzato in un modulo adattivo basato su XFA. Visualizza le informazioni acquisite nel pannello Riempimento in modalità di sola lettura per la verifica.
   * **Firma** elettronica: Contiene il  **** componente Firma che può essere utilizzato in un modulo adattivo basato su XFA. fornisce i seguenti servizi di firma:

      * Servizi eSign di Adobe Document Cloud
      * Firma scarabocchio
   * **Conferma**: Contiene il componente  **** Riepilogo che visualizza un messaggio di conferma dell’invio del modulo dopo che un utente firma il modulo e raggiunge il passaggio Conferma (Riepilogo) nella sequenza. Gli autori possono configurare il testo del componente Riepilogo, visualizzare un messaggio di ringraziamento, visualizzare un collegamento al PDF generato e così via.


1. Selezionare il layout del pannello principale come **[!UICONTROL Procedura guidata]**.
1. Completare i passaggi successivi per creare il modello di modulo. Per ulteriori informazioni, vedere [Creazione di un modello di modulo adattivo personalizzato](/help/forms/using/custom-adaptive-forms-templates.md).

Dopo aver definito la sequenza del modulo nel modello di modulo, è possibile utilizzarla per creare moduli che avranno la struttura di base definita come sequenza in posizione, anche se è sempre possibile personalizzare il modulo in base alle proprie esigenze.

