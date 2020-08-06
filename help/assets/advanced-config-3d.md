---
title: Impostazioni di configurazione avanzate
seo-title: Impostazioni di configurazione avanzate
description: Scopri le impostazioni di configurazione avanzate che si applicano all'integrazione di AEM 3D per le distribuzioni Maya e non Maya.
seo-description: Scopri le impostazioni di configurazione avanzate che si applicano all'integrazione di AEM 3D per le distribuzioni Maya e non Maya.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# Impostazioni di configurazione avanzate {#advanced-configuration-settings}

Anche se le impostazioni di configurazione predefinite sono adatte a casi di utilizzo tipici, alcune situazioni possono richiedere l’esecuzione di modifiche.

Le seguenti impostazioni di configurazione avanzate si applicano all&#39;integrazione di AEM 3D sia per le installazioni Maya che per quelle non Maya.

Tutte le impostazioni sono accessibili tramite **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**).

>[!NOTE]
>
>Se reinstallate il pacchetto, vengono reimpostate tutte le impostazioni sui valori predefiniti.

>[!CAUTION]
>
>La modifica di eventuali impostazioni non elencate nella tabella seguente potrebbe causare un comportamento inatteso o indesiderato del programma.

## Configurazione dei tipi di risorsa {#asset-types-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Specifica il tipo di file per il formato 3D intermedio creato durante l&#39;assimilazione. Deve essere vuoto per i formati di file &#39;fbx&#39; e &#39;obj&#39; o &#39;fbx&#39; per i formati abilitati da Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Impostate su true o false per abilitare o disabilitare questa voce nell&#39;elenco **[!UICONTROL assetTypes]** . |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Specificate uno o più suffissi o estensioni di file separati da virgole da associare a questo tipo di risorsa. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Deve essere `native` per i formati di file FBX e OBJ e `maya` per i formati abilitati da Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Specifica il tipo mime per il tipo di risorsa. Per i formati attivati da Maya si consiglia di utilizzare `application/x-ext`, dove `ext` è la stringa specificata come `Extension` valore. |

## Configurazione di inserimento {#ingestion-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Percorso</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>Abilita la generazione di un’ombra esterna di occlusione ambiente quando si visualizza o si esegue il rendering con un’area di visualizzazione IBL. Si applica a Anteprima e rendering con RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Impostate su <strong>false</strong> per mantenere i file temporanei nella cartella MayaWork dopo la conversione e il rendering. Può essere utile quando si verificano problemi di debug con la conversione e il rendering Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>Se abilitata, ImageMagick viene installato sul server e magickPath è configurato. Rapid Refine viene utilizzato per creare una semplice animazione per gli oggetti 3D utilizzati come miniatura nella vista a schede e in altre viste.</p> <p>La creazione di animazioni richiede notevoli risorse CPU durante il processo di assimilazione.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>Consente la creazione automatica di mappe luminose durante l'assimilazione. Impostare su <strong>false</strong> per disattivare la creazione automatica di mappe luminose; questo può ridurre notevolmente il consumo della CPU a costi ridotti per l'anteprima e il rendering con Rapid Refine. Non influenza il rendering con Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Se è impostata su <strong>true</strong> (impostazione predefinita), gli oggetti vengono spostati verticalmente, se necessario, per assicurare che tutte le parti dell'oggetto siano posizionate sopra il piano terreno (y=0).</p> <p>Se è impostata su <strong>false</strong> (impostazione predefinita), gli oggetti non vengono riposizionati e possono essere parzialmente nascosti dal piano terreno di un’area di visualizzazione. (Applicabile solo all’anteprima e al rendering con Rapida perfezionamento). Tuttavia, non influisce sul rendering con Maya. Se è <strong>true</strong>, la posizione verticale degli oggetti in Maya potrebbe essere diversa da quella dell'anteprima o durante il rendering con Rapida perfezionamento.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Percorso e nome dell’utilità di conversione ImageMagick. Se è abilitata la creazione di miniature animate, è necessario un percorso assoluto.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>Specifica quante CPU utilizzare al massimo per l'elaborazione dell'assimilazione delle risorse 3D.</p> <p>Valori più elevati velocizzano le assimilazioni, ma possono causare AEM diventare complessivamente meno reattivi. Questa impostazione è approssimativa. In altre parole, la precisione aumenta con il numero di core CPU disponibili.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazioni di configurazione Cloud Services {#cloud-services-configuration-settings}

I valori per le seguenti impostazioni sono forniti dal responsabile commerciale  Adobe, dall&#39;esperto di provisioning o dal rappresentante di supporto.

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | ID account dell&#39;account AWS  Adobe. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | il nome della benna di trasferimento S3; normalmente `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | L&#39;ID univoco assegnato da  Adobe all&#39;organizzazione. Utilizzato come ID utente di AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | La password associata a questo customerId. Utilizzata come password AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/region` | Area AWS in cui vengono distribuiti i servizi cloud. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | L&#39;ID del pool di utenti AWS Cognito applicabile. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | L&#39;ID client AWS Cognito per il servizio di conversione dncr. |

## Impostazioni di elaborazione comuni {#common-processing-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Nome e posizione della cartella di lavoro per la conversione e il rendering Maya. La cartella viene creata automaticamente se non esiste. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nome e posizione della cartella di lavoro per la conversione 3ds Max. La cartella viene creata automaticamente se non esiste. |
| `/libs/settings/dam/v3D/settings/debugNative` | Impostato su **[!UICONTROL true]** per abilitare la creazione di informazioni di debug durante la conversione e il rendering del formato con il renderer RapidRefine. |

