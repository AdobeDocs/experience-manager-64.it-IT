---
title: Flusso di lavoro incentrato su Forms su OSGi - Riferimento dettagliato
seo-title: Forms-centric workflow on OSGi - Step Reference
description: I passaggi OSGi di Forms-centric consentono di creare rapidamente flussi di lavoro basati su moduli adattivi.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '4637'
ht-degree: 0%

---

# Flusso di lavoro incentrato su Forms su OSGi - Riferimento dettagliato {#forms-centric-workflow-on-osgi-step-reference}

## Passaggi Forms Workflow {#forms-workflow-steps}

I passaggi del flusso di lavoro Forms eseguono operazioni specifiche per AEM Forms in un flusso di lavoro AEM. Questi passaggi ti consentono di creare rapidamente flussi di lavoro incentrati su Forms basati su moduli adattivi su OSGi. Questi flussi di lavoro possono essere utilizzati per lo sviluppo di flussi di lavoro di revisione e approvazione di base, processi aziendali interni e attraverso il firewall. È inoltre possibile utilizzare i passaggi di Forms Workflow per avviare document services, integrarsi con il flusso di lavoro della firma Acrobat Sign ed eseguire altre operazioni AEM Forms. Richiedi [Componente aggiuntivo AEM Forms](https://www.adobe.com/go/learn_aemforms_documentation_63) per utilizzare questi passaggi in un flusso di lavoro.

## Assegna passaggio attività {#assign-task-step}

Il passaggio dell&#39;attività di assegnazione crea un&#39;attività e la assegna a un utente o a un gruppo. Oltre ad assegnare l’attività, il componente specifica anche il modulo adattivo o PDF non interattivo per l’attività. Il modulo adattivo è necessario per accettare l’input degli utenti e PDF non interattivo o un modulo adattivo di sola lettura viene utilizzato per i flussi di lavoro di sola revisione.

È inoltre possibile utilizzare il componente per controllare il comportamento dell’attività. Ad esempio, creazione di un documento di record automatico, assegnazione dell&#39;attività a un utente o a un gruppo specifico, specifica il percorso dei dati inviati, specifica il percorso dei dati da precompilare e specifica le azioni predefinite. Il passaggio Assegna attività ha le seguenti proprietà:

* **Titolo:** Titolo dell’attività. Il titolo viene visualizzato in AEM casella in entrata.
* **Descrizione:** Spiegazione delle operazioni eseguite nell&#39;attività. Queste informazioni sono utili per altri sviluppatori di processi quando lavori in un ambiente di sviluppo condiviso.

* **Percorso miniature:** Percorso della miniatura dell&#39;attività. Se non viene specificato alcun percorso, per una miniatura predefinita di un modulo adattivo e per Documento di record viene visualizzata un’icona predefinita.
* **Fase del flusso di lavoro:** Un flusso di lavoro può avere più fasi. Queste fasi vengono visualizzate nella casella in entrata AEM. Puoi definire questi stadi nelle proprietà del modello (Barra laterale > Pagina > Proprietà pagina > Stadi).
* **Priorità:** La priorità selezionata viene visualizzata nella casella in entrata AEM. Le opzioni disponibili sono Alta, Media e Bassa. Il valore predefinito è Medio.
* **Data di scadenza:** Specificare il numero di giorni o ore dopo le quali l&#39;attività è contrassegnata come scaduta. Se si seleziona **Disattivato**, quindi l&#39;attività non viene mai contrassegnata come scaduta. È inoltre possibile specificare un gestore di timeout per eseguire attività specifiche dopo la scadenza dell&#39;attività.

* **Giorni:** Numero di giorni precedenti al completamento dell&#39;attività. Il numero di giorni conteggiati dopo l’assegnazione dell’attività a un utente. Se un&#39;attività non è completa e supera il numero di giorni specificato nel campo Giorni, se selezionato, viene attivato un gestore di timeout dopo la data di scadenza.
* **Ore:** Numero di ore prima del completamento dell&#39;attività. Il numero di ore viene conteggiato dopo che l’attività è stata assegnata a un utente. Se un&#39;attività non è completa e supera il numero di ore specificato nel campo Ore, se selezionato, viene attivato un gestore di timeout dopo le ore di scadenza.
* **Timeout dopo la data di scadenza:** Selezionare questa opzione per abilitare il campo di selezione Gestore timeout.
* **Gestore di timeout:** Selezionare lo script da eseguire quando la fase dell&#39;attività di assegnazione supera la data di scadenza. Script inseriti nell’archivio CRX in [app]/fd/dashboard/scripts/timeoutHandler sono disponibili per la selezione. Il percorso specificato non esiste in crx-repository. Un amministratore crea il percorso prima di utilizzarlo.
* **Evidenziare l&#39;azione e il commento dell&#39;ultima attività in Dettagli attività:** Selezionare questa opzione per visualizzare l’ultima azione eseguita e il commento ricevuto sulla sezione dei dettagli dell’attività di un’attività.
* **Tipo:** Scegliere il tipo di documento da compilare all&#39;avvio del flusso di lavoro. È possibile scegliere un modulo adattivo, un modulo adattivo di sola lettura o un documento PDF non interattivo.
* **Usa modulo adattivo:** Specifica il metodo per individuare il modulo adattivo di input. Puoi utilizzare il modulo adattivo disponibile in un percorso assoluto, inviato come payload al flusso di lavoro o disponibile in un percorso calcolato utilizzando una variabile. È possibile utilizzare una variabile di tipo String per specificare il percorso.
* **Percorso modulo adattivo**: Specifica il percorso del modulo adattivo. Il campo è disponibile quando utilizzi un modulo adattivo o un modulo adattivo di sola lettura nel campo Tipo , insieme all’opzione Percorso assoluto del campo Usa modulo adattivo .
* **Percorso PDF:** Specifica il percorso di un documento PDF non interattivo. Il campo è disponibile quando si sceglie un documento PDF non interattivo nel campo Tipo. Il percorso è sempre relativo al payload. Ad esempio: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Il percorso non esiste in crx-repository. Un amministratore crea il percorso prima di utilizzarlo. Per utilizzare l’opzione Percorso di PDF è necessario abilitare l’opzione Documento di record o i moduli adattivi basati su modelli di modulo.
* **Per l’attività completata, esegui il rendering del modulo adattivo come**: Quando un’attività è contrassegnata come completa, è possibile eseguire il rendering del modulo adattivo come modulo adattivo di sola lettura o come documento PDF. Per eseguire il rendering del modulo adattivo come documento di record, è necessario abilitare l’opzione Documento di record o i moduli adattivi basati su modelli di modulo.
* **Informazioni da precompilare:** I campi seguenti elencati fungono da input per l’attività:

   * **Percorso file dati:** Percorso del file di dati di input (.json o .xml). Il percorso è sempre relativo al payload. Ad esempio, il file contiene i dati inviati per il modulo tramite un’applicazione Casella in entrata AEM. Un esempio di percorso è [Payload_Directory]/workflow/data.
   * **Percorso allegato:** Gli allegati disponibili nella posizione vengono allegati al modulo associato all&#39;attività. Il percorso è sempre relativo al payload. Un esempio di percorso è [Payload_Directory]/allegati/

* **Informazioni trasmesse:** I campi seguenti elencati fungono da percorsi di output per l’attività:

   * **Percorso file dati:** Percorso del file di dati (.json o .xml). Il file di dati contiene informazioni inviate tramite il modulo associato. Il percorso è sempre relativo al payload. Ad esempio: [Payload_Directory]/Workflow/data, dove i dati sono un file.
   * **Percorso allegato:** Percorso per il salvataggio degli allegati del modulo forniti in un&#39;attività.
   * **Percorso del documento di registrazione:** Percorso per il salvataggio di un file del documento di record. Ad esempio: [Payload_Directory]/DocumentofRecord/credit-card.pdf. Il documento di record non viene generato se il campo percorso viene lasciato vuoto. Il percorso è sempre relativo al payload.

* **Opzioni di assegnazione:** Specificare il metodo per assegnare l&#39;attività a un utente. È possibile assegnare dinamicamente l&#39;attività a un utente o a un gruppo utilizzando lo script Selezione partecipanti o assegnarla a un utente o gruppo AEM specifico.
* **Selettore partecipante:** L’opzione è disponibile quando **In modo dinamico per un utente o un gruppo** l’opzione è selezionata nel campo Assegna opzioni . È possibile utilizzare uno script ECMAScript o un servizio per selezionare in modo dinamico un utente o un gruppo. Per ulteriori informazioni, consulta [Assegnazione dinamica di un flusso di lavoro agli utenti](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) e [Creazione di un passaggio personalizzato Adobe Experience Manager Dynamic Participant .](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Partecipanti:** Il campo è disponibile quando la **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** l’opzione è selezionata nel campo Selettore partecipante . Il campo consente di selezionare utenti o gruppi per l’opzione RandomParticipantChooser.

* **Argomenti:** Il campo è disponibile quando nel campo Selettore partecipante è selezionato uno script diverso da quello RandomParticipantChoose . Il campo consente di fornire un elenco di argomenti separati da virgola per lo script selezionato nel campo Selettore partecipante.

* **Utente o gruppo:** L&#39;attività viene assegnata all&#39;utente o al gruppo selezionato. L’opzione è disponibile quando **Per un utente o un gruppo specifico** è selezionato nel campo Opzioni di assegnazione . Il campo elenca tutti gli utenti e i gruppi del gruppo utenti del flusso di lavoro.

* **Invia notifica all&#39;assegnatario tramite e-mail:** Seleziona questa opzione per inviare notifiche e-mail all’assegnatario. Queste notifiche vengono inviate quando un’attività viene assegnata a un utente. Prima di utilizzare l’opzione , abilita le notifiche dalla console AEM Web. Per istruzioni dettagliate, consulta [configurare le notifiche e-mail per la fase dell’attività di assegnazione](/help/forms/using/aem-forms-workflow.md)

* **Modello e-mail HTML**: Seleziona il modello e-mail per l’e-mail di notifica. Per modificare un modello, modifica il file che si trova in /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in crx-repository.
* **Consenti Delega A:** AEM casella in entrata fornisce all’utente connesso un’opzione per delegare il flusso di lavoro assegnato a un altro utente. Puoi delegare all’interno dello stesso gruppo o all’utente del flusso di lavoro di un altro gruppo. Se l’attività viene assegnata a un singolo utente e la **consentire la delega ai membri del gruppo assegnatario** l’opzione è selezionata, quindi non è possibile delegare l’attività a un altro utente o gruppo.

* **Azioni predefinite:** Sono disponibili le azioni Invia, Salva e Ripristina predefinite. Per impostazione predefinita sono abilitate tutte le azioni predefinite.
* **Variabile di percorso:** Nome della variabile di route. La variabile di route acquisisce le azioni personalizzate selezionate da un utente nella casella in entrata AEM.
* **Percorsi:** Un&#39;attività può essere suddivisa in percorsi diversi. Se selezionata in AEM casella in entrata, la route restituisce un valore e i rami del flusso di lavoro in base alla route selezionata.
* **Titolo**: Specifica il titolo della route. Viene visualizzato in AEM casella in entrata.
* **Icona Corallo**: Specifica l&#39;attributo HTML di un&#39;icona corallo. La libreria CorelUI di Adobe fornisce un ampio set di icone touch-first. È possibile scegliere e utilizzare un&#39;icona per il percorso. Viene visualizzato insieme al titolo nella casella in entrata AEM.
* **Consenti all&#39;assegnatario di aggiungere un commento**: Selezionare questa opzione per abilitare i commenti per l&#39;attività. Al momento dell’invio dell’attività, un assegnatario può aggiungere i commenti all’interno AEM casella in entrata.
* **Consenti all&#39;assegnatario di aggiungere allegati all&#39;attività**: Selezionare questa opzione per abilitare gli allegati per l&#39;attività. Al momento dell’invio dell’attività, un assegnatario può aggiungere gli allegati dall’interno AEM casella in entrata.
* **Percorso di output degli allegati dell&#39;attività**: Specificare il percorso della cartella dell&#39;allegato. La posizione è relativa al payload.
* **Utilizza metadati personalizzati:** Seleziona questa opzione per abilitare il campo metadati personalizzato. I metadati personalizzati vengono utilizzati nei modelli e-mail.
* **Metadati personalizzati:** Seleziona un metadati personalizzato per i modelli e-mail. I metadati personalizzati sono disponibili in crx-repository su apps/fd/dashboard/scripts/metadataScripts. Il percorso specificato non esiste in crx-repository. Un amministratore crea il percorso prima di utilizzarlo. Puoi anche utilizzare un servizio per i metadati personalizzati. È inoltre possibile estendere `WorkitemUserMetadataService` per fornire metadati personalizzati.

* **Mostra dati dai passaggi precedenti**: Selezionare questa opzione per consentire agli assegnatari di visualizzare gli assegnatari precedenti, le azioni già eseguite sull&#39;attività, i commenti aggiunti all&#39;attività e il documento di registrazione dell&#39;attività completata, se disponibile.
* **Mostra dati dai passaggi successivi:** Selezionare questa opzione per consentire all&#39;assegnatario corrente di visualizzare l&#39;azione intrapresa e i commenti aggiunti all&#39;attività dagli assegnatari successivi. Consente inoltre all&#39;assegnatario corrente di visualizzare un documento di registrazione dell&#39;attività completata, se disponibile.
* **Visibilità del tipo di dati:** Per impostazione predefinita, un assegnatario può visualizzare un documento di registrazione, gli assegnatari, le azioni intraprese e i commenti aggiunti dagli assegnatari precedenti e successivi. Utilizza l’opzione di visibilità del tipo di dati per limitare il tipo di dati visibili agli assegnatari.

## Invia passaggio e-mail {#send-email-step}

Utilizza il passaggio e-mail per inviare un’e-mail, ad esempio un messaggio e-mail con un documento di registrazione, un collegamento di un modulo adattivo, un collegamento di una comunicazione interattiva o un documento PDF allegato. Supporto dei passaggi di invio e-mail [E-mail HTML](https://en.wikipedia.org/wiki/HTML_email). Le e-mail di HTML sono reattive e si adattano al client e-mail e alle dimensioni dello schermo dei destinatari. Puoi utilizzare un modello e-mail di HTML per definire l’aspetto, lo schema di colori e il comportamento dell’e-mail.

Il passaggio e-mail utilizza Day CQ Mail Service per inviare e-mail. Prima di utilizzare il passaggio e-mail, assicurati che [servizio e-mail](/help/forms/using/aem-forms-workflow.md) è configurato. Il passaggio e-mail ha le seguenti proprietà:

**Titolo:** Il titolo del passaggio ti aiuta a identificare il passaggio nell’editor del flusso di lavoro.

**Descrizione:** La spiegazione è utile per altri sviluppatori di processi quando lavori in un ambiente di sviluppo condiviso.

**Oggetto e-mail** L’oggetto può essere recuperato dai metadati di un flusso di lavoro o specificato manualmente. Seleziona la **Letterale** opzione per specificare manualmente un oggetto o selezionare la **Recupera dai metadati del flusso di lavoro** per recuperare l’oggetto da una proprietà metadati.

**Modello e-mail HTML**: Modello HTML per l’e-mail. Puoi specificare le variabili in un modello e-mail. Il Passaggio e-mail estrae e visualizza tutte le variabili incluse in un modello per gli input.

**Metadati modello e-mail:** Il valore delle variabili del modello e-mail può essere un valore specificato dall’utente, il percorso di una risorsa sull’autore o sul server di pubblicazione, sull’immagine o su una proprietà di metadati del flusso di lavoro.

* **Letterale:** Utilizza l’opzione quando conosci il valore esatto da specificare. Ad esempio: [example@example.com](mailto:example@example.com).

* **Metadati flusso di lavoro:** Utilizza l’opzione quando il valore da utilizzare viene salvato in una proprietà di metadati di un flusso di lavoro. Dopo aver selezionato l’opzione , immetti il nome della proprietà metadati nella casella di testo vuota sotto l’opzione Metadati flusso di lavoro . Ad esempio, emailAddress.
* **URL risorsa:** Utilizza l’opzione per incorporare un collegamento web di una comunicazione interattiva all’e-mail. Dopo aver selezionato l&#39;opzione , sfoglia e scegli la comunicazione interattiva da incorporare. La risorsa può risiedere sull’autore o sul server di pubblicazione.
* **Immagine:** Utilizza l’opzione per incorporare un’immagine nell’e-mail. Dopo aver selezionato l&#39;opzione , sfoglia e scegli l&#39;immagine. L’opzione immagine è disponibile solo per i tag immagine (&lt;img src=&quot;&amp;ast;&quot; />) disponibili nel modello e-mail.

**Indirizzo e-mail del mittente/destinatario:** Seleziona la **Letterale** opzione per specificare manualmente un indirizzo e-mail o selezionare **Recupera dai metadati del flusso di lavoro** per recuperare l’indirizzo e-mail da una proprietà metadati. È inoltre possibile specificare un elenco di array di proprietà di metadati per **Recupera dai metadati del flusso di lavoro** opzione .

**Percorso allegato file:** La risorsa disponibile nel percorso specificato viene allegata all’e-mail. Il percorso della risorsa può essere relativo al payload o al percorso assoluto. Un esempio di percorso è [Payload_Directory]/allegati/

**Nome file:** Nome del file allegato e-mail. Il Passaggio e-mail modifica il nome file originale dell’allegato al nome file specificato. Il nome può essere specificato manualmente o recuperato da una proprietà di metadati di un flusso di lavoro. Utilizza la **Letterale** quando si conosce il valore esatto da specificare. Utilizza la **Recupera da un metadati del flusso di lavoro** quando il valore da utilizzare viene salvato in una proprietà di metadati del flusso di lavoro.

## Passaggio Genera documento di record {#generate-document-of-record-step}

Quando un modulo viene compilato o inviato, è possibile conservare un record del modulo, in formato cartaceo o documento. Questo viene definito documento di registrazione (DoR). È possibile utilizzare il passaggio Genera documento di record per creare una versione PDF interattiva o di sola lettura di un modulo adattivo. La versione PDF contiene informazioni inserite nel modulo insieme al layout del modulo adattivo.

Il passaggio Documento di record ha le seguenti proprietà:

**Usa modulo adattivo**: Specifica il metodo per individuare il modulo adattivo di input. Puoi utilizzare il modulo adattivo disponibile in un percorso assoluto, inviato come payload al flusso di lavoro o disponibile in un percorso calcolato utilizzando una variabile. È possibile utilizzare una variabile di tipo String per specificare il percorso.

**Percorso modulo adattivo**: Specifica il percorso del modulo adattivo. Il campo è disponibile quando utilizzi un modulo adattivo o un modulo adattivo di sola lettura nel campo Tipo , insieme all’opzione Percorso assoluto del campo Usa modulo adattivo .

**Percorso dati di input:** Percorso dei dati di input per il modulo adattivo. È possibile mantenere i dati in una posizione relativa al payload o specificare un percorso assoluto dei dati. I dati di input vengono uniti al modulo adattivo per creare un documento di record.

**Percorso allegato di input:** Percorso allegato di input: Percorso degli allegati. Questi allegati sono inclusi nel documento di registrazione. È possibile mantenere gli allegati in una posizione relativa al payload o specificare un percorso assoluto degli allegati.

Se si specifica il percorso di una cartella, ad esempio gli allegati, tutti i file direttamente disponibili nella cartella vengono allegati al documento di record. Se sono disponibili file nelle cartelle direttamente disponibili nel percorso allegato specificato, i file sono inclusi nel documento di registrazione come allegati. Se sono presenti cartelle in cartelle direttamente disponibili, queste vengono ignorate.

**Percorso del documento di record generato:** Specificare il percorso in cui conservare un documento del file di record. È possibile scegliere di sovrascrivere la cartella payload o posizionare il documento di record in una posizione all’interno della directory di payload.

**Impostazioni internazionali**: Specificare la lingua del documento di registrazione.

## Passaggio Invoca il servizio del modello dati del modulo {#invoke-form-data-model-service-step}

È possibile utilizzare [Integrazione dei dati di AEM Forms](/help/forms/using/data-integration.md) per configurare e connettersi a origini dati diverse. Queste origini dati possono essere un database, un servizio Web, un servizio REST, un servizio OData e una soluzione CRM. L’integrazione dei dati di AEM Forms consente di creare un modello di dati del modulo che include vari servizi per eseguire operazioni di recupero, aggiunta e aggiornamento dei dati sul database configurato. È possibile utilizzare **Richiama del passaggio Servizio del modello dati** per selezionare un modello dati modulo (FDM) e utilizzare i servizi di FDM per recuperare, aggiornare o aggiungere dati a origini dati diverse.

Per spiegare gli input per i campi del passaggio , come esempio vengono utilizzati la seguente tabella di database e il file JSON :

**Tabella CustomerDetails di esempio**

<table> 
 <tbody> 
  <tr> 
   <td>Proprietà</td> 
   <td>Valore<br /> </td> 
  </tr> 
  <tr> 
   <td>Nome<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Cognome</td> 
   <td>Rosa</td> 
  </tr> 
  <tr> 
   <td>ID cliente</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Indirizzo e-mail<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**File JSON di esempio**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

Il passaggio Invoke Form Data Model Service presenta i campi elencati di seguito per facilitare le operazioni del modello dati del modulo:

* **Titolo:** Titolo del passaggio. Consente di identificare il passaggio nell’editor del flusso di lavoro.
* **Descrizione:** Spiegazione utile per altri sviluppatori di processi quando lavori in un ambiente di sviluppo condiviso.

* **Percorso modello dati modulo**: Sfogliare e selezionare un modello di dati modulo presente sul server.

* **Servizio**: Elenco dei servizi forniti dal modello dati modulo selezionato.
* **Input for services > Fornisci dati di input utilizzando letterale, metadati del flusso di lavoro e un file JSON**: Un servizio può avere più argomenti. Seleziona l’opzione per ottenere il valore degli argomenti del servizio da una proprietà dei metadati di un flusso di lavoro, da un oggetto JSON o immetti direttamente il valore nella casella di testo fornita:

   * **Letterale:** Utilizza l’opzione quando conosci il valore esatto da specificare. Ad esempio, srose@we.info.
   * **Recupera dai metadati del flusso di lavoro:** Utilizza l’opzione quando il valore da utilizzare viene salvato in una proprietà di metadati di un flusso di lavoro. Ad esempio, emailAddress.
   * **Notazione punto JSON:** Utilizza l’opzione quando il valore da utilizzare si trova in un file JSON. Ad esempio, Insurance.customerDetails.emailAddress.L’opzione JSON Dot Notation è disponibile solo se è selezionata l’opzione Mappa campi di input dall’input JSON .
   * **Mappare i campi di input da JSON di input:** Specifica il percorso di un file JSON per ottenere il valore di input di alcuni argomenti di servizio dal file JSON. Il percorso del file JSON può essere relativo al payload o a un percorso assoluto.

* **Input for services > Fornisci dati di input utilizzando un file JSON:** Seleziona l’opzione per ottenere i valori per tutti gli argomenti da un file JSON.
* **Percorso file JSON di input**: Percorso del file JSON contenente valori per tutti gli argomenti del servizio. Il percorso del file JSON può essere **relativo al payload** o **percorso assoluto**.

* **Notazione punto JSON:** Lascia vuoto il campo per utilizzare tutti gli oggetti del file JSON specificato come input per gli argomenti del servizio. Per leggere un oggetto JSON specifico dal file JSON specificato come input per gli argomenti del servizio, specifica la notazione del punto per l’oggetto JSON, ad esempio, se disponi di un JSON simile a quello elencato all’inizio della sezione, specifica Insurance.customerDetails per fornire tutti i dettagli di un cliente come input al servizio.
* **Output del servizio > Mappa e scrittura dei valori di output nei metadati:** Seleziona l&#39;opzione per salvare i valori di output come proprietà del nodo di metadati dell&#39;istanza del flusso di lavoro in crx-repository. Specifica il nome della proprietà metadati e seleziona l&#39;attributo di output del servizio corrispondente da mappare con la proprietà metadati, ad esempio, mappa il numero_telefono restituito dal servizio di output con la proprietà numero_telefono dei metadati del flusso di lavoro.
* **Output del servizio > Salva output come JSON:** Seleziona l’opzione per salvare i valori di output in un file JSON.
* **Percorso file JSON di output:** Percorso per salvare il file JSON di output. Il percorso del file JSON di output può essere relativo al payload o a un percorso assoluto.

## Passaggio Firma documento {#sign-document-step}

Il passaggio Firma documento consente di utilizzare Acrobat Sign per firmare i documenti. Il passaggio Firma documento ha le seguenti proprietà:

* **Nome accordo:** Specifica il titolo del contratto. Il nome del contratto fa parte dell’oggetto e del corpo del messaggio e-mail inviato ai firmatari.
* **Impostazioni internazionali:** Specifica la lingua per le opzioni di e-mail e verifica.
* **Configurazione di Acrobat Sign Cloud**: Scegli una configurazione cloud di Acrobat Sign. Se non hai configurato Acrobat Sign per AEM Forms, consulta [Integrare Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento da firmare:** È possibile scegliere un documento da una posizione relativa al payload, utilizzare il payload come documento o specificare un percorso assoluto del documento.
* **Percorso allegato di input:** Selezionare un allegato. Questi allegati sono inclusi nel documento di firma. È possibile mantenere gli allegati in una posizione relativa al payload o specificare un percorso assoluto degli allegati.

   Se si specifica il percorso di una cartella, ad esempio gli allegati, tutti i file direttamente disponibili nella cartella vengono allegati al documento di record. Se sono disponibili file nelle cartelle direttamente disponibili nel percorso allegato specificato, i file sono inclusi nel documento di firma come allegati. Se sono presenti cartelle in cartelle direttamente disponibili, queste vengono ignorate.
* **Giorni fino alla scadenza:** Un documento viene contrassegnato come scaduto (superato il termine) dopo che non vi è alcuna attività sull&#39;attività per il numero di giorni specificato nel **Giorni fino alla scadenza** campo . Il numero di giorni viene conteggiato dopo che il documento è stato assegnato a un utente per la firma.

* **Frequenza e-mail promemoria:** Puoi inviare un messaggio e-mail di promemoria a intervalli giornalieri o settimanali. La settimana viene conteggiata dal giorno in cui il documento viene assegnato a un utente per la firma.
* **Processo firma:** È possibile scegliere di firmare un documento in ordine sequenziale o parallelo. In ordine sequenziale, un firmatario riceve il documento alla volta per la firma. Al termine della firma del documento da parte del primo firmatario, il documento viene inviato al secondo firmatario e così via. In ordine parallelo, più firmatari possono firmare un documento alla volta.

* **URL di reindirizzamento:** Specifica un URL di reindirizzamento. Dopo aver firmato il documento, è possibile reindirizzare l’assegnatario a un URL. Di solito, questo URL contiene un messaggio di ringraziamento o ulteriori istruzioni.
* **Fase del flusso di lavoro:** Un flusso di lavoro può avere più fasi. Queste fasi vengono visualizzate nella casella in entrata AEM. Puoi definire questi stadi nelle proprietà del modello (Barra laterale > Pagina > Proprietà pagina > Stadi).
* **Selezionare i firmatari:** Specificare il metodo per scegliere i firmatari per il documento. Puoi assegnare dinamicamente il flusso di lavoro a un utente o a un gruppo oppure aggiungere manualmente i dettagli di un firmatario.
* **Script o servizio per selezionare i firmatari:** L’opzione è disponibile solo se nel campo Seleziona firmatari è selezionata l’opzione Dinamicamente . È possibile specificare uno script ECMAScript o un servizio per scegliere i firmatari e le opzioni di verifica di un documento.

* **Dettagli del firmatario:** L’opzione è disponibile solo se l’opzione Manualmente è selezionata nel campo Seleziona firmatari . Specifica l’indirizzo e-mail e scegli un meccanismo di verifica facoltativo. Prima di selezionare un meccanismo di verifica in due fasi, assicurati che l’opzione di verifica corrispondente sia abilitata per l’account Acrobat Sign configurato.
* **Variabile di stato:** Un documento abilitato per Acrobat Sign memorizza lo stato di firma del documento in una variabile. Specifica il nome della variabile di stato (adobeSignStatus). Una variabile di stato di un&#39;istanza è disponibile in CRXDE in /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData contiene lo stato di una variabile.
* **Percorso documento firmato:** Specificare il percorso in cui conservare i documenti firmati. È possibile scegliere di sovrascrivere il file di payload o posizionare il documento firmato in una posizione all’interno della directory di payload.

## Passaggi di Document Services {#document-services-steps}

AEM Document Services è un insieme di servizi per la creazione, l’assemblaggio e la protezione di documenti PDF. AEM Forms fornisce un passaggio separato AEM flusso di lavoro per ogni servizio di documentazione:

### Passaggio del timestamp del documento {#apply-document-time-stamp-step}

Aggiungi una marca temporale a un documento. Fornisci dettagli del documento quali il percorso del documento di input, il nome del documento di input, la posizione in cui memorizzare i dati esportati. È possibile scegliere di sovrascrivere il file di payload esistente o scegliere un nome file diverso per memorizzare i dati in un file diverso in una cartella di payload.

### Passaggio Converti in immagine {#convert-to-image-step}

Converte un documento PDF in un file di immagine. I formati immagine supportati sono JPEG, JPEG2000, PNG e TIFF. Le seguenti informazioni si applicano alle conversioni nelle immagini di TIFF:

* Viene generato un file TIFF multipagina.
* Alcune annotazioni non sono incluse nelle immagini di TIFF. Le annotazioni per le quali Acrobat deve generare l’aspetto non sono incluse.

### Passaggio Converti in PDF/A {#convert-to-pdf-a-step}

Converte un documento PDF in formato PDF/A utilizzando le opzioni disponibili. La versione PDF/A di Portable Document Format (PDF) è specializzata nell&#39;archiviazione e nella conservazione a lungo termine dei documenti.

### Passaggio Converti in PS {#convert-to-ps-step}

Convertire documenti PDF in PostScript. Durante la conversione in PostScript, è possibile utilizzare l&#39;operazione di conversione per specificare il documento di origine e se convertire in PostScript di livello 2 o 3. Il documento PDF convertito in un file PostScript deve essere non interattivo.

### Crea PDF dal passaggio del tipo specificato {#create-pdf-from-specified-type-step}

Generare un documento PDF da un file di input. Il documento di input può essere relativo al payload, avere un percorso assoluto o può essere il payload stesso.

### Crea PDF da un passaggio URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Genera un documento PDF dal file URL, HTML e ZIP fornito.

### Passaggio Esporta dati {#export-data-step}

Esporta dati da un file PDF forms o XDP. Richiede di inserire il percorso file del documento di input e del formato di esportazione dei dati. Le opzioni per Formato dati esportazione sono Auto, XDP e XmlData.

### Export PDF al passaggio del tipo specificato {#export-pdf-to-specified-type-step}

Converte un documento PDF in un formato selezionato.

### Passaggio Genera PDF non interattivo {#generate-non-interactive-pdf-step}

Generare un PDF non interattivo. Offre diverse opzioni di personalizzazione.

### Passaggio Importa dati {#import-data-step}

Unisce i dati del modulo in un modulo PDF. È possibile importare i dati del modulo in un modulo PDF.

### Richiama passaggio DDX {#invoke-ddx-step}

Esegue il file DDX sulla mappa specificata dei documenti di input e restituisce i documenti PDF manipolati.

### Passaggio Optimize PDF {#optimize-pdf-step}

Ottimizza i file PDF riducendone le dimensioni. Il risultato di questa conversione sono i file PDF che possono essere più piccoli delle versioni originali. Questa operazione converte anche i documenti PDF nella versione di PDF specificata nei parametri di ottimizzazione.

Le impostazioni di ottimizzazione specificano la modalità di ottimizzazione dei file. Di seguito sono riportati alcuni esempi di impostazioni:

* Versione di Target PDF
* Eliminazione di oggetti come azioni JavaScript e miniature di pagina incorporate
* Eliminazione dei dati utente, ad esempio commenti e allegati di file
* Eliminazione delle impostazioni non valide o non utilizzate
* Compressione dei dati non compressi o utilizzo di algoritmi di compressione più efficienti
* Rimozione dei font incorporati
* Impostazione dei valori di trasparenza

### Passaggio Rendering del modulo PDF {#render-pdf-form-step}

Esegue il rendering di un modulo creato in Form Designer (XDP) in un modulo PDF.

### Passaggio Secure Document {#secure-document-step}

Cifrare, firmare e certificare un documento. AEM Forms supporta sia la crittografia basata su password che la crittografia basata su certificato. È inoltre possibile scegliere tra vari algoritmi per la firma dei documenti. Ad esempio, SHA-256 e SH-512. È inoltre possibile utilizzare il passaggio del flusso di lavoro per estendere i documenti PDF tramite il lettore. Il passaggio del flusso di lavoro fornisce l’opzione per abilitare la decodifica del codice a barre, le firme digitali, l’importazione e l’esportazione di dati di PDF e altre opzioni.

### Passaggio Invia a stampante {#send-to-printer-step}

Invia un documento direttamente a una stampante. Supporta i seguenti meccanismi di accesso alla stampa:

* **Stampante con accesso diretto**: Una stampante installata sullo stesso computer è denominata stampante diretta accessibile e il computer è denominato host della stampante. Questo tipo di stampante può essere una stampante locale collegata direttamente al computer.
* **Stampante con accesso indiretto**: La stampante installata in un server di stampa è accessibile da altri computer. Per la connessione a una stampante di rete sono disponibili tecnologie come il sistema di stampa UNIX® (CUPS) comune e il protocollo Line Printer Daemon (LPD). Per accedere a una stampante con accesso indiretto, specificare il nome IP o host del server di stampa. Utilizzando questo meccanismo, è possibile inviare un documento a un URI LPD quando la rete ha un LPD in esecuzione. Il meccanismo consente di indirizzare il documento a qualsiasi stampante collegata alla rete che dispone di un LPD in esecuzione.
