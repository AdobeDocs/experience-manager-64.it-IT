---
title: Configurazione della segmentazione
seo-title: Configuring Segmentation
description: Scopri come configurare la segmentazione per AEM Campaign.
seo-description: Learn how to configure segmentation for AEM Campaign.
uuid: f22e41b6-d9d9-4f18-9925-2d4aebc167b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 49c9c9ab-632a-40f7-8c30-d6a8c0f1b420
exl-id: 92302067-3500-41ca-9855-87f36148bfbc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 15%

---

# Configurazione della segmentazione{#configuring-segmentation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Questo documento descrive la configurazione della segmentazione come utilizzata con ClientContext. Per configurare i segmenti con ContextHub utilizzando l’interfaccia utente touch, vedi [Configurazione della segmentazione con ContextHub](/help/sites-administering/segmentation.md).

La segmentazione è un concetto chiave per la creazione di una campagna. Vedi [Glossario di segmentazione](/help/sites-authoring/segmentation-overview.md) per informazioni sul funzionamento della segmentazione e sui termini chiave.

A seconda delle informazioni che hai già raccolto sui visitatori del tuo sito e degli obiettivi che desideri raggiungere, dovrai definire i segmenti e le strategie necessarie per i contenuti di destinazione.

Questi segmenti verranno poi utilizzati per fornire al visitatore i contenuti di destinazione più pertinenti. Questo contenuto viene mantenuto nel [Campagne](/help/sites-authoring/personalization.md) sezione del sito web. Le pagine teaser qui definite possono essere incluse come paragrafi teaser in qualsiasi pagina e definire per quale segmento di visitatori si applica il contenuto specializzato.

AEM consente di creare e aggiornare facilmente segmenti, teaser e campagne. Consente inoltre di verificare i risultati delle definizioni.

La **Editor segmenti** consente di definire facilmente un segmento:

![segmenteditor-1](assets/segmenteditor-1.png)

È possibile **Modifica** ogni segmento deve specificare un **Titolo**, **Descrizione** e **Incremento** fattore. Utilizzando la barra laterale è possibile aggiungere **E** e **O** contenitori per definire **Logica del segmento**, quindi aggiungi il **Caratteristiche del segmento** per definire i criteri di selezione.

## Fattore di incremento {#boost-factor}

Ogni segmento ha una **Incremento** parametro utilizzato come fattore di ponderazione; un numero maggiore indica che il segmento verrà selezionato preferibilmente a un segmento con un numero inferiore.

* Valore minimo: `0`
* Valore massimo: `1000000`

## Logica del segmento {#segment-logic}

I seguenti contenitori di logica sono disponibili out-of-the-box e consentono di creare la logica della selezione dei segmenti. Puoi trascinarli dalla barra laterale all’editor:

<table> 
 <tbody> 
  <tr> 
   <td> Contenitore E<br /> </td> 
   <td> Operatore AND boolean.<br /> </td> 
  </tr> 
  <tr> 
   <td> Contenitore O<br /> </td> 
   <td> Operatore OR boolean.</td> 
  </tr> 
 </tbody> 
</table>

## Caratteristiche del segmento {#segment-traits}

Sono disponibili le seguenti caratteristiche del segmento pronte all’uso; possono essere trascinati dalla barra laterale all’editor:

<table> 
 <tbody> 
  <tr> 
   <td> Intervallo IP<br /> </td> 
   <td>Definisce un intervallo di indirizzi IP che il visitatore può avere.<br /> </td> 
  </tr> 
  <tr> 
   <td> Hit pagina<br /> </td> 
   <td>Con quale frequenza è stata richiesta la pagina. <br /> </td> 
  </tr> 
  <tr> 
   <td> Proprietà pagina<br /> </td> 
   <td>Qualsiasi proprietà della pagina visitata.<br /> </td> 
  </tr> 
  <tr> 
   <td> Parole chiave di riferimento<br /> </td> 
   <td>Parole chiave da abbinare alle informazioni del sito web di riferimento. <br /> </td> 
  </tr> 
  <tr> 
   <td> Script</td> 
   <td>Espressione JavaScript da valutare.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riferimento segmento <br /> </td> 
   <td>Riferimento a un’altra definizione di segmento.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tag cloud<br /> </td> 
   <td>I tag da abbinare a quelli delle pagine visitate.<br /> </td> 
  </tr> 
  <tr> 
   <td> Età utente<br /> </td> 
   <td>Come tratto dal profilo utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> Proprietà utente<br /> </td> 
   <td>Qualsiasi altra informazione disponibile nel profilo utente. </td> 
  </tr> 
 </tbody> 
</table>

