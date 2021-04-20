---
title: Ricerca full-text GQL
description: Esplora la funzione di ricerca full-text GQL in AEM Assets. Puoi utilizzarlo per cercare le risorse in base a metadati specifici, come titolo, descrizione e nome dell’autore.
contentOwner: AG
feature: Search,Metadata
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 2%

---


# Ricerca full-text GQL {#gql-full-text-search}

Esplora la funzione di ricerca full-text GQL in AEM Assets. Puoi utilizzarlo per cercare le risorse in base a metadati specifici, come titolo, descrizione e nome dell’autore.

La funzione di ricerca full-text GQL consente di cercare le risorse in base a metadati specifici, come titolo, descrizione, autore e così via.

Per cercare una risorsa in base ai relativi metadati, ad esempio il titolo, specifica la parola chiave di metadati seguita dal relativo valore nel pannello di ricerca. La funzione di ricerca full-text di GQL recupererà solo le risorse i cui metadati corrispondono esattamente al valore corrispondente immesso.

Ad esempio, per cercare le risorse con il titolo &quot;Target&quot;, effettua le seguenti operazioni:

## Ricerca delle risorse {#searching-assets}

1. Dalla barra degli strumenti dell’interfaccia utente Assets, tocca o fai clic sull’icona **[!UICONTROL Cerca]** per visualizzare la casella di ricerca Omnisearch.

   ![](assets/do-not-localize/chlimage_1.png)

1. Con il cursore nella casella Omnisearch, premere Invio.
1. Tocca o fai clic sull&#39;icona di navigazione globale per visualizzare il pannello **[!UICONTROL Filtri]** .
1. Nella casella Ricerca Omni, specifica il valore &quot;Target&quot;. Per limitare la ricerca a una cartella specifica, tocca o fai clic sull’icona Sfoglia nel pannello Filtri e seleziona la cartella. In questo caso, la ricerca della corrispondenza viene eseguita solo all’interno della cartella e delle sottocartelle.

   >[!NOTE]
   >
   >È inoltre possibile eseguire ricerche full-text nella cartella . In questo caso, è necessario specificare un termine di ricerca full-text non vuoto.

   ![gql_search](assets/gql_search.png)

1. Premere **[!UICONTROL Invio]**. L’interfaccia utente di AEM Assets visualizza solo le risorse il cui titolo corrisponde esattamente a &quot;Target&quot;.

La funzione di ricerca full-text GQL consente di cercare le risorse in base ai seguenti elementi:

* Query complessa generata dalla combinazione di un’operazione AND, i valori specificati per più campi di metadati (proprietà)
* Valori multipli per un singolo campo di metadati
* Corrispondenza della stringa secondaria

La funzione di ricerca full-text GQL consente di cercare le risorse in base alle seguenti proprietà di metadati. I nomi delle proprietà (ad esempio autore, titolo e così via) e i valori sono sensibili all’uso di maiuscole e minuscole.

>[!NOTE]
>
>La ricerca full-text GQL funziona solo per predicati full-text.

