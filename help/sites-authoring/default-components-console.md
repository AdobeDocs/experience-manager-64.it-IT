---
title: Console Componenti
seo-title: Console Componenti
description: 'null'
seo-description: 'null'
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Console Componenti{#components-console}

La console Componenti consente di consultare tutti i componenti definiti nell’istanza e di visualizzare le informazioni chiave di ciascun componente.

It can be accessed from **Tools** -> **General** -> **Components**. Nella console sono disponibili le viste a schede e a elenco. Poiché non esiste una struttura ad albero per i componenti, la vista a colonne non è disponibile.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>La console dei componenti mostra tutti i componenti del sistema. Il [browser Componenti](/help/sites-authoring/author-environment-tools.md#components-browser) mostra i componenti disponibili agli autori e nasconde eventuali gruppi di componenti che iniziano con un punto ( `.`).

## Ricerca {#search-features}

Dall’icona **Solo contenuto** (in alto a sinistra) puoi aprire il pannello **Ricerca** per cercare e/o filtrare i componenti:

![chlimage_1-302](assets/chlimage_1-302.png)

## Dettagli componente {#component-details}

Per visualizzare i dettagli relativi a un componente specifico, tocca/fai clic sulla risorsa desiderata. Sono disponibili tre schede:

* **Proprietà**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Nella scheda Proprietà puoi:

   * Visualizzare le proprietà generali del componente.
   * Visualizzare come è stata definita [l’icona o l’abbreviazione](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) per il componente.

      * Facendo clic sull’origine dell’icona passerai al relativo componente.
   * Visualizzare il **tipo di risorsa** e il **Super Type della risorsa** (se definito) per il componente.

      * Facendo clic su Super Type della risorsa passerai al relativo componente.
   >[!NOTE]
   >
   >Because `/apps` is not editable at runtime, the Components Console is read-only.

* **Criteri**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **Utilizzo live**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >A causa della natura delle informazioni raccolte, può essere necessario qualche momento per combinarle e visualizzarle.

* **Documentazione**

   Se lo sviluppatore ha fornito la [documentazione per il componente](/help/sites-developing/developing-components.md#documenting-your-component), questa viene visualizzata nella scheda **Documentazione**. Se non è presente documentazione, la scheda **Documentazione** non verrà visualizzata.

   ![chlimage_1-305](assets/chlimage_1-305.png)

