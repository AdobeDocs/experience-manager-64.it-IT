---
title: Monitoraggio degli eventi
seo-title: Monitoring events
description: Quando la funzionalità di controllo è abilitata, la protezione dei documenti consente di monitorare determinati tipi di eventi. È possibile cercare e ordinare facilmente l’elenco degli eventi utilizzando la protezione del documento.
seo-description: When the auditing capability is enabled, document security enables you to monitor certain types of events. You can easily search and sort the events list using the document security.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
feature: Document Security
exl-id: 0c4a846f-4e31-435b-a6f6-d0b7c4cd1259
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---

# Monitoraggio degli eventi {#monitoring-events}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando la funzionalità di controllo è abilitata, la protezione dei documenti consente di monitorare determinati tipi di eventi. Gli eventi visualizzabili dipendono dal tuo ruolo:

**Utenti:** Può visualizzare gli eventi controllati per i loro documenti protetti da policy e per tutti i documenti protetti che ricevono e utilizzano.

**Coordinatori dei set di criteri:** Può visualizzare gli eventi controllati, inclusi gli eventi relativi a documenti e politiche, per i documenti protetti dai criteri dai rispettivi set di criteri.

**Amministratori:** Può visualizzare gli eventi controllati relativi a tutti i documenti e gli utenti protetti da policy. Gli amministratori possono inoltre tenere traccia di altri tipi di eventi, tra cui eventi utente, documento, policy ed eventi di sistema.

>[!NOTE]
>
>Anche gli eventi che vengono eseguiti su una copia di un documento protetto da policy vengono tracciati come eventi nel documento protetto originale.

