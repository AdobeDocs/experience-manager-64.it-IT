---
title: Modifica del logo dell’organizzazione per il branding
seo-title: Changing the organization logo for branding
description: Per assegnare il marchio all’area di lavoro AEM Forms, fornisci il logo della tua organizzazione personalizzando il logo predefinito.
seo-description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---

# Modifica del logo dell’organizzazione per il branding {#changing-the-organization-logo-for-branding}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il logo dell’organizzazione viene visualizzato nell’angolo in alto a sinistra dell’area di lavoro di AEM Forms. Per aggiornare il logo, segui la [Passaggi generici della personalizzazione dell’area di lavoro AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) e quindi i seguenti passaggi.

1. Creare un logo e denominare il file come `NewWorkspace.png`. Posiziona il file immagine nella cartella /apps/ws/images utilizzando un client WebDAV.

   >[!NOTE]
   >
   >La dimensione consigliata dell&#39;immagine logo è 218 px × 20 px.

   >[!NOTE]
   >
   >Per ulteriori informazioni sull&#39;accesso a WebDAV, vedi [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Fare riferimento alla nuova immagine del logo nel foglio di stile /apps/ws/css/newStyle.css aggiungendo il seguente stile.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```
