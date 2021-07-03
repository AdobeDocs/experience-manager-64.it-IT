---
title: Attività correlate
description: Scopri come mettere in relazione le risorse che condividono alcuni attributi comuni. È inoltre possibile utilizzare la funzione per creare relazioni sorgente/derivate tra le risorse.
contentOwner: AG
feature: Gestione risorse, collaborazione
role: User
exl-id: d19544c4-c8e7-4a39-9c86-15a46dca848e
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 3%

---

# Attività correlate {#related-assets}

Risorse Adobe Experience Manager (AEM) consente di collegare manualmente le risorse in base alle esigenze dell’organizzazione tramite la funzione Risorse correlate. Ad esempio, puoi correlare un file di licenza con una risorsa o un&#39;immagine/video su un argomento simile. È possibile correlare le risorse che condividono determinati attributi comuni. È inoltre possibile utilizzare la funzione per creare relazioni sorgente/derivate tra le risorse. Ad esempio, se si dispone di un file PDF generato da un file INDD, è possibile collegare il file PDF al relativo file INDD di origine.

In questo modo, puoi condividere un file a bassa risoluzione (ad esempio PDF/JPG) con fornitori/agenzie e rendere disponibile il file ad alta risoluzione (ad esempio INDD) solo su richiesta.

## Risorse correlate {#relating-assets}

1. Dall’interfaccia di Assets, apri la pagina delle proprietà di una risorsa che desideri correlare.

   ![chlimage_1-272](assets/chlimage_1-272.png)

   In alternativa, seleziona la risorsa dalla vista a elenco.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   Puoi anche selezionare la risorsa da una raccolta.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Per correlare un’altra risorsa alla risorsa selezionata, tocca o fai clic sull’icona **[!UICONTROL Relate]** nella barra degli strumenti.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Effettua una delle operazioni seguenti:

   * Per correlare il file di origine della risorsa, seleziona **[!UICONTROL Origine]** dall’elenco.
   * Per correlare un file derivato, selezionare **[!UICONTROL Derivato]** dall&#39;elenco.
   * Per creare una relazione bidirezionale tra le risorse, seleziona **[!UICONTROL Altri]** dall’elenco.

   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Dalla schermata **[!UICONTROL Seleziona risorsa]** , individua la posizione della risorsa da correlare e selezionala.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Tocca o fai clic sull’icona **[!UICONTROL Conferma]** .
1. Tocca o fai clic su **[!UICONTROL OK]** per chiudere la finestra di dialogo. A seconda della relazione scelta nel passaggio 3, la risorsa correlata è elencata sotto una categoria appropriata nella sezione **[!UICONTROL Correlata]** . Ad esempio, se la risorsa correlata è il file di origine della risorsa corrente, è elencata in **[!UICONTROL Origine]**.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Per annullare la correlazione di una risorsa, tocca o fai clic sull’icona **[!UICONTROL Annulla relazione]** nella barra degli strumenti.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Seleziona le risorse da rimuovere dalla finestra di dialogo **[!UICONTROL Rimuovi relazioni]** e tocca o fai clic su **[!UICONTROL Annulla relazione]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Tocca o fai clic su **[!UICONTROL OK]** per chiudere la finestra di dialogo. Le risorse per le quali hai rimosso le relazioni vengono eliminate dall’elenco delle risorse correlate nella sezione **[!UICONTROL Correlate]** .

## Traduzione di risorse correlate {#translating-related-assets}

La creazione di relazioni sorgente/derivate tra risorse tramite la funzione Risorse correlate è utile anche nei flussi di lavoro di traduzione. Quando esegui un flusso di lavoro di traduzione su una risorsa derivata, AEM Assets recupera automaticamente tutte le risorse a cui fa riferimento il file di origine e le include per la traduzione. In questo modo, la risorsa a cui fa riferimento la risorsa di origine viene tradotta insieme alle risorse di origine e derivate. Ad esempio, considera uno scenario in cui la copia in lingua inglese include una risorsa derivata e il relativo file di origine come mostrato.

![chlimage_1-281](assets/chlimage_1-281.png)

Se il file di origine è correlato a un’altra risorsa, AEM Assets recupera la risorsa di riferimento e la include per la traduzione.

![chlimage_1-282](assets/chlimage_1-282.png)

1. Traduci le risorse nella cartella di origine in una lingua di destinazione seguendo i passaggi descritti in [Crea un nuovo progetto di traduzione](translation-projects.md#create-a-new-translation-project). Ad esempio, in questo caso, traduci le tue risorse in francese.
1. Dalla pagina Progetti , apri la cartella di traduzione.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Tocca o fai clic sulla porzione del progetto per aprire la pagina dei dettagli.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Tocca o fai clic sui puntini di sospensione sotto la scheda Processo di traduzione per visualizzare lo stato della traduzione.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Seleziona la risorsa e tocca o fai clic su **[!UICONTROL Mostra in Assets]** nella barra degli strumenti per visualizzare lo stato di traduzione della risorsa.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Per verificare che le risorse correlate all’origine siano state tradotte, tocca o fai clic sulla risorsa sorgente.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Seleziona la risorsa correlata all’origine, quindi tocca o fai clic su **[!UICONTROL Mostra in Assets]**. Viene visualizzata la risorsa correlata tradotta.

   ![chlimage_1-288](assets/chlimage_1-288.png)
