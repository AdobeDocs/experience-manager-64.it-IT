---
title: Impostazioni di configurazione avanzate
seo-title: Impostazioni di configurazione avanzate
description: Scopri le impostazioni di configurazione avanzate applicabili all’integrazione di AEM 3D per le distribuzioni Maya e non Maya.
seo-description: Scopri le impostazioni di configurazione avanzate applicabili all’integrazione di AEM 3D per le distribuzioni Maya e non Maya.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
exl-id: fdc82bca-e676-4052-b3e9-a198c685df96
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 1%

---

# Impostazioni di configurazione avanzate {#advanced-configuration-settings}

Sebbene le impostazioni di configurazione predefinite siano appropriate per i casi d’uso tipici, in alcune situazioni potrebbe essere necessario apportare modifiche.

Le seguenti impostazioni di configurazione avanzate si applicano all’integrazione di AEM 3D per le distribuzioni Maya e non Maya.

Tutte le impostazioni sono accessibili utilizzando **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**).

>[!NOTE]
>
>Se reinstalli il pacchetto, reimposta tutte le impostazioni sui valori predefiniti.

>[!CAUTION]
>
>La modifica di impostazioni non elencate nella tabella seguente potrebbe causare un comportamento imprevisto o indesiderato del programma.

## Configurazione dei tipi di risorse {#asset-types-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Specifica il tipo di file per il formato 3D intermedio creato durante l&#39;acquisizione. Deve essere vuoto per i formati di file &#39;fbx&#39; e &#39;obj&#39; o &#39;fbx&#39; per i formati abilitati da Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Imposta su true o false per abilitare o disabilitare questa voce nell&#39;elenco **[!UICONTROL assetTypes]**. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Specifica uno o più suffissi di file o estensioni di file separati da virgole da associare a questo tipo di risorsa. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Deve essere `native` per i formati di file FBX e OBJ e `maya` per i formati abilitati da Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Specifica il tipo di MIME per questo tipo di risorsa. Per i formati abilitati da Maya si consiglia di utilizzare `application/x-ext`, dove `ext` è la stringa specificata come valore `Extension`. |

## Configurazione dell&#39;acquisizione {#ingestion-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Percorso</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>Abilita la generazione di un’ombra esterna di inclusione ambientale durante la visualizzazione o il rendering con un’area di visualizzazione IBL. Si applica a Anteprima e rendering con RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Imposta su <strong>false</strong> per mantenere i file temporanei nella cartella MayaWork dopo la conversione e il rendering. Può essere utile quando si verificano problemi di debug con la conversione e il rendering di Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>Quando abilitato, ImageMagick viene installato sul server e magickPath è configurato. Rapid Refine viene utilizzato per creare una semplice animazione per oggetti 3D utilizzati come miniatura nella vista a schede e in altre viste.</p> <p>La creazione di animazioni consuma notevoli risorse CPU durante il processo di acquisizione.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>Consente la creazione automatica di mappe luminose durante l'acquisizione. Impostare su <strong>false</strong> per disabilitare la creazione automatica di mappe luminose; questo può ridurre notevolmente il consumo della CPU a costo di una qualità ridotta per l'anteprima e il rendering con Rapid Refine. Non influisce sul rendering con Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Se impostato su <strong>true</strong> (predefinito), gli oggetti vengono spostati verticalmente, se necessario, per garantire che tutte le parti dell'oggetto siano al di sopra del piano terreno (y=0).</p> <p>Quando è impostato su <strong>false</strong> (predefinito), gli oggetti non vengono riposizionati e possono essere parzialmente nascosti dal piano terreno di un'area di visualizzazione. (Si applica solo all’anteprima e al rendering con Rapid Refine.) Tuttavia, non influisce sul rendering con Maya. Se è impostato su <strong>true</strong>, la posizione verticale degli oggetti in Maya può essere diversa da quella dell'anteprima o del rendering con Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Il percorso e il nome dell'utilità di conversione ImageMagick. Se è abilitata la creazione di miniature animate, è necessario un percorso assoluto.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>Specifica quante CPU vengono utilizzate al massimo per l'elaborazione dell'acquisizione di risorse 3D.</p> <p>Valori più elevati velocizzano le acquisizioni ma possono causare AEM una minore reattività complessiva. Questa impostazione è approssimativa. In altre parole, la precisione aumenta con il numero di core della CPU disponibili.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazioni di configurazione dei Cloud Services {#cloud-services-configuration-settings}

I valori per le seguenti impostazioni vengono forniti dal responsabile dell&#39;account Adobe, da un esperto di provisioning o da un rappresentante del supporto.

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | ID account dell&#39;account AWS di Adobe. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | il nome del secchio di trasferimento S3; normalmente `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | L’ID univoco assegnato dall’Adobe alla tua organizzazione. Utilizzato come ID utente AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | Password associata a questo customerId. Utilizzato come password di Cognito AWS. |
| `/libs/settings/dam/v3D/services/aws/region` | Area AWS in cui vengono distribuiti i servizi cloud. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | ID del pool di utenti AWS Cognito applicabile. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | L’ID client AWS Cognito per il servizio di conversione dncr. |

## Impostazioni di elaborazione comuni {#common-processing-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Nome e posizione della cartella di lavoro per la conversione e il rendering di Maya. La cartella viene creata automaticamente se non esiste. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nome e posizione della cartella di lavoro per la conversione 3ds Max. La cartella viene creata automaticamente se non esiste. |
| `/libs/settings/dam/v3D/settings/debugNative` | Imposta su **[!UICONTROL true]** per abilitare la creazione di informazioni di debug durante la conversione e il rendering del formato con il modulo di rendering RapidRefine. |

