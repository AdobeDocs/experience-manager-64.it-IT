---
title: Integrazione AEM 3D con Autodesk Maya
seo-title: Integrazione AEM 3D con Autodesk Maya
description: È possibile integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file Maya nativi (.MA e .MB) e per consentire il rendering delle risorse 3D in AEM con qualsiasi renderer Maya disponibile.
seo-description: È possibile integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file Maya nativi (.MA e .MB) e per consentire il rendering delle risorse 3D in AEM con qualsiasi renderer Maya disponibile.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---


# Integrazione AEM 3D con Autodesk Maya {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>Questa attività è facoltativa e riguarda solo Windows.

È possibile integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file Maya nativi (`.MA` e `.MB`) e per consentire il rendering delle risorse 3D in AEM con qualsiasi renderer Maya disponibile.

*Questa integrazione è disponibile solo* per Windows.

Quando si esegue l&#39;integrazione con Autodesk Maya, è necessario installare e configurare Autodesk Maya, aggiungere il percorso alla cartella eseguibile Maya, abilitare Maya per l&#39;inserimento e il rendering e verificare l&#39;integrazione.

Vedere [Impostazioni di configurazione avanzate](advanced-config-3d.md).

Vedere anche [Integrazione AEM 3D con AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md).

**Per integrare AEM 3D con Autodesk Maya**:

1. Installate il software Autodesk Maya 2016 sugli stessi server in cui è AEM.

   Dopo l&#39;installazione, verificate di poter aprire e utilizzare Maya e che non vi siano problemi di licenza.

   >[!NOTE]
   >
   >AEM utilizza solo lo strumento di rendering della riga di comando Maya (`render.exe`). Una singola licenza di rete Maya consente fino a cinque server di elaborare o eseguire simultaneamente il rendering dei contenuti Maya.

1. In Maya, abilitare il plug-in Autodesk FBX®.
1. Installate il plug-in di rendering MentalRay o un altro renderer desiderato.

   Dopo l&#39;installazione, verificare che MentalRay sia disponibile in Maya.

1. Aggiungete il percorso alla cartella eseguibile Maya alla variabile di ambiente PATH di Windows.

   Ad esempio, in Windows Server 2012, toccare **[!UICONTROL Start] > [!UICONTROL Pannello di controllo Campaign] > [!UICONTROL System and Security] > [!UICONTROL System] > [!UICONTROL Advanced System Settings] > [!UICONTROL Environment Variables]**. Aggiungete il percorso completo della cartella `Maya2016\bin` alla variabile di sistema `Path`.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Per abilitare Maya per l&#39;assimilazione e il rendering, aprire **[!UICONTROL CRXDE Lite]** e passare a `/libs/settings/dam/v3D/assetTypes/maya` e impostare la proprietà **[!UICONTROL Enabled]** su `true`.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. Per abilitare il formato di file JT (Siemens PLM Open CAD), passare a `/libs/settings/dam/v3D/assetTypes/jt` e impostare la proprietà **[!UICONTROL Enabled]** su `true`.
1. In AEM, abilitate Maya come renderer. Per iniziare, passare a **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Dalla pagina **[!UICONTROL CRXDE Lite]**, nel pannello a sinistra, individuate quanto segue:

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Impostare la proprietà **[!UICONTROL Enabled]** su `true`.

1. Vicino all&#39;angolo superiore sinistro della pagina **[!UICONTROL CRXDE Lite]**, toccare **[!UICONTROL Salva tutto]**.

   Maya ora è abilitata come renderer.

## Verifica dell&#39;integrazione di AEM 3D con Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. Aprite  AEM Assets, quindi caricate i file `.MA` che si trovano in `sample-3D-content/models` nella cartella `test3d`.

   `sample-3D-content.zip` è stato precedentemente scaricato per la convalida della funzionalità 3D di base.

1. Tornate alla vista **[!UICONTROL Scheda]** e osservate i banner dei messaggi mostrati sulle risorse caricate.

   Il banner di conversione del formato viene visualizzato mentre Maya converte il formato nativo `.MA` in `.FBX`.

