---
title: NON PUBBLICARE l'interfaccia utente basata su ruolo in Gestione della corrispondenza
seo-title: NON PUBBLICARE l'interfaccia utente basata su ruolo in Gestione della corrispondenza
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 1%

---


# NON PUBBLICARE l&#39;interfaccia utente basata su ruolo in Gestione corrispondenza {#do-not-publish-role-based-user-interface-in-correspondence-management}

In AEM, l&#39;amministratore può fornire l&#39;accesso basato sui ruoli a diversi gruppi di utenti, eseguendo varie azioni su risorse diverse. Ad esempio, la funzionalità di creazione o modifica dei dizionari di dati potrebbe essere disponibile solo per gli utenti di un determinato gruppo di utenti, mentre altri utenti potrebbero visualizzare e utilizzare solo i dizionari di dati.

L&#39;interfaccia AEM visualizza le opzioni, ad esempio per creare o modificare un tipo di risorsa, in base al livello di accesso di un utente. Ad esempio, se un utente non dispone delle autorizzazioni necessarie per creare un dizionario dati, l&#39;opzione per creare un dizionario dati non viene visualizzata nell&#39;interfaccia utente.

Sebbene CRX consenta di configurare i diritti di accesso per gli account utente e per i gruppi, questo articolo riguarda i diritti di accesso basati su ruoli o gruppi di utenti.

Per ulteriori informazioni su gruppi, autorizzazioni, elenchi di controllo degli accessi e gestione di utenti e gruppi, vedere [Amministrazione utente e sicurezza](/help/sites-administering/security.md).

## Gestione delle autorizzazioni {#managing-permissions}

1. Accertatevi che l’utente per il quale desiderate gestire le autorizzazioni sia aggiunto al gruppo di utenti interessato.

   Ad esempio, l&#39;utente John Doe viene aggiunto ai gruppi `agents` e `cm-creditcard`. Per ulteriori informazioni, consultate Aggiunta di utenti o gruppi a un gruppo. Per ulteriori informazioni, vedere [Gestione di utenti e gruppi di utenti](/help/communities/users.md).

   ![]()

1. Create le cartelle in base alle autorizzazioni desiderate.

   Ad esempio, se un&#39;azienda possiede divisioni di mutuo per la casa, carta di credito e assicurazione, può creare cartelle denominate `HomeMortgage`, `CreditCard,`e `Insurance` per mantenere le attività rilevanti e consentire l&#39;accesso selettivo agli agenti solo per le attività rilevanti per i loro reparti.

1. Per accedere AEM protezione WCM, effettuare una delle seguenti operazioni:

   1. Nella schermata introduttiva o in diverse aree di AEM, fate clic sull’icona relativa alla protezione:

   1. Andate direttamente a `https://[server]:[port]/useradmin`. Assicuratevi di accedere AEM come amministratore.

      ![]()
   Nella struttura ad albero a sinistra sono elencati tutti gli utenti e i gruppi attualmente presenti nel sistema. È possibile selezionare le colonne desiderate, ordinare il contenuto delle colonne e persino modificare l&#39;ordine di visualizzazione delle colonne trascinando l&#39;intestazione della colonna in una nuova posizione.

   Le schede forniscono l&#39;accesso a varie configurazioni:

1. Nell’elenco della struttura a sinistra, toccate due volte il nome del gruppo interessato e selezionate la scheda Autorizzazioni.

   Per individuare il nome del gruppo, potete digitare il nome del gruppo nello spazio disponibile.

1. Nella scheda Autorizzazioni, andate al percorso al quale desiderate aggiungere le autorizzazioni. Le cartelle Gestione corrispondenza si trovano nella cartella `content/apps/cm/`.

   Selezionate la casella di controllo nella colonna Membro per i membri per i quali desiderate disporre delle autorizzazioni per tale percorso. Deselezionare la casella di controllo relativa al membro per il quale si desidera rimuovere le autorizzazioni. Nella cella a cui sono state apportate modifiche viene visualizzato un triangolo rosso.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Le autorizzazioni specificate in una cartella sostituiscono quelle specificate nelle relative sottocartelle.

1. Toccate Salva.
1. Testo del passaggio
1. Testo del passaggio
1. Testo del passaggio

