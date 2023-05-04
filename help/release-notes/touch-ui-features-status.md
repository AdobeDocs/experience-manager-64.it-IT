---
title: Stato delle funzioni dell’interfaccia touch
seo-title: Touch UI Feature Status
description: Note sulla versione specifiche dell’interfaccia utente touch di Adobe Experience Manager 6.3.
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 15%

---

# Stato delle funzioni dell’interfaccia touch {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Con la versione 6.4 di AEM, il [L’interfaccia classica è obsoleta](/help/release-notes/deprecated-removed-features.md). Adobe non prevede di apportare ulteriori miglioramenti all’interfaccia utente classica e gli utenti sono invitati a sfruttare le nuove potenti funzioni disponibili nell’interfaccia touch.

A partire dalla versione 6.0, AEM introdotto una nuova interfaccia utente denominata &quot;interfaccia touch&quot; (detta anche semplicemente &quot;interfaccia touch&quot;) allineata a Adobe Marketing Cloud e alle linee guida generali dell’interfaccia utente di Adobe. Una volta raggiunta una certa parzialità nelle funzioni, questa è diventata l’interfaccia standard in AEM con l’interfaccia legacy, orientata al desktop, denominata &quot;interfaccia classica&quot;.

La maggior parte delle funzionalità è presente nell’interfaccia touch, ma alcune non sono ancora complete e verranno aggiunte nelle versioni future.

L’elenco seguente mostra lo stato attuale delle funzionalità implementate in AEM 6.4.

Per consigli per i clienti che eseguono l’aggiornamento a AEM 6.4, consulta [Interfaccia utente Recommendations per clienti](/help/sites-deploying/ui-recommendations.md) per i dettagli.

>[!NOTE]
>
>Tieni presente che questa pagina tratta solo la parità delle funzioni con l’interfaccia classica.
>
>Le funzionalità aggiunte e uniche all’interfaccia touch che non sono presenti nell’interfaccia classica non sono elencate.

>[!NOTE]
>
>Questo elenco si prefigge di essere completo, ma non deve essere considerato esaustivo.

## Legenda {#legend}

* **Completa**: La funzione è completamente disponibile nell’interfaccia touch
* **Principalmente**: La funzione è disponibile principalmente nell’interfaccia touch.
* **Mancante**: La funzione non è presente nell’interfaccia touch, ma è necessario utilizzare l’interfaccia classica per eseguire questa azione.
* **Sostituito**: La funzione è stata sostituita da una nuova implementazione che funziona in modo diverso.
* **Rimosso**: La funzione non esiste più nell’interfaccia touch e non verrà sostituita.

## Stato della funzione: Amministratore di Sites {#feature-status-sites-admin}

Elenco delle funzionalità per l’amministrazione dei siti nell’interfaccia classica ( `/siteadmin`) e lo stato nell’interfaccia touch ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta<br /> </strong></td> 
   <td><strong>Stato<br /> </strong></td> 
   <td><strong>Commenti</strong></td> 
  </tr>
  <tr>
   <td>Spostarsi nella gerarchia del sito</td> 
   <td>Completa<br /> </td> 
   <td>AEM 6.4 introduce <a href="/help/sites-authoring/basic-handling.md#content-tree">visualizzazione struttura contenuto</a>.</td> 
  </tr>
  <tr>
   <td>Avvia flusso di lavoro</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crea nuova pagina</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crea nuovo sito</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crea nuovo lancio</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Creare una nuova Live Copy <br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Crea cartella</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Mostra stato di pubblicazione</td> 
   <td>Principalmente</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ricerca</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copia/Incolla pagina (duplicato)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Sposta pagina/e</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pubblicare le pagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pubblicare pagine senza diritti di replica</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pubblica più tardi</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pubblica albero</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annullare la pubblicazione di pagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annullare la pubblicazione di pagine senza diritti di replica</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulla pubblicazione più tardi</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Eliminare</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blocca/Sblocca</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Visualizza/Modifica proprietà</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Impostare le autorizzazioni sulle pagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cronologia delle versioni</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ripristina versione</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Ripristinare la struttura ad albero e ripristinare le pagine eliminate</td> 
   <td>Mancante</td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Mostra differenza tra versione precedente e versione corrente<br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Azioni Livecopy (rollout)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Vedere copie per lingua</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trova e sostituisci</td> 
   <td>Mancante<br /> </td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Casella in entrata notifica (eventi JCR)</td> 
   <td>Mancante</td> 
   <td>Utilizzare l’interfaccia classica. Verrà sostituito con un’implementazione diversa.</td> 
  </tr>
  <tr>
   <td>Riferimenti</td> 
   <td>Principalmente</td> 
   <td>La visualizzazione dei collegamenti alle pagine in arrivo verrà aggiunta nella versione 2019 di AEM.</td> 
  </tr>
 </tbody>
