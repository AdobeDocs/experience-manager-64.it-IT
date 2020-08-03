---
title: Problemi noti in AEM 6.4
seo-title: Problemi noti in AEM 6.4
description: Problemi noti in  Adobe Experience Manager 6.4
seo-description: Problemi noti  Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 4%

---


# Problemi noti {#known-issues}

Questa pagina contiene un elenco dei problemi noti  Adobe Experience Manager 6.4, rilasciato nell’aprile 2018. Per ulteriori informazioni sui problemi noti, [contattate il supporto](https://helpx.adobe.com/it/support/experience-manager.html).

## Dispositivi ibridi {#hybrid-devices}

I dispositivi ibridi non sono supportati. Durante l&#39;utilizzo di tali dispositivi possono verificarsi diversi problemi. Le procedure suggerite di seguito consentono di risolvere molti problemi:

Se utilizzate Google Chrome come browser:

* Digitate `chrome://flags/` la barra degli indirizzi e premete Invio.
* Fate clic su Attiva eventi di tocco > Disattivato.
* Riavviate il browser (tutte le schede e le finestre).

Se si utilizza Mozilla Firefox come browser:

* Digitate `about:config` la barra degli indirizzi e premete Invio.
* Filtrare le impostazioni su `dom.w3c`.
* Verificate che le impostazioni siano `0` e `false`.
* Riavviate il browser.

Se utilizzate Microsoft Edge come browser:

* Digitate `about:flags` nella barra degli indirizzi e premete Invio.
* Scorrete fino alle funzioni Sperimentali e quindi **[!UICONTROL toccate]**.
* Fate clic su **[!UICONTROL Abilita eventi]** di tocco.
* Selezionare **[!UICONTROL Sempre disattivato]**.
* Riavviate il browser.

## Platform {#platform}

* **Pannello operazioni:** La barra di avanzamento non viene visualizzata quando nel file di backup manca l&#39;estensione .zip. (GRANITE-10713)
* **HTL:** Oggetto Java Use con spazi vuoti finali nella dichiarazione del pacchetto blocca il servizio SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:** File di configurazione ancora presente nell&#39;archivio anche dopo configurazione.delete() (GRANITE-20618)
* **Impostazioni cloud:** Console viene interrotta dopo la modifica del contenitore di configurazione (GRANITE-20726)
* **Sicurezza:** L&#39;integrazione IMS non riesce con il percorso contestuale personalizzato (GRANITE-20639)
* **Sicurezza:** Migliorare la classificazione JAAS predefinita dei moduli di login SSO, esterni e predefiniti (GRANITE-20590)
* **Tooling - CRX DE Lite:** La vista Ridge of properties continua a muoversi verso l&#39;alto (GRANITE-12040)
* **Tooling - CRX DE Lite:** Non è possibile salvare le modifiche in &quot;Long&quot; Value Types a meno che non si faccia doppio clic su Property Name (GRANITE-12351)

* **Tooling - CRX DE Lite:** ctrl+F per la ricerca sui file di testo aperti si blocca nella ricerca RegExp (GRANITE-5996)

* **Tooling - CRX DE Lite:** La proprietà Node non viene visualizzata dopo aver rinominato il nodo (GRANITE-7160)
* **Interfaccia utente:** Pulldown &quot;more...&quot; non visualizza tutti gli elementi quando viene aperto in un elemento del puntatore su IE e Firefox (GRANITE-16326)
* **Interfaccia utente:** La descrizione delle informazioni viene nascosta quando si utilizza il layout delle colonne fisse con 2 colonne affiancate (GRANITE-16869)
* **Interfaccia utente:** Errore non gestito durante la rappresentazione come utente inesistente (GRANITE-23228). Soluzione [implementando un gestore](/help/sites-developing/customizing-errorhandler-pages.md) di errori per personalizzare il messaggio di errore.

* **Omnisearch:** Ricerche con eccezione di causa barra rovesciata (GRANITE-11769)
* **Omnisearch:** Aprite &quot;Visualizza impostazioni&quot; nella vista a elenco per cambiare il filtro di ricerca (GRANITE-16524)
* **Omnisearch:** Elenco errato di configurazioni di colonne visualizzate durante la ricerca di risorse da Siti (GRANITE-16527)

* **Omnisearch:** I predicati della barra a sinistra vanno di pari passo con la richiesta del server Omnisearch (GRANITE-20524)
* **Omnisearch:** Omnisearch non supporta i percorsi contestuali (GRANITE-16044)

## Assets {#assets}

* **Ricerca**: La ricerca non restituisce alcun risultato se la stringa di ricerca inizia con uno spazio vuoto [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Ricerca**: Nell’interfaccia classica i tag non sono visibili nella ricerca (CQ-4235239)

* **Interfaccia**: L&#39;interfaccia utente delle risorse non risponde più dopo Copy-Paste e Select-All (CQ-4236142)

* **Interfaccia**: Impossibile spostare le risorse dopo il caricamento inattivo (CQ-4236134)

* **Rapporti**: Errore nella creazione del report sulla modifica delle risorse (CQ-4239744)

* **Rapporti**: Generazione del rapporto sulle risorse pianificata e regolare non coerente (alcuni rapporti rimangono in coda) (CQ-4239089)

* **Metadati**: Quando si aggiunge un campo di testo con più valori allo schema delle risorse, la regola di CSS del campo richiesto non funziona (CQ-423933)

* **BrandPortal**: Publish to BrandPortal non funziona per le raccolte (CQ-4238731)

* **Carica**: Durante il caricamento di risorse con caratteri speciali nel nome del file, per ogni risorsa non viene visualizzato il messaggio di errore di convalida relativo ai caratteri non consentiti. Anche se viene visualizzata solo per la prima risorsa, l&#39;interfaccia indica chiaramente all&#39;utente che il nome file della risorsa fornita non è consentito. (CQ-4256876)

## Communities {#communities}

* **Moderazione** - Impossibile eliminare il post principale come singola operazione di eliminazione dall&#39;interfaccia utente di moderazione in blocco (CQ-4236797)

* **Console** - Il collegamento Password o Nome utente dimenticato viene reindirizzato alla pagina di accesso invece del modulo di recupero password corrispondente (CQ-4237682)

## Forms {#forms}

### Installazione e implementazione

* (Solo AEM Forms JEE) Quando si esegue l&#39;avvio del server applicazioni JBoss durante l&#39;esecuzione di Configuration Manager, vengono restituiti errori di chiamata EJB e di avvio automatico. Tuttavia, potete ignorarli. (Ref. CQ-4229793)
* All&#39;avvio dei AEM Forms, viene visualizzato l&#39; `SAX Security Manager could not be setup` avviso. (CQ-4297403)

### Comunicazioni interattive

* L&#39;interfaccia utente dell&#39;agente richiede un po&#39; di tempo per caricare comunicazioni interattive che includono elementi grafici o immagini. (CQ-4236630)
* Il formato di visualizzazione dei dati nell&#39;anteprima di stampa è gg-mm-aaaa mentre nell&#39;anteprima Web è `dd-mmm-yy` (CQ-4237045)
* Il canale Web di comunicazione interattiva supporta solo elenchi ordinati e non ordinati. Nei frammenti di documento elenco, l&#39;elenco composto e il rientro non sono supportati per il canale Web della comunicazione interattiva. (CQ-4233672)
* Quando il canale Web si sincronizza con il canale di stampa si verificano i seguenti problemi:

   * La sincronizzazione del canale Web richiede un po&#39; di tempo quando si passa dal canale di stampa per la prima volta.
   * Il canale Web non si sincronizza se il canale di stampa include un componente grafico non configurato. Per risolvere il problema, eliminare il componente grafico e sincronizzarlo di nuovo.
   * A volte la sincronizzazione non riesce con l&#39;errore &quot;Errore durante la sincronizzazione della Live Copy&quot;. Per risolvere il problema, aggiornate la pagina.
   * Il testo statico in un frammento di layout viene sostituito con il nome della cella della tabella quando la prima colonna della tabella è una colonna di intestazione nel modello del canale di stampa.
   * Impossibile aggiungere componenti o risorse in qualsiasi posizione diversa dalla parte inferiore della comunicazione tramite canale Web. Per posizionarlo in un’altra posizione, aggiungete un pannello nella parte inferiore del canale Web e riordinatelo utilizzando la struttura ad albero del contenuto.
   * Può spostare il contenuto nell&#39;area di destinazione ereditata del canale Web senza rimuovere l&#39;ereditarietà Live Copy.

(CQ-4239780)

### Integrazione dei dati

* Le configurazioni di autenticazione per i servizi Web basati su SOAP non sono visibili e pertanto non possono essere configurate nei servizi cloud. Per risolvere il problema:

   1. Nella console CRXDE Lite, passare al seguente nodo.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/create_loudconfigWizard/cloudservices/\
      wsdlauthenticationsettings/items/fissedcolumn/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Aggiornare il valore della proprietà value in modo che corrisponda al valore della proprietà text.
   1. Fate clic su Salva tutto per salvare la configurazione.

(CQ-4238462)

### Integrazione  Adobe Sign

*  pianificazione Adobe Sign smette di funzionare in modo intermittente e pertanto i moduli in attesa di firma non passano all&#39;invio. Per risolvere il problema, riavviate il bundle **Apache Sling Scheduler Support** dalla console Web AEM https://[*server*]:[*port*]/system/console/bundle.

### Authoring Forms adattivo

* Il componente Grafico nei moduli adattivi occupa più spazio di quanto non lo sia normalmente.
* Viene restituita un’eccezione quando si salvano le proprietà per moduli adattivi, frammenti di moduli adattivi o comunicazioni interattive nell’interfaccia utente di Forms Manager.
* Nei dispositivi Samsung con Android 6.0 non viene rispettato il numero massimo di caratteri specificato per una casella di testo di modulo adattivo. (Ref. CQ-4235205)