## Configurazione rendering {#renderer-configuration}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| **Percorso** | **Descrizione** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Se impostato su **[!UICONTROL true]** e le mappe di luce pre-generate non sono disponibili (vale a dire invokeLightMapsOnIngest=false), il renderer di definizione rapida crea mappe di luce durante il rendering per migliorare la qualità di rendering. Questa impostazione può aumentare notevolmente il tempo di rendering. L’impostazione su **[!UICONTROL false]** riduce al minimo l’utilizzo della CPU in tali situazioni, ma può ridurre la qualità di rendering. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Impostare su **[!UICONTROL true]** o **[!UICONTROL false]** per attivare o disattivare rispettivamente un renderer. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Consente di modificare la stringa visualizzata per un renderer abilitato nel selettore del renderer nel pannello Rendering. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Specifica quante CPU vengono utilizzate al massimo per il rendering delle scene 3D. Valori più elevati velocizzano il rendering, ma possono causare AEM meno reattivi nel complesso. Questa impostazione è approssimativa. In altre parole, la precisione aumenta con il numero di core CPU disponibili. |

## Impostazioni di anteprima delle risorse 3D {#d-asset-preview-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Impostare su **[!UICONTROL true]** o **[!UICONTROL false]** per attivare o disattivare la rotazione automatica (orbita automatica della fotocamera) al caricamento della pagina. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Impostate su **[!UICONTROL true]** per riavviare la rotazione automatica dopo aver premuto **[!UICONTROL Reset]** . Ignorato quando la rotazione automatica è disattivata. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Specifica la velocità (giri al minuto) e la direzione di rotazione automatica, con valori negativi per i valori da destra a sinistra e positivi per la rotazione da sinistra a destra. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Impostate su **[!UICONTROL false]** per disattivare la continuazione con la graduale dissolvenza delle risposte del visualizzatore ai gesti touch e del mouse. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Specifica il colore della tenda di carico che può eventualmente coprire la finestra di anteprima della risorsa 3D durante il caricamento e l&#39;inizializzazione. Valore R,G,B, con ciascun componente colore compreso tra 0 e 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Quando è impostata su **[!UICONTROL true]**, la tenda di carico si dissolve gradualmente durante le ultime parti dell&#39;inizializzazione del visualizzatore. Se impostata su **[!UICONTROL false]**, la tenda rimane opaca fino al completamento del caricamento e dell&#39;inizializzazione. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Impostate **[!UICONTROL true]** o **[!UICONTROL false]** per attivare o disattivare la tenda di caricamento per l&#39;anteprima delle risorse 3D. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Quando la rotazione automatica è attivata e attiva, la posizione verticale della telecamera viene regolata automaticamente in relazione all&#39;altezza dell&#39;oggetto 3D. Se impostata su 0,5, la telecamera posiziona verticalmente a 1/2 l&#39;altezza dell&#39;oggetto, il che fa sì che l&#39;orizzonte sia centrato verticalmente nella finestra del visualizzatore. Valori maggiori fanno sì che la telecamera guardi verso il basso l&#39;oggetto e alzi l&#39;altezza dell&#39;orizzonte di cui è stato effettuato il rendering, mentre valori più bassi fanno sì che la telecamera guardi verso l&#39;alto l&#39;oggetto e riduca l&#39;orizzonte. |

## Impostazioni dei componenti di Siti 3D {#d-sites-component-settings}

In **CRXDE Lite** in AEM (**[!UICONTROL Strumenti > Generale > CRXDE Lite]**), accedi alle seguenti configurazioni:

| Percorso | Descrizione |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Impostato su **[!UICONTROL true]** per riattivare la rotazione automatica (orbita automatica della telecamera) dopo la pressione di Home. Ignorato quando la rotazione automatica è disattivata. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Impostate su **[!UICONTROL false]** per disattivare la continuazione con la graduale dissolvenza delle risposte del visualizzatore ai gesti touch e del mouse. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Specifica il colore della tenda di carico che può eventualmente coprire la finestra del componente Siti 3D durante il caricamento. Valore R,G,B, con ciascun componente colore compreso tra 0 e 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Se impostata su **[!UICONTROL true]**, la tenda di carico si dissolve gradualmente durante le ultime parti di caricamento e inizializzazione. Se impostata su **[!UICONTROL false]**, la tenda rimane opaca fino al completamento del caricamento e dell&#39;inizializzazione. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Impostare su **[!UICONTROL true]** o **[!UICONTROL false]** per attivare o disattivare la tenda di caricamento per il componente Siti 3D. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Quando la rotazione automatica è attivata e attiva, la posizione verticale della telecamera viene regolata automaticamente in relazione all&#39;altezza dell&#39;oggetto 3D. Se impostata su 0,5, la telecamera posiziona verticalmente a 1/2 l&#39;altezza dell&#39;oggetto, il che fa sì che l&#39;orizzonte sia centrato verticalmente nella finestra del visualizzatore. Valori maggiori fanno sì che la telecamera guardi verso il basso l&#39;oggetto e alzi l&#39;altezza dell&#39;orizzonte di cui è stato effettuato il rendering, mentre valori più bassi fanno sì che la telecamera guardi verso l&#39;alto l&#39;oggetto e riduca l&#39;orizzonte. |