</table>

## Stato della funzione: Editor pagina {#feature-status-page-editor}

Elenco delle funzionalità dell’interfaccia classica Editor pagina ( `/cf#`) e lo stato in touch-enabled ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta</strong></td> 
   <td><strong>Stato</strong></td> 
   <td><strong>Commenti</strong></td> 
  </tr>
  <tr>
   <td>Modifica pagine Web</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica pagine web mobili<br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modificare i contenuti importati tramite Importazione progettazione<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica e-mail</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modificare le app per dispositivi mobili</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica Forms</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica offerte</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica modelli di flussi di lavoro<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Codice: Modifica e anteprima</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Anteprima reattiva<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modalità: Modifica progettazione</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modalità: Scaffolding</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modalità: Stato Live Copy<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Aggiungi annotazioni</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica delle proprietà<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pagina di rollout</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Avvia e mostra flusso di lavoro</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Gestione dei pacchetti del flusso di lavoro</td> 
   <td>Principalmente</td> 
   <td>Completamente accessibile nell’interfaccia touch. Payload per flussi di lavoro multipli viene comunque presentato nell’interfaccia classica.<br /> </td> 
  </tr>
  <tr>
   <td>Blocca/Sblocca pagina</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pubblica pagina <br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulla pubblicazione pagina</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copia pagina</td> 
   <td>Rimosso<br /> </td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiare le pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Sposta pagina</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">spostare le pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Elimina pagina</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">eliminare le pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostra riferimenti</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/author-environment-tools.md#references">vedere l'elenco di riferimento dettagliato</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Registro di controllo</td> 
   <td>Rimosso</td> 
   <td>Utilizza Site Admin e <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">barra delle attività aperta</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Crea versione</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">creare nuove versioni</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Ripristina versione</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">ripristina versioni</a>.</td> 
  </tr>
  <tr>
   <td>Avvii switch</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-authoring/launches-promoting.md">passare da un avvio all'altro</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Traduci pagina</td> 
   <td>Rimosso</td> 
   <td>Usa amministratore del sito per <a href="/help/sites-administering/tc-manage.md">aggiungi pagina ai progetti di traduzione</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (scegli data/ora e sfoglia il sito così come ha guardato)<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Impostare le autorizzazioni</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaccia utente Client Context<br /> </td> 
   <td>Sostituito</td> 
   <td>Utilizza la <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> L’interfaccia utente continua.</td> 
  </tr>
  <tr>
   <td>Content Finder per i vari tipi di contenuti multimediali<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Elenco dei componenti</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiare e incollare i componenti<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Elenco dei componenti negli Appunti</td> 
   <td>Mancante</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulla/Ripeti</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trascina e rilascia il contenuto nel segnaposto del componente</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trascina e rilascia i contenuti direttamente nel segnaposto parsys con la creazione automatica dei componenti<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Stato della funzione: Editor di testo, tabelle e immagini {#feature-status-text-table-and-image-editors}

Elenco delle funzionalità disponibili nell’interfaccia classica per l’editor di testo, tabelle e immagini e dello stato nell’interfaccia touch.

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta</strong></td> 
   <td><strong>Stato </strong></td> 
   <td><strong>Commenti<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor Rich Text</td> 
   <td>Completa</td> 
   <td>Utilizzabile in-place, nella finestra di dialogo e a schermo intero.</td> 
  </tr>
  <tr>
   <td>Abilitare/disabilitare i plug-in RTE</td> 
   <td>Completa<br /> </td> 
   <td>Può essere eseguito utilizzando <a href="/help/sites-authoring/templates.md">Editor modelli</a>.</td> 
  </tr>
  <tr>
   <td>Usa editor Rich Text per testo normale</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Collegamenti e ancoraggio</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Mappa dei caratteri</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Copia/Incolla</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Incolla da Microsoft Word<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Trova e sostituisci</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Formati di testo (grassetto, ...)</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Sottoscritto</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Giustifica</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Elenchi (puntini/numeri)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Formato paragrafo</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Stili testo</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Editor origine (Modifica HTML)<br /> </td> 
   <td>Completa<br /> </td> 
   <td>Disponibile solo nella finestra di dialogo e a schermo intero.<br /> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Controllo ortografia</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Tabella (Editor tabella incorporato)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Annulla/Ripristina<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Consenti immagini in linea</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Editor tabella</td> 
   <td>Completa</td> 
   <td>Utilizzabile in-place, nella finestra di dialogo e a schermo intero.<br /> </td> 
  </tr>
  <tr>
   <td>Trascina l’immagine nella cella della tabella<br /> </td> 
   <td>Completa</td> 
   <td>Utilizzabile in linea</td> 
  </tr>
  <tr>
   <td>Editor immagine<br /> </td> 
   <td>Completa</td> 
   <td>Utilizzabile in-place, nella finestra di dialogo e a schermo intero.<br /> </td> 
  </tr>
  <tr>
   <td>Abilitare/disabilitare i plug-in IPE</td> 
   <td>Completa</td> 
   <td>È ora disponibile un’interfaccia utente nel <a href="/help/sites-authoring/templates.md">Editor modelli</a>.</td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Ritaglio</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Capovolgimento</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Annulla/Ripristina</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Mappa immagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Ruota</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in IPE: Zoom</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Stato della funzione: Strumenti {#feature-status-tools}

Elenco dei vari strumenti disponibili nell’interfaccia classica e dello stato nell’interfaccia touch.

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta<br /> </strong></td> 
   <td><strong>Stato<br /> </strong></td> 
   <td><strong>Commenti</strong></td> 
  </tr>
  <tr>
   <td>Gestione attività</td> 
   <td>Sostituito</td> 
   <td>6.0 introdotto <a href="/help/sites-authoring/projects.md">Progetti e attività</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Casella in entrata flusso di lavoro<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configurazione del modello da flusso di lavoro a pagina (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Mancante<br /> </td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Assegnazione di tag all’interfaccia utente amministratore<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Centro di controllo MSM/Blueprint</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaccia utente di Blueprint Manager</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaccia utente di configurazione del rollout</td> 
   <td>Mancante</td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Interfaccia utente utente, gruppi e autorizzazioni<br /> </td> 
   <td>Più completo<br /> </td> 
   <td>Per la modifica avanzata delle autorizzazioni, utilizza l’interfaccia classica.<br /> </td> 
  </tr>
  <tr>
   <td>Elimina versioni (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Mancante</td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Verifica collegamenti esterni (<code>/etc/linkchecker.html</code>)</td> 
   <td>Mancante</td> 
   <td>Utilizzare l’interfaccia classica.<br /> </td> 
  </tr>
  <tr>
   <td>Modifiche in serie (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Mancante<br /> </td> 
   <td>Utilizzare l’interfaccia classica.</td> 
  </tr>
 </tbody>
</table>
