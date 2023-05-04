---
title: NON PUBBLICARE l'interfaccia utente basata su ruolo in Gestione della corrispondenza
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: NON PUBBLICARE l'interfaccia utente basata su ruolo in Gestione della corrispondenza
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---


# NON PUBBLICARE l&#39;interfaccia utente basata su ruolo in Gestione della corrispondenza {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In AEM, l’amministratore può fornire un accesso basato su ruoli a diversi gruppi di utenti che esegue varie azioni su risorse diverse. Ad esempio, la funzionalità per creare o modificare i dizionari di dati potrebbe essere disponibile solo per gli utenti di un gruppo di utenti specifico, mentre altri utenti potrebbero visualizzare e utilizzare solo i dizionari di dati.

L’interfaccia AEM visualizza le opzioni, ad esempio per creare o modificare un tipo di risorsa, in base al livello di accesso di un utente. Ad esempio, se un utente non dispone delle autorizzazioni necessarie per creare un dizionario dati, l’opzione per creare un dizionario dati non viene visualizzata nell’interfaccia utente.

Sebbene CRX ti consenta di configurare i diritti di accesso per account utente e gruppi, questo articolo tratta i diritti di accesso basati su ruolo o gruppo di utenti.

Per ulteriori informazioni su gruppi, autorizzazioni, elenchi di controllo degli accessi e gestione di utenti e gruppi, consulta [Amministrazione degli utenti e sicurezza](/help/sites-administering/security.md).

## Gestione delle autorizzazioni {#managing-permissions}

1. Assicurati che l&#39;utente per il quale desideri gestire le autorizzazioni sia aggiunto al gruppo di utenti interessato.

   Ad esempio, l’utente John Doe viene aggiunto ai gruppi `agents` e `cm-creditcard`. Per ulteriori informazioni, vedere Aggiunta di utenti o gruppi a un gruppo. Per ulteriori informazioni, consulta [Gestione di utenti e gruppi di utenti](/help/communities/users.md).

   ![]()

1. Crea le cartelle in modo da consentire le autorizzazioni desiderate.

   Ad esempio, se un&#39;azienda dispone di divisioni mutui, carte di credito e assicurazioni per la casa, può creare cartelle denominate `HomeMortgage`, `CreditCard,`e `Insurance` mantenere le attività rilevanti e consentire l&#39;accesso selettivo agli agenti solo per le attività rilevanti per i loro dipartimenti.

1. Per accedere AEM protezione WCM, effettuare una delle seguenti operazioni:

   1. Nella schermata introduttiva o in diverse aree di AEM, fai clic sull’icona di protezione :

   1. Passa direttamente a `https://[server]:[port]/useradmin`. Assicurati di accedere a AEM come amministratore.

      ![]()
   Nella struttura ad albero a sinistra sono elencati tutti gli utenti e i gruppi attualmente presenti nel sistema. È possibile selezionare le colonne desiderate, ordinare il contenuto delle colonne e persino modificare l’ordine di visualizzazione delle colonne trascinando l’intestazione della colonna in una nuova posizione.

   Le schede consentono di accedere a varie configurazioni:

1. Nell’elenco ad albero a sinistra, tocca due volte il nome del gruppo interessato e seleziona la scheda Autorizzazioni .

   Per individuare il nome del gruppo, è possibile digitare il nome del gruppo nello spazio fornito.

1. Nella scheda Autorizzazioni , individua il percorso a cui desideri aggiungere le autorizzazioni. Le cartelle Gestione Corrispondenza si trovano in `content/apps/cm/` cartella.

   Selezionare la casella di controllo nella colonna Membro per i membri che si desidera disporre delle autorizzazioni per tale percorso. Deselezionare la casella di controllo relativa al membro per il quale si desidera rimuovere le autorizzazioni. Nella cella in cui sono state apportate modifiche viene visualizzato un triangolo rosso.

   ![scheda di credito useradmin](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Le autorizzazioni specificate in una cartella sostituiscono le autorizzazioni specificate nelle relative sottocartelle.

1. Tocca Salva.
1. Testo del passaggio
1. Testo del passaggio
1. Testo del passaggio

