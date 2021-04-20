---
title: Integrazione AEM 3D con Autodesk Maya
seo-title: Integrazione AEM 3D con Autodesk Maya
description: È possibile integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file nativi Maya (.MA e .MB) e per consentire il rendering delle risorse 3D in AEM con qualsiasi modulo di rendering Maya disponibile.
seo-description: È possibile integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file nativi Maya (.MA e .MB) e per consentire il rendering delle risorse 3D in AEM con qualsiasi modulo di rendering Maya disponibile.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
exl-id: 52ecbf81-0953-4c44-bc2c-d40e507b8d98
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# Integrazione di AEM 3D con Autodesk Maya {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>Questa attività è facoltativa e riguarda solo Windows.

Facoltativamente, puoi integrare AEM 3D con il software Autodesk® Maya® per abilitare il supporto per i file nativi Maya (`.MA` e `.MB`) e per consentire il rendering delle risorse 3D in AEM con qualsiasi modulo di rendering Maya disponibile.

*Questa integrazione è disponibile solo* per Windows.

Quando si esegue l’integrazione con Autodesk Maya, è necessario installare e configurare Autodesk Maya, aggiungere il percorso alla cartella eseguibile Maya, abilitare Maya per l’acquisizione e il rendering e verificare l’integrazione.

Consulta [Impostazioni di configurazione avanzate](advanced-config-3d.md).

Vedere anche [Integrazione AEM 3D con AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md).

**Per integrare AEM 3D con Autodesk Maya**:

1. Installa il software Autodesk Maya 2016 sugli stessi server in cui è ospitato AEM.

   Dopo l’installazione, verifica di poter aprire e utilizzare Maya e che non ci siano problemi di licenza.

   >[!NOTE]
   >
   >AEM utilizza solo lo strumento di rendering della riga di comando Maya (`render.exe`). Una singola licenza di rete Maya consente fino a cinque server di elaborare o eseguire il rendering simultaneo dei contenuti Maya.

1. In Maya, abilita il plug-in Autodesk FBX®.
1. Installa il plug-in di rendering MentalRay o un altro renderer desiderato.

   Dopo l&#39;installazione, verifica che MentalRay sia disponibile in Maya.

1. Aggiungi il percorso della cartella eseguibile Maya alla variabile di ambiente PATH di Windows.

   Ad esempio, su Windows Server 2012, toccare **[!UICONTROL Start] > [!UICONTROL Pannello di controllo Campaign] > [!UICONTROL Sistema e sicurezza] > [!UICONTROL Sistema] > [!UICONTROL Impostazioni di sistema avanzate] > [!UICONTROL Variabili di ambiente]**. Aggiungi il percorso completo della cartella `Maya2016\bin` alla variabile di sistema `Path`.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Per abilitare Maya per l’acquisizione e il rendering, apri **[!UICONTROL CRXDE Lite]** e passa a `/libs/settings/dam/v3D/assetTypes/maya` e imposta la proprietà **[!UICONTROL Enabled]** su `true`.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. Per abilitare il formato di file JT (Siemens PLM Open CAD), passa a `/libs/settings/dam/v3D/assetTypes/jt` e imposta la proprietà **[!UICONTROL Enabled]** su `true`.
1. In AEM, abilita Maya come renderer. Per iniziare, passa a **[!UICONTROL Strumenti > Generale > CRXDE Lite]**.
1. Dalla pagina **[!UICONTROL CRXDE Lite]**, nel pannello a sinistra, passa alla seguente pagina:

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Imposta la proprietà **[!UICONTROL Enabled]** su `true`.

1. Nell’angolo in alto a sinistra della pagina **[!UICONTROL CRXDE Lite]**, tocca **[!UICONTROL Salva tutto]**.

   Maya ora è abilitata come renderer.

## Verifica dell&#39;integrazione di AEM 3D con Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. Apri AEM Assets, quindi carica i file `.MA` che si trovano in `sample-3D-content/models` nella cartella `test3d`.

   Nota che `sample-3D-content.zip` è stato scaricato in precedenza per la convalida della funzionalità 3D di base.

