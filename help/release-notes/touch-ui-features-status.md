---
title: Stato delle funzioni dell’interfaccia touch
seo-title: Stato delle funzioni dell’interfaccia touch
description: Note sulla versione specifiche dell’interfaccia utente touch di Adobe Experience Manager 6.3.
seo-description: Note sulla versione specifiche dell’interfaccia utente touch di Adobe Experience Manager 6.3.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 14%

---


# Stato delle funzioni dell&#39;interfaccia touch{#touch-ui-feature-status}

>[!CAUTION]
>
>Con la versione 6.4 di AEM, l&#39; [interfaccia classica è obsoleta](/help/release-notes/deprecated-removed-features.md).  Adobe non intende apportare ulteriori miglioramenti all’interfaccia classica e gli utenti sono invitati a utilizzare le nuove potenti funzioni disponibili nell’interfaccia touch.

A partire dalla versione 6.0, AEM introdotto una nuova interfaccia utente denominata &quot;interfaccia touch&quot; (detta anche &quot;interfaccia touch&quot;), allineata all’Adobe Marketing Cloud e alle linee guida generali dell’interfaccia Adobe . Una volta raggiunta la parità di funzionalità, questa è diventata l&#39;interfaccia standard in AEM con l&#39;interfaccia precedente, orientata al desktop, detta &quot;interfaccia classica&quot;.

Anche se la maggior parte delle funzionalità sono presenti nell’interfaccia touch, alcune funzioni non sono ancora complete e verranno aggiunte nelle release future.

L&#39;elenco seguente mostra lo stato corrente delle funzionalità come implementato in AEM 6.4.

Per le raccomandazioni per i clienti che eseguono l&#39;aggiornamento alla AEM 6.4, vedere [Recommendations interfaccia utente per i clienti](/help/sites-deploying/ui-recommendations.md) per i dettagli.

>[!NOTE]
>
>In questa pagina vengono elencate solo le funzionalità dell’interfaccia classica.
>
>Non sono elencate le funzionalità aggiunte e univoche nell’interfaccia touch che non sono presenti nell’interfaccia classica.

>[!NOTE]
>
>L&#39;elenco si prefigge di essere completo, ma non deve essere considerato esaustivo.

## Legenda {#legend}

* **Completa**: La funzione è completamente disponibile nell’interfaccia touch
* **Principalmente**: Questa funzione è disponibile per la maggior parte nell’interfaccia touch.
* **Mancanti**: La funzione non è disponibile nell’interfaccia touch, ma deve essere utilizzata anche l’interfaccia classica.
* **Sostituito**: La funzione è stata sostituita da una nuova implementazione che funziona in modo diverso.
* **Rimosso**: La funzione non esiste più nell’interfaccia touch e non verrà sostituita.

## Stato funzione: Amministratore siti {#feature-status-sites-admin}

Si tratta di un elenco delle funzionalità di cui dispone l&#39;amministratore del sito dell&#39;interfaccia classica ( `/siteadmin`) e dello stato nell&#39;interfaccia touch ( `/sites.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta<br /> </strong></td> 
   <td><strong>Stato<br /> </strong></td> 
   <td><strong>Commento</strong></td> 
  </tr>
  <tr>
   <td>Naviga gerarchia sito</td> 
   <td>Completa<br /> </td> 
   <td>AEM 6.4 ha introdotto una <a href="/help/sites-authoring/basic-handling.md#content-tree">visualizzazione struttura del contenuto</a>.</td> 
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
   <td>Mostra stato pubblicazione</td> 
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
   <td>Sposta pagine</td> 
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
   <td>Annullamento della pubblicazione delle pagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annullamento della pubblicazione delle pagine senza diritti di replica</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulla pubblicazione più tardi</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Elimina</td> 
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
   <td>Impostazione delle autorizzazioni sulle pagine</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Cronologia versioni</td> 
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
   <td>Usa interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Mostra differenza tra versione precedente e versione corrente<br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Azioni Live Copy (Roll-out)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Vedere copie della lingua</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trova e sostituisci</td> 
   <td>Missing<br /> </td> 
   <td>Usa interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Inbox notifica (eventi JCR)</td> 
   <td>Mancante</td> 
   <td>Usa interfaccia classica. Sarà sostituito con un'implementazione diversa.</td> 
  </tr>
  <tr>
   <td>Riferimenti</td> 
   <td>Principalmente</td> 
   <td>La visualizzazione dei collegamenti alle pagine in arrivo verrà aggiunta nella release 2019 di AEM.</td> 
  </tr>
 </tbody>
</table>

## Stato funzione: Editor pagina {#feature-status-page-editor}

