---
title: Schermata principale
seo-title: Schermata principale
description: 'Descrizione dei componenti della schermata iniziale dell’app AEM Forms '
seo-description: 'Descrizione dei componenti della schermata iniziale dell’app AEM Forms '
uuid: 7705b499-8b38-4c2e-abd8-6901cf268428
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e4636b25-20a4-4326-82fb-f22f735e43c0
translation-type: tm+mt
source-git-commit: 79dcf6816e1156604c0c9279b727ea436ad1826a
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Schermata principale {#home-screen}

Quando effettuate l&#39;accesso all&#39;app AEM Forms , viene reindirizzato alla schermata iniziale.

## Schermata iniziale predefinita {#default-home-screen}

Per impostazione predefinita, nella schermata Home sono visualizzati tutti i moduli, inclusi i punti di avvio e le attività (se il server connesso è  AEM Forms Workflow abilitato), insieme alle relative miniature. Potete specificare le miniature nel server AEM Forms .

Nella figura riportata di seguito vengono annotate le chiamate ai componenti essenziali nella schermata iniziale predefinita.
![Forms app home ](assets/home-screen-1.png)
[screenFare clic per ingrandire](assets/home-screen-1-1.png)

1. **Pulsante** menu: Toccate il  **** pulsante Menu per passare ad Attività, Forms, In uscita e Impostazioni. Se l&#39;app AEM Forms  è connessa a un server AEM Forms JEE , potete visualizzare l&#39;opzione Attività. L&#39;opzione Attività memorizza inoltre le bozze create dalle attività in un processo. Per  server AEM Forms OSGi, l’opzione Attività è nascosta. In Output vengono memorizzati i moduli e le bozze salvati prima della sincronizzazione con il server. Tutti i moduli e le bozze salvati nella casella in uscita vengono caricati nel server AEM Forms  quando l&#39;app è [sincronizzata con il server](/help/forms/using/sync-app.md). Per informazioni sulle impostazioni, vedere [Aggiorna impostazioni generali](/help/forms/using/update-general-settings.md).
1. **Attività o modulo**: Toccare l&#39;attività o il modulo elencati con cui si desidera lavorare.
1. **Ellissi** orizzontale: Indica che sono disponibili azioni per il modulo. Toccando i puntini di sospensione vengono visualizzate le azioni e la descrizione fornite dall’autore. L&#39;opzione **Elimina bozza** e **Completa** è visibile quando si toccano i puntini di sospensione.
1. **Icona** Aggiorna: Toccate l&#39;icona di aggiornamento per sincronizzare l&#39;app con il server AEM Forms .

## Personalizzazione della schermata iniziale {#customizing-the-home-screen}

![Impostazioni generali](assets/gen-settings.png)

È possibile modificare la schermata iniziale predefinita dell&#39;app sia dalle **[Impostazioni generali](/help/forms/using/update-general-settings.md)** dell&#39;app, sia dalla scheda **Preferenze** in HTML Workspace.

La modifica apportata alla schermata iniziale dell&#39;app ha effetto sulla schermata iniziale dell&#39;utente attualmente registrato o sul dispositivo mobile corrente.

Tuttavia, la modifica apportata in Area di lavoro HTML ha effetto su tutti  utenti dell&#39;app AEM Forms che hanno eseguito l&#39;accesso al server AEM Forms .

