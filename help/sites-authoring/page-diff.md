---
title: Differenze tra pagine
seo-title: Differenze tra pagine
description: È possibile confrontare in modalità affiacanta i contenuti di due pagine, evidenziandone le differenze rilevate.
seo-description: È possibile confrontare in modalità affiacanta i contenuti di due pagine, evidenziandone le differenze rilevate.
uuid: cf029ed8-606e-4f12-ac8e-5ea9ebd70b1b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 5a771d8c-cc56-4979-aeab-b508755a2078
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Differenze tra pagine{#page-diff}

## Introduzione {#introduction}

La creazione di contenuti è un processo iterativo. Per un authoring efficace, è necessario essere in grado di vedere cosa è cambiato da un&#39;iterazione all’altro. La visualizzazione separata di due versioni di una pagina è inefficiente e soggetta a errori. L&#39;autore desidera poter confrontare facilmente la pagina corrente affiancata a un’altra sua versione.

È possibile confrontare in modalità affiacanta i contenuti di due pagine, evidenziandone le differenze rilevate.

>[!CAUTION]
>
>The user must have the **Modify/Create/Delete** permission on the node `/content/versionhistory` in order to use the feature.
>
>Per ulteriori informazioni tecniche su questa funzione, consulta [Sviluppo e differenze tra pagine](/help/sites-developing/pagediff.md#operation-details).

## Utilizzo {#use}

La visualizzazione affiancata delle differenze permette di confrontare:

* [Versioni](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - Versione precedente di una pagina con il relativo stato corrente
* [Live Copy](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live Copy con la sua Blueprint
* [Lanci](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - Lancio con la sua origine
* [Copie](/help/sites-administering/tc-manage.md#comparing-language-copies) lingua - Una pagina prima e dopo la (ri)traduzione

Consulta i rispettivi argomenti su come avviare la funzione per il rilevamento delle differenze in questi contesti.

### Presentazione delle differenze {#presentation-of-differences}

A prescindere dal contenuto, la presentazione delle differenze rimane la stessa.

* Il contenuto selezionato viene visualizzato a sinistra (punto di ingresso per il rilevamento delle differenze).
* Il contenuto con cui viene confrontato è visualizzato a destra.

Ad esempio, se si confrontano due versioni, la versione corrente è a sinistra e quella precedente a destra.

L’origine di entrambe le pagine è indicata chiaramente nella barra dell’intestazione, nella parte superiore della finestra del browser.

![chlimage_1-355](assets/chlimage_1-355.png)

Vengono rilevate le modifiche apportate a livello di componente e di codice HTML. Gli elementi che sono stati modificati sono evidenziati con colori diversi.

**Modifica componenti**

* Verde chiaro - Componente aggiunto
* Rosa - Componente rimosso
* Blu - Componente modificato
* Blu - Componente spostato

Nota: il colore dei componenti modificati e spostati è lo stesso.

**Modifiche HTML**

* Verde scuro - HTML aggiunto
* Rosso - HTML rimosso

>[!NOTE]
>
>Quando si confrontano le copie per lingua, l’evidenziazione è disattivata poiché in una traduzione tutto cambia.

### Modalità a schermo intero e Uscita {#fullscreen-and-exiting}

Per concentrarti su un contenuto particolare, fai clic sull&#39;icona schermo intero di entrambi i “lati” a confronto, per ingrandire il contenuto nella finestra del browser a schermo intero.

![](do-not-localize/chlimage_1-24.png)

Il lato selezionato riempie l’intera finestra, ma la barra rimane nella parte superiore consentendo di passare da una pagina all’altra.

![chlimage_1-356](assets/chlimage_1-356.png)

Per chiudere la visualizzazione a schermo intero, fai clic sull’icona per uscire dalla modalità a schermo intero.

![](do-not-localize/chlimage_1-25.png)

Puoi uscire dalla modalità di confronto affiancato delle differenze in qualsiasi momento facendo clic sul pulsante Chiudi, nell&#39;intestazione.

## Limiti {#limitations}

Esistono alcune situazioni in cui il confronto delle differenze della pagina non è in grado di rilevare una differenza nel modo previsto.

* Nel confronto di versioni e lanci, la funzione non prende in considerazione le differenze dinamiche, come i componenti breadcrumb, i menu, gli elenchi di prodotti o i loghi (componenti che si basano sulla struttura del sito per eseguire il rendering del contenuto).
* Per le versioni, non viene ricreato il criterio per il controllo degli accessi e le relazioni Live Copy.
* Se vengono apportate modifiche a un’immagine, ad esempio la modifica degli attributi alt, title o src, quest’ultima verrà evidenziata in blu come modificata. In alcuni casi, tuttavia, l&#39;immagine ha una rappresentazione Base64 dell&#39;attributo src e anche se entrambe le immagini hanno lo stesso aspetto, saranno contrassegnate dalla diff come diverse a causa dei diversi attributi src.
* Il confronto non è in grado di rilevare la rotazione di un’immagine.
* Se una pagina viene spostata, non ti sarà più possibile eseguire una rilevazione delle differenze con qualsiasi versione creata prima dello spostamento.

   * Se rilevi dei problemi con una differenza, controlla la [Timeline](/help/sites-authoring/basic-handling.md#timeline) per verificare se la pagina è stata spostata.

>[!NOTE]
>
>Le versioni non possono essere confrontate tra di loro. È possibile confrontare solo la versione corrente con altre versioni della pagina. La versione corrente è sempre la versione con le modifiche evidenziate.

>[!NOTE]
>
>Per ulteriori informazioni sull’operazione del meccanismo di differenze tra pagine e sui limiti che possono influenzare tale meccanismo, consulta la [documentazione per gli sviluppatori](/help/sites-developing/pagediff.md) per questa funzione.

