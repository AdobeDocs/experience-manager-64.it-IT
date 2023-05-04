---
title: NON PUBBLICARE, MA NON DELETE Personalizzazione dei modelli di frammenti di contenuto
seo-title: Customizing Content Fragment Models
description: I modelli per frammenti di contenuto possono essere personalizzati ed estesi.
seo-description: Content Fragment Models can be customized and extended.
page-status-flag: de-activated
uuid: 5bcfb5d8-37d4-4a0e-882d-bc8a1bac6ba7
contentOwner: AEM Docs
discoiquuid: 208225ee-9052-4a45-9cfd-f8d27d4d70ed
noindex: true
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---


# NON PUBBLICARE, MA NON DELETE Personalizzazione dei modelli di frammenti di contenuto{#do-not-publish-but-do-not-delete-customizing-content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’editor per modelli di frammento di contenuto è una procedura guidata basata su `Formbuilder`, ereditato da:

`granite/ui/components/foundation/form/formbuilder`

Questo componente dispone degli strumenti necessari per eseguire il rendering dell&#39;interfaccia di trascinamento dell&#39;editor modelli, completa di tipi di dati e proprietà per ciascuno di essi.

## Posizioni {#locations}

I modelli vengono salvati e creati in `/conf`, in una cartella contenente [Proprietà Modelli per frammenti di contenuto](/help/assets/content-fragments-models.md#enable-content-fragment-models) abilitato. Questa impostazione è visibile anche nella **Proprietà di configurazione**, accessibile dal **[Browser di configurazione](/help/sites-administering/configurations.md)**.

1. Passa al browser tramite **Strumenti**, **Generale**, **Browser di configurazione**
Ad esempio: 
`http://localhost:4502/libs/granite/configurations/content/view.html/conf`

1. Dal browser, seleziona la configurazione appropriata, quindi **Proprietà** dalla barra degli strumenti.

   Ad esempio, le proprietà `global`: `http://localhost:4502/libs/granite/configurations/content/edit.html/conf/global`

Nella console Modelli , tutte le cartelle con **Modelli per frammenti di contenuto** verrà visualizzata la proprietà . Passa a **Strumenti**, **Risorse**, **Modelli per frammenti di contenuto**; ad esempio, `http://localhost:4502/libs/dam/cfm/models/console/content/models.html/conf`.

Un utente può [creare un modello di frammento di contenuto](/help/assets/content-fragments-models.md#creating-a-content-fragment-model) utilizzando **Crea modello** procedura guidata **Crea** dalla console).

>[!CAUTION]
>
>You ***deve*** non modificare nulla nel `/libs` percorso.
>
>Questo perché il contenuto di `/libs` viene sovrascritto la prossima volta che aggiorni l’istanza (e può essere sovrascritto quando applichi un hotfix o un feature pack).

## Struttura di un modello {#structure-of-a-model}

Verrà creata una voce con questa struttura:

![cf-54](assets/cf-54.png)

* `../settings/dam/cfm/models`

   Tutti i modelli vengono salvati in sottocartelle di questa cartella.

* `jcr:content`

   Ogni modello contiene `jcr:content` nodo che:

   * contiene proprietà di informazioni sul modello quali `jcr:title`, `lastModified`, `lastModifiedBy`
   * di solito ha `sling:ResourceType` di `dam/cfm/models/console/components/data/entity/default`,

      con `sling:ResourceSuperType` di `dam/cfm/models/console/components/data/entity`

* `model`

   La `model` il nodo contiene una proprietà `dataTypesConfig`, utilizzato per determinare i tipi di dati utilizzati nell&#39;editor modelli.

* `items`

   Sotto la `items` vengono salvati tutti i tipi di dati aggiunti al modello (trascinati e rilasciati nell&#39;editor modelli). A ogni elemento viene assegnato un nome di nodo casuale, ma affinché l’editor dei frammenti di contenuto funzioni con questo modello, ogni elemento deve avere un `name` proprietà. Inoltre, su questo nodo vengono salvate tutte le proprietà di configurazione per un particolare tipo di dati, incluse le proprietà predefinite necessarie per il rendering dei componenti.

>[!CAUTION]
>
>Tutti i tipi di dati trascinati e rilasciati in un editor modelli, e come tali istanziati, **deve** hanno `name` proprietà immessa dall&#39;utente.
>
>Viene visualizzato come **Nome proprietà &amp;ast;** in **Proprietà** scheda dell&#39;editor modelli.

## Struttura dell&#39;Editor modelli {#structure-of-the-model-editor}

La **Editor modello frammento di contenuto** presenta due parti:

* Il pannello di anteprima o di visualizzazione sul lato sinistro, in cui è possibile rilasciare elementi. Tale comportamento:

   * Mostra un&#39;anteprima del **Tipo di dati** viene creata un&#39;istanza.
   * Consente l&#39;ordinamento all&#39;interno dell&#39;Editor modello.

* La **Tipi di dati**/**Proprietà** nel pannello a destra. Tale comportamento:

   * Mostra un elenco di tipi di dati che possono essere trascinati e istanziati.
   * Per l’editor di modelli preconfigurato, l’elenco è presente in:

      `/libs/settings/dam/cfm/models/formbuilderconfig/datatypes`

      <!-- Please uncomment when file is used
      This node contains all the data types currently supported in the model editor. For more information on how to configure the data types, see [Customizing Data Types for Content Fragment Models](/help/sites-developing/customizing-content-fragment-model-data-types.md).
      -->

   * Tutti i tipi di dati di cui è stato eseguito il rendering hanno due tag script che, una volta creata l’istanza, formano la visualizzazione (il componente di cui è stato eseguito il rendering sul lato sinistro) e il **Proprietà** , che definisce le proprietà che un utente può definire per un determinato componente.

>[!CAUTION]
>
>You ***deve*** non modificare nulla nel `/libs` percorso.
>
>Questo perché il contenuto di `/libs` viene sovrascritto la prossima volta che aggiorni l’istanza (e può essere sovrascritto quando applichi un hotfix o un feature pack).

<!-- Please uncomment when files are used
The properties on the right side define a form that is submitted directly into JCR under `/conf`; see the path in the example [Structure of a Model](/help/sites-developing/customizing-content-fragment-models.md#structure-of-a-model).
-->

Quando viene creata un’istanza di un tipo di dati, gli input di HTML vengono creati per ogni proprietà di cui è necessario eseguire il rendering in un frammento di contenuto. Ad esempio:

* **Nome proprietà &amp;ast;** ( `name`): funge da identificatore per i componenti

* **Rendering come** ( `metaType`) - il tipo di componente deve essere rappresentato come

* **Descrizione** ( `fieldDescription`) - descrizione del componente nel frammento di contenuto

* e altri.

