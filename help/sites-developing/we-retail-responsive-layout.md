---
title: Layout reattivo in We.Retail
seo-title: Trying out Responsive Layout in We.Retail
description: Layout reattivo in We.Retail
seo-description: null
uuid: d9613655-f54e-458f-9175-d07bb868f58b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 2d374e88-ea09-43d5-986c-5d77b0705b93
exl-id: ccb792f7-e837-4790-818f-e2c446328e71
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 4%

---

# Layout reattivo in We.Retail{#trying-out-responsive-layout-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Tutte le pagine We.Retail utilizzano il componente Contenitore di layout per implementare una progettazione reattiva. Il contenitore layout fornisce un sistema paragrafo che consente di posizionare i componenti all’interno di una griglia reattiva. Questa griglia può ridisporre il layout in base alle dimensioni e al formato del dispositivo/finestra. Il componente viene utilizzato insieme al **Layout** nell’editor di pagine, che consente di creare e modificare il layout dinamico a seconda del dispositivo.

## Prova {#trying-it-out}

1. Modifica la pagina Navigazione artica nella sezione Esperienze del ramo principale lingua.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html

1. Passa a **Anteprima** per visualizzare l’aspetto che la pagina avrebbe rappresentato per un visitatore del sito web. Scorri verso il basso fino al contenuto dell’articolo *acquaviti di Aloha nella Norvegia settentrionale*.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Ridimensiona la finestra del browser e osserva come il layout si adatta dinamicamente al ridimensionamento.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Passa alla modalità Layout . Viene visualizzata automaticamente la barra degli strumenti dell’emulatore, che consente di pianificare il layout per dispositivo di destinazione.

   Quando si seleziona un componente, vengono visualizzate le opzioni mobili e nascoste nel menu di modifica e le relative maniglie di ridimensionamento.

   ![chlimage_1-180](assets/chlimage_1-180.png)

1. Quando si seleziona e si trascina la maniglia di ridimensionamento del componente, viene automaticamente visualizzata la griglia di layout che consente di eseguire le operazioni di ridimensionamento.

   ![chlimage_1-181](assets/chlimage_1-181.png)

## Ulteriori informazioni {#further-information}

Per ulteriori informazioni, consulta il documento di authoring [Layout reattivo](/help/sites-authoring/responsive-layout.md) o il documento dell&#39;amministratore [Configurazione del contenitore di layout e della modalità di layout](/help/sites-administering/configuring-responsive-layout.md) per informazioni tecniche complete.
