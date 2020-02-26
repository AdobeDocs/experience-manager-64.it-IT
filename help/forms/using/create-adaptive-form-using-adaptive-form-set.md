---
title: Creare un modulo adattivo utilizzando un set di moduli adattivi
seo-title: Creare un modulo adattivo utilizzando un set di moduli adattivi
description: 'Con AEM Forms, è possibile unire moduli adattivi per creare un singolo modulo adattivo di grandi dimensioni e comprenderne le funzioni. '
seo-description: 'Con AEM Forms, è possibile unire moduli adattivi per creare un singolo modulo adattivo di grandi dimensioni e comprenderne le funzioni. '
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Creare un modulo adattivo utilizzando un set di moduli adattivi {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

## Panoramica {#overview}

In un flusso di lavoro, ad esempio un&#39;applicazione per l&#39;apertura di un conto bancario, gli utenti possono compilare più moduli. Anziché chiedere loro di compilare un set di moduli, è possibile raggruppare i moduli e creare un modulo di grandi dimensioni (modulo principale). Quando si aggiunge un modulo adattivo al modulo più grande, questo viene aggiunto come pannello (modulo figlio). È possibile aggiungere un set di moduli secondari per creare un modulo principale. Potete visualizzare o nascondere i pannelli in base all’input dell’utente. I pulsanti del modulo principale, ad esempio Invia e Reimposta, sovrascrivono i pulsanti del modulo figlio. Per aggiungere un modulo adattivo al modulo principale, è possibile trascinare il modulo adattivo dal browser delle risorse (come i frammenti di modulo adattivo).

Le funzioni disponibili sono:

* Authoring indipendente
* Visualizzazione/nascondere i moduli appropriati
* Caricamento pigro

Funzioni quali authoring indipendente e caricamento lento migliorano le prestazioni rispetto all’utilizzo di singoli componenti per creare il modulo principale.

>[!NOTE]
>
>Non è possibile utilizzare moduli/frammenti adattivi basati su XFA come moduli figlio o padre.

## Dietro le quinte {#behind-the-scenes}

È possibile aggiungere moduli adattivi e frammenti XSD nel modulo principale. La struttura del modulo principale è identica a [qualsiasi modulo](/help/forms/using/prepopulate-adaptive-form-fields.md)adattivo. Quando si aggiunge un modulo adattivo come modulo secondario, questo viene aggiunto come pannello nel modulo principale. I dati di un modulo figlio associato sono memorizzati nella `data`directory principale della `afBoundData` sezione dello schema XML del modulo padre.

Ad esempio, i clienti compilano un modulo di richiesta. I primi due campi del modulo sono nome e identità. XML è:

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

Nell&#39;applicazione è possibile aggiungere un altro modulo che consenta ai clienti di compilare l&#39;indirizzo dell&#39;ufficio. La radice dello schema del modulo figlio è `officeAddress`. Applica `bindref` `/application/officeAddress` o `/officeAddress`. Se non `bindref`viene fornito, il modulo secondario viene aggiunto come `officeAddress` sottostruttura. Vedere l&#39;XML del modulo seguente:

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

Se si inserisce un altro modulo che consente ai clienti di fornire l&#39;indirizzo della casa, applicare `bindref` l&#39;aspetto `/application/houseAddress or /houseAddress.`XML:

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

Se si desidera mantenere lo stesso nome della radice dello schema ( `Address`in questo esempio), utilizzare bindrefs indicizzati.

Ad esempio, potete applicare bindrefs `/application/address[1]` o `/address[1]` e `/application/address[2]` o `/address[2]`. Il codice XML del modulo è:

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

È possibile modificare la struttura secondaria predefinita del modulo/frammento adattivo utilizzando la `bindRef` proprietà . La `bindRef` proprietà consente di specificare il percorso che punta a una posizione nella struttura ad albero dello schema XML.

Se il modulo figlio non è associato, i relativi dati vengono memorizzati nella `data`directory principale della `afUnboundData` sezione dello schema XML del modulo padre.

È possibile aggiungere più volte un modulo adattivo come modulo secondario. Assicurarsi che la modifica `bindRef` sia corretta in modo che ogni istanza utilizzata del modulo adattivo punti a un sottoprincipale diverso sotto la radice dei dati.

>[!NOTE]
>
>Se diversi moduli/frammenti sono mappati alla stessa subroot, i dati vengono sovrascritti.

## Aggiunta di un modulo adattivo come modulo secondario tramite il browser delle risorse {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Per aggiungere un modulo adattivo come modulo secondario mediante il browser delle risorse, effettuate le seguenti operazioni.

1. Aprire il modulo principale in modalità di modifica.
1. Nella barra laterale, fate clic su **Risorse** ![nel browser](assets/assets-browser.png)Risorse. In Risorse, seleziona Modulo **** adattivo dall’elenco a discesa.
   [ ![Selezione del modulo adattivo in Risorse](assets/asset.png)](assets/asset-1.png)

1. Trascinare il modulo adattivo da aggiungere come modulo secondario.
   [ Trascinare ![il modulo adattivo nel](assets/drag-drop.png)](assets/drag-drop-1.png)sitoIl modulo adattivo rilasciato viene aggiunto come modulo secondario.