Si tratta di un elenco delle funzionalità dell&#39;editor pagina dell&#39;interfaccia classica ( `/cf#`) e dello stato nell&#39;editor touch ( `/editor.html`).

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta</strong></td> 
   <td><strong>Stato</strong></td> 
   <td><strong>Commento</strong></td> 
  </tr>
  <tr>
   <td>Modifica pagine Web</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica pagine Web per dispositivi mobili<br /> </td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modificare il contenuto importato tramite Importazione progettazione<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica e-mail</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Modifica di app mobili</td> 
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
   <td>Modifica modelli flussi di lavoro<br /> </td> 
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
   <td>Aggiunta di annotazioni</td> 
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
   <td>Gestione del pacchetto di workflow</td> 
   <td>Principalmente</td> 
   <td>Completamente accessibile nell’interfaccia touch. Payload di flussi di lavoro multipli ancora presentati nell'interfaccia classica.<br /> </td> 
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
   <td>Utilizzare Amministrazione sito per <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">copiare le pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Sposta pagina</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Amministrazione sito per <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">spostare le pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Elimina pagina</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Amministrazione sito per <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">eliminare pagine</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Mostra riferimenti</td> 
   <td>Rimosso</td> 
   <td>Utilizzate Amministrazione sito per <a href="/help/sites-authoring/author-environment-tools.md#references">visualizzare l'elenco di riferimento dettagliato</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Registro di controllo</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Amministrazione sito e <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">barra delle attività aperta</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Crea versione</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Amministrazione sito per <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">creare nuove versioni</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Ripristina versione</td> 
   <td>Rimosso</td> 
   <td>Utilizzate Site Admin per <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">ripristinare le versioni</a>.</td> 
  </tr>
  <tr>
   <td>Interrompi avvii</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Amministrazione sito per passare da un avvio all'altro</a>.<br /><a href="/help/sites-authoring/launches-promoting.md"> </a></td> 
  </tr>
  <tr>
   <td>Traduci pagina</td> 
   <td>Rimosso</td> 
   <td>Utilizzare Site Admin per <a href="/help/sites-administering/tc-manage.md">aggiungere pagina ai progetti di traduzione</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Timewarp (scegliere data/ora e navigare nel sito come cercava)<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Imposta autorizzazioni</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Interfaccia utente ClientContext<br /> </td> 
   <td>Sostituito</td> 
   <td>Utilizzare l'interfaccia utente <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> in futuro.</td> 
  </tr>
  <tr>
   <td>Content Finder per i vari tipi di supporti<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Elenco componenti</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Copiare e incollare componenti<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Elenco di componenti negli Appunti</td> 
   <td>Mancante</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Annulla/Ripristina</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trascinamento del contenuto nel segnaposto del componente</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Trascinamento dei contenuti direttamente nel segnaposto parsys con creazione automatica dei componenti<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Stato funzione: Editor di testo, tabelle ed immagini {#feature-status-text-table-and-image-editors}

Si tratta di un elenco delle funzionalità dell’interfaccia classica Testo, Tabella e Editor immagine e dello stato nell’interfaccia touch.

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta</strong></td> 
   <td><strong>Stato </strong></td> 
   <td><strong>Commento<br /> </strong></td> 
  </tr>
  <tr>
   <td>Editor Rich Text</td> 
   <td>Completa</td> 
   <td>Utilizzabile in posizione, nella finestra di dialogo e a schermo intero.</td> 
  </tr>
  <tr>
   <td>Abilitare/disabilitare i plug-in RTE</td> 
   <td>Completa<br /> </td> 
   <td>Può essere eseguito utilizzando l' <a href="/help/sites-authoring/templates.md">Editor modelli</a>.</td> 
  </tr>
  <tr>
   <td>Usa editor Rich Text per testo semplice</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Collegamenti e ancoraggio</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Mappa carattere</td> 
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
   <td>Plug-in RTE: Sottoscrittura</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Giustifica</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Elenchi (elenchi puntati/numeri)</td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Formato paragrafo</td> 
   <td>Completa<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Plug-in RTE: Stili di testo</td> 
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
   <td>Utilizzabile in posizione, nella finestra di dialogo e a schermo intero.<br /> </td> 
  </tr>
  <tr>
   <td>Trascina immagine nella cella della tabella<br /> </td> 
   <td>Completa</td> 
   <td>Utilizzabile in linea</td> 
  </tr>
  <tr>
   <td>Editor immagine<br /> </td> 
   <td>Completa</td> 
   <td>Utilizzabile in posizione, nella finestra di dialogo e a schermo intero.<br /> </td> 
  </tr>
  <tr>
   <td>Abilitare/disabilitare i plug-in IPE</td> 
   <td>Completa</td> 
   <td>Ora è disponibile un'interfaccia utente in <a href="/help/sites-authoring/templates.md">Editor modelli</a>.</td> 
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

## Stato funzione: Strumenti {#feature-status-tools}

Si tratta di un elenco di diversi strumenti disponibili nell’interfaccia classica e dello stato nell’interfaccia touch.

<table> 
 <tbody>
  <tr>
   <td><strong>Funzione obsoleta<br /> </strong></td> 
   <td><strong>Stato<br /> </strong></td> 
   <td><strong>Commento</strong></td> 
  </tr>
  <tr>
   <td>Gestione attività</td> 
   <td>Sostituito</td> 
   <td>6.0 introdotto <a href="/help/sites-authoring/projects.md">Progetti e attività</a>.<br /> </td> 
  </tr>
  <tr>
   <td>Inbox workflow<br /> </td> 
   <td>Completa</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Configurazione del flusso di lavoro per il modello di pagina (<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>Missing<br /> </td> 
   <td>Usa interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Assegnazione di tag all'interfaccia utente amministratore<br /> </td> 
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
   <td>Usa interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Interfaccia utente, gruppi e autorizzazioni<br /> </td> 
   <td>Principalmente completo<br /> </td> 
   <td>Per la modifica avanzata delle autorizzazioni, utilizzate l'interfaccia classica.<br /> </td> 
  </tr>
  <tr>
   <td>Rimuovi versioni (<code>/etc/versioning/purge.html</code>)</td> 
   <td>Mancante</td> 
   <td>Usa interfaccia classica.</td> 
  </tr>
  <tr>
   <td>Verifica collegamenti esterni (<code>/etc/linkchecker.html</code>)</td> 
   <td>Mancante</td> 
   <td>Usa interfaccia classica.<br /> </td> 
  </tr>
  <tr>
   <td>Editor di massa (<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>Missing<br /> </td> 
   <td>Usa interfaccia classica.</td> 
  </tr>
 </tbody>
</table>

