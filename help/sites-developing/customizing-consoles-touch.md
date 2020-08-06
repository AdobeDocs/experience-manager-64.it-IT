---
title: Personalizzazione delle console
seo-title: Personalizzazione delle console
description: AEM offre diversi metodi per personalizzare le console dell’istanza di authoring
seo-description: AEM offre diversi metodi per personalizzare le console dell’istanza di authoring
uuid: f10cea87-ef8a-468e-94ca-89a1017dcf44
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 221ed05b-855d-4dc2-9df6-12fdeabb157a
translation-type: tm+mt
source-git-commit: 1dc15f323dc30d5730e2af6c0e762d623523870d
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 1%

---


# Personalizzazione delle console{#customizing-the-consoles}

>[!CAUTION]
>
>Questo documento descrive come personalizzare le console nell’interfaccia touch moderna e non applicabile all’interfaccia classica.

AEM offre diversi metodi per personalizzare le console (e la funzionalità [di authoring delle](/help/sites-developing/customizing-page-authoring-touch.md)pagine) dell’istanza di authoring.

* Clientlibs

   Clientlibs consente di estendere l&#39;implementazione predefinita per realizzare nuove funzionalità, riutilizzando le funzioni, gli oggetti e i metodi standard. Quando si personalizzano, è possibile creare clientlib personalizzate in `/apps.` Ad esempio, può contenere il codice richiesto per il componente personalizzato.

* Sovrapposizioni

   Le sovrapposizioni si basano sulle definizioni dei nodi e consentono di sovrapporre la funzionalità standard (in `/libs`) con la propria funzionalità personalizzata (in `/apps`). Quando create una sovrapposizione, non è necessaria una copia 1:1 dell’originale, in quanto la fusione delle risorse di sling consente l’ereditarietà.

che possono essere utilizzati in molti modi per estendere le console AEM. Di seguito è riportata una piccola selezione (ad alto livello).

>[!NOTE]
>
>Per ulteriori informazioni, consulta:
>
>* Utilizzo e creazione di [clientlibs](/help/sites-developing/clientlibs.md).
>* Utilizzo e creazione di [sovrapposizioni](/help/sites-developing/overlays.md).
>* [GRANITE](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)

>
>
Questo argomento è trattato anche nella sessione [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html) - Personalizzazione dell&#39;interfaccia [utente per AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).

>[!CAUTION]
>
>Non ***devi*** cambiare nulla nel `/libs` percorso.
>
>Questo perché il contenuto di `/libs` viene sovrascritto al successivo aggiornamento dell’istanza (e potrebbe essere sovrascritto quando si applica un hotfix o un feature pack).
>
>Il metodo consigliato per la configurazione e altre modifiche è:
>
>1. Ricreare l&#39;elemento richiesto (ovvero come esiste in `/libs`) in `/apps`
   >
   >
1. Apportare modifiche all&#39;interno `/apps`

>



Ad esempio, è possibile sovrapporre le seguenti posizioni all’interno della `/libs` struttura:

* console (tutte le console basate sulle pagine dell’interfaccia utente Granite); ad esempio:

   * `/libs/wcm/core/content`

<!-- Needs a review by Engineering -->
<!--
* secondary (inner) rails; for example:

    * `/libs/wcm/core/content/search`

* toolbar(s) (dependent on console; for example sites):

    * default 

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/default`

    * selection mode

      `/libs/wcm/core/content/sites/jcr:content/body/content/header/items/selection`

* help menu options (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/help`

* information shown on the card view (dependent on console; for example sites):

    * `/libs/wcm/core/content/sites/jcr:content/body/content/content/items/childpages`

-->
>[!NOTE]
>
>Per ulteriori suggerimenti e strumenti, consulta l’articolo della Knowledge Base [Risoluzione dei problemi](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)AEM TouchUI.

<!-- Needs a review by Engineering -->
<!--
## Code Samples {#code-samples}

Various packages have been made available on Github. These provide code samples related to the tasks covered on this page.

### aem-admin-extension-new-console {#aem-admin-extension-new-console}

