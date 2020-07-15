---
title: Note sulla versione di AEM 6.4 Cumulative Fix Pack
description: Note sulla versione specifiche  Adobe Experience Manager 6.4 Cumulative Fix Pack.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 1b6254e98b65b64071ab4634706bd1ad3d2fd8df
workflow-type: tm+mt
source-wordcount: '2119'
ht-degree: 21%

---


# Note sulla versione di AEM 6.4 Cumulative Fix Pack {#aem-cumulative-fix-pack-release-notes}

## Informazioni sulla versione {#release-information}

| Prodotti | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versione | 6.4.8.1 |
| Tipo | Cumulative Fix Pack |
| Data | 04 giugno 2020 |
| Prerequisito | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL di download | AEM 6.4.8.1 sulla distribuzione [del software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## Funzionalità incluse in AEM 6.4.8.1 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1 è un aggiornamento importante che include diverse correzioni interne e per i clienti, a partire dalla disponibilità generale di AEM 6.4 Service Pack 8 (6.4.8.0) nel marzo 2020.

AEM Cumulative Fix Pack 6.4.8.1 dipende da AEM 6.4 Service Pack 8. Pertanto, dopo l&#39;installazione di AEM 6.4.8.1 Service Pack 8, è necessario installare il pacchetto AEM Cumulative Fix Pack 6.4.

Alcuni degli elementi di rilievo di AEM 6.4.8.1 sono:

* È stata rimossa l&#39;integrazione di Package Share con  Adobe Experience Manager.
* Aggiornamento dell’archivio incorporato (Apache Jackrabbit Oak) alla versione 1.8.21.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## Elenco delle modifiche {#list-of-changes}

 Adobe Experience Manager 6.4.8.1 contiene le correzioni ai seguenti problemi.

### Sites {#sites-6481}

* Quando il nome di un componente locale in LiveCopy è identico al nome di un componente nel blueprint e il componente viene implementato dal blueprint, il termine _msm_move non viene aggiunto al nome del componente locale (NPR-33207).
* I parametri aggiunti alla richiesta originale non sono inclusi nell&#39;URL di reindirizzamento (NPR-33174).
* Quando l&#39;opzione Coral.Select imposta emptyOption=true o contiene un elemento predefinito con valore = &quot;, il file dropdownshowhide.js restituisce un errore: Errore di tipo non rilevato: component.getValue non è una funzione (NPR-33163).
* Quando un componente include un altro componente come risorsa semplice per i dati, il segnaposto del componente contenitore principale viene sostituito con il segnaposto dei componenti interni (NPR-33119).
* Se si basa un frammento di contenuto su uno schema e questo contiene un&#39;area di testo obbligatoria o un campo percorso, il frammento di contenuto non viene salvato (NPR-33007)
* Quando create un componente personalizzato utilizzando il componente per frammento esperienza fornito e lo utilizzate nelle pagine AEM Sites, AEM non visualizza riferimenti (utilizzo) per il componente personalizzato (NPR-32852).
* Quando una pagina di AEM Sites fa parte di un set di contenuti di grandi dimensioni con più Live Copy, l&#39;anteprima della cronologia della versione della pagina non viene caricata (NPR-32772).
* Quando promuovi un lancio, aggiunge il mixin &quot;cq:LiveRelationship&quot; a ogni componente aggiunto al lancio. Influisce su tutti gli avvii, indipendentemente dal fatto che sia stato creato un lancio con o senza selezionare il comando —  Eredita dati dal vivo della pagina di origine —  (NPR-32664).
* All&#39;avvio dell&#39;impaginazione, il Selettore frammenti esperienza non carica tutti gli elementi (NPR-32605).
* Impossibile creare un lancio per una pagina di AEM Sites. La creazione dell&#39;avvio genera un errore (NPR-32544).
* Manage Publication non include le risorse di riferimento nel flusso di lavoro di attivazione della richiesta (NPR-32463).
* Il controllo dello stato di Dispatcher visualizza un messaggio di `Invalid cookie header` avviso nei file di registro (NPR-33630).

### Assets {#assets-6481}

* Il conteggio delle risorse non cambia in base alla modifica nella selezione in visualizzazione a elenco (NPR-33285).

* Il pulsante Avanti non è attivato quando si seleziona il nodo principale (dove è visibile una singola cartella figlia) e si seleziona la cartella secondaria (NPR-33284).

* L’interfaccia utente touch non riesce a eseguire il rendering (con errore) per gli utenti che non dispongono dell’accesso in lettura nella directory principale dell’archivio, quando è abilitata la modalità DMS7 o ibrida (NPR-33175).

* I caratteri GB18030 che si verificano nei nomi delle cartelle e delle risorse diventano vuoti nei file zip scaricati (NPR-33150).

* Al ritaglio avanzato di una risorsa che si trova all’interno di una cartella principale con `.` carattere punto nel nome (NPR-32755) viene creata una cartella aggiuntiva.

* Il caricamento lento non viene attivato e non più di 100 risorse vengono visualizzate quando si seleziona per controllare le attività dalla inbox delle notifiche (NPR-32749).

* La pagina di collegamento per la condivisione della raccolta è interrotta a causa della modifica in coral-info (NPR-32510).

* L&#39;elaborazione delle risorse durante il caricamento in blocco si blocca (CQ-4293916).

### Platform {#platform-6481}

* Il [!DNL Sling] filtro non viene chiamato se la voce della `sling:match` mappa è creata in `/etc/maps` (NPR-33308).
* Tutti gli agenti di scaricamento vengono attivati quando si disattiva una pagina (NPR-32941).
* Quando si utilizza l&#39; `ScriptProcessor` API per minificare una libreria JavaScript, il file di registro visualizza un messaggio di errore che indica che il codice JavaScript non è conforme alla modalità rigorosa. L&#39;API non fornisce l&#39;opzione per abilitare o disabilitare la modalità rigorosa. (NPR-32746).
* Quando una query SQL viene eseguita per un periodo di tempo più lungo, ad esempio 7 ore, AEM smette di rispondere (NPR-33043).

### Interfaccia utente {#ui-6481}

* Quando eseguite una ricerca o sfogliate un percorso utilizzando una finestra di dialogo di selezione, viene visualizzato tutto il contenuto del nodo JCR selezionato invece di visualizzare solo le immagini (NPR-32712).

### Progetti traduzione {#tranlation-6481}

* Nei registri `NullPointerException` viene visualizzato un errore durante l&#39;esecuzione di un processo di traduzione (NPR-32220).

### Communities {#communities-6481}

* Gli autori, dopo aver creato un nuovo gruppo, non vengono reindirizzati alla sezione Gruppo  community sulla versione [!DNL Internet Explorer] 11 (NPR-33202).
* Errore durante l&#39;accesso alla pagina Flusso  attività (NPR-33152).
* La modifica di un [!DNL Communities] gruppo e la modifica dell&#39;immagine in miniatura non comporta l&#39;aggiornamento della miniatura del gruppo (NPR-32603).
* Durante la creazione di una versione di notifiche e sottoscrizioni di contenuti generati dall&#39;utente (UGC), viene memorizzato un ID errato della pagina di origine (CQ-4289703).

### Flusso di lavoro {#workflow-6481}

* Alcuni componenti non vengono visualizzati nella finestra di dialogo visualizzata quando un utente completa un flusso di lavoro che include un passaggio [!UICONTROL Partecipante alla] finestra di dialogo (NPR-32989).

* Il caricamento dell&#39;opzione [!UICONTROL Timeline] nella parte sinistra richiede più tempo del previsto (NPR-32850).

### Forms {#forms-6481}

>[!NOTE]
>
>AEM Cumulative Fix Pack non include correzioni per i AEM Forms. Tali correzioni vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi per Forms. Inoltre, viene rilasciato un programma di installazione cumulativo che include correzioni per AEM Forms su JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Gestione corrispondenza: Quando un utente incolla contenuto da un [!DNL Word] documento, il frammento del documento di testo non mantiene la formattazione (NPR-33213).
* Moduli adattivi: Una nuova riga di una stringa in un dizionario di moduli adattivi aggiunge `&#xa;` caratteri al dizionario (NPR-33265).
* Moduli adattivi: L&#39;utente non è in grado di salvare un modulo adattivo con più allegati (NPR-33214).
* Moduli adattivi: `AddInstance` e `RemoveInstance` i metodi per la classe Instance Manager non aggiungono un numero dinamico di istanze per i frammenti di caricamento pigri in [!DNL Internet Explorer 11] (NPR-33201).
* Moduli adattivi:  Analytics abilitato su un modulo adattivo incorporato in una [!DNL Sites] pagina non registra i dati per gli eventi Submit e Abandon (NPR-31359).
* Moduli adattivi: Quando un utente incolla il contenuto di un [!DNL Word] documento in un modulo adattivo e lo invia, il modulo adattivo inviato include caratteri unicode. Inoltre, la conversione da PDF a PDF/A non riesce a causa dei caratteri unicode (NPR-33348).
* BackendIntegration: Le richieste del modello dati del modulo non riescono a causa dello stato inattivo non corretto del token di aggiornamento (NPR-33168).
* Document Services: Il servizio Converti PDF non è in grado di convertire i documenti PDF in PostScript a causa di jar Gibson mancanti [!DNL WebLogic] sul [!DNL Linux] server (NPR-33515, CQ-4292239).
* Document Services: Quando un utente converte un file di testo in un PDF, i caratteri giapponesi non vengono rappresentati correttamente (NPR-33239).

## Install 6.4.8.1 {#install}

### Requisiti di configurazione {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Per i clienti con Feature Pack installati in AEM 6.4. I Feature Pack opzionali forniti da Adobe dipendono dalla versione release e dai service pack. Se avete installato Feature Pack, contattate il team di assistenza clienti di AEM per verificare la compatibilità di questi pacchetti con questo fix pack cumulativo per AEM 6.4.

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* In una distribuzione con MongoDB e più istanze, installa AEM 6.4.8.1 in una delle istanze Autore tramite Gestione pacchetti.
* Prima di installare il fix pack cumulativo, accertati di disporre di uno snapshot o di un nuovo backup dell’istanza AEM.
* Riavvia l’istanza prima dell’installazione. Anche se ciò è necessario solo quando l&#39;istanza è ancora in modalità di aggiornamento (e questo accade quando l&#39;istanza è stata appena aggiornata da una versione precedente), si consiglia generalmente se l&#39;istanza è in esecuzione per un periodo di tempo più lungo.

>[!NOTE]
>
>Adobe sconsiglia la rimozione o la disinstallazione del pacchetto AEM 6.4.8.1.

### Installare Cumulative Fix Pack {#install-cumulative-fix-pack}

Per installare il Cumulative Fix Pack in un’istanza AEM 6.4.8.0 esistente, effettua le seguenti operazioni:

1. Fate clic sul collegamento Distribuzione [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) software per scaricare il pacchetto.

1. Aprite [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) e fate clic su **[!UICONTROL Carica pacchetto]** per caricare il pacchetto.

1. Selezionate il nome del pacchetto e fate clic su **[!UICONTROL Installa]**.

>[!NOTE]
>
>**La finestra di dialogo nell’interfaccia utente di Gestione pacchetti talvolta si chiude prematuramente durante l’installazione della versione 6.4.8.1**
>
>È consigliabile attendere che i registri degli errori si stabilizzino prima di accedere all’istanza. L&#39;utente deve attendere i registri specifici relativi alla disinstallazione del bundle dell&#39;utility di aggiornamento prima di assicurarsi che l&#39;installazione abbia esito positivo. Il problema si verifica in genere in Safari, ma può accadere in modo intermittente in qualsiasi browser.

### Installazione automatica {#auto-installation}

Esistono due modi per installare automaticamente AEM 6.4.8.1 in un’istanza in esecuzione:

A. Inserite il pacchetto in ..*/crx-quickstart/install* mentre il server è in esecuzione. Il pacchetto viene installato automaticamente.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.1 non supporta l’installazione tramite bootstrap.

### Convalidare l’installazione {#validate-install}

1. La pagina Informazioni sul prodotto (*/system/console/ productinfo *) deve ora mostrare la stringa di versione aggiornata &quot; Adobe Experience Manager, versione 6.4.8.1&quot; in Prodotti installati.
1. Tutti i bundle OSGi risultano come ATTIVI o FRAMMENTI nella console OSGi (usa la console Web: /system/console/bundles).
1. Il bundle OSGI org.apache.jackrabbit.oak-core è sulla versione 1.8.17 o successiva (Usa console Web: /system/console/bundle).

Per determinare la piattaforma certificata da eseguire con questa versione di AEM Sites e risorse, consulta Requisiti [](../sites-deploying/technical-requirements.md)tecnici.

>[!Note]
>On successful installation of the package, an >informational message appears indicating that the content >package has installed successfully,  such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Aggiornamento dei visualizzatori Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.1 contiene la nuova versione dei visualizzatori Dynamic Media (5.10.1) che consente di verificare la presenza di nomi duplicati nella pagina dei predefiniti per immagini. Ai clienti Dynamic Media viene consigliato di eseguire il comando seguente per aggiornare i predefiniti per visualizzatori in scatola.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

che copierà i nuovi predefiniti per visualizzatori nella posizione /conf.

### Installare il pacchetto di componenti aggiuntivi per AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms. Le correzioni apportate in AEM Forms vengono distribuite utilizzando un pacchetto separato di componenti aggiuntivi.

1. Accertatevi di aver installato AEM Cumulative Fix Pack.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/it/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://helpx.adobe.com/experience-manager/6-4/forms/using/installing-configuring-aem-forms-osgi.html#InstallAEMFormsaddonpackage).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Ignora questa sezione se non usi AEM Forms in JEE. Le correzioni apportate in JEE per AEM Forms vengono distribuite tramite un programma di installazione separato.

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0016](https://helpx.adobe.com/it/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### JAR Uber {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Funzioni rimosse/obsolete {#removed-deprecated-features}

In questa sezione sono elencate le funzionalità rimosse o dichiarate obsolete in AEM 6.4.

| Area | Funzione obsoleta | Sostituzione | Versione |
|---|---|---|---|
| Assets | Gestisci azione tag per risorse secondarie | Nessuna sostituzione | AEM 6.4.2.0   |
| Integrazione di Assets con Adobe Creative Cloud | [AEM per la condivisione](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/creative-cloud.html) di cartelle di Creative Cloud è stato introdotto in AEM 6.2 per consentire agli utenti creativi di accedere alle risorse da AEM. Una nuova funzionalità introdotta nell’applicazione Creative Cloud, Adobe Asset Link, offre un’esperienza utente migliore e un accesso più efficace alle risorse da AEM direttamente da Photoshop, InDesign e Illustrator. Adobe non apporterà ulteriori miglioramenti alla funzionalità di condivisione cartelle. Sebbene la funzione sia inclusa in AEM, i clienti sono invitati a usare la sostituzione. | Collegamento risorse Adobe o app desktop. Per ulteriori informazioni, consulta l’articolo sull’[integrazione di AEM con Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0   |

## Problemi noti {#known-issues}

* Durante l&#39;installazione di AEM 6.4.8.1, l&#39;aggiornamento della [!DNL Chrome] versione 83 causa un problema nella creazione di pacchetti. Per risolvere il problema, utilizzate altri browser disponibili, ad esempio [!DNL Internet Explorer] e [!DNL Firefox], o altre opzioni di installazione dei pacchetti standard di AEM. Il problema viene risolto dopo l&#39;installazione di AEM 6.4.8.1.

* Impossibile inviare un&#39;e-mail al server SMTP remoto utilizzando il mittente di posta predefinito di AEM, in quanto consente solo la comunicazione mediante TLS v1.2. Rimuovete il bundle `javax.mail:mail:1.5.0-b01` da `system/console` e aggiornate i bundle per risolvere il problema.

Per informazioni sui problemi noti di AEM 6.4.8.0 Service Pack, consultate le note sulla versione di [AEM 6.4.8.0 Service Pack](sp-release-notes.md).

## Bundle OSGi e pacchetti di contenuti inclusi {#osgi-bundles-and-content-packages-included}

Nei documenti di testo seguenti sono elencati i bundle OSGi e i pacchetti di contenuti inclusi in AEM 6.4.8.1.

Elenco dei bundle OSGi inclusi in AEM 6.4.8.1

[Ottieni file](assets/6.4.8.1_osgi_bundles.txt)

Elenco dei pacchetti di contenuti inclusi in AEM 6.4.8.1

[Ottieni file](assets/6.4.8.1_content_packages.txt)

## Risorse utili {#helpful-resources}

* [Note sulla versione di AEM 6.4](../release-notes/release-notes.md)
* [Pagina del prodotto AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentazione di AEM 6.4](https://helpx.adobe.com/it/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Siti con limitazioni {#restricted-sites-new}

Questi siti sono disponibili solo per i clienti. Se sei un cliente e hai bisogno di accedere, contatta il manager del tuo account Adobe.

* [Download del prodotto da licensing.adobe.com](https://licensing.adobe.com/)
* [Assistenza clienti](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
