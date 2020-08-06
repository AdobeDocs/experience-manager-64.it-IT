---
title: Supporto per crittografia per le proprietà di configurazione
seo-title: Supporto per crittografia per le proprietà di configurazione
description: 'null'
seo-description: 'null'
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---


# Supporto per crittografia per le proprietà di configurazione{#encryption-support-for-configuration-properties}

## Panoramica {#overview}

Questa funzione consente di memorizzare tutte le proprietà di configurazione OSGi in un modulo crittografato protetto anziché in un testo non crittografato. Il modulo nell’interfaccia utente della console Web viene utilizzato per creare testo cifrato da testo nitido utilizzando la chiave master di crittografia a livello di sistema.

È stato aggiunto il supporto del plug-in di configurazione OSGi per decrittografare la proprietà prima che venga utilizzata da un servizio.

>[!NOTE]
>
>I servizi che prevedono un valore crittografato devono utilizzare il controllo IsProtected per verificare se il valore è crittografato prima di tentare di decrittografarlo, in quanto potrebbe essere già stato decrittografato.

## Abilitazione del supporto per la crittografia {#enabling-encryption-support}

Questi passaggi mostrano come crittografare la password SMTP per il servizio Mail. Per una proprietà OSGI che si desidera cifrare, è possibile completare i passaggi indicati di seguito.

1. Andate alla console Web AEM all&#39;indirizzo *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Nell&#39;angolo in alto a sinistra, andate a **Main - Crypto Support**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Viene visualizzata la pagina **Adobe Experience Manager Web Console Crypto Support** .

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. Nel campo Testo **** normale, immettere il testo dei dati sensibili da proteggere.
1. Selezionate **Protect**. Il testo protetto viene visualizzato come testo crittografato.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Copiare il testo protetto dal passaggio 5 e incollarlo nel valore Modulo OSGI. In questo esempio, la password **** SMTP crittografata viene aggiunta al servizio *di posta* Day CQ.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Salvare le proprietà Day CQ Mail Service. La password SMTP verrà ora inviata come valore crittografato.

## Supporto per decrittazione {#decryption-support}

AEM ora fornisce un plug-in di configurazione per decifrare le proprietà di configurazione. Questo plug-in AEM decrittograferà automaticamente e recupererà le proprietà di testo chiare.