1. Torna alla visualizzazione **[!UICONTROL Scheda]** e osserva i banner dei messaggi mostrati sulle risorse caricate.

   Il banner Formato di conversione viene visualizzato mentre Maya sta convertendo il formato nativo `.MA` in `.FBX`.

1. Al termine dell’elaborazione, apri la risorsa `logo-sphere.ma` e seleziona il passaggio `stage-helipad.ma` .

   L’esperienza Anteprima è la stessa di `logo_sphere.fbx` e `stage-helipad.fbx`.

1. Nell’angolo in alto a sinistra della pagina, tocca o fai clic sull’elenco a discesa, quindi seleziona **[!UICONTROL CRender]**.

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. Nell&#39;elenco a discesa **[!UICONTROL Renderer]** , seleziona **[!UICONTROL Autodesk Maya]**, quindi tocca **[!UICONTROL Avvia rendering]**.
1. Nell’angolo in alto a destra della pagina, tocca o fai clic su **[!UICONTROL Chiudi]** per tornare alla vista **[!UICONTROL Scheda]**.

   Osserva il banner messaggio sulla risorsa immagine di cui viene eseguito il rendering (`logo-sphere`, a meno che non sia stato specificato un nome immagine diverso). Una barra di avanzamento sul banner mostra l’avanzamento del rendering.

   >[!NOTE]
   >
   >Il rendering richiede molta CPU e può richiedere alcuni minuti per essere completato

1. Al termine del rendering, apri la risorsa immagine di cui è stato effettuato il rendering.

   Controlla che l&#39;immagine di cui hai effettuato il rendering corrisponda ragionevolmente all&#39;immagine che stavi visualizzando al momento in cui hai fatto clic su **[!UICONTROL Esegui rendering ora]**.

## Abilitazione Di Formati Aggiuntivi Supportati Da Maya {#enabling-additional-formats-supported-by-maya}

(Facoltativo) Maya supporta una serie di formati di input 3D, ciascuno dei quali può essere attivato in modo che AEM riconosca il tipo di file. Quando abilitato, AEM invia il file a Maya per convertirlo in un formato intermedio che può essere acquisito direttamente da AEM.

A seconda del formato, il supporto delle funzioni può essere limitato (ad esempio, i materiali potrebbero non essere trasmessi) e la qualità/fedeltà può essere limitata (ad esempio, facce rovesciate). L’Adobe supporta solo il meccanismo generale, ma non una conversione di formato specifica.

Consulta [Formati di importazione dei dati supportati | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) per informazioni sui formati supportati da Maya.

**Per abilitare formati aggiuntivi supportati da AEM**:

1. Utilizzando **[!UICONTROL CRXDE Lite]**, passa a `/libs/settings/dam/v3D/assetTypes`.
1. Crea una copia del nodo **[!UICONTROL jt]**. Fai clic con il pulsante destro del mouse sul nodo **[!UICONTROL jt]** e seleziona **[!UICONTROL Copia]**, quindi fai clic con il pulsante destro del mouse sulla cartella **[!UICONTROL assetTypes]** e seleziona **[!UICONTROL Incolla]**. Questo dovrebbe produrre un nuovo nodo `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. Rinomina il nuovo nodo per assegnargli un nome univoco che rappresenta il tipo di file da aggiungere. È possibile utilizzare il suffisso di file o qualsiasi altro identificatore univoco.

1. Imposta la proprietà **[!UICONTROL Enabled]** del nuovo nodo su `true`.

1. Imposta la proprietà **[!UICONTROL Extension]** della nuova nota sul suffisso/estensione file del formato da aggiungere.
1. Imposta la proprietà **[!UICONTROL MimeType]** su un valore appropriato. `application/x-` seguito dal valore della proprietà  **** Extension deve funzionare per la maggior parte dei tipi di file.
1. Assicurati che la proprietà **[!UICONTROL Conversion]** sia impostata su `fbx` e **[!UICONTROL IngestRegime]** su `Maya`.
1. Fai clic su **[!UICONTROL Salva tutto]** in alto a sinistra nella pagina.

La schermata seguente illustra un formato di file aggiunto, utilizzando COLLADA DAE come esempio:

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)
