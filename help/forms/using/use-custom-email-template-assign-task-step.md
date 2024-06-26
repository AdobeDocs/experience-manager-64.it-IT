---
title: Utilizzare modelli e-mail personalizzati in un passaggio Assegna attività
seo-title: Use custom email templates in an Assign Task step
description: Modelli e-mail personalizzati per le notifiche e-mail del flusso di lavoro dei moduli
seo-description: Custom email templates for forms workflow email notifications
uuid: bc2af94d-d4ad-417e-b3d2-bcfffc1b306d
topic-tags: publish
discoiquuid: c447fc39-c0f3-4932-ac6c-465d1fb83f8c
exl-id: 5af73823-2c32-41b3-9ab8-a7ad9fd9532f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Utilizzare modelli e-mail personalizzati in un passaggio Assegna attività {#use-custom-email-templates-in-an-assign-task-step}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Modelli e-mail personalizzati per le notifiche e-mail del flusso di lavoro dei moduli

È possibile utilizzare il passaggio Assegna attività per creare e assegnare attività a un utente o a un gruppo. Quando un’attività viene assegnata a un utente o a un gruppo, viene inviata una notifica e-mail all’utente definito o a ciascun membro del gruppo definito. Una tipica notifica e-mail contiene il collegamento dell’attività assegnata e le informazioni relative all’attività. L’immagine seguente mostra un esempio di notifica e-mail:

![Notifica via e-mail con modello preconfigurato](do-not-localize/default-email-template.png)

Puoi personalizzare l’aspetto e utilizzare metadati personalizzati in una notifica e-mail. AEM Forms fornisce un modello preconfigurato per le notifiche e-mail. Puoi personalizzare il modello preconfigurato o creare un nuovo modello da zero.

I modelli di notifica e-mail si basano su [E-mail HTML](https://en.wikipedia.org/wiki/HTML_email). Queste e-mail si adattano a diversi client e-mail e dimensioni dello schermo. Inoltre, lo stile dell’e-mail è definito all’interno del modello.

L’immagine seguente mostra una notifica e-mail personalizzata:

![Notifica tramite e-mail utilizzando un modello personalizzato](do-not-localize/customized-email.png)

## Personalizzare il modello esistente {#customize-the-existing-template}

Con AEM Forms è disponibile un modello per le notifiche e-mail. Il modello fornisce la descrizione del titolo, la data di scadenza, la priorità, il nome del flusso di lavoro e il collegamento dell’attività assegnata. È possibile personalizzare il modello per modificare l’aspetto. Esegui i seguenti passaggi per personalizzare il modello:

1. Accedi a CRXDE con l&#39;account amministratore.

1. Passa a /libs/fd/dashboard/templates/email.

1. Apri il file htmlEmailTemplate.txt . Contiene il modello predefinito.

1. Sostituisci il contenuto del file htmlEmailTemplate.txt con contenuto personalizzato.

   Un modello di notifica e-mail è un [E-mail HTML](https://en.wikipedia.org/wiki/HTML_email). Puoi sostituire il codice HTML esistente con il codice personalizzato per modificare l’aspetto del modello.

1. Salva il file. Ora il modello personalizzato è pronto per l’uso.

## Creare un modello e-mail {#create-an-email-template}

Con AEM Forms è disponibile un modello per le notifiche e-mail. Il modello fornisce la descrizione del titolo, la data di scadenza, la priorità, il nome del flusso di lavoro e il collegamento dell’attività assegnata. È inoltre possibile aggiungere un modello e-mail personalizzato (il proprio modello) per i passaggi dell’attività Assegna. Esegui i seguenti passaggi per aggiungere un modello e-mail personalizzato:

1. Accedi a CRXDE con l&#39;account amministratore.

1. Passa a /libs/fd/dashboard/templates/email.

1. Crea un file .txt. Ad esempio, EmailOnTaskAssign.txt.

1. Aggiungi il codice HTML personalizzato al file .

   Un modello di notifica e-mail è un [E-mail HTML](https://en.wikipedia.org/wiki/HTML_email). Puoi aggiungere codice HTML personalizzato al file per creare un nuovo modello.

1. Salva il file. Il modello è pronto per essere utilizzato nel passaggio Assegna attività.

## Utilizzare un modello e-mail in un passaggio Assegna attività {#use-an-email-template-in-an-assign-task-step}

Il passaggio dell’attività Assegna è configurato in modo da utilizzare il modello predefinito, htmlEmailTemplate.txt. Puoi scegliere di utilizzare un modello personalizzato. Per modificare il modello:

1. Apri **[!UICONTROL Assegna attività]** passo.

1. Passa a **[!UICONTROL Assegnatario > Modello e-mail HTML]**.

1. Selezionare il modello e-mail di HTML appena creato.

1. Fai clic su **[!UICONTROL OK]**. Il modello viene modificato.

Una notifica e-mail utilizza anche [metadati](/help/forms/using/use-metadata-in-email-notifications.md). Ad esempio, data di scadenza, priorità, nome del flusso di lavoro e altro ancora. Puoi anche configurare il modello da utilizzare [metadati personalizzati](/help/forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification).
