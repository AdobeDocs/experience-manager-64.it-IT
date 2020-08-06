---
title: Interfaccia utente Recommendations per clienti
seo-title: Interfaccia utente Recommendations per clienti
description: 'Un elenco di raccomandazioni relative alle interfacce utente classiche e ottimizzate per il tocco. '
seo-description: 'Un elenco di raccomandazioni relative alle interfacce utente classiche e ottimizzate per il tocco. '
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
translation-type: tm+mt
source-git-commit: b01e95110bffc1ee96e0814e782d716ed949c1b4
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Interfaccia utente Recommendations per clienti{#user-interface-recommendations-for-customers}

Adobe Experience Manager 6.4 viene fornito con due interfacce: l’interfaccia utente del Experience Cloud  unificata e l’interfaccia classica.

Questo documento è pensato per guidare i clienti nella scelta dell’interfaccia da utilizzare a seconda della loro situazione.

Termini di interesse:

* **Interfaccia utente (o interfaccia standard)Interfaccia utente** moderna introdotta in 5.6.0 come anteprima tecnologica ed estesa nelle versioni successive. Si basa sull’esperienza utente unificata di Adobe Experience Cloud, precedentemente nota come interfaccia touch o interfaccia touch.

* **Interfaccia utente** classica basata sulla tecnologia ExtJS introdotta con CQ 5.1 nel 2008.

* **Amministrazione** sito: funzionalità per gestire la gerarchia del sito (spostamento, attivazione, riferimenti gestiti) e creare nuove pagine.

* **Funzionalità di authoring** delle pagine per aggiungere o modificare il contenuto di una pagina.

* **Funzionalità di amministrazione** di DAM/Assets per la gestione delle risorse digitali (immagini, video, documenti, download).

* **ContextHub** Capabilities per aggregare le informazioni sul visitatore e utilizzarle per vari scopi. Fornisce un&#39;interfaccia utente per simulare le persone che visitano il sito. A partire da AEM 6.2, ContextHub ha sostituito la tecnologia precedente, ClientContext.

## Generale {#general}

Negli ultimi anni  Adobe ha aggiornato tutte le soluzioni Adobe Experience Cloud con un&#39;interfaccia utente unificata. Gli utenti di tutte le soluzioni  Experience Cloud godono di un&#39;esperienza coerente con pattern comuni su come utilizzare e utilizzare le applicazioni. Con ogni versione,  Adobe ha perfezionato l&#39;interfaccia utente in base al feedback ricevuto dai clienti che lavoravano tra le varie soluzioni.

L’interfaccia utente originale per Adobe Experience Manager (precedentemente nota come CQ5), introdotta nel 2008 e utilizzata dai clienti con versioni 5.0-5.6.1, è presente nella AEM 6.4. Questo garantisce che i clienti possano effettuare l&#39;aggiornamento alla versione 6.4 e beneficiare di una piattaforma aggiornata con nuove funzionalità, continuando a utilizzare la stessa interfaccia utente.

 Adobe consiglia ai clienti di passare alla nuova interfaccia nel 2018/19. Questo può essere fatto durante l’aggiornamento alla versione 6.4 oppure in un progetto separato dopo l’aggiornamento, che includerà le modifiche necessarie alle finestre di dialogo delle personalizzazioni e dei componenti.

 Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia classica a partire da AEM 6.4. L’interfaccia classica rimane completamente supportata anche se è obsoleta.

## Regole e Recommendations {#rules-and-recommendations}

Di seguito è riportato un elenco di raccomandazioni di Product Management per Adobe Experience Manager 6.4:

<table> 
 <tbody> 
  <tr> 
   <th>Il mio progetto...</th> 
   <th>Consigli</th> 
  </tr> 
  <tr> 
   <td>Sto iniziando a usare Adobe Experience Manager.</td> 
   <td>Utilizzare l'interfaccia utente predefinita.</td> 
  </tr> 
  <tr> 
   <td><p>Ha usato AEM per un po'.</p> <p>Ha utilizzato l'interfaccia utente del prodotto e sviluppato componenti personalizzati per i siti.<br /> </p> </td> 
   <td> 
    <ol> 
     <li>Aggiornamento a 6.4</li> 
     <li>Usa l’interfaccia utente predefinita per l’amministrazione del sito, le risorse, ... etc.<br /> </li> 
     <li>Configura l’azione "Modifica pagina" per aprire l’editor classico delle pagine dell’interfaccia utente. See <a href="#selecting-your-ui">Selecting Your UI</a>.</li> 
    </ol> <p>Quindi, in una seconda fase:</p> 
    <ol> 
     <li>Aggiornate le finestre di dialogo dei componenti per utilizzare il formato di dialogo Coral 3.  Adobe consiglia di utilizzare <a href="/help/sites-developing/dialog-conversion.md">Dialog Conversion Tool</a> per aggiornare i componenti.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Ha creato un sito che utilizza il ClientContext con integrazioni.<br /> </td> 
   <td> 
    <ol> 
     <li>Aggiornamento a 6.4</li> 
     <li>Usa l’interfaccia utente predefinita per l’amministrazione del sito, le risorse, ... etc.</li> 
     <li>Configura l’azione "Modifica pagina" per aprire l’editor classico delle pagine dell’interfaccia utente. See <a href="#selecting-your-ui">Selecting Your UI</a>.</li> 
    </ol> <p>Quindi, in una seconda fase:</p> 
    <ol> 
     <li>Aggiornate le finestre di dialogo dei componenti per utilizzare il formato di dialogo Coral 3.  Adobe consiglia di utilizzare <a href="/help/sites-developing/dialog-conversion.md">Dialog Conversion Tool</a> per aggiornare i componenti.</li> 
     <li>Configurate ContextHub (la sostituzione del ClientContext) e aggiornate i modelli di pagina per utilizzare ContextHub. ContextHub dispone di una modalità di compatibilità che consente il caricamento di store di ClientContext personalizzati.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>Ha utilizzato CQ/AEM per molti anni.</p> <p>Ha esteso l'interfaccia utente del prodotto (ad esempio Amministratore sito) e integrato componenti con ampie finestre di dialogo per la modifica.</p> </td> 
   <td><p>Aggiornamento alla versione 6.4 e configurazione dell’interfaccia classica come impostazione predefinita per l’authoring delle pagine per tutti gli utenti. See <a href="#selecting-your-ui">Selecting Your UI</a>.</p> <p>Quindi avviate un progetto per applicare la personalizzazione e ottimizzare le finestre di dialogo dei componenti in formato Coral 3. Consulta <a href="#resources-to-help">Risorse per l’Aiuto</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

Per informazioni dettagliate, consultate l&#39;articolo Knowledge Base, [Touch UI Authoring FAQ](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html); incluse eventuali informazioni sulla pianificazione obsoleta dell’interfaccia classica.

## Selecting Your UI {#selecting-your-ui}

Consultate [Selezione dell’interfaccia](/help/sites-authoring/select-ui.md) utente per informazioni sulla configurazione del sistema in base alle esigenze.

## Stato interfaccia touch {#touch-optimized-ui-status}

Per informazioni dettagliate sui miglioramenti apportati all’interfaccia touch nella AEM 6.3, consultate [Novità](/help/release-notes/release-notes.md#what-s-new) nelle note sulla versione.

Panoramica completa Visualizza la pagina Stato [delle funzioni dell’interfaccia](/help/release-notes/touch-ui-features-status.md) touch

## Risorse per l&#39;Aiuto {#resources-to-help}

Per informazioni di base sulla gestione di base:

* [Utilizzo dell’ambiente](/help/sites-authoring/home.md)Authoring.
* [Authoring delle pagine](/help/sites-authoring/author-environment-tools.md).

Per informazioni dettagliate sullo sviluppo:

* [Architettura](/help/sites-developing/touch-ui-concepts.md)dell’interfaccia touch.
* Usate lo strumento [di conversione finestra di](/help/sites-developing/dialog-conversion.md) dialogo per convertire le finestre di dialogo di modifica dei componenti dall’interfaccia classica all’interfaccia touch.

* [Struttura dell’interfaccia](/help/sites-developing/touch-ui-structure.md)touch.

* [Personalizzazione delle console nell’interfaccia](/help/sites-developing/customizing-consoles-touch.md) touch (include codice di esempio).

* [Personalizzazione dell’authoring delle pagine nell’interfaccia](/help/sites-developing/customizing-page-authoring-touch.md) touch (include codice di esempio).

* [AEM Sessione Gem sulla personalizzazione](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html)ottimizzata per il tocco.
* [Documentazione](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html)sull’interfaccia utente Granite.

