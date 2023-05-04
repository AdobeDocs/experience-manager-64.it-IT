---
title: Gestori di accesso singolo e timeout
seo-title: Single Sign On and timeout handlers
description: Come impostare il valore di timeout della sessione per l’area di lavoro AEM Forms.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 3%

---

# Gestori di accesso singolo e timeout {#single-sign-on-and-timeout-handlers}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L&#39;area di lavoro di AEM Forms è abilitata per SSO. Se un utente ha effettuato l’accesso a un’applicazione AEM Forms come l’interfaccia utente di Forms Manager o PDF Generator e accede all’area di lavoro di AEM Forms nella stessa sessione del browser, l’utente ha effettuato l’accesso all’area di lavoro di AEM Forms e viceversa.

## Gestione del timeout del server nell’area di lavoro di AEM Forms {#handling-server-timeout-in-nbsp-aem-forms-workspace}

Il timeout della sessione per un utente può essere configurato nella console di amministrazione.

Per impostare il timeout, accedi a `https://[server]:[port]/adminui`, passa a **Impostazioni > Gestione utente > Configurazione > Configura attributi di sistema avanzati** e imposta le impostazioni desiderate.

In AEM Forms il timeout dell’area di lavoro viene gestito come segue:

* La durata della sessione per un utente è disponibile in risposta a `initialize` chiamata che inizializza la sessione utente.
* Una finestra di dialogo a comparsa notifica all’utente che la sessione sta per scadere, 15 secondi prima della scadenza della sessione.

In questa finestra di dialogo a comparsa:

* Fare clic su OK per terminare la sessione utente.
* Fare clic su Annulla per reinizializzare la sessione utente.

>[!NOTE]
>
>Se non viene eseguita alcuna azione, l’utente viene disconnesso automaticamente dall’area di lavoro di AEM Forms tre secondi prima della scadenza della sessione.
