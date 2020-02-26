---
title: File di registro
seo-title: File di registro
description: Eventi quali errori di esecuzione o di avvio vengono registrati nei file di registro del server applicazione, che possono essere aperti utilizzando qualsiasi editor di testo.
seo-description: Eventi quali errori di esecuzione o di avvio vengono registrati nei file di registro del server applicazione, che possono essere aperti utilizzando qualsiasi editor di testo.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8

---


# Log files {#log-files}

Eventi quali errori di esecuzione o di avvio vengono registrati nei file di registro del server dell&#39;applicazione. In caso di problemi durante l&#39;implementazione nel server dell&#39;applicazione, è possibile utilizzare i file di registro per individuare il problema. Potete aprire i file di registro utilizzando un editor di testo qualsiasi.

(JBoss) I seguenti file di registro si trovano nella `*[appserver root]*/server/*[server]*/log` directory:

* boot.log
* server.log.*[aaaa-mm-gg]*
* server.log

(WebLogic) I file di registro del dominio si trovano nella directory *[appserverdomain]* e i file di registro del server si trovano nella directory *[appserverdomain]/server/nome[]appserver/logs *:

* access.log
* *[appserver name]*.log
* *[nomeappserver]*.out.*[numero incrementale]*

(WebSphere) I seguenti file di registro si trovano nella directory principale *[/profili/default/logs/]* appserver name *[]* :

* SystemErr.log
* SystemOut.log
* StartServer.log

