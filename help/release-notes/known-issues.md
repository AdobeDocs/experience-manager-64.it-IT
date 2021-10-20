---
title: Problemi noti in AEM 6.4
seo-title: Known Issues in AEM 6.4
description: Problemi noti in Adobe Experience Manager 6.4
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: 7f80933dfe8439bbd57ef85ece96399f7ec39f64
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 4%

---

# Problemi noti {#known-issues}

Questa pagina tiene un elenco dei problemi noti rilasciati da Adobe Experience Manager 6.4 ad aprile 2018. Per ulteriori informazioni sui problemi noti, [contattare il supporto](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=it).

## Dispositivi ibridi {#hybrid-devices}

I dispositivi ibridi non sono supportati. Durante l’utilizzo di tali dispositivi è possibile rilevare diversi problemi. Le seguenti procedure suggerite aiutano a risolvere molti problemi:

Se utilizzi Google Chrome come browser:

* Tipo `chrome://flags/` nella barra degli indirizzi e premere Invio.
* Fai clic su Abilita eventi touch > Disabilitato.
* Riavvia il browser (tutte le schede e le finestre).

Se utilizzi Mozilla Firefox come browser:

* Tipo `about:config` nella barra degli indirizzi e premere Invio.
* Filtra le impostazioni in `dom.w3c`.
* Assicurati che le impostazioni siano `0` e `false`.
* Riavvia il browser.

Se utilizzi Microsoft Edge come browser:

* Tipo `about:flags` nella barra degli indirizzi e premere Invio.
* Scorri fino a Funzioni sperimentali **[!UICONTROL Touch]**.
* Fai clic su **[!UICONTROL Abilita eventi touch]**.
* Seleziona **[!UICONTROL Sempre disattivato]**.
* Riavvia il browser.

## Platform {#platform}

* **Dashboard delle operazioni:** La barra di avanzamento non viene visualizzata quando nel file di backup manca l&#39;estensione .zip. (GRANITE-10713)
* **HTL:** L&#39;oggetto Java Use con spazi bianchi finali nella dichiarazione del pacchetto blocca il servizio SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:** File di configurazione ancora presente nell&#39;archivio anche dopo configuration.delete() (GRANITE-20618)
* **Impostazioni cloud:** La console viene interrotta dopo aver modificato il contenitore di configurazione (GRANITE-20726)
* **Sicurezza:** L&#39;integrazione IMS non riesce con il percorso contestuale personalizzato (GRANITE-20639)
* **Sicurezza:** Migliorare la classificazione JAAS predefinita dei moduli di accesso SSO, esterni e predefiniti (GRANITE-20590)
* **Tooling - CRX DE Lite:** L&#39;onda della vista delle proprietà continua a muoversi verso l&#39;alto (GRANITE-12040)
* **Tooling - CRX DE Lite:** Impossibile salvare le modifiche a Tipi di valore &quot;lunghi&quot; a meno che non si faccia doppio clic su Nome proprietà (GRANITE-12351)

* **Tooling - CRX DE Lite:** la ricerca ctrl+F sui file di testo aperti si blocca alla ricerca RegExp (GRANITE-5996)

* **Tooling - CRX DE Lite:** Proprietà del nodo non visualizzata dopo aver rinominato il nodo (GRANITE-7160)
* **Interfaccia utente:** Pulldown &quot;more...&quot; non mostra tutti gli elementi quando viene aperto in un elemento pover su IE e Firefox (GRANITE-16326)
* **Interfaccia utente:** La descrizione comando Info viene nascosta quando si utilizza il layout a colonne fisse con 2 colonne affiancate (GRANITE-16869)
* **Interfaccia utente:** Errore non gestito durante la rappresentazione come utente inesistente (GRANITE-23228). Soluzione alternativa [implementazione di un gestore di errori](/help/sites-developing/customizing-errorhandler-pages.md) personalizzare il messaggio di errore.

* **Omnisearch:** Ricerche con eccezione di causa barra rovesciata (GRANITE-11769)
* **Omnisearch:** Apri &quot;Visualizza impostazioni&quot; nella vista a elenco e causa la modifica del filtro di ricerca (GRANITE-16524)
* **Omnisearch:** Elenco errato di configurazioni colonna visualizzate durante la ricerca di Assets da Sites (GRANITE-16527)

* **Omnisearch:** I predicati della barra a sinistra vanno d&#39;accordo con la richiesta del server Omnisearch (GRANITE-20524)
* **Omnisearch:** Omnisearch non supporta i percorsi contestuali (GRANITE-16044)

## Assets {#assets}

