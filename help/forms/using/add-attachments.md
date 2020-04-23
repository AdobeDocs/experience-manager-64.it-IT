---
title: Aggiunta di allegati
seo-title: Aggiunta di allegati
description: Aggiungere fotografie e note di script come annotazioni all'attività nell'app AEM Forms
seo-description: Aggiungere fotografie e note di script come annotazioni all'attività nell'app AEM Forms
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
translation-type: tm+mt
source-git-commit: 0ce79686522da4fb3d017068b623c76f81c6b23a

---


# Aggiunta di allegati {#adding-attachments}

## Aggiunta di allegati ai moduli sincronizzati con il server AEM Forms Workflow (AEM Forms on JEE) {#adding-annotations}

L&#39;app AEM Forms consente di allegare immagini, note con script e note di testo al modulo sincronizzate con il server AEM Forms JEE. Se il modulo viene caricato da un server AEM Forms Workflow, gli allegati vengono aggiunti al modulo. È possibile toccare il pulsante allegato ![allegati-app](assets/attachments-app.png) per visualizzare tutti gli allegati di un modulo insieme. La notifica rossa specifica il numero di allegati nel modulo. Se nel modulo non sono presenti allegati, non è possibile visualizzare il pulsante rosso delle notifiche. Se non sono presenti allegati nel modulo, toccando il pulsante degli allegati ![allegare](assets/attch.png)è possibile allegare foto o script.

Le opzioni disponibili sono:

* **[!UICONTROL Galleria]**: Consente di aggiungere un&#39;immagine dalle immagini salvate sul dispositivo.

* **[!UICONTROL Telecamera]**: Consente di scattare una foto e aggiungerla al modulo.

* **[!UICONTROL Note]**: Consente di aggiungere uno script o una nota di testo. Utilizzare ![gli scarabocchi](assets/scribble.png) per aggiungere uno scarabocchio e la ![tastiera](assets/keyboard.png) per aggiungere una nota di testo.

>[!NOTE]
>
>Gli allegati aggiunti da un utente sono visibili agli altri utenti delle app AEM Forms. Altri utenti non possono eliminare gli allegati aggiunti da un utente.


### Schermata Allegati {#the-attachments-screen}

Per visualizzare tutti gli allegati in una posizione, toccate ![attachments-app](assets/attachments-app.png). È possibile aggiungere, rinominare ed eliminare gli allegati.

![Tutti gli allegati in una posizione](assets/attachments-screen.png)

È possibile utilizzare il pulsante **+** nella schermata Allegati per allegare un&#39;altra immagine, uno script o un testo.

### Aggiunta di una fotografia {#adding-a-photograph}

È possibile utilizzare la fotocamera del dispositivo mobile o le immagini salvate nel dispositivo per allegare un&#39;immagine al modulo.

1. Toccare il pulsante di collegamento ![fissato](assets/attch.png) nella parte inferiore della finestra.
1. Toccate **[!UICONTROL Galleria]** o **[!UICONTROL Fotocamera]** nella finestra a comparsa.
1. In base all’opzione selezionata, effettuate le seguenti operazioni:

   1. Se selezionate **[!UICONTROL Fotocamera]**.

      Scatta una fotografia. Quindi toccate il pulsante **[!UICONTROL Use]** ![use-pic](assets/use-pic.png) .

      Oppure toccate il pulsante **[!UICONTROL Riproduci]** ![di nuovo](assets/retake.png) per riprendere la foto.

   1. Se selezionate **[!UICONTROL Galleria]**.

      Viene visualizzato il browser delle immagini del dispositivo. Nel browser delle immagini del dispositivo, toccate l&#39;immagine da allegare.

### Aggiunta di una nota {#adding-a-note}

L&#39;opzione **Note** consente di aggiungere script a mano libera e allegati di testo nel modulo.

1. Toccare il pulsante di collegamento ![fissato](assets/attch.png) nella parte inferiore della finestra.
1. Toccate **[!UICONTROL Note]** nella finestra a comparsa.
1. Nell’interfaccia utente Note che viene avviata, acquisite uno script a mano libera.

   ![Interfaccia scarabocchio](assets/scribble-ui.png)
   **Figura:** *scarabocchio*

   Nell&#39;interfaccia Scribble è possibile utilizzare le seguenti opzioni:

   * **[!UICONTROL Cancella]**: Cancella lo schermo.
   * **[!UICONTROL Fatto]**: Associa lo script corrente.
   * **[!UICONTROL Annulla]**: Elimina lo script corrente ed esce dall&#39;interfaccia utente di Scribble.
   * ![tastiera](assets/keyboard.png): Cancella lo script e consente di aggiungere una nota di testo.
   ![Tastiera nello script dell&#39;app AEM Forms](assets/keyboard-inapp.png)

## Allegati in moduli sincronizzati con i server AEM Forms senza AEM Forms Workflow (AEM Forms su OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Gli allegati per i moduli mobili sincronizzati con i server AEM Forms OSGi funzionano in modo simile ai server AEM Forms JEE.

Gli allegati a livello di modulo non sono supportati per i moduli adattivi caricati nell&#39;app da un server AEM Forms OSGi. Per allegare immagini o note di testo, è necessario abilitare gli allegati a livello di campo nel modulo al momento della creazione. Trascinare il componente Allegato dal Browser componenti sul campo.

Nel caso di moduli adattivi, è possibile visualizzare i file allegati nel documento record (DoR). Vedere [Genera documento record per i moduli](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)adattivi non XFA.
