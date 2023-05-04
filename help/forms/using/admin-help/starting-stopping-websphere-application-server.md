---
title: Avvio e arresto di WebSphere Application Server
seo-title: Starting and stopping WebSphere Application Server
description: Diverse procedure richiedono l’arresto o l’avvio dell’istanza di WebSphere in cui si desidera distribuire i prodotti AEM forms. In questo documento viene descritto come avviare e arrestare WebSphere Application Server.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 8e3bb77f-b187-42c8-a90e-fe0fee50dc34
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# Avvio e arresto di WebSphere Application Server {#starting-and-stopping-websphere-application-server}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Diverse procedure richiedono l’arresto o l’avvio dell’istanza di WebSphere in cui si desidera distribuire i prodotti AEM forms. Se non si è certi che il server applicazioni sia stato avviato, è innanzitutto possibile visualizzare lo stato di WebSphere Application Server.

## Visualizza lo stato di WebSphere Application Server {#view-the-status-of-websphere-application-server}

1. Da un prompt dei comandi, passa alla *[root appserver]*/bin.
1. Immettere il seguente comando, sostituendo *nome_server* con il nome del server applicazioni WebSphere:

   * (Windows) `serverStatus.bat`*nome_server*
   * (Linux, UNIX) ./ `serverStatus.sh`*nome_server*

## Avvia server applicazioni WebSphere {#start-websphere-application-server}

1. Da un prompt dei comandi, passa alla *[root appserver]*/bin.
1. Immettere il seguente comando, sostituendo *nome_server* con il nome del server applicazioni WebSphere:

   * (Windows) `startServer.bat`*nome_server*
   * (Linux, UNIX) ./ `startServer.sh`*nome_server*

## Arresta server applicazioni WebSphere {#stop-websphere-application-server}

1. Da un prompt dei comandi, passa alla *[root appserver]*/bin.
1. Immettere il seguente comando, sostituendo *nome_server* con il nome del server applicazioni WebSphere:

   * (Windows) `stopServer.bat`*nome_server*
   * (Linux, UNIX) ./ `stopServer.sh`*nome_server*
