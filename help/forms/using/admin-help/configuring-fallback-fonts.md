---
title: Configurazione dei font di fallback
seo-title: Configuring fallback fonts
description: Scopri come configurare i font di fallback.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---

# Configurazione dei font di fallback {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile configurare manualmente il file FontManagerResources.properties per mappare i font predefiniti dei moduli AEM a fallback (o sostituzione) se i font predefiniti non sono disponibili sul server. Questo file di proprietà si trova nel file adobe-fontmanager.jar .

>[!NOTE]
>
>La configurazione dei font di fallback si applica anche al servizio assembler.

1. Passa a adobe-livecycle-*[appserver]* file .ear nel *[root di aem forms]*/configurationManager/export directory, crea una copia di backup e scompone l&#39;originale.
1. Individua il file adobe-fontmanager.jar e decrea il pacchetto.
1. Individua il file FontManagerResources.properties e aprilo in un editor di testo.
1. Modifica le posizioni e i nomi dei font Generico e Fallback come richiesto e salva il file.

   Le voci di font nel file FontManagerResources.properties sono relative al *[root di aem forms]*/fonts directory. Se si specificano font che non sono predefiniti AEM font dei moduli, è necessario installarli all’interno di questa struttura di directory (all’interno di una directory esistente o in una directory appena creata).

   >[!NOTE]
   >
   >Se il font o il font predefinito specificato non contiene un carattere unicode specifico o se non è disponibile, il carattere viene tratto da un font di fallback in base alla seguente priorità:

   * Font specifico per le impostazioni internazionali
   * Font ROOT se le impostazioni internazionali non sono impostate
   * Font generico, ricercato per ordine impostato nella tabella di fallback

1. Ricomprimi il file adobe-fontmanager.jar.
1. Ricompila il pacchetto adobe-livecycle-*[appserver]*.ear e quindi ridistribuirlo manualmente o eseguendo Configuration Manager.

>[!NOTE]
>
>Non utilizzare Configuration Manager per creare un nuovo pacchetto di adobe-livecycle-[appserver]file .ear perché le modifiche verranno sovrascritte con i valori predefiniti dei moduli AEM.
