---
title: Integrazione AEM 3D con Autodesk 3ds Max
seo-title: Integrazione AEM 3D con AutoDesk 3ds Max
description: È possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento, il rendering tramite 3ds Max non è supportato.
seo-description: È possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento, il rendering tramite 3ds Max non è supportato.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Integrazione AEM 3D con Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Questa attività è facoltativa e riguarda solo Windows.

È possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento, il rendering tramite 3ds Max non è supportato.

Consultate Impostazioni [di configurazione](advanced-config-3d.md)avanzate.

Vedere anche [Integrazione AEM 3D con AutoDesk Maya](integrate-maya-with-3d.md).

**Per integrare AEM 3D con Autodesk 3ds Max**:

1. Installate il software Autodesk 3ds Max sugli stessi server in cui sono installati i nodi AEM Author.

   Dopo l&#39;installazione, verificate di poter aprire e utilizzare Maya e che non vi siano problemi di licenza.

   >[!NOTE]
   >
   >Per evitare problemi di accesso negato, installa 3ds Max utilizzando lo stesso account utente amministratore AEM.

1. In 3ds Max, fate clic su **[!UICONTROL Personalizza > Gestione]** plug-in.

   Individuate `FBXMAX.DLU` e verificate che **[!UICONTROL lo stato]** sia **[!UICONTROL caricato**.

   Chiudete la finestra di dialogo Gestione **** plug-in e chiudete 3ds Max.

1. Aggiornare lo script di conversione.

   AEM utilizza uno script della riga di comando per richiamare l&#39;utilità della riga di comando 3ds Max `3dsmaxcmd.exe`. È necessario modificare questo script se è stata installata una versione diversa da 3ds Max 2016, o se è stato installato 3ds Max in una posizione non standard, o se è stato installato AEM su una partizione o unità diversa.

   1. Aprite il CRXDE Lite e passate a `/libs/settings/dam/v3D/scripts/max`.
   1. Fate doppio clic `export-fbx.bat` per aprirlo.
   1. Modificate la prima riga dello script in base alle esigenze per riflettere la posizione dell&#39; `3dsmaxcmd.exe` utilità. Ad esempio, se si utilizza 3ds Max 2017 e AEM è installato su un&#39;altra unità disco:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Nell’angolo in alto a sinistra della pagina del CRXDE Lite, toccate **[!UICONTROL Salva tutto]**.

   Nell’angolo in alto a sinistra della pagina del CRXDE Lite, toccate **[!UICONTROL Salva tutto]**.

1. Rimuovere la cartella di lavoro (necessaria solo se è stato effettuato un tentativo precedente di assimilare un file .MAX).

   1. In CRXDE Lite, andate a `/libs/settings/dam/v3D/Paths/maxWorkPath`. Per impostazione predefinita, il valore di questa impostazione è `./MaxWork`, relativo alla cartella principale di installazione AEM.
   1. Accedete al server stesso e utilizzate Esplora file per passare alla cartella principale di installazione AEM.
   1. Eliminate la cartella **[!UICONTROL MaxWork]** , incluso tutto il contenuto, se esiste.

      La cartella viene ricreata automaticamente al successivo assimilazione di un file .MAX.

1. Abilita 3ds Max per l’assimilazione eseguendo le operazioni seguenti:

   1. In CRXDE Lite , andate a `/libs/settings/dam/v3D/assetTypes/max` e impostate la proprietà **[!UICONTROL Enabled]** su true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Nell’angolo in alto a sinistra della pagina del CRXDE Lite, toccate **[!UICONTROL Salva tutto]**.

## Verifica dell&#39;integrazione di AEM 3D con Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Aprite  AEM Assets, quindi caricate il `.max` file che si trova `sample-3D-content/models` nella cartella **[!UICONTROL test3d]** .

   Tenete presente che sample-3D-content.zip è stato scaricato in precedenza per la convalida delle funzionalità 3D di base.

1. Tornate alla vista **[!UICONTROL Scheda]** e osservate i banner dei messaggi mostrati sulle risorse caricate.

   Il banner di conversione del formato viene visualizzato mentre 3ds Max converte il formato nativo 3ds Max in .FBX.

1. Al termine dell’elaborazione, aprite `logo-sphere.max` nella visualizzazione **[!UICONTROL Dettagli]** .

   L&#39;esperienza Anteprima è la stessa di quella con `logo_sphere.fbx`.