Puoi combinare queste caratteristiche utilizzando gli operatori booleani OR e AND (vedi [Creazione di un nuovo segmento](#creating-a-new-segment)) per definire lo scenario esatto per la selezione di questo segmento.

Quando l’intera istruzione restituisce true, questo segmento è stato risolto. Nel caso in cui siano applicabili più segmenti, viene utilizzato anche il fattore **[Incremento.](/help/sites-administering/campaign-segmentation.md#boost-factor)**

>[!CAUTION]
>
>L’editor segmento non verifica la presenza di riferimenti circolari. Ad esempio, il segmento A fa riferimento a un altro segmento B, che a sua volta fa riferimento al segmento A. È necessario assicurarsi che i segmenti non contengano riferimenti circolari.

>[!NOTE]
>
>Proprietà con **_i18n** Il suffisso è impostato da uno script che fa parte della clientlib dell’interfaccia utente di personalizzazione. Tutte le clientlib relative all’interfaccia utente vengono caricate solo sull’autore, poiché l’interfaccia utente non è necessaria al momento della pubblicazione.
>
>Pertanto, quando si crea un segmento con tali proprietà è normalmente necessario fare affidamento su **browserFamily** ad esempio anziché **browserFamily_i18n**.

## Creazione di un nuovo segmento {#creating-a-new-segment}

Per definire il nuovo segmento:

1. Nella barra, scegli **Strumenti > Operazioni > Configurazione**.
1. Fai clic sul pulsante **Segmentazione** nel riquadro a sinistra e passare alla posizione desiderata.
1. Crea un [nuova pagina](/help/sites-authoring/managing-pages.md) utilizzando **Segmento** modello.
1. Apri la nuova pagina per visualizzare l’editor dei segmenti:

   ![screen_shot_2012-02-02at101726am](assets/screen_shot_2012-02-02at101726am.png)

1. Usa la barra laterale o il menu di scelta rapida (solitamente fai clic con il pulsante destro del mouse, quindi seleziona **Nuovo...** per aprire la finestra Inserisci nuovo componente) e trovare la caratteristica del segmento desiderata. Quindi trascinala nella sezione **Editor segmenti** apparirà nel valore predefinito **E** contenitore.
1. Fai doppio clic sulla nuova caratteristica per modificare i parametri specifici; ad esempio la posizione del mouse:

   ![screen_shot_2012-02-02at103135am-1](assets/screen_shot_2012-02-02at103135am-1.png)

1. Fai clic su **OK** per salvare la definizione:
1. È possibile **Modifica** la definizione del segmento per assegnargli un **Titolo**, **Descrizione** e **[Incremento](/help/sites-administering/campaign-segmentation.md#boost-factor)** fattore:

   ![screen_shot_2012-02-02at103547am](assets/screen_shot_2012-02-02at103547am.png)

1. Se necessario, aggiungi altre caratteristiche. Puoi formulare espressioni booleane utilizzando la variabile **Contenitore E** e **Contenitore OR** componenti trovati in **Logica del segmento**. Con l’editor dei segmenti è possibile eliminare caratteristiche o contenitori non più necessari oppure trascinarli in nuove posizioni all’interno dell’istruzione.

## Utilizzo dei contenitori AND e OR {#using-and-and-or-containers}

Puoi creare segmenti complessi in AEM. È utile tenere presenti alcuni punti fondamentali:

* Il livello superiore della definizione è sempre il contenitore AND creato inizialmente; questo non può essere modificato, ma non ha un effetto sul resto della definizione del segmento.
* Assicurati che la nidificazione del contenitore abbia una logica. I contenitori possono essere visualizzati come parentesi dell’espressione boolean.

L’esempio seguente viene utilizzato per selezionare i visitatori che sono:

Maschio e tra i 16 e i 65 anni

OPPURE

Femmina e tra i 16 e i 62 anni

Poiché l’operatore principale è OR è necessario iniziare con un **Contenitore OR**. All’interno di questo sono disponibili 2 istruzioni AND, per ognuna di queste è necessario un **Contenitore E**, in cui puoi aggiungere le singole caratteristiche.

![screen_shot_2012-02-02at105145am-1](assets/screen_shot_2012-02-02at105145am-1.png)

## Test dell’applicazione di un segmento {#testing-the-application-of-a-segment}

Una volta definito il segmento, è possibile testare i risultati potenziali con l’aiuto di **[Contesto client](/help/sites-administering/client-context.md)**:

1. Seleziona il segmento da testare.
1. Press **[Ctrl-Alt-C](/help/sites-authoring/keyboard-shortcuts.md)** per aprire **[Contesto client](/help/sites-administering/client-context.md)**, che mostra i dati raccolti. A scopo di test, è possibile **Modifica** determinati valori, oppure **Load** un altro profilo per vederne l&#39;impatto.

1. A seconda delle caratteristiche definite, i dati disponibili per la pagina corrente possono corrispondere o meno alla definizione del segmento. Lo stato della corrispondenza viene visualizzato sotto la definizione.

Ad esempio, una semplice definizione del segmento può essere basata sull’età e sul genere dell’utente. Il caricamento di un profilo specifico mostra che il segmento è stato risolto correttamente:

![screen_shot_2012-02-02at105926am-1](assets/screen_shot_2012-02-02at105926am-1.png)

Oppure no:

![screen_shot_2012-02-02at110019am-1](assets/screen_shot_2012-02-02at110019am-1.png)

>[!NOTE]
>
>Tutte le caratteristiche vengono risolte immediatamente, anche se la maggior parte si modifica solamente quando la pagina viene ricaricata. Le modifiche alla posizione del mouse sono visibili immediatamente, utili a scopo di test.

Tali test possono essere eseguiti anche su pagine di contenuto e in combinazione con **Teaser** componenti.

Il passaggio del mouse su un paragrafo teaser mostra i segmenti applicati, a prescindere dal fatto che siano attualmente risolti e, quindi, il motivo per cui è stata selezionata l’istanza teaser corrente:

![chlimage_1-408](assets/chlimage_1-408.png)

## Utilizzo del segmento {#using-your-segment}

I segmenti sono attualmente utilizzati in [Campagne](/help/sites-authoring/personalization.md). Vengono utilizzati per gestire il contenuto effettivo visualizzato da tipi di pubblico specifici. Vedi [Informazioni sui segmenti](/help/sites-authoring/segmentation-overview.md) per ulteriori informazioni.
