---
title: Invio di una conferma dell’invio di un modulo via e-mail
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms consente di configurare l’azione di invio tramite e-mail che invia una conferma all’utente al momento dell’invio del modulo.
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# Invio di una conferma dell’invio di un modulo via e-mail {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Invio di dati del modulo adattivo {#adaptive-form-data-submission}

I moduli adattivi forniscono diversi elementi predefiniti [invia azioni](/help/forms/using/configuring-submit-actions.md) flussi di lavoro per l’invio dei dati del modulo a endpoint diversi.

Ad esempio, il **Azione e-mail** l’azione invia invia un’e-mail dopo l’invio di un modulo adattivo. Può anche essere configurato per inviare i dati del modulo e PDF nell’e-mail.

Questo articolo descrive i passaggi per abilitare l’azione E-mail su un modulo adattivo e le diverse configurazioni che fornisce.

>[!NOTE]
>
>È inoltre possibile utilizzare **Azione E-mail PDF** per inviare il modulo compilato via e-mail come allegato di PDF. Le opzioni di configurazione disponibili per questa azione sono le stesse opzioni disponibili per l’azione E-mail. L’azione E-mail PDF è disponibile solo per i moduli adattivi basati su XFA

## Azione e-mail {#email-action}

L’azione E-mail consente all’autore di inviare automaticamente e-mail a uno o più destinatari dopo l’invio corretto di un modulo adattivo.

>[!NOTE]
>
>Per utilizzare l’azione E-mail, è necessario configurare il servizio e-mail AEM come descritto in [Configurazione del servizio di posta](/help/sites-administering/notification.md#configuring-the-mail-service).

### Abilitazione dell’azione E-mail su un modulo adattivo {#enabling-email-action-on-an-adaptive-form}

1. Apri un modulo adattivo in modalità di modifica.

1. Fai clic su **Modifica** accanto al **Inizio di un modulo adattivo** barra degli strumenti.

   Viene visualizzata la finestra di dialogo Modifica componente.

   ![Finestra di dialogo Modifica componente per un modulo adattivo](assets/start_of_adp_form.png)

1. Seleziona la **Inviare azioni** scheda e scegli **Azione e-mail** dall’elenco a discesa Invia azione .

   Nella scheda vengono visualizzate le opzioni per configurare l’azione E-mail per il modulo corrente.

   ![Scheda Azioni di invio](assets/dialog.png)

1. Specifica gli ID e-mail validi nei campi Mailto, CC e CCN.

   Specifica l’oggetto e il corpo dell’e-mail rispettivamente nei campi Oggetto e Modello e-mail .

   È inoltre possibile specificare segnaposto variabili nei campi. In tal caso, i valori dei campi vengono elaborati quando un utente finale invia correttamente il modulo. Per ulteriori informazioni, consulta [Utilizzo dei nomi dei campi del modulo adattivo per creare in modo dinamico contenuti e-mail](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Selezionare Includi allegati se il modulo include allegati di file e si desidera allegare tali file nell&#39;e-mail.

   >[!NOTE]
   >
   >Se scegli la **Azione E-mail PDF**, è necessario selezionare l’opzione Includi allegati .

1. Fai clic su **OK** per salvare le modifiche.

### Utilizzo dei nomi dei campi del modulo adattivo per creare in modo dinamico contenuti e-mail {#using-adaptive-form-field-names-to-dynamically-create-email-content}

I nomi di campo in un modulo adattivo sono denominati segnaposto che vengono sostituiti con il valore di tale campo dopo l’invio del modulo da parte dell’utente.

Nella scheda Azione e-mail puoi utilizzare i segnaposto elaborati al momento dell’esecuzione dell’azione. Ciò implica che le intestazioni dell’e-mail (ad esempio Mailto, CC, CCN, oggetto) vengono generate quando l’utente invia il modulo.

Per definire un segnaposto, specificare `${<field name>}` in un campo della scheda Azioni di invio .

Ad esempio, se il modulo contiene **Indirizzo e-mail** campo denominato `email_addr`, per acquisire l’ID e-mail di un utente, è possibile specificare quanto segue nei campi Mailto, CC o Ccn.

`${email_addr}`

Quando un utente invia il modulo, viene inviata un’e-mail all’ID e-mail immesso nel `email_addr` campo del modulo.

>[!NOTE]
>
>Puoi trovare il nome di un campo nella **Modifica** finestra di dialogo per il campo .

I segnaposto variabili possono essere utilizzati anche nella variabile **Oggetto** e **Modello e-mail** campi.

Ad esempio:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>I campi nei pannelli ripetibili non possono essere utilizzati come segnaposto variabili.
