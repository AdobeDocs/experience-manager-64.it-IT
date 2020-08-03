---
title: Note sulla versione AEM 3D
seo-title: Note sulla versione AEM 3D
description: Note sulla versione specifiche per il contenuto 3D in  risorse di Adobe Experience Manager.
seo-description: Note sulla versione specifiche per il contenuto 3D in  risorse di Adobe Experience Manager.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
content-type: reference
topic-tags: 3D
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 0%

---


# Note sulla versione AEM 3D {#aem-d-release-notes}

AEM-6.4-DynamicMedia-3D versione 3.1.0 (10 ottobre 2018)

Il AEM feature pack 3D consente il supporto del contenuto 3D nei AEM Assets. Offre funzionalità di caricamento, gestione, anteprima e rendering delle risorse 3D. Il supporto per la visualizzazione e il rendering è ottimizzato per singoli oggetti (anziché per scene complesse con più oggetti).

AEM 3D supporta  tipi di risorse Adobe Dimension (Dn) e glTF. L’implementazione per questi tipi di risorse è sostanzialmente diversa da quella per i tipi 3D tradizionali descritti nella presente documentazione. Consultate [Utilizzo di  risorse](/help/assets/working-dimension-assets.md)Adobe Dimension.

Sono incluse anche le integrazioni lato server con Autodesk® Maya® (solo Windows). Quando si installa e si configura Maya sullo stesso server AEM si abilita il supporto per i formati di file Maya nativi, compreso il rendering di alta qualità con il plug-in NVIDIA® mental ray® Standalone per Maya. L&#39;installazione e la configurazione di 3ds Max sul server abilita il supporto per il formato di file nativo .max.

Consulta [Integrazione con Autodesk Maya](/help/assets/integrate-maya-with-3d.md).

Consultate anche [Installazione e configurazione AEM risorse](/help/assets/install-config-3d.md) 3D e impostazioni [di configurazione](/help/assets/advanced-config-3d.md)avanzate.

Consultate anche [Utilizzo di risorse](/help/assets/assets-3d.md)3D.

## Requisiti di sistema {#system-requirements}

**Prerequisiti**

* AEM 6.4.2 (AEM 6.4 con Service Pack 2)
* Autodesk® FBX® SDK 2016.1.2

**Sistemi operativi supportati**

* Microsoft Windows 2012 Server o versione successiva
* Apple OS X El Capitan 10.6 o versione successiva
* RedHat Enterprise Linux 7.3

**Browser Web supportati per AEM Assets**

* Google Chrome 53 o versione successiva (consigliato).
* Apple Safari 9.1 o versione successiva.
* Firefox 48 o versione successiva.
* Microsoft Edge 25.10586 o versione successiva.

Altri browser potrebbero non supportare la visualizzazione interattiva di contenuto 3D in AEM. Solo Google Chrome supporta le ombre proiettate in Anteprima.

**Requisiti hardware e raccomandazioni**

* CPU - L&#39;elaborazione e il rendering 3D sono molto esigenti sulla CPU di un computer. Si consiglia pertanto di utilizzare un server contemporaneo con almeno otto core CPU.
* Memoria: si consiglia un minimo di 32 GB.
* Storage di massa - È consigliabile un&#39;elevata larghezza di banda per l&#39;archiviazione SSD.

   Al momento del caricamento, le risorse 3D vengono convertite in un formato proprietario per una visualizzazione rapida e interattiva. A seconda del tipo di risorsa 3D, è necessario uno spazio di archiviazione pari a 2-3 volte la dimensione della risorsa 3D caricata.

Consultate anche [Utilizzo di risorse](/help/assets/assets-3d.md)3D.

## Installazione e configurazione AEM 3D {#installing-and-configuring-aem-d}

See [Installing and configuring AEM 3D](/help/assets/install-config-3d.md).

