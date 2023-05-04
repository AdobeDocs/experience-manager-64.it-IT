---
title: Schermata principale
seo-title: Home screen
description: Descrizione dei componenti della schermata iniziale dell’app AEM Forms
seo-description: Description of the components of the AEM Forms app Home screen
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
exl-id: b8f515fd-7ab7-4237-9a35-2840f708e856
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# Schermata principale {#home-screen}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando accedi all’app AEM Forms, vieni reindirizzato alla schermata iniziale.

## Schermata Home predefinita {#default-home-screen}

Per impostazione predefinita, nella schermata iniziale sono visualizzati tutti i moduli, compresi i punti di avvio e le attività (se il server connesso è abilitato per AEM Forms Workflow), insieme alle miniature associate. Puoi specificare le miniature nel server AEM Forms.

La figura seguente viene annotata con le chiamate ai componenti essenziali nella schermata iniziale predefinita.
![Schermata iniziale dell’app Forms](assets/home-screen-1.png)
[Fare clic per ingrandire](assets/home-screen-1-1.png)

1. **Pulsante Menu**: Tocca **Menu** per passare a Attività, Forms, Posta in uscita e Impostazioni. Se l’app AEM Forms è connessa a un server JEE di AEM Forms, puoi visualizzare l’opzione Attività . L&#39;opzione Task consente inoltre di memorizzare le bozze create dalle attività in un processo. Per i server OSGi di AEM Forms, l&#39;opzione Attività è nascosta. In Posta in uscita vengono memorizzati i moduli salvati e le bozze prima della sincronizzazione con il server. Tutti i moduli e le bozze salvati nella casella in uscita vengono caricati sul server AEM Forms quando l’app è [sincronizzato con il server](/help/forms/using/sync-app.md). Per informazioni sulle impostazioni, consulta [Aggiorna impostazioni generali](/help/forms/using/update-general-settings.md).
1. **Attività o modulo**: Toccare l’attività o il modulo elencato con cui si desidera lavorare.
1. **Ellissi orizzontale**: Indica che per il modulo sono disponibili azioni. Tocca i puntini di sospensione per visualizzare le azioni e le descrizioni fornite dall’autore. La **Elimina bozza** e **Completa** è visibile quando tocchi i puntini di sospensione.
1. **Icona Aggiorna**: Tocca l’icona di aggiornamento per sincronizzare l’app con il server AEM Forms.

## Personalizzazione della schermata iniziale {#customizing-the-home-screen}

![Impostazioni generali](assets/gen-settings.png)

Puoi modificare la schermata iniziale predefinita dell’app da **[Impostazioni generali](/help/forms/using/update-general-settings.md)** dell&#39;app o dal **Preferenza** in HTML Workspace.

La modifica apportata all’impostazione della schermata iniziale sull’app ha effetto sulla schermata iniziale dell’utente attualmente registrato o sul dispositivo mobile corrente.

Tuttavia, la modifica apportata in HTML Workspace ha effetto su tutti gli utenti delle app AEM Forms che hanno effettuato l’accesso al server AEM Forms.
