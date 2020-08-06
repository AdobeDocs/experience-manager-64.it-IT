---
title: Ricerca full-text GQL
description: Esplora la funzione di ricerca full-text GQL in  AEM Assets. Potete usarlo per cercare risorse basate su metadati specifici, quali titolo, descrizione e nome dell’autore.
contentOwner: AG
translation-type: tm+mt
source-git-commit: adf44677a0ac833a131aad8187529b094aaca9ef
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 2%

---


# Ricerca full-text GQL {#gql-full-text-search}

Esplora la funzione di ricerca full-text GQL in  AEM Assets. Potete usarlo per cercare risorse basate su metadati specifici, quali titolo, descrizione e nome dell’autore.

La funzione di ricerca full-text GQL consente di cercare risorse in base a metadati specifici, quali titolo, descrizione, autore e così via.

Per cercare una risorsa in base ai relativi metadati, ad esempio il titolo, specificate la parola chiave di metadati seguita dal relativo valore nel pannello di ricerca. La funzione di ricerca full-text GQL recupererà solo le risorse i cui metadati corrispondono esattamente al valore corrispondente immesso.

Ad esempio, per cercare le risorse con il titolo &quot;Target&quot;, effettuate le seguenti operazioni:

## Ricerca delle risorse {#searching-assets}

1. Dalla barra degli strumenti dell’interfaccia utente Risorse, tocca o fai clic sull’icona **[!UICONTROL Cerca]** per visualizzare la casella di ricerca Omnico.

   ![](assets/do-not-localize/chlimage_1.png)

1. Con il cursore nella casella Omnisearch, premere Invio.
1. Tocca o fai clic sull’icona GlobalNav per visualizzare il pannello **[!UICONTROL Filtri]** .
1. Nella casella Ricerca Omni, specificate il valore &quot;Target&quot;. Per limitare la ricerca a una cartella specifica, toccate o fate clic sull’icona Sfoglia nel pannello Filtri e selezionate la cartella. In questo caso, la ricerca viene effettuata solo all’interno della cartella e delle sottocartelle al suo interno.

   >[!NOTE]
   >
   >Potete anche eseguire una ricerca full-text nella cartella. In questo caso, dovete specificare un termine di ricerca full-text non vuoto.

   ![gql_search](assets/gql_search.png)

1. Press **[!UICONTROL Enter]**. L&#39;interfaccia utente  AEM Assets visualizza solo le risorse il cui titolo corrisponde esattamente a &quot;Target&quot;.

La funzione di ricerca full-text GQL consente di effettuare ricerche di risorse basate sui seguenti elementi:

* Query complessa creata combinando tramite un&#39;operazione AND i valori specificati per più campi di metadati (proprietà)
* Più valori per un singolo campo di metadati
* Sottostringa

La funzione di ricerca full-text di GQL consente di cercare le risorse in base alle seguenti proprietà di metadati. I nomi delle proprietà (ad esempio autore, titolo e così via) e i valori seguono la distinzione tra maiuscole e minuscole.

>[!NOTE]
>
>La ricerca full-text GQL funziona solo per i predicati full-text.

| Proprietà | Formato di ricerca (valore facet) |
|---|---|
| [!UICONTROL Titolo] | title:John |
| [!UICONTROL Creatore] | creatore:John |
| [!UICONTROL Collaboratore] | collaboratore:John |
| [!UICONTROL Posizione] | posizione:India |
| [!UICONTROL Descrizione] | descrizione:&quot;Immagine campione&quot; |
| [!UICONTROL Strumento di creazione] | creatortool:&quot; Adobe Photoshop 7.0&quot; |
| [!UICONTROL Proprietario copyright] | copyrightowner:&quot; Adobe Systems&quot; |
| [!UICONTROL Collaboratore] | collaboratore:John |
| [!UICONTROL Condizioni d&#39;uso] | usageterms:&quot;CopyRights Reserved&quot; |
| [!UICONTROL Creato] | create:AAAA-MM-DDTHH:MM:SS.000+05:30.AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Data scadenza] | scade:AAAA-MM-DTHH:MM:SS.000+05:30.AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Ora di attivazione] | ora:AAAA-MM-DTHH:MM:SS.000+05:30.AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Ora di disattivazione] | offtime:AAAA-MM-DTHH:MM:SS.000+05:30.AAAA-MM-DTHH:MM:SS.000+05:30 |
| [!UICONTROL Intervallo di tempo] (data di scadenza, ora di disattivazione) | campo facet: in basso..upperbound |
| [!UICONTROL Percorso] | /content/dam/&lt;nome cartella> |
| [!UICONTROL Titolo PDF] | pdftitle:&quot;Documento  Adobe&quot; |
| [!UICONTROL Oggetto] | oggetto: &quot;Formazione&quot; |
| [!UICONTROL Tag] | tags:&quot;Location And Travel&quot; |
| [!UICONTROL Tipo] | type:&quot;image\png&quot; |
| [!UICONTROL Larghezza dell’immagine] | width:lowerbound.upperbound |
| [!UICONTROL Altezza dell’immagine] | height:lowerbound.upperbound |
| [!UICONTROL Person] | persona:John |

