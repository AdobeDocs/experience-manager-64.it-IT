---
title: Interfaccia utente Recommendations per clienti
seo-title: Interfaccia utente Recommendations per clienti
description: 'Un elenco di consigli relativi alle interfacce utente classica e ottimizzata per il tocco. '
seo-description: 'Un elenco di consigli relativi alle interfacce utente classica e ottimizzata per il tocco. '
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
translation-type: tm+mt
source-git-commit: 5b00783e4471a6b142ab17a7bc4a647ab04aec5f
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Interfaccia utente Recommendations per clienti{#user-interface-recommendations-for-customers}

Adobe Experience Manager 6.4 include due interfacce: l’interfaccia utente unificata di Experience Cloud e l’interfaccia classica.

Questo documento ha lo scopo di guidare i clienti nella scelta dell’interfaccia da utilizzare a seconda della loro situazione.

Termini di interesse:

* **Interfaccia utente (o interfaccia standard)**
Interfaccia utente moderna introdotta in 5.6.0 come anteprima di tecnologia ed estesa nelle versioni successive. Si basa sull’esperienza utente unificata di Adobe Experience Cloud, precedentemente nota come interfaccia touch o interfaccia touch.

* **Interfaccia classica**
UIUser basata sulla tecnologia ExtJS introdotta con CQ 5.1 nel 2008.

* **Site**
AdminCapabilities per gestire la gerarchia del sito (spostare, attivare, gestire i riferimenti) e creare nuove pagine.

* **Funzionalità di**
authoring delle pagine per aggiungere/modificare il contenuto di una pagina.

* **Funzionalità**
amministratore DAM/Assets per gestire le risorse digitali (immagini, video, documenti, download).

* ****
ContextHubCapabilities per aggregare informazioni sul visitatore e utilizzarlo per vari scopi. Fornisce un&#39;interfaccia utente per simulare le persone che visitano il sito. A partire AEM 6.2, ContextHub ha sostituito la tecnologia precedente, Client Context.

## Generale {#general}

Negli ultimi anni Adobe ha aggiornato tutte le soluzioni Adobe Experience Cloud con un&#39;interfaccia utente unificata. Gli utenti di tutte le soluzioni di Experience Cloud godono di un&#39;esperienza coerente con pattern comuni su come utilizzare e utilizzare le applicazioni. Ad ogni versione, Adobe ha perfezionato l’interfaccia utente in base ai feedback ricevuti dai clienti che lavorano tra le varie soluzioni.

L’interfaccia utente originale per Adobe Experience Manager (precedentemente nota come CQ5), introdotta nel 2008 e utilizzata dai clienti che eseguono le versioni 5.0-5.6.1, è presente nella AEM 6.4. Questo garantisce ai clienti la possibilità di eseguire l’aggiornamento alla versione 6.4 e di usufruire di una piattaforma aggiornata con nuove funzionalità, continuando a utilizzare la stessa interfaccia utente.

Adobe consiglia ai clienti di pianificare il passaggio alla nuova interfaccia utente nel 2018/19. Questo può essere fatto durante l&#39;aggiornamento alla versione 6.4 oppure in progetti separati dopo l&#39;aggiornamento, che includerebbero le necessarie modifiche alle personalizzazioni e alle finestre di dialogo dei componenti.

Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica a partire da AEM 6.4. L’interfaccia classica rimane completamente supportata anche se obsoleta.

## Regole e Recommendations {#rules-and-recommendations}

Di seguito è riportato un elenco di raccomandazioni di Product Management per Adobe Experience Manager 6.4:

<table> 
 <tbody> 
  <tr> 
   <th>Il mio progetto..</th> 
   <th>Consigli</th> 
  </tr> 
  <tr> 
   <td>Sta iniziando a usare Adobe Experience Manager.</td> 
   <td>Utilizza l’interfaccia utente predefinita.</td> 
  </tr> 
  <tr> 
   <td><p>Ha usato AEM per un po'.</p> <p>Ha utilizzato l'interfaccia utente del prodotto pronta all'uso e sviluppato componenti personalizzati per i siti.<br /> </p> </td> 
   <td> 
    <ol> 
     <li>Aggiornamento a 6.4</li> 
     <li>Utilizza l’interfaccia utente predefinita per l’amministrazione del sito, le risorse .. etc.<br /> </li> 
     <li>Configura l’azione "Modifica pagina" per aprire l’Editor pagina dell’interfaccia classica. Consulta <a href="#selecting-your-ui">Selezione dell'interfaccia utente</a>.</li> 
    </ol> <p>Poi, in una seconda fase:</p> 
    <ol> 
     <li>Aggiorna le finestre di dialogo dei componenti per utilizzare il formato di dialogo Coral 3. Adobe consiglia di utilizzare <a href="/help/sites-developing/modernization-tools.md">AEM Strumenti di modernizzazione</a> per aggiornare i componenti.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>Ha creato un sito che utilizza il ClientContext con le integrazioni.<br /> </td> 
   <td> 
    <ol> 
     <li>Aggiornamento a 6.4</li> 
     <li>Utilizza l’interfaccia utente predefinita per l’amministrazione del sito, le risorse .. etc.</li> 
     <li>Configura l’azione "Modifica pagina" per aprire l’Editor pagina dell’interfaccia classica. Consulta <a href="#selecting-your-ui">Selezione dell'interfaccia utente</a>.</li> 
    </ol> <p>Poi, in una seconda fase:</p> 
    <ol> 
     <li>Aggiorna le finestre di dialogo dei componenti per utilizzare il formato di dialogo Coral 3. Adobe consiglia di utilizzare <a href="/help/sites-developing/modernization-tools.md">AEM Strumenti di modernizzazione</a> per aggiornare i componenti.</li> 
     <li>Configura ContextHub (la sostituzione del ClientContext) e aggiorna i modelli di pagina per utilizzare ContextHub. ContextHub dispone di una modalità di compatibilità che consente di caricare archivi di ClientContext personalizzati.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>Ha usato CQ/AEM per molti anni.</p> <p>Ha esteso l’interfaccia utente del prodotto (ad esempio Amministratore sito) e generato componenti con finestre di dialogo di modifica estese.</p> </td> 
   <td><p>Aggiorna alla versione 6.4 e configura l’interfaccia classica come impostazione predefinita per l’authoring delle pagine per tutti gli utenti. Consulta <a href="#selecting-your-ui">Selezione dell'interfaccia utente</a>.</p> <p>Quindi avvia un progetto per applicare la personalizzazione e ottimizzare le finestre di dialogo dei componenti in formato Coral 3. Vedere <a href="#resources-to-help">Risorse per la Guida</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Domande frequenti {#faq}

Per ulteriori informazioni, consulta l’articolo della Knowledge Base [Domande frequenti sull’authoring dell’interfaccia utente touch](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html); incluse eventuali informazioni sulla pianificazione obsoleta dell’interfaccia classica.

## Selezione dell&#39;interfaccia utente {#selecting-your-ui}

Per informazioni sulla configurazione del sistema, consulta [Selezione dell&#39;interfaccia utente](/help/sites-authoring/select-ui.md) .

## Stato dell&#39;interfaccia touch {#touch-optimized-ui-status}

Per informazioni dettagliate sui miglioramenti apportati all’interfaccia touch nella AEM 6.3, consulta [Novità](/help/release-notes/release-notes.md#what-s-new) nelle note sulla versione.

Panoramica completa della pagina [Stato delle funzioni dell&#39;interfaccia touch](/help/release-notes/touch-ui-features-status.md)

## Risorse per la Guida {#resources-to-help}

Per informazioni generali sulla gestione di base:

* [Utilizzo dell’ambiente](/help/sites-authoring/home.md) Authoring.
* [Authoring delle pagine](/help/sites-authoring/author-environment-tools.md).

Per informazioni dettagliate sullo sviluppo:

* [Architettura dell’interfaccia touch](/help/sites-developing/touch-ui-concepts.md).
* Utilizza gli [AEM strumenti di modernizzazione](/help/sites-developing/modernization-tools.md) per convertire le finestre di dialogo Modifica dei componenti dall&#39;interfaccia classica all&#39;interfaccia touch.

* [Struttura dell’interfaccia](/help/sites-developing/touch-ui-structure.md) touch.

* [Personalizzazione delle console nell’interfaccia touch](/help/sites-developing/customizing-consoles-touch.md)  (con codice di esempio).

* [Personalizzazione dell’authoring delle pagine nell’interfaccia touch](/help/sites-developing/customizing-page-authoring-touch.md)  (con codice di esempio).

* [AEM sessione Gem sulla personalizzazione](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html) ottimizzata per il tocco.
* [Documentazione dell’interfaccia utente Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