`aem-admin-extension-new-console` is a sample package showing how to [create a new AEM 6 console](#create-a-custom-console). This package provides a UI for managing [Launches](/help/sites-authoring/launches.md) and adds a link in the navigation:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)

### aem-admin-extension-customize-sites {#aem-admin-extension-customize-sites}

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Create a Custom Console {#create-a-custom-console}

1. You can create a custom console with related actions; for example, Launches at the top level (below Sites):

   This involves:

    * creating the root space definition of your new console ``; for example:

        * `/apps/<yourProject>/admin/ext/launches`

    * this can contain (according to requirements):

        * the corresponding [clientlibs](/help/sites-developing/clientlibs.md) for custom actions and `less`/ `css` definitions

            * `/apps/<yourProject>/admin/ext/launches/clientlibs`

        * components that need to be redefined/adjusted; for example, the breadcrumbs, datasource and the launch

            * `/apps/<yourProject>/admin/ext/launches/components`

        * the Granite UI page resource:

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content`

              property: `sling:resourceType`

        * the page definition of the console

            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/head`
            * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body`

   ![chlimage_1-236](assets/chlimage_1-236.png)

   To use the new console (for example in the [rail for navigation](#add-new-navigation-option-to-rail)) an ID is used, so that it can be explicitly referenced. The ID is used to connect the console and its navigation definition. The ID is defined in the `rail` node of the page; for example, for the Sites console:

    * the rail node is: 

      `/libs/wcm/core/content/sites/jcr:content/body/rail`

        * here the `currentId` property is defined: 

          `currentId` = `cq-sites`

   For the Launches console example:

    * the node is:

        * `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`

    * with the following properties:

        * `currentId` = `cq-launches`
        * `sling:resourceType` = `granite/ui/components/endor/navcolumns`
        * `srcPath` = `cq/core/content/nav`
-->

## Personalizzazione della visualizzazione predefinita per una console {#customizing-the-default-view-for-a-console}

Potete personalizzare la visualizzazione predefinita (colonna, scheda, elenco) per una console:

1. Potete riordinare le viste sovrapponendo la voce richiesta da sotto:

   `/libs/wcm/core/content/sites/jcr:content/views`

   La prima voce sarà quella predefinita.

   I nodi disponibili sono correlati alle opzioni di visualizzazione disponibili:

   * `column`
   * `card`
   * `list`

1. Ad esempio, in una sovrapposizione per un elenco:

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Definire la proprietà seguente:

   * **Nome**: `sling:orderBefore`
   * **Tipo**: `String`
   * **Valore**: `column`

<!-- Needs a review by Engineering -->
<!--
`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-customize-sites project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-customize-sites/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
### Add New Navigation Option to Rail {#add-new-navigation-option-to-rail}

1. You can add a navigation entry in the rail (for example, a [custom console](#create-a-custom-console) such as Launches).

   To do this, you create an overlay of:

   `/libs/cq/core/content/nav`

   In the `/apps` overlay:

   `/apps/cq/core/content/nav`

   Create the new nodes and properties:

   ![chlimage_1-237](assets/chlimage_1-237.png)

    * Extend navigation:

        * `/apps/cq/core/content/nav/launches`

    * Specify location in the tree:

        * property: `sling:orderBefore`

    * To create the connection, the `id` property references (i.e. must be the same as) the `currentID` property [for the appropriate console](#create-a-custom-console):

        * property: `id`
        * value: same as for your console (e.g. `cq-launches`) 

          for example: the same value as the `currentId` property on:

          `/apps/<yourProject>/admin/ext/launches/content/jcr:content/body/rail`
-->

## Aggiungi nuova azione alla barra degli strumenti {#add-new-action-to-the-toolbar}

1. Potete creare componenti personalizzati e includere le librerie client corrispondenti per le azioni personalizzate. Ad esempio, un&#39;azione **Promote to Twitter** all&#39;indirizzo:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   È quindi possibile collegarlo a un elemento della barra degli strumenti presente nella console:

   `/apps/<yourProject>/admin/ext/launches`

   Ad esempio, in modalità di selezione:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

## Limitare un&#39;azione barra degli strumenti a un gruppo specifico {#restrict-a-toolbar-action-to-a-specific-group}

1. Potete utilizzare una condizione di rendering personalizzata per sovrapporre l&#39;azione standard e imporre condizioni specifiche che devono essere soddisfatte prima del rendering.

   Ad esempio, create un componente per controllare le condizioni di rendering in base al gruppo:

   `/apps/myapp/components/renderconditions/group`

1. Per applicare queste opzioni all’azione Crea sito nella console Siti:

   `/libs/wcm/core/content/sites`

   Create la sovrapposizione:

   `/apps/wcm/core/content/sites`

1. Quindi aggiungete la condizione di rendering per l’azione:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Utilizzando le proprietà di questo nodo è possibile definire le `groups` autorizzazioni per eseguire l&#39;azione specifica; ad esempio, `administrators`

<!-- Needs a review by Engineering -->
<!--
## Remove Access to Navigation Option on Rail {#remove-access-to-navigation-option-on-rail}

1. You can rename a navigation entry in the rail by overlaying the required entry from under:

   `/libs/cq/core/content/nav`

   The nodes available correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`

1. For example, on a overlay at:

   `/apps/cq/core/content/nav/sites`

   Define the following property:

    * **Name**: `sling:hideResource`
    * **Type**: `String` 
    * **Value**: `true`

`aem-admin-extension-customize-sites` is a sample package showing how to customize an existing AEM 6 admin console. This package provides updates to Sites administration:

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-admin-extension-new-console project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-admin-extension-new-console/archive/master.zip)
-->

<!-- Needs a review by Engineering -->
<!--
## Restrict Access to Navigation Option on Rail {#restrict-access-to-navigation-option-on-rail}

You can restrict access to a navigation option using ACLs:

1. Open the [user and/or group management](/help/sites-administering/security.md) and select the user/group you want to restrict access for.

   >[!NOTE]
   >
   >Avoid assigning/restricting permissions on a user-by-user basis. It is [recommended to use groups](/help/sites-administering/security.md#best-practices).

1. Remove access [permissions](/help/sites-administering/security.md#permissions) to the appropriate node(s) under `/libs/cq/core/content/nav/sites`. These correlate to the navigation options in the rail:

    * `projects`
    * `sites`
    * `assets`
    * `apps`
    * `forms`
    * `screens`
    * `personalization`
    * `commerce`
    * `tools`
    * `communities`
-->

## Personalizzazione delle colonne nella vista Elenco {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Questa funzione è ottimizzata per le colonne di campi di testo; per altri tipi di dati è possibile sovrapporre `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

<!-- Needs a review by Engineering -->
<!--
CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-sites-extension-listview-columns project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns)
* Download the project as [a ZIP file](https://github.com/Adobe-Marketing-Cloud/aem-sites-extension-listview-columns/archive/master.zip)
-->

Per personalizzare le colonne nella vista a elenco:

1. Sovrapporre l’elenco delle colonne disponibili.

   * Sul nodo:

      `/apps/wcm/core/content/common/availablecolumns`

   * Aggiungete le nuove colonne o rimuovete quelle esistenti.
   Per ulteriori informazioni, consultate [Utilizzo delle sovrapposizioni (e Sling Resource Merger)](/help/sites-developing/overlays.md) .

1. Facoltativamente:

   * Se si desidera collegare dati aggiuntivi, è necessario scrivere un ` [PageInforProvider](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)` con un

      `pageInfoProviderType` proprietà.
   Ad esempio, vedete la classe/pacchetto collegato (da GitHub) di seguito.

1. È ora possibile selezionare la colonna nel configuratore colonna della vista a elenco.

## Risorse filtro {#filtering-resources}

Quando si utilizza una console, un caso comune è quando l’utente deve selezionare una delle risorse (ad esempio pagine, componenti, risorse ecc.). Può assumere la forma di un elenco, ad esempio da cui l’autore deve scegliere un elemento.

Per mantenere l&#39;elenco a dimensioni ragionevoli e anche pertinente al caso d&#39;uso, è possibile implementare un filtro sotto forma di predicato personalizzato. Consultate [questo articolo](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) per i dettagli.