| Proprietà | Formato di ricerca (valore facet) |
|---|---|
| [!UICONTROL Titolo] | title:John |
| [!UICONTROL Creatore] | creatore:John |
| [!UICONTROL Collaboratore] | collaboratore:John |
| [!UICONTROL Posizione] | posizione:India |
| [!UICONTROL Descrizione] | descrizione:&quot;Immagine campione&quot; |
| [!UICONTROL Strumento di creazione] | strumento creatore:&quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL Proprietario copyright] | copyrightowner: &quot;Adobe Systems&quot; |
| [!UICONTROL Collaboratore] | collaboratore:John |
| [!UICONTROL Condizioni d&#39;uso] | usageterms:&quot;CopyRights riservati&quot; |
| [!UICONTROL Creato] | creato:YYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Data di scadenza] | scade:AAAA-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Ora di attivazione] | ora:AAAA-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Ora di disattivazione] | tempo libero:AAAA-MM-DTHH:MM:SS.000+05:30..AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Intervallo di tempo]  (dateontime, offtime) | campo facet: in basso..superiore |
| [!UICONTROL Percorso] | /content/dam/&lt;nome cartella> |
| [!UICONTROL Titolo PDF] | pdftitle:&quot;Documento di Adobe&quot; |
| [!UICONTROL Oggetto] | oggetto: &quot;Formazione&quot; |
| [!UICONTROL Tag] | tags:&quot;Località E Viaggi&quot; |
| [!UICONTROL Tipo] | tipo:&quot;image\png&quot; |
| [!UICONTROL Larghezza immagine] | larghezza:in basso.superiore |
| [!UICONTROL Altezza dell&#39;immagine] | altezza:in basso.superiore |
| [!UICONTROL Person] | persona:John |

Di seguito sono riportati alcuni esempi di formati di ricerca per query complesse:

* Per visualizzare tutte le risorse con più campi facet (ad esempio: title=John Doe strumento creatore = Adobe Photoshop):

tiltle: &quot;John Doe&quot; creatortool : Adobe&amp;ast;

* Per visualizzare tutte le risorse quando il valore dei facet non è una singola parola ma una frase (ad esempio: title=Scott Reynolds)

title:&quot;Scott Reynolds&quot;

* Per visualizzare le risorse con più valori di una singola proprietà (ad esempio: title=Scott Reynolds o John Doe)

title: &quot;Scott Reynolds&quot; O &quot;John Doe&quot;

* Per visualizzare le risorse con valori di proprietà che iniziano con una stringa specifica (ad esempio: titolo è Scott Reynolds)

title: &quot;Scott&quot;

* Per visualizzare le risorse con valori di proprietà che terminano con una stringa specifica (ad esempio: titolo è Scott Reynolds)

title: &quot;Reynolds&quot;

* Per visualizzare le risorse con un valore di proprietà contenente una stringa specifica (ad esempio: title = Sala riunioni di Basilea)

titolo:&quot;Riunione&quot;;

* Per visualizzare le risorse che contengono una stringa particolare e hanno un valore di proprietà specifico (ad esempio: cerca l&#39;Adobe di stringa nelle risorse con title=John Doe)

&amp;ast;Adobe&amp;ast; titolo:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>Il percorso, il limite, le dimensioni e l&#39;ordine delle proprietà non possono essere ORed con nessun&#39;altra proprietà.
>
>La parola chiave per una proprietà generata dall’utente è l’etichetta del relativo campo nell’editor delle proprietà in minuscolo, con gli spazi rimossi.


>[!NOTE]
>
>Se scrivi una query JCR per cercare solo le risorse secondarie, vengono visualizzate anche le risorse di riferimento corrispondenti insieme alle risorse secondarie corrispondenti.

La ricerca full-text supporta anche operatori quali -, ^ e così via. Per cercare queste lettere come stringhe letterali, racchiudere l&#39;espressione di ricerca tra virgolette doppie. Ad esempio, utilizza &quot;Notebook - Bellezza&quot; invece di Notebook - Bellezza.

## Incremento della ricerca {#boosting-search}

Puoi migliorare la pertinenza delle parole chiave per particolari risorse per migliorare le ricerche in base alle parole chiave. In altre parole, le immagini per le quali promuovi parole chiave specifiche vengono visualizzate nella parte superiore dei risultati della ricerca quando esegui una ricerca in base a queste parole chiave.

1. Dall’interfaccia utente di Assets, apri la pagina delle proprietà della risorsa per la quale vuoi promuovere una parola chiave.
1. Passa alla scheda **[!UICONTROL Avanzate]** e tocca o fai clic su **[!UICONTROL Aggiungi]** in **[!UICONTROL Privilegi elevati per parole chiave di ricerca]**.

   ![elev_for_search](assets/elevate_for_search.png)

1. Nella casella **[!UICONTROL Promuovi ricerca]**, specifica una parola chiave per la quale desideri incrementare la ricerca dell&#39;immagine, quindi tocca o fai clic su **[!UICONTROL Aggiungi]**. Se necessario, specificare più parole chiave nello stesso modo.

   ![add_search_word](assets/add_search_word.png)

1. Tocca o fai clic su **[!UICONTROL Salva e chiudi]**.
1. Cerca la parola chiave utilizzando la casella Omnisearch. La risorsa per la quale hai promosso questa parola chiave viene visualizzata tra i primi risultati della ricerca.