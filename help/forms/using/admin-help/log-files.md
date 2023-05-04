---
title: File di registro
seo-title: Log files
description: Eventi quali errori di esecuzione o di avvio vengono registrati nei file di registro dell'application server, che possono essere aperti utilizzando qualsiasi editor di testo.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 4%

---

# File di registro {#log-files}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Eventi quali errori di esecuzione o di avvio vengono registrati nei file di registro dell&#39;application server. In caso di problemi durante l&#39;implementazione nel server dell&#39;applicazione, è possibile utilizzare i file di registro per trovare il problema. È possibile aprire i file di registro utilizzando qualsiasi editor di testo.

(JBoss) I seguenti file di log si trovano nella `*[appserver root]*/server/*[server]*/log` directory:

* boot.log
* server.log.*[aaaa-mm-gg]*
* server.log

I file di registro del dominio (WebLogic) si trovano nella *[appserverdomain]* e i file di registro del server si trovano nel *[appserverdomain]/server/[nome appserver]/logs *directory:

* access.log
* *[nome appserver]*.log
* *[nome appserver]* Fuori.*[numero incrementale]*

(WebSphere) I seguenti file di log si trovano nella *[root appserver]*/profiles/default/logs/*[nome appserver]* directory:

* SystemErr.log
* SystemOut.log
* StartServer.log
