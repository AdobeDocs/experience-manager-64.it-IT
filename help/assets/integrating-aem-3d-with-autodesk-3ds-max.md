---
title: Integrazione AEM 3D con Autodesk 3ds Max
seo-title: Integrazione AEM 3D con AutoDesk 3ds Max
description: Facoltativamente è possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento il rendering tramite 3ds Max non è supportato.
seo-description: Facoltativamente è possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento il rendering tramite 3ds Max non è supportato.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
exl-id: 2edecd53-0a2d-44bb-968a-d988c780e142
feature: Risorse 3D
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Integrazione AEM 3D con Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Questa attività è facoltativa e riguarda solo Windows.

Facoltativamente è possibile integrare AEM 3D con il software Autodesk 3ds Max per abilitare il supporto per i file nativi 3ds Max (.MAX). Al momento il rendering tramite 3ds Max non è supportato.

Consulta [Impostazioni di configurazione avanzate](advanced-config-3d.md).

Vedi anche [Integrazione AEM 3D con AutoDesk Maya](integrate-maya-with-3d.md).

**Per integrare AEM 3D con Autodesk 3ds Max**:

1. Installa il software Autodesk 3ds Max sugli stessi server in cui sono installati i nodi AEM Author.

   Dopo l’installazione, verifica di poter aprire e utilizzare Maya e che non ci siano problemi di licenza.

   >[!NOTE]
   >
   >Per evitare problemi di accesso negato, installa 3ds Max utilizzando lo stesso account utente amministratore di AEM.

1. In 3ds Max, fai clic su **[!UICONTROL Personalizza > Gestione plug-in]**.

   Individua `FBXMAX.DLU` e verifica che il relativo **[!UICONTROL Stato]** sia **[!UICONTROL caricato]**.

   Chiudi la finestra di dialogo **[!UICONTROL Gestione plug-in]** e 3ds Max.

1. Aggiorna lo script di conversione.

   AEM utilizza uno script della riga di comando per richiamare l&#39;utilità della riga di comando 3ds Max `3dsmaxcmd.exe`. È necessario modificare questo script se si è installata una versione diversa da 3ds Max 2016, se si è installato 3ds Max in una posizione non standard, o se si è installato AEM su una partizione o unità diversa.

   1. Apri CRXDE Lite e passa a `/libs/settings/dam/v3D/scripts/max`.
   1. Fai doppio clic su `export-fbx.bat` per aprirlo.
   1. Modifica la prima riga dello script in base alle esigenze per riflettere la posizione dell&#39;utilità `3dsmaxcmd.exe`. Ad esempio, se si utilizza 3ds Max 2017 e AEM è installato su un&#39;altra unità disco:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Nell’angolo in alto a sinistra della pagina CRXDE Lite, tocca **[!UICONTROL Salva tutto]**.

   Nell’angolo in alto a sinistra della pagina CRXDE Lite, tocca **[!UICONTROL Salva tutto]**.

1. Rimuovere la cartella di lavoro (necessaria solo se è stato effettuato un tentativo precedente di acquisire un file .MAX).

   1. In CRXDE Lite, passa a `/libs/settings/dam/v3D/Paths/maxWorkPath`. Per impostazione predefinita, il valore di questa impostazione è `./MaxWork`, relativo alla cartella principale di installazione AEM.
   1. Accedere al server stesso e utilizzare Esplora file per passare alla cartella principale di installazione AEM.
   1. Elimina la cartella **[!UICONTROL MaxWork]**, incluso l&#39;intero contenuto, se esiste.

      La cartella viene ricreata automaticamente alla successiva acquisizione di un file .MAX.

1. Abilita 3ds Max per l’acquisizione eseguendo le operazioni seguenti:

   1. In CRXDE Lite, passa a `/libs/settings/dam/v3D/assetTypes/max` e imposta la proprietà **[!UICONTROL Enabled]** su true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Nell’angolo in alto a sinistra della pagina CRXDE Lite, tocca **[!UICONTROL Salva tutto]**.

## Verifica dell&#39;integrazione di AEM 3D con Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Apri AEM Assets, quindi carica il file `.max` che si trova in `sample-3D-content/models` nella cartella **[!UICONTROL test3d]** .

   Si noti che sample-3D-content.zip è stato scaricato in precedenza per la convalida della funzionalità 3D di base.

1. Torna alla visualizzazione **[!UICONTROL Scheda]** e osserva i banner dei messaggi mostrati sulle risorse caricate.

   Il banner di conversione del formato viene visualizzato mentre 3ds Max sta convertendo il formato nativo 3ds Max in .FBX.

1. Al termine dell&#39;elaborazione, apri `logo-sphere.max` nella vista **[!UICONTROL Dettaglio]** .

   L’esperienza Anteprima è la stessa di `logo_sphere.fbx`.
