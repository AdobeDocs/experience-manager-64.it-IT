---
title: Flusso di lavoro Forms basato su OSGi - Riferimento passo
seo-title: Flusso di lavoro Forms basato su OSGi - Riferimento passo
description: Flusso di lavoro Forms incentrato sui passaggi OSGi per creare rapidamente flussi di lavoro basati su moduli adattivi.
seo-description: Flusso di lavoro Forms incentrato sui passaggi OSGi per creare rapidamente flussi di lavoro basati su moduli adattivi.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: aheimoz
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '4561'
ht-degree: 0%

---


# Flusso di lavoro Forms incentrato su OSGi - Riferimento passo {#forms-centric-workflow-on-osgi-step-reference}

## Passaggi Forms Workflow {#forms-workflow-steps}

I passaggi del flusso di lavoro Forms eseguono  operazioni specifiche di AEM Forms in un flusso di lavoro AEM. Questi passaggi consentono di creare rapidamente in OSGi un flusso di lavoro basato su Forms basato su moduli adattivi. Questi flussi di lavoro possono essere utilizzati per sviluppare flussi di lavoro di revisione e approvazione di base, processi aziendali interni e attraverso il firewall. È inoltre possibile utilizzare i passaggi di Forms Workflow per avviare Document Services, integrarsi con  flusso di lavoro di firma Adobe Sign ed eseguire altre operazioni  AEM Forms. È necessario [ componente aggiuntivo AEM Forms](https://www.adobe.com/go/learn_aemforms_documentation_63) per utilizzare questi passaggi in un flusso di lavoro.

## Assegna passaggio attività {#assign-task-step}

Il passaggio dell&#39;attività di assegnazione crea un&#39;attività e la assegna a un utente o gruppo. Oltre ad assegnare l’attività, il componente specifica anche il modulo adattivo o il PDF non interattivo per l’attività. Il modulo adattivo è richiesto per accettare l&#39;input degli utenti e i PDF non interattivi oppure un modulo adattivo di sola lettura viene utilizzato per i flussi di lavoro di sola revisione.

È inoltre possibile utilizzare il componente per controllare il comportamento dell&#39;attività. Ad esempio, creazione di un documento di record automatico, assegnazione dell&#39;attività a un utente o gruppo specifico, specifica il percorso dei dati inviati, specifica il percorso dei dati da precompilare e specifica delle azioni predefinite. Il passaggio Assegna attività ha le seguenti proprietà:

* **Titolo:** Titolo dell’attività. Il titolo viene visualizzato in AEM Posta in arrivo.
* **Descrizione:** Spiegazione delle operazioni eseguite nell&#39;attività. Queste informazioni sono utili per altri sviluppatori di processi quando si lavora in un ambiente di sviluppo condiviso.

* **Percorso miniatura:** percorso della miniatura dell’attività. Se non viene specificato alcun percorso, per la miniatura predefinita di un modulo adattivo e per il documento di registrazione viene visualizzata un&#39;icona predefinita.
* **Fase flusso di lavoro:** Un flusso di lavoro può avere più fasi. Questi passaggi vengono visualizzati nella AEM Posta in arrivo. È possibile definire questi passaggi nelle proprietà del modello (barra laterale > Pagina > Proprietà pagina > Stadi).
* **Priorità: la priorità** selezionata viene visualizzata nella casella in entrata AEM. Le opzioni disponibili sono Alta, Media e Bassa. Il valore predefinito è Medium.
* **Data scadenza:** specificare il numero di giorni o ore dopo i quali l&#39;attività è contrassegnata come scaduta. Se si seleziona **Off**, l&#39;attività non viene mai contrassegnata come scaduta. È inoltre possibile specificare un gestore di timeout per eseguire attività specifiche dopo la scadenza dell&#39;attività.

* **Giorni:** il numero di giorni prima dei quali deve essere completata l&#39;attività. Numero di giorni contati dopo che l’attività è stata assegnata a un utente. Se un&#39;attività non è completa e supera il numero di giorni specificato nel campo Giorni, se selezionata, viene attivato un gestore di timeout dopo la data di scadenza.
* **Ore:** il numero di ore prima delle quali l&#39;attività deve essere completata. Numero di ore contate dopo che l’attività è stata assegnata a un utente. Se un&#39;attività non è completa e supera il numero di ore specificato nel campo Ore, se selezionata, viene attivato un gestore di timeout dopo le ore di scadenza.
* **Timeout dopo la data di scadenza:** selezionate questa opzione per abilitare il campo di selezione Gestore timeout.
* **Gestore di timeout:** selezionare lo script da eseguire quando il passaggio dell&#39;attività di assegnazione supera la data di scadenza. Gli script inseriti nell&#39;archivio CRX in [apps]/fd/dashboard/scripts/timeoutHandler sono disponibili per la selezione. Il percorso specificato non esiste nell&#39;archivio crx. Un amministratore crea il percorso prima di utilizzarlo.
* **Evidenziare l&#39;azione e il commento dall&#39;ultima attività in Dettagli attività:** selezionare questa opzione per visualizzare l&#39;ultima azione eseguita e il commento ricevuto sulla sezione dei dettagli dell&#39;attività di un&#39;attività.
* **Tipo:** scegliete il tipo di documento da compilare all’avvio del flusso di lavoro. È possibile scegliere un modulo adattivo, un modulo adattivo di sola lettura o un documento PDF non interattivo.
* **Usa modulo adattivo:** specifica il metodo per individuare il modulo adattivo di input. È possibile utilizzare il modulo adattivo disponibile in un percorso assoluto, inviato come payload al flusso di lavoro o disponibile in un percorso calcolato utilizzando una variabile. È possibile utilizzare una variabile di tipo String per specificare il percorso.
* **Percorso** modulo adattivo: Specificare il percorso del modulo adattivo. Il campo è disponibile quando si utilizza un modulo adattivo o un&#39;opzione per moduli adattivi di sola lettura nel campo Tipo insieme all&#39;opzione del percorso assoluto nel campo Usa modulo adattivo.
* **Percorso PDF:** specificare il percorso di un documento PDF non interattivo. Il campo è disponibile quando si sceglie un documento PDF non interattivo nel campo Tipo. Il percorso è sempre relativo al payload. Ad esempio, [Payload_Directory]/Workflow/PDF/credit-card.pdf. Il percorso non esiste nell&#39;archivio crx. Un amministratore crea il percorso prima di utilizzarlo. Per utilizzare l&#39;opzione Percorso PDF è necessario abilitare l&#39;opzione Documento di registrazione o utilizzare moduli adattivi basati su modelli di modulo.
* **Per l&#39;attività completata, eseguite il rendering del modulo adattivo come** segue: Quando un&#39;attività è contrassegnata come completa, è possibile eseguire il rendering del modulo adattivo come modulo adattivo di sola lettura o come documento PDF. Per eseguire il rendering del modulo adattivo come documento di registrazione, è necessario abilitare l&#39;opzione Documento di registrazione o i moduli adattivi basati su modelli di modulo.
* **Informazioni da precompilare:** I seguenti campi elencati di seguito fungono da input per l’attività:

   * **Percorso file dati:** percorso del file di dati di input (.json o .xml). Il percorso è sempre relativo al payload. Ad esempio, il file contiene i dati inviati per il modulo tramite un&#39;applicazione Casella in entrata AEM. Un percorso di esempio è [Payload_Directory]/workflow/data.
   * **Percorso allegato:** gli allegati disponibili nella posizione sono allegati al modulo associato all&#39;attività. Il percorso è sempre relativo al payload. Un percorso di esempio è [Payload_Directory]/attachments/

* **Informazioni inviate:** I seguenti campi elencati di seguito fungono da posizioni di output per l’attività:

   * **Percorso file dati:** percorso del file di dati (.json o .xml). Il file di dati contiene informazioni inviate tramite il modulo associato. Il percorso è sempre relativo al payload. Ad esempio, [Payload_Directory]/Workflow/data, dove i dati sono un file.
   * **Percorso allegato:** percorso di salvataggio degli allegati del modulo fornito in un&#39;attività.
   * **Percorso record:** percorso per salvare un file del documento di registrazione. Ad esempio, [Payload_Directory]/DocumentofRecord/credit-card.pdf. Il documento di record non viene generato se il campo percorso viene lasciato vuoto. Il percorso è sempre relativo al payload.

* **Opzioni di assegnazione:** specificare il metodo per assegnare l’attività a un utente. Potete assegnare dinamicamente l’attività a un utente o a un gruppo utilizzando lo script Selezione partecipanti o assegnando l’attività a un utente o gruppo AEM specifico.
* **Selettore partecipanti:** l&#39;opzione è disponibile quando l&#39;opzione  **Dynamically to a user or** groupoption (Destinazione dinamica a un utente o gruppo) è selezionata nel campo Assign options (Opzioni assegnabili). È possibile utilizzare uno script ECMAS o un servizio per selezionare in modo dinamico un utente o un gruppo. Per ulteriori informazioni, vedere [Assegnare dinamicamente un flusso di lavoro agli utenti](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) e [Creazione di un passaggio personalizzato per i partecipanti dinamici di Adobe Experience Manager.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Partecipanti:** il campo è disponibile se nel campo Selezione partecipanti è selezionata l’opzione  **[!UICONTROL com.adobe.granite.workflow.core.process.]** RandomParticipantChooserer. Il campo consente di selezionare utenti o gruppi per l&#39;opzione RandomParticipantChooser.

* **Argomenti:** Il campo è disponibile quando nel campo Selezione partecipanti è selezionato uno script diverso da RandomParticipantChoose. Il campo consente di fornire un elenco di argomenti separati da virgola per lo script selezionato nel campo Selezione partecipanti.

* **Utente o gruppo:** l&#39;attività è assegnata all&#39;utente o al gruppo selezionato. L&#39;opzione è disponibile quando l&#39;opzione **Per un utente o un gruppo specifico** è selezionata nel campo Opzioni assegnabili. Il campo elenca tutti gli utenti e i gruppi del gruppo Workflow-utenti.

* **Notifica all&#39;assegnatario tramite e-mail:** selezionate questa opzione per inviare le notifiche e-mail all&#39;assegnatario. Queste notifiche vengono inviate quando un&#39;attività viene assegnata a un utente. Prima di utilizzare l&#39;opzione, abilita le notifiche dalla console AEM Web. Per istruzioni dettagliate, vedere [configurare le notifiche e-mail per l&#39;assegnazione delle attività](/help/forms/using/aem-forms-workflow.md)

* **Modello** e-mail HTML: Selezionate il modello e-mail per il messaggio e-mail di notifica. Per modificare un modello, modificate il file che si trova in /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in crx-repository.
* **Consenti delega a:** AEM Posta in arrivo fornisce all&#39;utente che ha effettuato l&#39;accesso un&#39;opzione per delegare il flusso di lavoro assegnato a un altro utente. Potete delegare lo stesso gruppo o l’utente del flusso di lavoro di un altro gruppo. Se l&#39;attività è assegnata a un singolo utente e l&#39;opzione **consenti delega ai membri del gruppo assegnatario** è selezionata, non è possibile delegare l&#39;attività a un altro utente o gruppo.

* **Azioni predefinite:** sono disponibili le azioni Invia, Salva e Ripristina. Per impostazione predefinita sono attivate tutte le azioni predefinite.
* **Variabile route:** nome della variabile route. La variabile route acquisisce le azioni personalizzate selezionate da un utente AEM Posta in arrivo.
* **Cicli:** Un&#39;attività può essere indirizzata a percorsi diversi. Se selezionato in AEM Posta in arrivo, la route restituisce un valore e i rami del flusso di lavoro in base alla route selezionata.
* **Titolo**: Specificare il titolo della route. Viene visualizzato in AEM Posta in arrivo.
* **Icona** Corallo: Specificate l&#39;attributo HTML di un&#39;icona corallo.  libreria CorelUI Adobe offre un vasto set di icone per i primi tocco. È possibile scegliere e utilizzare un&#39;icona per la route. Viene visualizzato insieme al titolo in AEM Posta in arrivo.
* **Consenti all&#39;assegnatario di aggiungere un commento**: Selezionare questa opzione per abilitare i commenti per l&#39;attività. Un assegnatario può aggiungere i commenti dall&#39;interno AEM Posta in arrivo al momento dell&#39;invio dell&#39;attività.
* **Consenti all&#39;assegnatario di aggiungere allegati all&#39;attività**: Selezionare questa opzione per abilitare gli allegati per l&#39;attività. Un assegnatario può aggiungere gli allegati dall&#39;interno AEM Posta in arrivo al momento dell&#39;invio dell&#39;attività.
* **Percorso di output degli allegati** attività: Specificate il percorso della cartella dell&#39;allegato. La posizione è relativa al payload.
* **Usa metadati personalizzati:** selezionate questa opzione per abilitare il campo di metadati personalizzato. I metadati personalizzati vengono utilizzati nei modelli e-mail.
* **Metadati personalizzati:** selezionate i metadati personalizzati per i modelli e-mail. I metadati personalizzati sono disponibili nell&#39;archivio crx in apps/fd/dashboard/scripts/metadataScripts. Il percorso specificato non esiste nell&#39;archivio crx. Un amministratore crea il percorso prima di utilizzarlo. Potete anche utilizzare un servizio per i metadati personalizzati. È inoltre possibile estendere l&#39;interfaccia `WorkitemUserMetadataService` per fornire metadati personalizzati.

* **Mostra dati dai passaggi** precedenti: Selezionare questa opzione per consentire agli assegnatari di visualizzare gli assegnatari precedenti, le azioni già eseguite sull&#39;attività, i commenti aggiunti all&#39;attività e il documento di registrazione dell&#39;attività completata, se disponibile.
* **Mostra dati dai passaggi successivi:** selezionare questa opzione per consentire all&#39;assegnatario corrente di visualizzare l&#39;azione eseguita e i commenti aggiunti all&#39;attività dagli assegnatari successivi. Consente inoltre all&#39;assegnatario corrente di visualizzare un documento di registrazione dell&#39;attività completata, se disponibile.
* **Visibilità del tipo di dati:** per impostazione predefinita, un assegnatario può visualizzare un documento di registrazione, assegnatari, azioni eseguite e commenti aggiunti da assegnatari precedenti e successivi. Utilizzare l&#39;opzione di visibilità del tipo di dati per limitare il tipo di dati visibili agli assegnatari.

## Invia passaggio e-mail {#send-email-step}

Utilizzare il passaggio e-mail per inviare un messaggio e-mail, ad esempio un messaggio e-mail contenente un documento record, un collegamento a un modulo adattivo, un collegamento a una comunicazione interattiva o un documento PDF allegato. Invia e-mail supporta [HTML email](https://en.wikipedia.org/wiki/HTML_email). Le e-mail HTML sono reattive e si adattano al client e-mail e alle dimensioni dello schermo dei destinatari. Potete utilizzare un modello e-mail HTML per definire l’aspetto, lo schema colore e il comportamento del messaggio e-mail.

Il passaggio e-mail utilizza Day CQ Mail Service per inviare e-mail. Prima di utilizzare il passaggio e-mail, assicurarsi che il [servizio e-mail](/help/forms/using/aem-forms-workflow.md) sia configurato. Il passaggio e-mail ha le seguenti proprietà:

**Titolo:** Il titolo del passaggio consente di identificare il passaggio nell’editor del flusso di lavoro.

**Descrizione:** Spiegazione è utile per altri sviluppatori di processi quando si lavora in un ambiente di sviluppo condiviso.

**Oggetto e-mail:** L’oggetto può essere recuperato dai metadati di un flusso di lavoro o specificato manualmente. Selezionare l&#39;opzione **Letterale** per specificare manualmente un oggetto oppure selezionare l&#39;opzione **Recupera dai metadati del flusso di lavoro** per recuperare l&#39;oggetto da una proprietà di metadati.

**Modello** e-mail HTML: Modello HTML per l’e-mail. Potete specificare le variabili in un modello e-mail. Il Passaggio e-mail estrae e visualizza per gli input tutte le variabili incluse in un modello.

**Metadati modello e-mail:** il valore delle variabili del modello e-mail può essere un valore specificato dall’utente, il percorso di una risorsa sull’autore o sul server di pubblicazione, l’immagine o la proprietà dei metadati di un flusso di lavoro.

* **Letterale:** utilizzare l&#39;opzione quando si conosce il valore esatto da specificare. Ad esempio, [example@example.com](mailto:example@example.com).

* **Metadati flusso di lavoro:** utilizzate questa opzione quando il valore da utilizzare viene salvato in una proprietà di metadati del flusso di lavoro. Dopo aver selezionato l’opzione, immettete il nome della proprietà dei metadati nella casella di testo vuota sotto l’opzione Metadati flusso di lavoro. Ad esempio, emailAddress.
* **URL risorsa:** utilizzate l’opzione per incorporare un collegamento Web di una comunicazione interattiva all’e-mail. Dopo aver selezionato l&#39;opzione, individuate e scegliete la comunicazione interattiva da incorporare. La risorsa può risiedere sull’autore o sul server di pubblicazione.
* **Immagine:** utilizzate l&#39;opzione per incorporare un&#39;immagine nell&#39;e-mail. Dopo aver selezionato l’opzione, sfogliate e scegliete l’immagine. L’opzione immagine è disponibile solo per i tag immagine (&lt;img src=&quot;&amp;ast;&quot;/>) disponibili nel modello e-mail.

**Indirizzo e-mail del mittente/destinatario:** selezionare l&#39;opzione  **** Lettera per specificare manualmente un indirizzo e-mail oppure selezionare l&#39;opzione  **Recupera dai** metadati del flusso di lavoro per recuperare l&#39;indirizzo e-mail da una proprietà di metadati. Potete anche specificare un elenco di array di proprietà di metadati per l&#39;opzione **Recupera dai metadati del flusso di lavoro**.

**Percorso allegato file:** la risorsa disponibile nel percorso specificato viene associata all’e-mail. Il percorso della risorsa può essere relativo al payload o al percorso assoluto. Un percorso di esempio è [Payload_Directory]/attachments/

**Nome file:** nome del file allegato e-mail. Il Passaggio e-mail modifica il nome file originale dell&#39;allegato in base al nome file specificato. Il nome può essere specificato manualmente o recuperato da una proprietà di metadati di un flusso di lavoro. Utilizzare l&#39;opzione **Letterale** quando si conosce il valore esatto da specificare. Utilizzate l&#39;opzione **Recupera da un metadati del flusso di lavoro** quando il valore da utilizzare viene salvato in una proprietà di metadati del flusso di lavoro.

## Passaggio Genera documento record {#generate-document-of-record-step}

Quando un modulo viene compilato o inviato, è possibile tenere un record del modulo, in formato cartaceo o in formato documento. Questo viene definito documento di registrazione (DoR). È possibile utilizzare il passaggio Genera documento di record per creare una versione PDF in sola lettura o interattiva di un modulo adattivo. La versione PDF contiene informazioni inserite nel modulo insieme al layout del modulo adattivo.

Il passaggio Documento di registrazione ha le proprietà seguenti:

**Usa modulo** adattivo: Specificare il metodo per individuare il modulo adattivo di input. È possibile utilizzare il modulo adattivo disponibile in un percorso assoluto, inviato come payload al flusso di lavoro o disponibile in un percorso calcolato utilizzando una variabile. È possibile utilizzare una variabile di tipo String per specificare il percorso.

**Percorso** modulo adattivo: Specificare il percorso del modulo adattivo. Il campo è disponibile quando si utilizza un modulo adattivo o un&#39;opzione per moduli adattivi di sola lettura nel campo Tipo insieme all&#39;opzione del percorso assoluto nel campo Usa modulo adattivo.

**Percorso dati di input:** percorso dei dati di input per il modulo adattivo. È possibile mantenere i dati in una posizione relativa al payload o specificare un percorso assoluto dei dati. I dati di input vengono uniti al modulo adattivo per creare un documento di record.

**Percorso di collegamento di input:percorso** di collegamento di input: Percorso degli allegati. Questi allegati sono inclusi nel documento di registrazione. È possibile mantenere gli allegati in una posizione relativa al payload o specificare un percorso assoluto degli allegati.

Se si specifica il percorso di una cartella, ad esempio gli allegati, tutti i file direttamente disponibili nella cartella vengono allegati al documento di registrazione. Se qualsiasi file è disponibile nelle cartelle direttamente disponibili nel percorso allegato specificato, i file sono inclusi nel documento di registrazione come allegati. Se sono presenti cartelle in cartelle direttamente disponibili, queste vengono ignorate.

**Percorso del documento di registrazione generato:** specifica la posizione in cui mantenere un file del documento di record. È possibile scegliere di sovrascrivere la cartella payload o posizionare il documento di record in una posizione all&#39;interno della directory di payload.

**Impostazioni internazionali**: Specificare la lingua del documento di record.

## Richiama il passaggio del servizio del modello dati modulo {#invoke-form-data-model-service-step}

È possibile utilizzare [ AEM Forms Data Integration](/help/forms/using/data-integration.md) per configurare e connettersi a origini dati diverse. Queste origini dati possono essere un database, un servizio Web, un servizio REST, un servizio OData e una soluzione CRM.  AEM Forms Data Integration consente di creare un modello dati modulo che include vari servizi per eseguire operazioni di recupero, aggiunta e aggiornamento dei dati nel database configurato. È possibile utilizzare il passaggio **Richiama servizio modello dati** per selezionare un modello dati del modulo (FDM) e utilizzare i servizi di FDM per recuperare, aggiornare o aggiungere dati a origini dati diverse.

Per spiegare gli input per i campi del passaggio, la seguente tabella di database e il file JSON sono utilizzati come esempio:

**Esempio di tabella CustomerDetails**

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

**Esempio di file JSON**

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

Il passaggio Richiama servizio modello dati modulo include i campi elencati di seguito per facilitare le operazioni del modello dati del modulo:

* **Titolo:** Titolo del passaggio. Consente di identificare il passaggio nell’editor del flusso di lavoro.
* **Descrizione:** Spiegazione utile per altri sviluppatori di processi quando si lavora in un ambiente di sviluppo condiviso.

* **Percorso** modello dati modulo: Individuare e selezionare un modello dati modulo presente sul server.

* **Servizio**: Elenco dei servizi forniti dal modello dati modulo selezionato.
* **Input per servizi > Fornisci dati di input utilizzando letterali, metadati del flusso di lavoro e un file** JSON: Un servizio può avere più argomenti. Selezionate l&#39;opzione per ottenere il valore degli argomenti del servizio da una proprietà di metadati di un flusso di lavoro, da un oggetto JSON o per immettere direttamente il valore nella casella di testo fornita:

   * **Letterale:** utilizzare l&#39;opzione quando si conosce il valore esatto da specificare. Ad esempio, srose@we.info.
   * **Recupera da metadati flusso di lavoro:** utilizzate l&#39;opzione quando il valore da utilizzare viene salvato in una proprietà di metadati del flusso di lavoro. Ad esempio, emailAddress.
   * **Notazione punto JSON:** utilizzate l&#39;opzione quando il valore da utilizzare si trova in un file JSON. Ad esempio, Insurance.customerDetails.emailAddress.L&#39;opzione JSON Dot Notation è disponibile solo se i campi di input Mappa dall&#39;opzione JSON di input è selezionata.
   * **Mappare i campi di input dal JSON di input:** specificate il percorso di un file JSON per ottenere il valore di input di alcuni argomenti del servizio dal file JSON. Il percorso del file JSON può essere relativo al payload o a un percorso assoluto.

* **Input per i servizi > Fornisce i dati di input utilizzando un file JSON:** Selezionare l&#39;opzione per ottenere i valori per tutti gli argomenti da un file JSON.
* **Percorso** file JSON di input: Percorso del file JSON contenente valori per tutti gli argomenti del servizio. Il percorso del file JSON può essere **relativo al payload** o un percorso **assoluto**.

* **Notazione punto JSON:** lasciate vuoto il campo per utilizzare tutti gli oggetti del file JSON specificato come input per gli argomenti del servizio. Per leggere un oggetto JSON specifico dal file JSON specificato come input per gli argomenti del servizio, specificate la notazione del punto per l&#39;oggetto JSON, ad esempio, se disponete di un JSON simile a quello elencato all&#39;inizio della sezione, specificate Insurance.customerDetails per fornire tutti i dettagli di un cliente come input al servizio.
* **Output di service > Mappa e scrittura dei valori di output nei metadati:** Selezionare l&#39;opzione per salvare i valori di output come proprietà del nodo di metadati dell&#39;istanza del flusso di lavoro in crx-repository. Specificate il nome della proprietà dei metadati e selezionate l&#39;attributo di output del servizio corrispondente da mappare con la proprietà dei metadati, ad esempio, mappate il numero_telefono restituito dal servizio di output con la proprietà phone_number dei metadati del flusso di lavoro.
* **Output di servizio > Salva output come JSON:** selezionare l&#39;opzione per salvare i valori di output in un file JSON.
* **Percorso file JSON di output:** percorso per salvare il file JSON di output. Il percorso del file JSON di output può essere relativo al payload o a un percorso assoluto.

## Sign Document step {#sign-document-step}

Il passaggio Firma documento consente di utilizzare  Adobe Sign per firmare i documenti. Il passaggio Firma documento presenta le proprietà seguenti:

* **Nome accordo:** specifica il titolo del contratto. Il nome del contratto fa parte dell’oggetto e del corpo del messaggio e-mail inviato ai firmatari.
* **Lingua:** specifica la lingua per le opzioni di e-mail e verifica.
* **Configurazione** Adobe Sign Cloud : Scegliete una configurazione  Adobe Sign Cloud. Se non avete configurato  Adobe Sign per  AEM Forms, consultate [Integrare  Adobe Sign con  AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Documento da firmare:** è possibile scegliere un documento da una posizione relativa al payload, utilizzare il payload come documento o specificare un percorso assoluto del documento.
* **Giorni fino alla scadenza:** Un documento è contrassegnato come scadenza (scadenza trascorsa) dopo l&#39;assenza di attività sull&#39;attività per il numero di giorni specificato nel campo  **Giorni fino alla** scadenza. Il numero di giorni contati dopo che il documento è stato assegnato a un utente per la firma.

* **Frequenza e-mail promemoria:** puoi inviare un promemoria a intervalli giornalieri o settimanali. La settimana viene conteggiata a partire dal giorno in cui il documento viene assegnato a un utente per la firma.
* **Procedura di firma:** è possibile scegliere di firmare un documento in ordine sequenziale o parallelo. In ordine sequenziale, un firmatario riceve il documento alla volta per la firma. Dopo che il primo firmatario ha completato la firma del documento, quest&#39;ultimo viene inviato al secondo firmatario e così via. In ordine parallelo, più firmatari possono firmare un documento alla volta.

* **URL di reindirizzamento:** specificate un URL di reindirizzamento. Dopo aver firmato il documento, è possibile reindirizzare l&#39;assegnatario a un URL. In genere, questo URL contiene un messaggio di ringraziamento o ulteriori istruzioni.
* **Fase flusso di lavoro:** Un flusso di lavoro può avere più fasi. Questi passaggi vengono visualizzati nella AEM Posta in arrivo. È possibile definire questi passaggi nelle proprietà del modello (barra laterale > Pagina > Proprietà pagina > Stadi).
* **Seleziona Firmatari:** specifica il metodo per scegliere i firmatari per il documento. Puoi assegnare il flusso di lavoro in modo dinamico a un utente o a un gruppo oppure puoi aggiungere manualmente i dettagli di un firmatario.
* **Script o servizio per selezionare i firmatari:** L&#39;opzione è disponibile solo se l&#39;opzione Dinamicamente è selezionata nel campo Seleziona firmatari. È possibile specificare uno script ECMAS o un servizio per scegliere i firmatari e le opzioni di verifica per un documento.

* **Dettagli firmatario:** l’opzione è disponibile solo se l’opzione Manualmente è selezionata nel campo Seleziona firmatari. Specificate l&#39;indirizzo e-mail e scegliete un meccanismo di verifica opzionale. Prima di selezionare un meccanismo di verifica in due fasi, accertatevi che l&#39;opzione di verifica corrispondente sia abilitata per l&#39;account Adobe Sign  configurato.
* **Variabile di stato:** un documento abilitato per  Adobe Sign memorizza lo stato di firma del documento in una variabile. Specificare il nome della variabile di stato (adobeSignStatus). Una variabile di stato di un&#39;istanza è disponibile in CRXDE in /etc/workflow/instance/&lt;server>/&lt;data-ora>/&lt;istanza del modello di flusso di lavoro>/workItems/&lt;nodo>/metaData contiene lo stato di una variabile.
* **Percorso documento firmato:** specifica il percorso in cui conservare i documenti firmati. È possibile scegliere di sovrascrivere il file di payload o posizionare il documento firmato in una posizione all&#39;interno della directory di payload.

## Passaggi di Document Services {#document-services-steps}

AEM Document Services è un insieme di servizi per la creazione, l&#39;assemblaggio e la protezione di documenti PDF.  AEM Forms fornisce un passaggio AEM flusso di lavoro separato per ogni servizio Document:

### Applica timestamp documento passaggio {#apply-document-time-stamp-step}

Aggiunta di marca temporale a un documento. Vengono forniti i dettagli del documento, ad esempio il percorso del documento di input, il nome del documento di input, la posizione in cui memorizzare i dati esportati. Potete scegliere di sovrascrivere il file di payload esistente o scegliere un nome file diverso per memorizzare i dati in un file diverso in una cartella payload.

### Converti in passaggio immagine {#convert-to-image-step}

Converte un documento PDF in un file di immagine. I formati immagine supportati sono JPEG, JPEG2000, PNG e TIFF. Le seguenti informazioni si applicano alle conversioni a immagini TIFF:

* Viene generato un file TIFF con più pagine.
* Alcune annotazioni non sono incluse nelle immagini TIFF. Le annotazioni che richiedono  Acrobat per generare il relativo aspetto non sono incluse.

### Converti in PDF/A passaggio {#convert-to-pdf-a-step}

Converte un documento PDF in formato PDF/A utilizzando le opzioni disponibili. La versione PDF/A del formato PDF (Portable Document Format) è specializzata nell&#39;archiviazione e nella conservazione a lungo termine dei documenti.

### Converti in fase PS {#convert-to-ps-step}

Convertire i documenti PDF in PostScript. Durante la conversione in PostScript, è possibile utilizzare l&#39;operazione di conversione per specificare il documento di origine e se convertire in PostScript livello 2 o 3. Il documento PDF convertito in file PostScript deve essere non interattivo.

### Crea PDF dal passaggio del tipo specificato {#create-pdf-from-specified-type-step}

Generare un documento PDF da un file di input. Il documento di input può essere relativo al payload, avere un percorso assoluto o essere payload stesso.

### Crea PDF da URL/HTML/passaggio ZIP {#create-pdf-from-url-html-zip-step}

Genera un documento PDF a partire da URL, HTML e file ZIP forniti.

### Passaggio dati di esportazione {#export-data-step}

Esporta i dati da un file PDF forms o XDP. È necessario immettere il percorso del file Documento di input e Formato dati di esportazione. Le opzioni di Esporta formato dati sono Auto, XDP e XmlData.

###  Export PDF al passaggio di tipo specificato {#export-pdf-to-specified-type-step}

Converte un documento PDF in un formato selezionato.

### Genera passaggio PDF non interattivo {#generate-non-interactive-pdf-step}

Generare un PDF non interattivo. Offre diverse opzioni di personalizzazione.

### Passaggio dati di importazione {#import-data-step}

Unisce i dati del modulo in un modulo PDF. È possibile importare i dati del modulo in un modulo PDF.

### Richiama il passaggio DDX {#invoke-ddx-step}

Esegue il file DDX sulla mappa specificata dei documenti di input e restituisce i documenti PDF modificati.

###  passo Optimize PDF {#optimize-pdf-step}

Ottimizza i file PDF riducendone le dimensioni. Il risultato di questa conversione è rappresentato da file PDF di dimensioni inferiori rispetto alle versioni originali. Questa operazione converte anche i documenti PDF nella versione PDF specificata nei parametri di ottimizzazione.

Le impostazioni di ottimizzazione specificano la modalità di ottimizzazione dei file. Di seguito sono riportati alcuni esempi di impostazioni:

* Versione PDF di destinazione
* Eliminazione di oggetti quali azioni JavaScript e miniature di pagina incorporate
* Eliminazione di dati utente quali commenti e allegati di file
* Eliminazione delle impostazioni non valide o non utilizzate
* Compressione di dati non compressi o utilizzo di algoritmi di compressione più efficienti
* Rimozione dei font incorporati
* Impostazione dei valori di trasparenza

### Rendering del modulo PDF passaggio {#render-pdf-form-step}

Consente di eseguire il rendering di un modulo creato in Form Designer (XDP) in un modulo PDF.

### Passaggio del documento protetto {#secure-document-step}

Cifra, firma e certifica un documento.  AEM Forms supporta sia la crittografia basata su password che la crittografia basata su certificato. È inoltre possibile scegliere tra vari algoritmi per la firma dei documenti. Ad esempio, SHA-256 e SH-512. È inoltre possibile utilizzare il passaggio del flusso di lavoro per leggere ed estendere i documenti PDF. Il passaggio del flusso di lavoro fornisce l&#39;opzione per abilitare la decodifica dei codici a barre, le firme digitali, l&#39;importazione e l&#39;esportazione di dati PDF e altre opzioni.

### Passaggio di invio alla stampante {#send-to-printer-step}

Inviare un documento direttamente a una stampante. Supporta i seguenti meccanismi di accesso alla stampa:

* **Stampante** con accesso diretto: Una stampante installata sullo stesso computer è denominata stampante con accesso diretto e il computer è denominato host della stampante. Questo tipo di stampante può essere una stampante locale collegata direttamente al computer.
* **Stampante** con accesso diretto: La stampante installata in un server di stampa è accessibile da altri computer. Per la connessione a una stampante di rete sono disponibili tecnologie quali il sistema di stampa comune UNIX® (CUPS) e il protocollo Line Printer Daemon (LPD). Per accedere a una stampante con accesso indiretto, specificare il nome IP o host del server di stampa. Utilizzando questo meccanismo, è possibile inviare un documento a un URI LPD quando la rete ha un LPD in esecuzione. Il meccanismo consente di indirizzare il documento a qualsiasi stampante collegata alla rete con un LPD in esecuzione.

