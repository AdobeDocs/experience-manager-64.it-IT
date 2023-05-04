---
title: Console Componenti
seo-title: Components Console
description: Console Componenti
seo-description: null
uuid: 308b7fa1-9525-43f3-8c15-1076485b3f8c
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8774c38a-abd2-4dc2-868e-d6760c96f3f6
exl-id: fa583a06-e75c-41de-a977-7e459ab8bca9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 49%

---

# Console Componenti{#components-console}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La console Componenti consente di consultare tutti i componenti definiti nell’istanza e di visualizzare le informazioni chiave di ciascun componente.

È accessibile da **Strumenti** -> **Generale** -> **Componenti**. Nella console sono disponibili le viste a schede e a elenco. Poiché non esiste una struttura ad albero per i componenti, la vista a colonne non è disponibile.

![chlimage_1-301](assets/chlimage_1-301.png)

>[!NOTE]
>
>La console Componenti mostra tutti i componenti del sistema. Il [browser Componenti](/help/sites-authoring/author-environment-tools.md#components-browser) mostra i componenti disponibili per gli autori e nasconde eventuali gruppi di componenti che iniziano con un punto ( `.`).

## Ricerca {#search-features}

L’icona **Solo contenuto** (in alto a sinistra) permette di aprire il pannello **Ricerca** per cercare e/o filtrare i componenti:

![chlimage_1-302](assets/chlimage_1-302.png)

## Dettagli dei componenti {#component-details}

Per visualizzare i dettagli di un componente specifico, tocca o fai clic sulla risorsa richiesta. Sono disponibili tre schede:

* **Proprietà**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Nella scheda Proprietà puoi:

   * Visualizzare le proprietà generali del componente.
   * Visualizza come [è stata definita un&#39;icona o un&#39;abbreviazione](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) per il componente.

      * Fai clic sull’origine dell’icona per passare al componente.
   * Visualizza la **Tipo di risorsa** e **Super Type risorsa** (se definito) per il componente.

      * Facendo clic sul Super Type della risorsa passerai al relativo componente.
   >[!NOTE]
   >
   >Poiché `/apps` non è modificabile in fase di esecuzione, la console Componenti è disponibile in sola lettura.

* **Criteri**

   ![chlimage_1-303](assets/chlimage_1-303.png)

* **Utilizzo live**

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!CAUTION]
   >
   >A causa della natura delle informazioni raccolte, può essere necessario qualche momento per combinarle e visualizzarle.

* **Documentazione**

   Se lo sviluppatore ha fornito [documentazione relativa al componente](/help/sites-developing/developing-components.md#documenting-your-component), apparirà sul **Documentazione** scheda . Se la documentazione non è disponibile, la scheda **Documentazione** non verrà visualizzata.

   ![chlimage_1-305](assets/chlimage_1-305.png)
