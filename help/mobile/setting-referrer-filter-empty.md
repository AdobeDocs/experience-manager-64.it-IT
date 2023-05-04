---
title: Impostazione del filtro di riferimento per consentire l'utilizzo vuoto
seo-title: Setting Your Referrer Filter to Allow Empty
description: Segui questa pagina per informazioni sul filtro referente. Per consentire ad AEM Mobile Application Viewer di visualizzare le app nell’istanza di authoring, è necessario impostare il filtro di riferimento HTML su "Consenti vuoto".
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

---

# Impostazione del filtro di riferimento per consentire l&#39;utilizzo vuoto{#setting-your-referrer-filter-to-allow-empty}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Adobe consiglia di utilizzare l’editor di SPA per i progetti che richiedono il rendering lato client basato sul framework di un’applicazione a pagina singola (ad esempio, React). [Ulteriori informazioni](/help/sites-developing/spa-overview.md).

Per consentire ad AEM Mobile Application Viewer di visualizzare le app nell’istanza di authoring, è necessario impostare il filtro di riferimento HTML su &quot;Consenti vuoto&quot;.

Se non si intende utilizzare il Visualizzatore applicazioni per rivedere le applicazioni negli stati di sviluppo e di staging, non è necessario modificare l&#39;impostazione predefinita del filtro referente.

Nell’istanza di authoring di AEM in esecuzione, passa a: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) e cerca &#39;Apache Sling Referrer Filter&#39;. Fai clic su per modificare il filtro del referente e seleziona la casella di controllo &quot;Consenti vuoto&quot; (vedi l&#39;immagine seguente). Quindi premi il pulsante salva e chiudi la pagina del browser.

![Impostazioni filtro referente](assets/chlimage_1-106.png)
