---
title: Implementazione di Chrome OS Player
seo-title: Implementazione di Chrome OS Player
description: 'Segui questa pagina per saperne di più sull''implementazione di Chrome OS Player tramite la console di gestione Chrome.  '
seo-description: 'Segui questa pagina per saperne di più sull''implementazione di Chrome OS Player tramite la console di gestione Chrome.  '
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Implementazione di Chrome OS Player {#implementing-chrome-os-player}

Questa sezione descrive come implementare Chrome OS Player utilizzando la console di gestione Chrome.

## Utilizzo della console di gestione Chrome {#using-chrome-management-console}

Per impostare la console di gestione di Chrome, effettuate le seguenti operazioni:

1. Registrati nella console di gestione Chrome. È necessario ottenere una licenza per Chrome Management Console. Per ulteriori informazioni, contattate [Google Support](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995) per gestire le impostazioni del dispositivo Chrome.
1. Iscrivere il dispositivo Chrome OS nel dominio attendere 15 minuti affinché il dispositivo si sincronizzi con la console di gestione Chrome. Per ulteriori informazioni sulla registrazione del dispositivo chrome, fare clic [qui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player sarà disponibile nello store Web Chrome.

>[!NOTE]
>
>Per l&#39;implementazione e la gestione dei dispositivi Chrome OS si consiglia una soluzione di gestione dei dispositivi, come la console di gestione Chrome. Anche se, questo documento fornisce l&#39;implementazione per Chrome Management Console ci sono altri fornitori che affermano di fornire funzionalità simili. Contattare il fornitore del software di gestione dei dispositivi.

### Abilitazione della modalità Kiosk {#enabling-kiosk-mode}

Per attivare la modalità Kiosk, effettuate le seguenti operazioni:

1. Accedete a Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Passare a Gestione **** dispositivo → Gestione **** Chrome → Impostazioni **dispositivo**.
1. Scorri verso il basso fino a **Kiosk Settings (Impostazioni** chiosco) e fai clic su **Manage Kiosk Applications (Gestisci applicazioni** chiosco).

   ![chiosco](assets/kiosk.png)

1. Selezionate AEM Screens Player dal Chrome Web Store.

   >[!NOTE]
   >
   >La visualizzazione di un&#39;app pubblicata di recente potrebbe richiedere circa 15 minuti.

1. Selezionate **AEM Screens Player** dal menu a discesa **Auto Launch Kiosk App** .

   L&#39;applicazione delle modifiche potrebbe richiedere alcuni minuti a seconda della rete. È consigliabile riavviare il sistema.

#### Controllo dello stato del dispositivo remoto {#checking-remote-device-status}

1. Accedete a Chrome Developer Console.
1. Passa a Gestione **** dispositivo → Dispositivi **** Chrome e seleziona il dispositivo che desideri controllare.

1. Fate clic su Attività **di sistema e risoluzione dei problemi**.
1. Controllare le proprietà **Reboot Device** e **Screen Capture** del dispositivo. Potete inoltre controllare lo stato del dispositivo e le informazioni sullo stato di salute.

>[!NOTE]
>
>Tenete presente che queste impostazioni possono essere attivate alcuni minuti dopo che il dispositivo è stato registrato. Ogni opzione può diventare abilitata nel tempo.

### Configurazione della configurazione remota dei lettori del sistema operativo Chrome {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player è un&#39;applicazione abilitata per il chiosco che abilita anche la configurazione dei criteri remoti per i lettori di sistema operativo Chrome.

Seguite i passaggi riportati di seguito per configurare le varie opzioni del lettore:

1. Accedi alla console di gestione Chrome.
1. Fate clic su Gestione **** dispositivo → Gestione **** Chrome → Gestione **app**. Nell&#39;elenco viene visualizzato AEM Screens Player.

1. Fate clic sull’applicazione **AEM Screens Player**.
1. Fate clic sulle impostazioni **** Kiosk e selezionate la vostra organizzazione (*se utilizzate un ambiente* di test).

1. Fate clic su **Carica file** di configurazione e caricate il criterio di configurazione (file ** Json).

1. Fai clic su **Salva**. Per sincronizzare il criterio dovete riavviare il dispositivo.

>[!NOTE]
>
>Riavviate il dispositivo per sincronizzare le modifiche ai criteri.

#### Esempio di file JSON per i criteri {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Attributi e finalità del criterio {#policy-attributes-and-purpose}

Nella tabella seguente sono riepilogati i criteri con le relative funzioni.

| **Nome criterio** | **Scopo** |
|---|---|
| *server* | URL di Adobe Experience Manager Server |
| *risoluzione* | La risoluzione del dispositivo Chrome OS |
| *RestartSchedule* | La pianificazione per riavviare il lettore Chrome |
| *enableAdminUI* | Abilita l’interfaccia utente amministratore per i tecnici che configurano il dispositivo sul sito. Impostato su false una volta configurato completamente e in produzione. |
| *enableOSD* | Abilitare l&#39;interfaccia utente dello switcher di canale per consentire agli utenti di cambiare canale sul dispositivo. Considerate l&#39;impostazione su false una volta che è completamente configurato e in produzione. |
| *enableActivityUI* | Consente di visualizzare l&#39;avanzamento delle attività quali download e sincronizzazione. Abilitate per la risoluzione dei problemi e disattivate una volta configurato completamente e in produzione. |

>[!NOTE]
>
>Le configurazioni dei criteri vengono applicate in modo rigoroso e non vengono sostituite manualmente nell&#39;interfaccia utente di amministrazione del lettore. Per consentire la configurazione manuale del lettore per un criterio specifico, non specificare il criterio nella configurazione del ***criterio,*** ad esempio, se si desidera consentire la configurazione manuale per la pianificazione del riavvio, non specificare la chiave ***RestartSchedule*** nella configurazione del criterio.

