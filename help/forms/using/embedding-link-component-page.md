---
title: Incorporazione di un componente collegamento in una pagina
seo-title: Embedding link component in a page
description: Puoi utilizzare il componente collegamento per collegare un documento adattivo o un modulo adattivo da qualsiasi pagina.
seo-description: You can use the link component to link an adaptive document or an adaptive form from any page.
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
exl-id: eb816a35-0773-4eda-95b2-1d351c71be8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 2%

---

# Incorporazione di un componente collegamento in una pagina{#embedding-link-component-in-a-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisiti {#prerequisites}

Il componente di collegamento è membro della categoria Document Services . Assicurarsi che la categoria Document Services sia visibile nel browser Componenti AEM. Se la categoria non è elencata, segui i passaggi elencati in [Abilitazione dei componenti del portale moduli](/help/forms/using/enabling-forms-portal-components.md).

## Componente collegamento {#link-component}

Il componente Collegamento permette agli autori di un portale moduli di creare un collegamento a un modulo adattivo da qualsiasi punto di una pagina. Il componente Collegamento è disponibile nella sezione Servizi documenti del browser componenti.

Per aggiungere un componente Collegamento alla pagina, effettua le seguenti operazioni:

1. Trascina **Collegamento** nella pagina. Seleziona il componente e tocca ![cmppr](assets/cmppr.png). Viene visualizzata la finestra di dialogo Modifica componente collegamento .

   ![edit-link-component](assets/edit-link-component.png)

1. In **Visualizzazione** , specifica quanto segue:

   * **Didascalia collegamento**: Collegamento di testo o didascalia per il collegamento.
   * **Descrizione collegamento**: Descrizione del collegamento.
   * **Modello di layout**: Modello per il layout del componente Collegamento .

1. Apri **Informazioni risorsa** e specifica il tipo di risorsa. Una risorsa può essere **modulo**. A seconda del tipo di risorsa selezionata, vengono visualizzate le opzioni elencate di seguito:

   * **Percorso risorsa**: Percorso archivio in cui viene memorizzata la risorsa.
   * **Tipo di rendering**: Il formato di rendering: PDF, HTML o Auto. Il tipo di rendering automatico rileva l’ambiente utente e, di conseguenza, esegue il rendering del modulo come HTML o PDF. Ad esempio, se l’accesso al modulo è effettuato da un dispositivo mobile, il tipo di rendering automatico esegue il rendering del modulo in HTML.
   * **URL di invio:**  URL del servlet in cui vengono inviati i dati del modulo.
   * **Profilo HTML**: Profilo per il rendering del modulo come HTML.
   * **Profilo PDF**: Profilo per il rendering del modulo come documento PDF.

1. Apri la scheda **Avanzate.** È possibile specificare i parametri aggiuntivi nel formato della coppia chiave-valore. Quando fai clic sul collegamento, questi parametri aggiuntivi vengono passati insieme al modulo.

   Tocca **Fine** per salvare la configurazione.

## Best practice per l’utilizzo del componente Collegamento {#best-practices-for-using-link-component-br}

* Assicurarsi di selezionare PDF come tipo di rendering se il percorso specificato in Percorso modulo punta a un documento con PDF come formato di rendering consentito.
* L’URL di invio di un modulo può essere specificato in più posizioni e il relativo ordine di precedenza è il seguente:

   1. L’URL di invio incorporato nel modulo (nel pulsante di invio) ha la priorità più alta.
   1. L’URL di invio menzionato in Forms Manager ha la priorità media.
   1. L’URL di invio menzionato nel portale dei moduli ha la priorità più bassa.
