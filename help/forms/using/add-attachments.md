---
title: Aggiunta di allegati
seo-title: Adding attachments
description: Aggiungi fotografie e note di scarabocchio come annotazioni all’attività nell’app AEM Forms
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 1%

---

# Aggiunta di allegati {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Aggiunta di allegati ai moduli sincronizzati con il server AEM Forms Workflow (AEM Forms su JEE) {#adding-annotations}

L’app AEM Forms ti consente di allegare immagini, note con script e note di testo al modulo sincronizzato con il server JEE di AEM Forms. Se il modulo viene caricato da un server AEM Forms Workflow, gli allegati vengono aggiunti al modulo. Tocca il pulsante allegato ![allegato-app](assets/attachments-app.png) per visualizzare tutti gli allegati di un modulo. La notifica rossa specifica il numero di allegati nel modulo. Se nel modulo non sono presenti allegati, non è possibile visualizzare il pulsante di notifica rosso. Se non sono presenti allegati nel modulo, quando si tocca il pulsante allegati ![attaccare](assets/attch.png), è possibile allegare foto o scarabocchi.

Le opzioni disponibili sono:

* **[!UICONTROL Galleria]**: Consente di aggiungere un&#39;immagine dalle immagini salvate sul dispositivo.

* **[!UICONTROL Telecamera]**: Consente di scattare una foto e aggiungerla al modulo.

* **[!UICONTROL Note]**: Consente di aggiungere uno scarabocchio o una nota di testo. Utilizzo ![scarabocchio](assets/scribble.png) per aggiungere uno scarabocchio, e ![tastiera](assets/keyboard.png) per aggiungere una nota di testo.

>[!NOTE]
>
>Gli allegati aggiunti da un utente sono visibili ad altri utenti dell’app AEM Forms. Altri utenti non possono eliminare gli allegati aggiunti da un utente.

### Schermata Allegati {#the-attachments-screen}

Per visualizzare tutti gli allegati in una posizione, tocca ![allegato-app](assets/attachments-app.png). Qui è possibile aggiungere, rinominare ed eliminare gli allegati.

![Tutti gli allegati in un luogo](assets/attachments-screen.png)

È possibile utilizzare **+** nella schermata Allegati per allegare un&#39;altra immagine, un altro scarabocchio o un altro testo.

### Aggiunta di una fotografia {#adding-a-photograph}

È possibile utilizzare la fotocamera del dispositivo mobile o le immagini salvate nel dispositivo per allegare un&#39;immagine nel modulo.

1. Toccare il pulsante allegato ![attaccare](assets/attch.png) in fondo alla finestra.
1. Tocca **[!UICONTROL Galleria]** o **[!UICONTROL Telecamera]** nella finestra a comparsa visualizzata.
1. In base all’opzione selezionata, esegui le seguenti operazioni:

   1. Se si seleziona **[!UICONTROL Telecamera]**.

      Scatta una fotografia. Quindi tocca **[!UICONTROL Utilizzo]** ![use-pic](assets/use-pic.png) pulsante .

      Oppure tocca **[!UICONTROL Ritorno]** ![nuovo](assets/retake.png) per riprendere la fotografia.

   1. Se si seleziona **[!UICONTROL Galleria]**.

      Viene visualizzato il browser delle immagini del dispositivo. Nel browser delle immagini del dispositivo, toccare l&#39;immagine che si desidera allegare.

### Aggiunta di una nota {#adding-a-note}

La **Note** consente di aggiungere nel modulo script a mano libera e allegati di testo.

1. Toccare il pulsante allegato ![attaccare](assets/attch.png) in fondo alla finestra.
1. Tocca **[!UICONTROL Note]** nella finestra a comparsa visualizzata.
1. Nell’interfaccia utente Note che viene avviata, acquisisci uno scarabocchio a mano libera.

   ![Interfaccia scribble](assets/scribble-ui.png)
   **Figura:** *Goccia*

   Nell’interfaccia Scribble è possibile utilizzare le seguenti opzioni:

   * **[!UICONTROL Cancella]**: Cancella lo schermo.
   * **[!UICONTROL Fine]**: Allega lo scarabocchio corrente.
   * **[!UICONTROL Annulla]**: Ignora lo scarabocchio corrente ed esce dall&#39;interfaccia utente Scribble.
   * ![tastiera](assets/keyboard.png): Cancella lo scarabocchio e consente di aggiungere una nota di testo.

   ![Tastiera nello scarabocchio dell’app AEM Forms](assets/keyboard-inapp.png)

## Allegati nei moduli sincronizzati con i server AEM Forms senza flusso di lavoro AEM Forms (AEM Forms su OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Gli allegati per i moduli mobili sincronizzati con i server OSGi di AEM Forms funzionano in modo simile ai server JEE di AEM Forms.

Gli allegati a livello di modulo non sono supportati per i moduli adattivi caricati nell’app da un server OSGi di AEM Forms. Per allegare immagini o note di testo, abilitare gli allegati a livello di campo nel modulo durante la creazione. Trascina il componente File allegato dal browser Componenti sul campo .

Nel caso di moduli adattivi, è possibile visualizzare i file allegati nel documento di record (DoR). Vedi [Genera documento di record per moduli adattivi non XFA](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