## Configurazione del rendering {#renderer-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Se è impostato su **[!UICONTROL true]** e le mappe luminose pre-generate non sono disponibili (cioè invokeLightMapsOnIngest=false), il modulo di rendering Rapid Refine crea mappe luminose durante il rendering per migliorare la qualità del rendering. Questa impostazione può aumentare notevolmente il tempo di rendering. L&#39;impostazione su **[!UICONTROL false]** riduce al minimo l&#39;utilizzo della CPU in tali situazioni, ma può comportare una qualità di rendering inferiore. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Impostare su **[!UICONTROL true]** o **[!UICONTROL false]** per abilitare o disabilitare rispettivamente un renderer. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Consente di modificare la stringa visualizzata per un renderer abilitato nel selettore Renderer nel pannello Rendering . |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Specifica quante CPU vengono utilizzate al massimo per il rendering delle scene 3D. Valori più alti velocizzano il rendering, ma possono causare AEM a diventare complessivamente meno reattivi. Questa impostazione è approssimativa. In altre parole, la precisione aumenta con il numero di core della CPU disponibili. |

## Impostazioni di anteprima delle risorse 3D {#d-asset-preview-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Impostare su **[!UICONTROL true]** o **[!UICONTROL false]** per abilitare o disabilitare la rotazione automatica (rotazione automatica della fotocamera) al caricamento della pagina. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Impostare su **[!UICONTROL true]** per riavviare la rotazione automatica dopo aver premuto **[!UICONTROL Reset]**. Ignorato quando la rotazione automatica è disabilitata. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Specifica la velocità (giri al minuto) e la direzione di rotazione automatica, con valori negativi per i valori da destra a sinistra e positivi per la rotazione da sinistra a destra. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Impostato su **[!UICONTROL false]** per disabilitare la continuazione con una graduale dissolvenza delle risposte del visualizzatore ai gesti touch e del mouse. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Specifica il colore della tenda di carico che può coprire facoltativamente la finestra di visualizzazione dell&#39;anteprima della risorsa 3D durante il caricamento e l&#39;inizializzazione. Valore R,G,B, con ciascun componente di colore compreso tra 0 e 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Quando è impostato su **[!UICONTROL true]**, la tenda di carico si dissolve gradualmente durante le ultime parti dell&#39;inizializzazione del visualizzatore. Se impostata su **[!UICONTROL false]**, la tenda rimane opaca fino al completamento del caricamento e dell&#39;inizializzazione. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Imposta su **[!UICONTROL true]** o **[!UICONTROL false]** per abilitare o disabilitare il blocco di caricamento per l&#39;anteprima delle risorse 3D. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Quando la rotazione automatica è attivata e attiva, la posizione verticale della telecamera viene regolata automaticamente in base all&#39;altezza dell&#39;oggetto 3D. Impostata su 0,5, la telecamera posiziona verticalmente a 1/2 l&#39;altezza dell&#39;oggetto, il che fa sì che l&#39;orizzonte sia centrato verticalmente nel riquadro di visualizzazione. Valori più grandi fanno sì che la telecamera guardi verso il basso sull&#39;oggetto e alzi l&#39;altezza dell&#39;orizzonte di cui è stato effettuato il rendering, valori più piccoli fanno sì che la telecamera guardi verso l&#39;alto l&#39;oggetto e abbassi l&#39;orizzonte. |

## Impostazioni del componente Siti 3D {#d-sites-component-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Impostare su **[!UICONTROL true]** per riattivare la rotazione automatica (rotazione automatica della fotocamera) dopo aver premuto il tasto Home. Ignorato quando la rotazione automatica è disabilitata. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Impostato su **[!UICONTROL false]** per disabilitare la continuazione con una graduale dissolvenza delle risposte del visualizzatore ai gesti touch e del mouse. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Specifica il colore della tenda di carico che può coprire facoltativamente il riquadro di visualizzazione del componente Siti 3D durante il caricamento. Valore R,G,B, con ciascun componente di colore compreso tra 0 e 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Quando è impostato su **[!UICONTROL true]**, la tenda di carico si dissolve gradualmente durante le ultime parti di caricamento e inizializzazione. Se impostata su **[!UICONTROL false]**, la tenda rimane opaca fino al completamento del caricamento e dell&#39;inizializzazione. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Imposta su **[!UICONTROL true]** o **[!UICONTROL false]** per abilitare o disabilitare la tenda di carico per il componente Siti 3D. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Quando la rotazione automatica è attivata e attiva, la posizione verticale della telecamera viene regolata automaticamente in base all&#39;altezza dell&#39;oggetto 3D. Impostata su 0,5, la telecamera posiziona verticalmente a 1/2 l&#39;altezza dell&#39;oggetto, il che fa sì che l&#39;orizzonte sia centrato verticalmente nel riquadro di visualizzazione. Valori più grandi fanno sì che la telecamera guardi verso il basso sull&#39;oggetto e alzi l&#39;altezza dell&#39;orizzonte di cui è stato effettuato il rendering, valori più piccoli fanno sì che la telecamera guardi verso l&#39;alto l&#39;oggetto e abbassi l&#39;orizzonte. |