1. Al termine dell&#39;elaborazione, aprite la risorsa `logo-sphere.ma` e selezionate il passaggio `stage-helipad.ma`.

   L&#39;esperienza Anteprima è la stessa di quella con `logo_sphere.fbx` e `stage-helipad.fbx`.

1. Nell&#39;angolo superiore sinistro della pagina, toccare o fare clic sull&#39;elenco a discesa, quindi selezionare **[!UICONTROL CRender]**.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. Nell&#39;elenco a discesa **[!UICONTROL Renderer]**, selezionare **[!UICONTROL Autodesk Maya]**, quindi toccare **[!UICONTROL Avvia rendering]**.
1. Nell&#39;angolo superiore destro della pagina, toccate o fate clic su **[!UICONTROL Chiudi]** per tornare alla vista **[!UICONTROL Scheda]**.

   Osservate il banner del messaggio sulla risorsa immagine di cui viene eseguito il rendering (`logo-sphere`, a meno che non sia stato specificato un nome immagine diverso). Una barra di avanzamento sul banner mostra l’avanzamento del rendering.

   >[!NOTE]
   >
   >Il rendering richiede molta CPU e può richiedere alcuni minuti per il completamento

1. Al termine del rendering, aprite la risorsa immagine di cui è stato effettuato il rendering.

   Verificare che l&#39;immagine di cui è stato effettuato il rendering corrisponda ragionevolmente all&#39;immagine visualizzata quando si faceva clic su **[!UICONTROL Esegui rendering ora]**.

## Abilitazione di formati aggiuntivi supportati da Maya {#enabling-additional-formats-supported-by-maya}

(Facoltativo) Maya supporta una serie di formati di input 3D, ciascuno dei quali può essere attivato in modo AEM riconoscere il tipo di file. Quando è attivata, AEM invia il file a Maya per convertirlo in un formato intermedio che può essere acquisito direttamente da AEM.

A seconda del formato, il supporto delle funzioni potrebbe essere limitato (ad esempio, i materiali potrebbero non essere passati attraverso) e la qualità/fedeltà potrebbe essere limitata (ad esempio, facce invertite).  Adobe supporta solo il meccanismo generale, ma non una conversione di formato specifica.

Vedere [Formati di importazione dati supportati | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) per informazioni sui formati supportati da Maya.

**Per abilitare formati aggiuntivi supportati da AEM**:

1. Utilizzando **[!UICONTROL CRXDE Lite]**, passare a `/libs/settings/dam/v3D/assetTypes`.
1. Effettuate una copia del nodo **[!UICONTROL jt]**. Fare clic con il pulsante destro del mouse sul nodo **[!UICONTROL jt]** e selezionare **[!UICONTROL Copia]**, quindi fare clic con il pulsante destro del mouse sulla cartella **[!UICONTROL assetTypes]** e selezionare **[!UICONTROL Incolla]**. Questo dovrebbe generare un nuovo nodo `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. Rinominare il nuovo nodo per assegnargli un nome univoco che rappresenta il tipo di file da aggiungere. È possibile utilizzare il suffisso del file o qualsiasi altro identificatore univoco.

1. Impostare la proprietà **[!UICONTROL Enabled]** del nuovo nodo su `true`.

1. Impostate la proprietà **[!UICONTROL Extension]** della nuova nota sul suffisso/estensione del file del formato da aggiungere.
1. Impostare la proprietà **[!UICONTROL MimeType]** su un valore appropriato. `application/x-` seguito dal valore della proprietà  **** Extensiondeve funzionare per la maggior parte dei tipi di file.
1. Assicurarsi che la proprietà **[!UICONTROL Conversion]** sia impostata su `fbx` e **[!UICONTROL IngestRegime]** su `Maya`.
1. Fare clic su **[!UICONTROL Salva tutto]** in alto a sinistra nella pagina.

La schermata seguente illustra un formato di file aggiunto, utilizzando COLLADA DAE come esempio:

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)

