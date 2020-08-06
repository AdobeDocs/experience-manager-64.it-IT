---
title: Impostazione del filtro di riferimento per consentire l'utilizzo di elementi vuoti
seo-title: Impostazione del filtro di riferimento per consentire l'utilizzo di elementi vuoti
description: Segui questa pagina per saperne di più sul filtro referente. Per consentire  AEM Mobile Application Viewer di visualizzare le app nell'istanza Author, dovrete impostare il filtro di riferimento HTML su "consenti vuoto".
seo-description: Segui questa pagina per saperne di più sul filtro referente. Per consentire  AEM Mobile Application Viewer di visualizzare le app nell'istanza Author, dovrete impostare il filtro di riferimento HTML su "consenti vuoto".
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
translation-type: tm+mt
source-git-commit: 64090e3c7cf722f44968467c51291a11aeeec237
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Impostazione del filtro di riferimento per consentire l&#39;utilizzo di elementi vuoti{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
> Adobe consiglia di utilizzare SPA Editor per i progetti che richiedono il rendering lato client basato sul framework di applicazioni a pagina singola (ad es. React). [Per saperne di più](/help/sites-developing/spa-overview.md).

Per consentire  AEM Mobile Application Viewer di visualizzare le app nell&#39;istanza Author, dovrete impostare il filtro di riferimento HTML su &quot;consenti vuoto&quot;.

Se non intendete utilizzare il visualizzatore applicazioni per rivedere le applicazioni negli stati di sviluppo e di pre-produzione, non dovete modificare l&#39;impostazione predefinita del filtro di riferimento.

All&#39;interno dell&#39;istanza Author di AEM in esecuzione, passa a: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) e cercate &#39;Filtro di riferimento Apache Sling&#39;. Fate clic per modificare il filtro del referente e selezionate la casella di controllo &quot;Consenti vuoto&quot; (vedete l&#39;immagine sotto). Quindi fate clic sul pulsante Salva e chiudete la pagina del browser.

![Impostazioni filtro referente](assets/chlimage_1-106.png)
