---
title: Implementazione di Android Player
seo-title: Implementazione di Android Player
description: 'Segui questa pagina per imparare l''implementazione di Android Watchdog, una soluzione per recuperare il lettore da arresti anomali. '
seo-description: 'Segui questa pagina per imparare l''implementazione di Android Watchdog, una soluzione per recuperare il lettore da arresti anomali. '
uuid: 37527a6a-dcc5-4256-abeb-e1f95ff80be4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: e6ec1641-4323-4c79-b932-b857feb1df21
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Implementazione di Android Player {#implementing-android-player}

Un ***cane da guardia*** è una soluzione per recuperare il giocatore da arresti anomali. Un&#39;applicazione deve registrarsi presso il servizio di controllo e inviare periodicamente messaggi al servizio che è attivo. Nel caso in cui il servizio di controllo non riceva un messaggio keep-alive entro un tempo stabilito, il servizio tenta di riavviare il dispositivo per un ripristino pulito (se dispone dei privilegi sufficienti) o di riavviare l&#39;applicazione.

## Implementazione di Android Watchdog {#implementing-android-watchdog}

A causa dell&#39;architettura di Android, il riavvio del dispositivo richiede che l&#39;applicazione disponga dei privilegi di sistema. A tal fine, è necessario firmare l&#39;apk utilizzando i tasti di firma del produttore. In caso contrario, watchdog riavvierà l&#39;applicazione del lettore e non riavvierà il dispositivo.

### Segnalazione di apk Android con produttore chiavi {#signage-of-android-apks-using-manufacturer-keys}

Per accedere ad alcune delle API privilegiate di Android quali *PowerManager* o *HDMIControlServices*, è necessario firmare l&#39;app Android utilizzando le chiavi del produttore.

>[!CAUTION]
>
>Prerequisiti:
>
>Prima di eseguire i seguenti passaggi, devi installare l’SDK Android.

Seguite i passaggi indicati di seguito per firmare il disco Android utilizzando i tasti del produttore:

1. Scaricate l&#39;app da Google Play o dalla pagina dei download [](https://download.macromedia.com/screens/) di AEM Screens Player
1. Ottenete le chiavi della piattaforma dal produttore per ottenere un *pk8* e un file *pem*

1. Individuate lo strumento apksigner in android sdk utilizzando trova ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;percorso> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Trovare il percorso dello strumento di allineamento zip in android sdk
1. &lt;percorso> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Installare ***aemscreensalign.apk*** utilizzando l&#39;installazione adb nel dispositivo

## Implementazione Android Watchdog {#android-watchdog-implementation}

Il servizio di controllo Android è implementato come plug-in cordova utilizzando *AlarmManager*.

Il diagramma seguente mostra l’implementazione del servizio di controllo:

![chlimage_1-43](assets/chlimage_1-43.png)

**1. Inizializzazione** Al momento dell&#39;inizializzazione del plug-in cordova, le autorizzazioni vengono verificate per verificare se disponiamo dei privilegi di sistema e quindi dell&#39;autorizzazione Riavvia. Se questi due criteri vengono soddisfatti, viene creato un Intento in sospeso per il riavvio, altrimenti viene creato un Intento in sospeso per riavviare l&#39;applicazione (in base all&#39;attività di avvio).

**2. Mantieni timer** attivo Un timer per mantenere in vita viene utilizzato per attivare un evento ogni 15 secondi. In questo caso, è necessario annullare l&#39;intento in sospeso esistente (per riavviare o riavviare l&#39;app) e registrare un nuovo intento in sospeso per gli stessi 60 secondi in futuro (in sostanza, posticipare il riavvio).

>[!NOTE]
>
>In Android, *AlarmManager* viene utilizzato per registrare gli *pendingIntents* che possono essere eseguiti anche se l&#39;app si è bloccata e la relativa consegna dell&#39;allarme non è esatta dall&#39;API 19 (Kitkat). Mantenere una certa distanza tra l&#39;intervallo del timer e l&#39;allarme di *AlarmManager* *pendingIntent* .

**3. Arresto anomalo** dell&#39;applicazione In caso di arresto anomalo, l&#39;intento in sospeso per il riavvio registrato con AlarmManager non viene più reimpostato ed esegue quindi un riavvio o un riavvio dell&#39;app (a seconda delle autorizzazioni disponibili al momento dell&#39;inizializzazione del plug-in cordova).
