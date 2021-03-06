---
title: Creazione di temi modulo adattivi personalizzati
seo-title: Creazione di temi modulo adattivi personalizzati
description: Un tema modulo adattivo è una libreria AEM client utilizzata per definire gli stili (aspetto e aspetto) di un modulo adattivo. Scoprite come creare temi per moduli adattivi personalizzati.
seo-description: Un tema modulo adattivo è una libreria AEM client utilizzata per definire gli stili (aspetto e aspetto) di un modulo adattivo. Scoprite come creare temi per moduli adattivi personalizzati.
uuid: b25df10e-b07c-4e9d-a799-30f1c6fb3c44
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 437e6581-4eb1-4fbd-a6da-86b9c90cec89
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Creazione di temi modulo adattivo personalizzati {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
> AEM Forms fornisce la funzionalità [Editor tema](/help/forms/using/themes.md) per creare e modificare moduli adattivi [temi](/help/forms/using/themes.md). Eseguite i passaggi elencati in questo articolo, solo se avete effettuato l&#39;aggiornamento da una versione che non dispone di [Editor tema](/help/forms/using/themes.md) e disponete di un investimento esistente in temi creati utilizzando file Less/CSS (metodo editor pre-tema).

## Prerequisiti {#prerequisites}

* Conoscenza del framework LESS (Leaner CSS)
* Come creare una libreria client in Adobe Experience Manager
* [Creazione di un ](/help/forms/using/custom-adaptive-forms-templates.md) modello di modulo adattivo per l’utilizzo del tema creato

## Tema modulo adattivo {#adaptive-form-theme}

Un **tema modulo adattivo** è una libreria client AEM che consente di definire gli stili (aspetto e aspetto) di un modulo adattivo.

Potete creare un **modello adattivo** e applicare il tema al modello. Quindi utilizzate questo modello personalizzato per creare un **modulo adattivo**.

![Modulo adattivo e libreria client](assets/hierarchy.png)

## Per creare un tema modulo adattivo {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>La procedura seguente è descritta utilizzando nomi di esempio per AEM oggetti quali nodo, proprietà e cartelle.
>
>Se si seguono questi passaggi utilizzando i nomi, il modello risultante dovrebbe essere simile all&#39;istantanea seguente:

![Foresta a tema Modulo adattivo ](assets/thumbnail.png)
**snapshotFigura:Esempio di tema** *foresta*

1. Creare un nodo di tipo `cq:ClientLibraryFolder` sotto il nodo `/apps`.

   Ad esempio, creare il nodo seguente:

   `/apps/myAfThemes/forestTheme`

1. Aggiungete al nodo una proprietà stringa con più valori `categories` e impostatene il valore in modo appropriato.

   Ad esempio, impostare la proprietà su: `af.theme.forest`.

   ![Snapshot archivio CRX](assets/3-2.png)

1. Aggiungete due cartelle, `less` e `css`, e un file `css.txt` al nodo creato al punto 1:

   * `less` cartella: Contiene i file  `less` variabili in cui vengono definite le  `less` variabili e  `less mixins` che vengono utilizzate per gestire gli stili .css.

      Questa cartella è composta da `less` file variabili, `less` file mixin, `less` file che definiscono gli stili usando mixin e variabili. E tutti questi meno file vengono poi importati in stili.less.

   * `css`cartella: Contiene i file .css in cui vengono definiti gli stili statici da utilizzare nel tema.

   **Meno file** variabili: Si tratta dei file in cui potete definire o ignorare le variabili utilizzate per definire gli stili CSS.

   I moduli adattivi forniscono variabili OOOTB definite nei seguenti file .less:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   I moduli adattivi forniscono anche variabili di terze parti definite in:

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   È possibile utilizzare meno variabili fornite con i moduli adattivi, ignorare queste variabili o creare nuove variabili minori.

   >[!NOTE]
   >
   >Durante l&#39;importazione dei file del pre-processore minore, nell&#39;istruzione import specificare il percorso relativo dei file.

   Esempio di sostituzione delle variabili:

   ```
   @button-background-color: rgb(19, 102, 44);
   @button-border-color: rgb(19, 102, 44);
   @button-border-size: 0px;
   @button-padding: 10px 15px;
   @button-font-color: #ffffff;
   ```

   Per sovrascrivere le variabili `less`:

   1. Importa variabili di modulo adattivo predefinite:

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Quindi importate il file minore che include le variabili sostituite.

   Esempio di nuove definizioni di variabili:

   ```
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Meno file mixin:** È possibile definire le funzioni che accettano le variabili come argomenti. L&#39;output di queste funzioni sono gli stili risultanti. Usate questi mixin all&#39;interno di stili diversi, per evitare di ripetere stili CSS.

   I moduli adattivi forniscono mixaggi OOOTB definiti in:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/adaptiveforms-mixins.less`

   I moduli adattivi forniscono anche mixin di terze parti definiti in:

   * `/apps/clientlibs/fd/af/third-party/less/mixins.less`

   Definizione mixin campione:

   ```
   .rounded-corners (@radius) {
     -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
     -ms-border-radius: @radius;
     -o-border-radius: @radius;
     border-radius: @radius;
   }
   
   .border(@color, @type, @size) {
      border: @color @size @type;
   }
   ```

   **Styles.less File:** utilizzate questo file per includere tutti i file minori (variabili, mixin, stili) da utilizzare nella libreria client.

   Nel seguente file di esempio `styles.less`, l&#39;istruzione import può essere inserita in qualsiasi ordine.

   Le istruzioni per importare i seguenti file .less sono obbligatorie:

   * `globalvariables.less`
   * `layoutvariables.less`
   * `components.less`
   * `layouts.less`

   ```
   @import "../../../clientlibs/fd/af/guidetheme/common/less/globalvariables.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layoutvariables.less";
   @import "forestTheme-variables";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/components.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layouts.less";
   
   /* custom styles */
   
   .guidetoolbar {
     input[type="button"], button, .button {
       .rounded-corners (@button-radius);
       &:hover {
         background-color: @button-hover-bg-color;
       }
       &:focus {
         background-color: @button-focus-bg-color;
       }
     }
   }
   
   form {
       background-image: url(../images/forest.png);
    background-repeat: no-repeat;
    background-size: 100%;
   }
   ```

   Il percorso `css.txt` contiene i percorsi dei file .css da scaricare per la libreria.

   Esempio:

   ```
   #base=/apps/clientlibs/fd/af/third-party/css
   bootstrap.css
   
   #base=less
   styles.less
   
   #base=/apps/clientlibs/fd/xfaforms/xfalib/css
   datepicker.css
   listboxwidget.css
   scribble.css
   dialog.css
   ```

   >[!NOTE]
   >
   >Il file Styles.less non è obbligatorio. Ciò significa che non è necessario creare questo file, se non sono stati definiti stili, variabili o mixin personalizzati.
   >
   >Tuttavia, se non create un file style.less, nel file css.txt dovete rimuovere il commento dalla riga seguente:
   >
   >**`#base=less`**
   >
   >E commenta la seguente riga:
   >
   >**`styles.less`**

## Per utilizzare un tema in un modulo adattivo {#to-use-a-theme-in-an-adaptive-form}

Dopo aver creato un tema modulo adattivo, effettuare le seguenti operazioni per utilizzare il tema in un modulo adattivo:

1. Per includere il tema creato in [per creare un tema modulo adattivo](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p), creare una pagina personalizzata di tipo `cq:Component`.

   Esempio, `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Aggiungete una proprietà `sling:resourceSuperType` e impostatene il valore come `fd/af/components/page/base`.

      ![Snapshot archivio CRX](assets/1-2.png)

   1. Per utilizzare un tema nella pagina, è necessario aggiungere al nodo un file library.jsp prevalente.

      Quindi, potete importare il tema creato in Per creare una sezione tema modulo adattivo di questo articolo.

      Il frammento di codice di esempio seguente importa il tema `af.theme.forest`.

      ```
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Facoltativo**: Nella pagina personalizzata, ignorate header.jsp, piè di pagina.jsp e body.jsp, a seconda delle necessità.

1. Creare un modello personalizzato (ad esempio: `/apps/myAfCustomizations/myAfTemplates/forestTemplate`) il cui jcr:content punta alla pagina personalizzata creata nel passaggio precedente (ad esempio: `myAfCustomizations/myAfPages/forestPage)`.

   ![Snapshot archivio CRX](assets/2-1.png)

1. Creare un modulo adattivo utilizzando il modello creato nel passaggio precedente. L&#39;aspetto del modulo adattivo è definito dal tema creato in Per creare una sezione del tema del modulo adattivo in questo articolo.

