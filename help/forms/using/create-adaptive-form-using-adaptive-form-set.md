---
title: Creare un modulo adattivo utilizzando un set di moduli adattivi
seo-title: Create an adaptive form using a set of adaptive forms
description: Con AEM Forms, è possibile unire i moduli adattivi per creare un singolo modulo adattivo di grandi dimensioni e comprenderne le funzioni.
seo-description: With AEM Forms, bring adaptive forms together to author a single large adaptive form, and understand its features.
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
feature: Adaptive Forms
exl-id: 969b0c11-adc7-476e-8c82-d444fccba984
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# Creare un modulo adattivo utilizzando un set di moduli adattivi {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

In un flusso di lavoro, ad esempio un’applicazione per l’apertura di un conto bancario, gli utenti compilano più moduli. Anziché chiedere loro di compilare un set di moduli, è possibile sovrapporre i moduli e creare un modulo di grandi dimensioni (modulo principale). Quando si aggiunge un modulo adattivo al modulo più grande, questo viene aggiunto come pannello (modulo figlio). Per creare un modulo principale è possibile aggiungere un set di moduli figlio. Puoi mostrare o nascondere i pannelli in base all’input dell’utente. I pulsanti del modulo principale, ad esempio invio e ripristino, sovrascrivono i pulsanti del modulo figlio. Per aggiungere un modulo adattivo nel modulo principale, puoi trascinare il modulo adattivo dal browser delle risorse (come i frammenti di modulo adattivo).

Le funzioni disponibili sono:

* Authoring indipendente
* Visualizzazione/eliminazione dei moduli appropriati
* Caricamento pigro

Funzioni quali authoring indipendente e caricamento lento migliorano le prestazioni rispetto all’utilizzo dei singoli componenti per creare il modulo principale.

>[!NOTE]
>
>Non è possibile utilizzare moduli/frammenti adattivi basati su XFA come moduli figlio o padre.

## Dietro le quinte {#behind-the-scenes}

È possibile aggiungere moduli adattivi basati su XSD e frammenti nel modulo principale. La struttura del modulo padre è la stessa del [qualsiasi modulo adattivo](/help/forms/using/prepopulate-adaptive-form-fields.md). Quando si aggiunge un modulo adattivo come modulo secondario, questo viene aggiunto come pannello nel modulo principale. I dati di un modulo figlio associato sono memorizzati nella `data`radice `afBoundData` sezione dello schema XML del modulo principale.

Ad esempio, i clienti compilano un modulo di richiesta. I primi due campi del modulo sono nome e identità. Il codice XML è:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
        </data>
    </afBoundData>
</afData>
```

Nell’applicazione è aggiunto un altro modulo che consente ai clienti di compilare il proprio indirizzo dell’ufficio. La radice dello schema del modulo figlio è `officeAddress`. Applica `bindref` `/application/officeAddress` o `/officeAddress`. Se `bindref`non viene fornito, il modulo figlio viene aggiunto come `officeAddress` sottoalbero. Vedere l&#39;XML del modulo seguente:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
        </data>
    </afBoundData>
</afData>
```

Se si inserisce un altro modulo che consente ai clienti di fornire l&#39;indirizzo della casa, applicare `bindref` `/application/houseAddress or /houseAddress.`Il codice XML si presenta così:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
            <houseAddress>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </houseAddress>
        </data>
    </afBoundData>
</afData>
```

Se desideri mantenere lo stesso nome della radice dello schema ( `Address`in questo esempio), utilizza i bindrefs indicizzati.

Ad esempio, applica caratteri binari `/application/address[1]` o `/address[1]` e `/application/address[2]` o `/address[2]`. XML del modulo:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <address>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
            <address>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
        </data>
    </afBoundData>
</afData>
```

È possibile modificare la struttura secondaria predefinita del modulo/frammento adattivo utilizzando `bindRef` proprietà. La `bindRef` consente di specificare il percorso che punta a una posizione nella struttura ad albero dello schema XML.

Se il modulo figlio non è associato, i relativi dati vengono memorizzati nella `data`radice `afUnboundData` sezione dello schema XML del modulo principale.

È possibile aggiungere più volte un modulo adattivo come modulo secondario. Assicurati che `bindRef` viene modificato correttamente in modo che ogni istanza utilizzata del modulo adattivo punti a una sottoradice diversa sotto la radice dati.

>[!NOTE]
>
>Se diversi moduli/frammenti sono mappati sulla stessa radice secondaria, i dati vengono sovrascritti.

## Aggiunta di un modulo adattivo come modulo figlio tramite il browser delle risorse {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Esegui le seguenti operazioni per aggiungere un modulo adattivo come modulo figlio utilizzando il browser risorse.

1. Aprire il modulo principale in modalità di modifica.
1. Nella barra laterale, fai clic su **Risorse** ![browser risorse](assets/assets-browser.png). In Risorse, seleziona **Modulo adattivo** dal menu a discesa.
   [ ![Selezione del modulo adattivo in Assets](assets/asset.png)](assets/asset-1.png)

1. Trascina il modulo adattivo da aggiungere come modulo figlio.
   [ ![Trascina il modulo adattivo nel sito](assets/drag-drop.png)](assets/drag-drop-1.png)Il modulo adattivo rilasciato viene aggiunto come modulo figlio.