Vedi anche [Integrazione AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md) e [Integrazione AEM 3D con Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## Formati di file 3D supportati {#supported-d-file-formats}

| Formato | Descrizione | Piattaforme | Note |
|--- |--- |--- |--- |
| DN |  Adobe Dimension | Tutti i bundle  | Richiede l&#39;accesso a un servizio di conversione basato su cloud. |
| GLTZ | Zipped gITF | Tutti i bundle  |  |
| GLB | Binary gITF | Tutti i bundle  | Solo download (le rappresentazioni GLB vengono create per le risorse DN). |
| OBJ | Wavefront OBJ 3D | Tutti i bundle  |  |
| FBX | Autodesk FBX (Kaydara Filmbox) | Tutti i bundle  | L’SDK Autodesk FBX deve essere installato sul nodo Author. |
| MA, MB | Autodesk nativo Maya | Solo Windows | Autodesk Maya è richiesto sul nodo Autore per abilitare questi formati di file. Consultate [Integrazione AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| JT | Siemens PLM Open CAD | Solo Windows | Autodesk Maya è richiesto sul nodo Autore per abilitare questi formati di file. Consultate [Integrazione AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| * | È possibile abilitare ulteriori formati di input 3D supportati da Autodesk Maya. Consultate [Abilitazione di formati aggiuntivi supportati da Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya). | Solo Windows | Autodesk Maya è richiesto sul nodo Autore per abilitare questi formati di file. Consultate [Integrazione AEM 3D con Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| MAX | Autodesk nativo 3ds Max | Solo Windows | Autodesk 3ds Max è richiesto nel nodo autore per abilitare questo formato di file. Consultate [Integrazione AEM 3D con Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md). |

## Miglioramenti e nuove funzioni {#enhancements-and-new-features}

Versione 3.0

* Supporto per il formato di file nativo Autodesk 3ds Max.
* Diverse modifiche e correzioni di bug per migliorare stabilità, qualità ed esperienza utente.
* Impostazioni di configurazione spostate in `/libs/settings/dam/v3d/`

Versione 3.1

* Supporto limitato per il formato di file nativo  Adobe Dimension (.dn).
* Un nuovo visualizzatore 3D per le risorse glTF.
* Una nuova interfaccia per un servizio di conversione basato su cloud  gestito dal Adobe ospitato in  Amazon AWS. Inizialmente, questo servizio converte solo dai formati Dn a glTF.

## Restrizioni e problemi noti {#restrictions-and-known-issues}

### Supporto per  Adobe Dimension {#adobe-dimension-support}

* Questa versione di AEM3D ha un supporto limitato per i file .dn creati con  Adobe Dimension.
* Durante l&#39;elaborazione del caricamento, AEM utilizza un servizio di conversione basato su cloud  ospitato dal Adobe per creare una rappresentazione GlTF dal file nativo .dn. È necessario accedere al servizio di conversione e selezionare  endpoint Amazon AWS.
* È disponibile un nuovo visualizzatore GlTF che supporta la visualizzazione delle risorse Dn in AEM Assets e in Siti/Schermi. Il supporto per le fasi nel visualizzatore non è ancora disponibile.
* I modelli Dn possono incorporare luci e sfondi IBL visualizzati, se presenti. In alternativa, il visualizzatore applica l’illuminazione predefinita, un colore di sfondo predefinito o entrambi.
* Il rendering di alta qualità per le risorse Dn non è ancora disponibile.
* Le dipendenze come le mappe di texture sono incorporate nelle risorse Dn e non possono essere gestite esplicitamente in AEM.

### Compatibilità {#compatibility}

* **L&#39;esecuzione come servizio Windows non è supportata (solo Windows)** . Questo potrebbe funzionare ma non è stato testato.
* **Dynamic Media** ( `dynamicmedia-scene7` modalità) - La compatibilità di AEM3D con la nuova soluzione Dynamic Media rilasciata con AEM 6.4 non è ancora completamente verificata. Se Dynamic Media e AEM3D vengono distribuiti insieme, si consiglia di inserire risorse 3D e le relative dipendenze solo in un&#39;area dell&#39;archivio AEM Assets che non è assegnata ad Dynamic Media. Questa raccomandazione è particolarmente importante per i file TIFF a 32 bit che sono richiesti per le fasi 3D ma non sono supportati da Dynamic Media.

### Generale {#general}

* **Collegamento** Risolvi dipendenze - Questa scelta rapida è disponibile nella vista a schede sulle risorse 3D. Le schede delle risorse nella vista a schede mostrano il banner &quot;Dipendenze non risolte&quot;. Il collegamento consente di aprire la scheda Proprietà **** base invece della scheda **Dipendenze** . Soluzione: passare manualmente alla scheda Dipendenze.

* **Selettore dello stage non disponibile** : le risorse 3D che includono luci vengono etichettate automaticamente da AEM come fasi 3D. Nella visualizzazione Dettagli non è disponibile il selettore Staggi. Per contrassegnare una risorsa 3D come oggetto 3D, andate a Proprietà **** di base, modificate Classe **** risorsa in Oggetto **** 3D e fate clic su **Salva**.

* **Download di risorse 3D con dipendenze e rappresentazioni** : quando si scaricano risorse 3D da AEM con entrambe le **dipendenze** e le rappresentazioni **** selezionate, il download include non solo le rappresentazioni della risorsa 3D principale, ma anche quelle di tutte le persone dipendenti.

* **Integrazione** Autodesk 3ds Max - Al momento il rendering con 3ds Max non è supportato.

### Limitazioni per i tipi di file {#file-type-restrictions}

* **File** Mathematica (.ma) - I file Mathematica usano lo stesso suffisso di file dei file Maya nativi. Quando il Feature Pack è installato e il formato di file Maya .ma è abilitato, AEM3D tenta di assimilare i file Mathematica come file Maya non riesce. Tali risorse visualizzano un banner di errore nella vista a schede.

* **File** di immagini Targa (.tga) - I file di modelli 3D precedenti possono includere riferimenti a file TGA. Questo formato non è supportato da AEM.  Adobe consiglia di convertire tali file in un formato diverso prima di caricare le risorse 3D in AEM.
* **Immagini** HDR - Le immagini HDR vengono utilizzate per fasi con illuminazione basata sulle immagini (IBL). Al momento, sono supportate solo immagini TIFF a 32 bit.
* **Immagini** TIFF a 32 bit - Le immagini TIFF a 32 bit vengono utilizzate per gli stadi con illuminazione basata sulle immagini. AEM non supporta la creazione di rappresentazioni per queste risorse, generando miniature vuote e non è possibile visualizzare l’anteprima. La risorsa funziona ancora correttamente se utilizzata con un passaggio IBL.
* **File** Autodesk 3ds Max (.max) - Se Autodesk 3ds Max è installato e configurato sui nodi Author, AEM supporta l&#39;assimilazione e la conversione di file .max. Al momento non è supportato l’utilizzo di file .max come fasi.

### Risoluzione dipendenza automatica {#automatic-dependency-resolution}

* **Dipendenze dei file non risolte dopo il caricamento** : quando risorse 3D e i relativi dipendenti vengono caricati con la stessa operazione di caricamento, è possibile che alcuni dipendenti non vengano risolti automaticamente. Questo problema è più probabile se i file dipendenti sono di grandi dimensioni. Per risolvere il problema, accedete alla pagina **Proprietà/Dipendenze** della risorsa che mostra i dipendenti non risolti dopo il caricamento. È ora necessario visualizzare i dipendenti non risolti in precedenza. Fate clic su **Salva** per finalizzare la risorsa. Per evitare questo problema in futuro, potete caricare tutti i dipendenti in una transazione separata prima di caricare gli oggetti 3D.

* **Sensibilità** alle maiuscole/minuscole: la risoluzione automatica delle dipendenze tenta di far corrispondere i nomi dei file in modo sensibile alle maiuscole/minuscole. Ad esempio, se la dipendenza originale trovata nella risorsa 3D è `image.jpg`, la dipendenza viene risolta in una risorsa denominata `Image.jpg`, `image.JPG`o in qualsiasi altra variante di caso.

### Fasi 3D {#d-stages}

* **Miniature per gli stadi** - Le miniature generate automaticamente per gli stadi potrebbero non rappresentare l’area di visualizzazione con precisione.
* **Geometria dello stage per gli stadi** non IBL - Il renderer rapido di perfezionamento non esegue il rendering della geometria da stadi con illuminazione non IBL, inclusi sfondi e piani di terra. Tale geometria viene ancora visualizzata in modo ragionevole nella visualizzazione Dettagli della risorsa (anteprima 3D).

* **Fasi FBX con illuminazione** IBL - È possibile caricare le fasi FBX con illuminazione IBL. Tuttavia, il formato FBX non dispone di disposizioni per trasferire il nome dell’immagine IBL. Di conseguenza, la risoluzione delle dipendenze del file non riesce. L’immagine IBL deve essere assegnata manualmente all’area di visualizzazione dopo il caricamento. È possibile assegnare la stessa immagine TIFF a 32 bit alle tre dipendenze che sono **Diffuse Lighting Environment Image**, **Reflection Environment Image** e **Background Environment Image**, oppure è possibile assegnare immagini diverse.

* **Immagine di sfondo delle fasi** IBL - Per alcune scene IBL, l&#39;immagine di sfondo potrebbe presentare una qualità scadente, ad esempio troppo luminosa o troppo sfocata. Per massimizzare la qualità visiva dello sfondo dell&#39;immagine delle fasi IBL,  Adobe consiglia di preparare un&#39;immagine JPEG a 8 bit ad alta risoluzione separata e di collegarla allo stadio IBL come immagine **dell&#39;ambiente di** sfondo.

* **Immagine nera durante il rendering con Maya con un passaggio** IBL - È probabile che Maya non trovi la dipendenza dall’immagine IBL perché l’immagine IBL originale a cui fa riferimento l’area di visualizzazione è stata sostituita da un’immagine con un nome diverso. Per evitare questo problema, accertatevi che almeno una delle tre dipendenze a cui fa riferimento il passaggio IBL Maya abbia lo stesso nome del riferimento originale del file IBL nel file Maya.
* **Immagine di sfondo inversa per l&#39;area di visualizzazione** IBL - Le immagini per gli stadi IBL vengono capovolte in orizzontale in modo intenzionale in modo da corrispondere al comportamento del modulo di rendering NVIDIA per i raggi mentali fornito con Autodesk Maya. Soluzione: Riflettete le immagini utilizzate per le fasi IBL in Photoshop prima di caricarle.
* **Luminosità delle fasi** IBL - L&#39;analisi automatica dell&#39;immagine IBL potrebbe produrre una scena troppo scura o troppo luminosa. Per regolare la luminosità dell&#39;illuminazione delle fasi IBL, andate a Proprietà **** di base e regolate il valore **luminoso** dell&#39;illuminazione dell&#39; **ambiente** in base alle esigenze.

### AEM Sites 3D Component {#aem-sites-d-component}

* **Un componente 3D per pagina** - Al momento, è consentita solo un’istanza del componente 3D in ogni pagina Web. Se alla stessa pagina vengono aggiunti più componenti 3D, nessuno di essi funziona correttamente.
* **Visualizzazione 3D mancante durante l&#39;anteprima in Siti** - Quando si utilizza **Anteprima** in Siti, la pagina deve essere ricaricata nel browser per inizializzare completamente il visualizzatore 3D. Non si tratta di un problema se visualizzate la pagina Web direttamente (ovvero quando `edit.html` viene rimossa dal percorso) sui nodi Autore o Pubblica.

* **Modalità a schermo intero non disponibile sui dispositivi** iOS. Il pulsante a schermo intero non è disponibile sui dispositivi iOS, indipendentemente dal browser utilizzato.

### Pubblicazione di contenuti 3D {#publishing-d-content}

* **Configurazione** di componenti 3D - È necessario installare il Feature Pack 3D su tutti i nodi Publish attivi e ogni nodo deve essere configurato con **CRXDE Lite** alle stesse opzioni di configurazione in `/libs/settings/dam/v3D/WebGLSites`.

* **texture, sfondo o illuminazione mancanti dopo la pubblicazione** - Il meccanismo **Pubblica** in AEM Sites pubblica automaticamente le dipendenze primarie della pagina, incluso il modello 3D e lo stage 3D a cui fa riferimento il componente 3D. Le fasi 3D e i modelli 3D in genere dipendono dalle risorse secondarie per le immagini IBL e le mappe di texture, che il meccanismo di pubblicazione di Siti non pubblica automaticamente. Soluzione: pubblicate tutte le risorse 3D da Risorse prima di pubblicare la pagina Web da Siti. In questo modo tutte le dipendenze per le risorse 3D saranno disponibili sui nodi Pubblica.
