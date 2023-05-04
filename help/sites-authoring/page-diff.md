---
title: Differenze tra pagine
seo-title: Page Diff
description: È possibile confrontare in modalità affiancata i contenuti di due pagine, evidenziandone le differenze rilevate.
seo-description: The page diff feature allows for the convenient side-by-side comparison of two pages with their differences highlighted.
uuid: cf029ed8-606e-4f12-ac8e-5ea9ebd70b1b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a771d8c-cc56-4979-aeab-b508755a2078
exl-id: 1b1fa592-a145-4abe-a455-df24d551b937
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 46%

---

# Differenze tra pagine {#page-diff}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La creazione dei contenuti è un processo iterativo. Per un authoring efficace, è necessario essere in grado di vedere cosa è cambiato da un’iterazione all’altro. La visualizzazione di una versione della pagina e dell’altra è inefficiente e soggetta a errori. L’autore desidera poter confrontare facilmente la pagina corrente affiancata a un’altra sua versione.

È possibile confrontare in modalità affiancata i contenuti di due pagine, evidenziandone le differenze rilevate.

>[!CAUTION]
>
>Se esegui una versione precedente alla versione 6.4.3 di AEM, l’utente deve disporre del **Modifica/Crea/Elimina** autorizzazione sul nodo `/content/versionhistory` per utilizzare la funzione .
>
>Per ulteriori informazioni tecniche su questa funzione, consulta [Sviluppo e differenze tra pagine](/help/sites-developing/pagediff.md#operation-details).

## Utilizzare {#use}

La visualizzazione affiancata delle differenze permette di confrontare:

* [Versioni](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - Versione precedente di una pagina con il relativo stato corrente
* [live Copy](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live Copy con la relativa blueprint
* [Lanci](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - Lancio con la rispettiva sorgente
* [Copie per lingua](/help/sites-administering/tc-manage.md#comparing-language-copies) - Una pagina prima e dopo la traduzione o la ritraduzione

Vedi i rispettivi argomenti su come avviare il confronto in tali contesti.

### Presentazione delle differenze   {#presentation-of-differences}

Indipendentemente dal contenuto confrontato, la presentazione del confronto rimane la stessa.

* Il contenuto selezionato all’avvio del confronto viene visualizzato a sinistra (il punto di ingresso del confronto).
* Il contenuto confrontato viene visualizzato a destra (rispetto al contenuto selezionato).

Ad esempio, se si confrontano le versioni, la versione corrente viene visualizzata a sinistra e la versione precedente a destra.

L’origine di entrambe le pagine viene visualizzata chiaramente nella barra dell’intestazione nella parte superiore della finestra del browser.

![chlimage_1-355](assets/chlimage_1-355.png)

Le differenze rilevano le modifiche a livello di componente e di HTML. Gli elementi modificati vengono evidenziati con colori diversi.

**Modifiche al componente**

* Verde chiaro - Componente aggiunto
* Rosa - Componente rimosso
* Blu - Componente modificato
* Blu - Componente spostato

I colori modificati e spostati sono gli stessi.

**Modifiche di HTML**

* Verde scuro - HTML aggiunto
* Rosso - HTML rimosso

>[!NOTE]
>
>Quando si confrontano le copie in lingua, l&#39;evidenziazione viene disattivata in quanto in una traduzione tutto cambia e l&#39;evidenziazione non avrebbe alcun vantaggio.

### Modalità a schermo intero e Uscita   {#fullscreen-and-exiting}

Per concentrarti su un contenuto particolare, fai clic sull’icona schermo intero di entrambi i “lati” a confronto, per ingrandire il contenuto nella finestra del browser a schermo intero.

![](do-not-localize/chlimage_1-24.png)

Il lato selezionato occupa l’intera finestra, ma nella parte superiore rimane visualizzata la barra che consente di alternare tra le due pagine.

![chlimage_1-356](assets/chlimage_1-356.png)

Per chiudere la visualizzazione a schermo intero, fai clic sull’icona per uscire dalla modalità a tutto schermo.

![](do-not-localize/chlimage_1-25.png)

Puoi uscire dalla modalità di confronto affiancato delle differenze in qualsiasi momento facendo clic sul pulsante Chiudi, nell’intestazione.

## Limiti   {#limitations}

In alcune situazioni le differenze tra pagine potrebbero non rilevare una differenza come previsto.

* Quando si diffondono versioni e lanci, il confronto non tiene conto di componenti dinamici quali breadcrumb, menu, elenchi di prodotti o loghi (componenti che si basano sulla struttura del sito per eseguire il rendering del contenuto).
* Per le versioni la differenza non ricrea i criteri di controllo accessi e le relazioni Live Copy.
* Le eventuali modifiche apportate a un’immagine, ad esempio agli attributi alt, title o src, vengono evidenziate in blu. Tuttavia, in alcuni casi le immagini hanno una rappresentazione Base64 dell’attributo src e, nonostante siano uguali, vengono contrassegnate come diverse a causa dei differenti attributi src.
* Il confronto non è in grado di rilevare la rotazione di un’immagine.
* Se una pagina viene spostata, non sarà più possibile eseguire una differenza con le versioni eseguite prima dello spostamento.

   * Se riscontri problemi con una differenza, controlla la [Timeline](/help/sites-authoring/basic-handling.md#timeline) per verificare se la pagina è stata spostata.

>[!NOTE]
>
>Le versioni non possono essere confrontate tra di loro. Solo la versione corrente può essere confrontata con altre versioni della pagina. La versione corrente è sempre la versione con le modifiche evidenziate.

>[!NOTE]
>
>Per ulteriori dettagli sul funzionamento del meccanismo di differenze tra pagine e sui limiti che possono influenzare tale meccanismo, consulta la sezione [documentazione per gli sviluppatori](/help/sites-developing/pagediff.md) di questa funzione.
