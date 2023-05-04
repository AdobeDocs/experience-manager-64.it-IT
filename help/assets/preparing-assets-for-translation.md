---
title: Preparazione delle risorse per la traduzione
description: Crea cartelle principali in lingua per preparare la traduzione di risorse multilingue.
contentOwner: AG
feature: Projects,Translation
role: User,Admin
exl-id: cc6c4f9e-8e22-4622-8b24-230ae258351c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 10%

---

# Preparazione delle risorse per la traduzione {#preparing-assets-for-translation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per risorse multilingue si intendono le risorse con file binari, metadati e tag in più lingue. In genere, i binari, i metadati e i tag delle risorse esistono in una lingua, che vengono poi tradotti in altre lingue per l’utilizzo in progetti multilingue.

In Risorse Adobe Experience Manager, le risorse multilingue sono incluse nelle cartelle, in cui ogni cartella contiene le risorse in una lingua diversa.

Ogni cartella della lingua è denominata copia della lingua. La cartella principale di una copia per lingua, nota come radice lingua, identifica la lingua del contenuto nella copia per lingua. Ad esempio: */content/dam/it* è la radice della lingua italiana per la copia in lingua italiana. Le copie per lingua devono utilizzare un [directory principale della lingua configurata correttamente](preparing-assets-for-translation.md#creating-a-language-root) in modo che venga usata la lingua corretta quando vengono eseguite le traduzioni delle risorse di origine.

La copia per lingua per la quale hai originariamente aggiunto le risorse è la lingua principale. Il linguaggio primario è la fonte tradotta in altre lingue.

La gerarchia delle cartelle di esempio include diverse directory principali della lingua:

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Per preparare le risorse per la traduzione, effettua le seguenti operazioni:

1. Creare la directory principale lingua della lingua primaria. Ad esempio, la directory principale della lingua della copia in lingua inglese nella gerarchia delle cartelle di esempio è `/content/dam/en`. Assicurati che la directory principale della lingua sia configurata correttamente in base alle informazioni in [Creazione di una directory principale della lingua](preparing-assets-for-translation.md#creating-a-language-root).

1. Aggiungi le risorse alla tua lingua primaria.
1. Crea la directory principale della lingua di ogni lingua di destinazione per la quale è necessaria una copia della lingua.

## Creazione di una directory principale della lingua {#creating-a-language-root}

Per creare la directory principale della lingua, creare una cartella e utilizzare un codice della lingua ISO come valore per la proprietà Name. Dopo aver creato la directory principale lingua, è possibile creare una copia della lingua a qualsiasi livello all’interno della directory principale lingua.

Ad esempio, la pagina principale della copia in lingua italiana della gerarchia dei campioni ha `it` come proprietà Name. La proprietà Name viene utilizzata come nome del nodo della risorsa nell’archivio e quindi determina il percorso delle risorse. (`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. Dalla console Assets, tocca o fai clic su **[!UICONTROL Crea]** e scegli dal menu la voce **[!UICONTROL Cartella]**.

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. Nel campo Nome digitare il codice del paese nel formato `<language-code>`.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Tocca o fai clic su **[!UICONTROL Crea]**. La directory principale della lingua viene creata nella console Risorse.

## Visualizzazione delle radici della lingua {#viewing-language-roots}

L’interfaccia touch fornisce un pannello Riferimenti che mostra un elenco delle radici della lingua create all’interno di [!DNL Experience Manager] Risorse.

1. Nella console Assets, seleziona la lingua principale per la quale vuoi creare delle copie per lingua.
1. Tocca o fai clic sull’icona di Navigazione globale e scegli **[!UICONTROL Riferimenti]** per aprire il riquadro Riferimento.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Nel riquadro Riferimenti, tocca o fai clic su **[!UICONTROL Copie per lingua]**. Il pannello Copie per lingua mostra le copie in lingua delle risorse.

   ![chlimage_1-123](assets/chlimage_1-123.png)