* **Ricerca**: La ricerca non restituisce alcun risultato se la stringa di ricerca inizia con uno spazio vuoto [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Ricerca**: Nell’interfaccia classica e i tag non sono visibili nella ricerca (CQ-4235239)

* **Interfaccia**: L’interfaccia utente delle risorse non risponde dopo l’opzione Copia-incolla e Seleziona-tutto (CQ-4236142)

* **Interfaccia**: Impossibile spostare le risorse dopo il caricamento lento (CQ-4236134)

* **Rapporti**: Errore nella creazione del rapporto sulla modifica delle risorse (CQ-4239744)

* **Rapporti**: La generazione regolare dei rapporti sulle risorse pianificata fallisce in modo incoerente (alcuni rapporti rimangono in coda) (CQ-4239089)

* **Metadati**: Quando si aggiunge un campo di testo con più valori allo schema delle risorse, la regola di CSS del campo richiesto non funziona (CQ-4239333)

* **BrandPortal**: La pubblicazione su BrandPortal non funziona per le raccolte (CQ-4238731)

* **Carica**: Durante il caricamento di risorse con caratteri speciali nel nome del file, il messaggio di errore di convalida relativo ai caratteri non consentiti non viene visualizzato per ciascuna risorsa. Anche se viene visualizzata solo per la prima risorsa, l’interfaccia indica chiaramente all’utente che il nome file della risorsa fornita non è consentito. (CQ-4256876)

## Communities {#communities}

* **Moderazione** - Impossibile eliminare il post principale come singola operazione di eliminazione dall&#39;interfaccia utente di moderazione in blocco (CQ-4236797)

* **Console** - Il collegamento Password o nome utente dimenticato viene reindirizzato alla pagina di accesso invece del modulo di recupero password corrispondente (CQ-4237682)

## Forms {#forms}

### Installazione

* (Solo JEE per AEM Forms) Quando si avvia il server applicazioni JBoss mentre si esegue Configuration Manager, vengono restituiti errori di chiamata EJB e di errore di avvio. Tuttavia, puoi ignorarli. (Ref. CQ-4229793)
* Quando AEM Forms viene avviato, la `SAX Security Manager could not be setup` viene visualizzato un avviso. (CQ-4297403)

### Comunicazioni interattive

* L&#39;interfaccia utente dell&#39;agente impiega un po&#39; a caricare comunicazioni interattive che includono elementi grafico o immagine. (CQ-4236630)
* Il formato di visualizzazione dei dati nell&#39;anteprima di stampa è gg-mm-aaaa mentre nell&#39;anteprima web è `dd-mmm-yy` (CQ-4237045)
* Il canale Web di comunicazione interattiva supporta solo elenchi ordinati e non ordinati. Nei frammenti di documento elenco, l’elenco composto e il rientro non sono supportati per il canale Web della comunicazione interattiva. (CQ-4233672)
* I seguenti problemi vengono osservati quando il canale web si sincronizza con il canale di stampa:

   * La sincronizzazione del canale Web richiede un po&#39; di tempo quando si passa dal canale di stampa per la prima volta.
   * Il canale web non si sincronizza se il canale di stampa include un componente grafico non configurato. Per risolvere il problema, elimina il componente grafico e sincronizza di nuovo.
   * A volte la sincronizzazione non riesce con l&#39;errore &quot;Errore durante la sincronizzazione della Live Copy&quot;. Per risolvere il problema, aggiorna la pagina.
   * Il testo statico in un frammento di layout viene sostituito con il nome della cella della tabella quando la prima colonna della tabella è una colonna di intestazione nel modello del canale di stampa.
   * Impossibile aggiungere componenti o risorse in qualsiasi posizione diversa dalla parte inferiore di una comunicazione canale web. Per posizionarlo in un’altra posizione, aggiungi un pannello nella parte inferiore del canale web e riordinalo utilizzando la struttura dei contenuti.
   * Può spostare il contenuto nell’area di destinazione ereditata del canale web senza rimuovere l’ereditarietà della Live Copy.

(CQ-4239780)

### Integrazione dei dati

* Le configurazioni di autenticazione per i servizi Web basati su SOAP non sono visibili e pertanto non possono essere configurate in Cloud Services. Per risolvere il problema:

   1. Nella console CRXDE Lite, passa al seguente nodo.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigWizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Aggiorna il valore della proprietà value allo stesso valore della proprietà text.
   1. Fai clic su Salva tutto per salvare la configurazione.

(CQ-4238462)

### Integrazione Adobe Sign

* La pianificazione di Adobe Sign smette di funzionare in modo intermittente, pertanto il segno in sospeso dei moduli non passa all’invio. Per risolvere il problema, riavvia il **Supporto per l&#39;utilità di pianificazione Apache Sling** dalla console Web AEM all&#39;indirizzo https://[*server*]:[*porta*]/system/console/bundles.

### Authoring Forms adattivo

* Il componente Grafico nei moduli adattivi occupa più spazio di quanto lo sia normalmente.
* Viene restituita un’eccezione quando si salvano proprietà per moduli adattivi, frammenti di moduli adattivi o comunicazioni interattive nell’interfaccia utente di Forms Manager.
* Nei dispositivi Samsung con Android 6.0 non viene rispettato il numero massimo di caratteri specificato per una casella di testo di modulo adattivo. (Ref. CQ-4235205)
* Quando si invia un modulo contenente un campo di caricamento HTML standard da un dispositivo Apple iOS, a volte il contenuto del file non viene inviato e viene ricevuto un file a 0 byte dall’altro lato. Apple iOS 15.1 fornisce una correzione al problema.

