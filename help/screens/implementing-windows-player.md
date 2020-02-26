---
title: Implementazione di Windows 10 Player
seo-title: Implementazione di Windows 10 Player
description: 'Segui questa pagina per saperne di più sulla configurazione del lettore Windows 10 di AEM Screens. '
seo-description: 'Segui questa pagina per saperne di più sulla configurazione del lettore Windows 10 di AEM Screens. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Implementazione di Windows 10 Player{#implementing-windows-player}

Questa sezione descrive la configurazione di AEM Screens Windows 10 Player. Fornisce informazioni sul file di configurazione e sulle opzioni disponibili e consigli sulle impostazioni da utilizzare per lo sviluppo e il test.

## Installazione di Windows Player {#installing-windows-player}

Per implementare Windows Player per AEM Screens, installate Windows Player per AEM Screens.

Visita la pagina dei download [**di **](https://download.macromedia.com/screens/)AEM 6.4 Player.

### Ad-Hoc, metodo {#ad-hoc-method}

Il metodo Ad-Hoc per installare la versione più recente di Windows Player (*.exe*), visita la pagina dei download [**di **](https://download.macromedia.com/screens/)AEM 6.4 Player.

Una volta scaricata l’applicazione, seguite i passaggi del lettore per completare l’installazione ad hoc:

1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
1. Andate a **Configurazione** dal menu delle azioni a sinistra e immettete il percorso (indirizzo) dell’istanza AEM a cui desiderate connettervi e fate clic su **Salva**.

1. Fai clic sul collegamento **Registrazione** dal menu delle azioni a sinistra per completare il processo di registrazione del dispositivo.

### Registrazione di più lettori Windows 10 con una configurazione {#registering-multiple-windows-players-with-one-configuration}

Una volta installato il lettore Windows, è possibile registrare più lettori con una configurazione.

>[!NOTE]
>
>**Registrazione di massa di Windows Player**
>
>Quando si implementa Windows Player non è necessario configurare manualmente ogni singolo lettore. Al contrario, potete aggiornare il file JSON di configurazione dopo che è stato testato ed è pronto per la distribuzione.
>
>La configurazione assicurerà che tutti i lettori eseguano il ping dello stesso server fornito nel file di configurazione. È comunque necessario registrare manualmente ogni lettore.

Per configurare Windows 10 Player, effettuate le seguenti operazioni:

1. Installare Windows Player.
1. Trovate il file di configurazione in ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Aggiornate il JSON di configurazione utilizzando le informazioni riportate di seguito, quindi copiate la stessa cartella in tutti i sistemi in cui risiede il lettore.

### Attributi dei criteri {#policy-attributes}

La tabella seguente riassume gli attributi del criterio con un JSON di esempio per riferimento:

| **Nome criterio** | **Scopo** |
|---|---|
| server | URL del server Adobe Experience Manager (AEM). |
| risoluzione | La risoluzione del dispositivo. |
| RestartSchedule | Pianificazione del riavvio del lettore. |
| enableAdminUI | Abilita l’interfaccia utente amministratore per configurare il dispositivo sul sito. Impostato su false una volta configurato completamente e in produzione. |
| enableOSD | Abilitare l&#39;interfaccia utente dello switcher di canale per consentire agli utenti di cambiare canale sul dispositivo. Considerate l&#39;impostazione su false una volta che è completamente configurato e in produzione. |
| enableActivityUI | Consente di visualizzare l&#39;avanzamento delle attività quali download e sincronizzazione. Abilitate per la risoluzione dei problemi e disattivate una volta configurato completamente e in produzione. |

#### Esempio di file JSON dei criteri {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