(Vedi [Opzioni di controllo degli eventi](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

Un evento non riuscito viene registrato se un utente non autorizzato tenta di visualizzare un documento o tenta di accedere utilizzando un nome utente o una password errati.

>[!NOTE]
>
>Gli eventi di accesso anonimo non riusciti per i documenti possono essere registrati se viene modificato un criterio per rimuovere l&#39;accesso anonimo. Quando un destinatario autorizzato tenta di accedere a un documento protetto dai criteri modificati, viene comunque effettuato un tentativo di accesso anonimo ma non riesce.

Se un criterio consente l&#39;accesso anonimo degli utenti, ma in seguito l&#39;amministratore disattiva l&#39;accesso anonimo per la sicurezza dei documenti, l&#39;accesso anonimo non riuscirà per i documenti protetti dal criterio e l&#39;evento non verrà registrato.

## Abilita controllo eventi {#enable-event-auditing}

Questi requisiti di configurazione devono essere soddisfatti affinché il controllo degli eventi abbia luogo:

* Il sistema o l&#39;amministratore deve abilitare la funzionalità di controllo per il server.

   (Vedi [Configurazione del controllo degli eventi e delle impostazioni della privacy](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* Per i criteri utilizzati per proteggere il documento è necessario che il controllo sia attivato. (Vedi [Creazione e modifica dei criteri](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Cercare un evento {#search-for-an-event}

È possibile cercare nell’elenco degli eventi e visualizzare descrizioni più dettagliate degli eventi. Le descrizioni dettagliate includono informazioni quali l’ID evento, la descrizione, l’indirizzo IP, l’organizzazione, l’utente interessato, la data e l’ora in cui si è verificato l’evento, le attività negate e gli eventi offline (quando gli utenti tentano di utilizzare un documento quando non sono connessi alla sicurezza del documento).

È possibile cercare gli eventi nella pagina Eventi utilizzando una combinazione di criteri di ricerca degli eventi e delle date in cui si sono verificati gli eventi. Gli eventi che puoi cercare dipendono dal tuo ruolo:

**Utenti:** Può visualizzare gli eventi controllati per i loro documenti protetti da policy e per tutti i documenti protetti che ricevono e utilizzano. Sono disponibili le seguenti opzioni di ricerca:

**Eventi relativi a me:** Gli utenti possono trovare eventi per qualsiasi documento protetto da policy creato o ricevuto. Ad esempio, se un utente apre, visualizza o stampa un documento protetto da un&#39;altra persona, l&#39;utente visualizza solo questi eventi per quel documento.

**Eventi relativi ai miei documenti:** Gli utenti possono trovare tutti gli eventi correlati ai propri documenti protetti da policy. Gli utenti visualizzano gli eventi generati da ogni persona che ha gestito i propri documenti.

**Coordinatori dei set di criteri:** Può visualizzare gli eventi controllati, inclusi gli eventi relativi a documenti e politiche, per i documenti protetti dai criteri dai rispettivi set di criteri. Sono disponibili le seguenti opzioni:

**Documentare gli eventi in cui sono un coordinatore di set di criteri:** I coordinatori di set di criteri che dispongono dell&#39;autorizzazione per l&#39;evento di visualizzazione possono trovare gli eventi correlati ai documenti protetti dai set di criteri.

**Eventi politici in cui sono un coordinatore set di politiche:** I coordinatori di set di criteri che dispongono dell’autorizzazione per la visualizzazione degli eventi possono trovare gli eventi relativi ai criteri dai rispettivi set di criteri.

**Amministratori:** Può visualizzare gli eventi controllati relativi a tutti i documenti e gli utenti protetti da policy. Gli amministratori possono anche tenere traccia di altri tipi. Inoltre, gli amministratori possono suddividere ulteriormente le ricerche degli eventi in base al tipo di utente:

**Utenti noti:** Gli utenti si trovano nelle directory di origine o sono registrati come utenti esterni.

**Utenti anonimi:** Utenti sconosciuti che accedono a un documento protetto da un criterio che consente l&#39;accesso anonimo.

**Utenti di sistema:** Eventi generati dal server, ad esempio la sincronizzazione della directory.

1. Nella pagina di protezione del documento fare clic su Eventi.
1. Nell’elenco Trova, selezionare i criteri di ricerca da utilizzare. A seconda della selezione nell’elenco Trova, viene visualizzato un secondo elenco che fornisce criteri di ricerca aggiuntivi. Se applicabile, digitare i criteri di ricerca nella casella di testo.

   Per ulteriori dettagli sui tipi di evento specifici, vedi [Opzioni di controllo degli eventi](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. Nell’elenco Utente, selezionare il tipo di utente che ha eseguito l’evento:

   * Se si seleziona Utente noto, viene visualizzata una seconda casella di ricerca in cui è necessario digitare il nome utente o l&#39;indirizzo e-mail dell&#39;utente.
   * Se non si conoscono questi valori, fare clic sull&#39;icona di ricerca Rubrica per cercare l&#39;utente in base al nome utente o all&#39;indirizzo e-mail.

1. Nell’elenco Data, selezionare un’opzione relativa all’intervallo di date. Se si seleziona Date personalizzate, vengono visualizzate le caselle in cui si digita la data nel formato aaaa/mm/gg oppure è possibile utilizzare il selettore data per specificare l’intervallo di date:

   * Fare clic sul calendario per aprire il selettore data.
   * Usa le frecce per trovare un anno e un mese.
   * Fai clic su un giorno del mese nel calendario.
   * Fare clic su OK per chiudere il selettore data.

1. Nell’elenco Visualizza, selezionare il numero di risultati di ricerca da visualizzare per pagina.
1. Fare clic su Trova.

   Tutti gli eventi non riusciti vengono evidenziati nell’elenco con un’icona negata.

1. Per visualizzare i dettagli di un evento, fare clic sulla descrizione dell’evento nell’elenco.

## Ordinare l’elenco degli eventi {#sort-the-event-list}

È possibile ordinare l’elenco degli eventi per intestazione di colonna per individuare più facilmente gli eventi. Le icone a triangolo accanto all’intestazione della colonna indicano quale colonna è attualmente utilizzata per l’ordinamento. Un triangolo rivolto verso l&#39;alto indica l&#39;ordine crescente, mentre un triangolo rivolto verso il basso indica l&#39;ordine decrescente.

1. Fai clic sull’intestazione di colonna appropriata.
1. Per modificare l’ordinamento, fai nuovamente clic sull’intestazione della colonna.