Di seguito sono riportati alcuni esempi di formati di ricerca per query complesse:

* Per visualizzare tutte le risorse con più campi facet (ad esempio: title=John Doe e strumento di creazione =  Adobe Photoshop):

tiltle: &quot;John Doe&quot; creatortool :  Adobe&amp;ast;

* Per visualizzare tutte le risorse quando il valore dei facet non è una singola parola ma una frase (ad esempio: title=Scott Reynolds)

title: &quot;Scott Reynolds&quot;

* Per visualizzare le risorse con più valori di una singola proprietà (ad esempio: title=Scott Reynolds o John Doe)

title: &quot;Scott Reynolds&quot; O &quot;John Doe&quot;

* Per visualizzare le risorse con valori di proprietà che iniziano con una stringa specifica (ad esempio: title is Scott Reynolds)

title: &quot;Scott&quot;

* Per visualizzare le risorse con valori di proprietà che terminano con una stringa specifica (ad esempio: title is Scott Reynolds)

title: &quot;Reynolds&quot;

* Per visualizzare le risorse con un valore di proprietà contenente una stringa specifica (ad esempio: title = Sala riunioni di Basilea)

title: &quot;Riunione&quot;;

* Per visualizzare le risorse che contengono una stringa particolare e hanno un valore di proprietà specifico (ad esempio: cercare una stringa  Adobe nelle risorse con titolo=John Doe)

&amp;ast; Adobe&amp;ast; titolo: &quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast; Adobe&amp;ast;

>[!NOTE]
>
>Il percorso, il limite, la dimensione e l&#39;ordine delle proprietà non possono essere eseguiti in ORed con altre proprietà.
>
>La parola chiave per una proprietà generata dall&#39;utente è la relativa etichetta campo nell&#39;editor delle proprietà in lettere minuscole, con la rimozione degli spazi.


>[!NOTE]
>
>Se scrivete una query JCR per cercare solo le risorse secondarie, vengono visualizzate anche le risorse di riferimento corrispondenti insieme alle risorse secondarie corrispondenti.

La ricerca full text supporta anche operatori quali -, ^ e così via. Per cercare queste lettere come stringhe letterali, racchiudere l&#39;espressione di ricerca tra virgolette. Ad esempio, utilizzare &quot;Notebook - Bellezza&quot; invece di Notebook - Bellezza.

## Incremento della ricerca {#boosting-search}

Potete migliorare la rilevanza delle parole chiave per risorse particolari per migliorare le ricerche in base alle parole chiave. In altre parole, le immagini per le quali vengono promosse parole chiave specifiche vengono visualizzate nella parte superiore dei risultati della ricerca quando si esegue una ricerca basata su tali parole chiave.

1. Nell’interfaccia utente delle risorse, apri la pagina delle proprietà per la risorsa per la quale vuoi promuovere una parola chiave.
1. Passate alla scheda **[!UICONTROL Avanzate]** e toccate o fate clic su **[!UICONTROL Aggiungi]** in **[!UICONTROL Elevate per cercare le parole chiave]**.

   ![elev_for_search](assets/elevate_for_search.png)

1. Nella casella **[!UICONTROL Search Promote (Promuovi]** ricerca), specificate una parola chiave per la quale desiderate incrementare la ricerca dell&#39;immagine e quindi fate clic o toccate **[!UICONTROL Aggiungi]**. Se necessario, specificate più parole chiave nello stesso modo.

   ![add_search_word](assets/add_search_word.png)

1. Click/tap **[!UICONTROL Save &amp; Close]**.
1. Cercate la parola chiave utilizzando la casella di ricerca Omnico. La risorsa per la quale hai promosso questa parola chiave viene visualizzata tra i primi risultati della ricerca.