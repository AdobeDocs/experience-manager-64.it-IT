---
title: Creazione di una pagina del portale moduli
seo-title: Creazione di una pagina del portale moduli
description: Forms Portal offre agli sviluppatori Web componenti per creare e personalizzare un portale moduli sui siti Web creati con Adobe Experience Manager (AEM).
seo-description: Forms Portal offre agli sviluppatori Web componenti per creare e personalizzare un portale moduli sui siti Web creati con Adobe Experience Manager (AEM).
uuid: 328f3342-d6ca-4413-9f1d-1a550df74bde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7387dfe8-0029-4ad0-b319-fc519928318b
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 1%

---


# Creazione di una pagina del portale moduli {#creating-a-forms-portal-page}

I componenti del portale Forms forniscono agli sviluppatori Web componenti per creare e personalizzare un portale moduli sui siti Web creati con Adobe Experience Manager (AEM). Per una panoramica rapida del portale dei moduli, vedere [Introduzione alla pubblicazione di moduli su un portale](/help/forms/using/introduction-publishing-forms.md).

## Prerequisiti {#prerequisites}

Per impostazione predefinita, i componenti del portale Forms non sono disponibili per l&#39;uso. Assicurarsi che le seguenti categorie di componenti del portale moduli siano abilitate come descritto in [Abilitazione dei componenti](/help/forms/using/enabling-forms-portal-components.md)del portale moduli.

**Document Services** include i componenti Ricerca e archiviazione, Collegamento, Bozze e Invii.

**Predicati** di Document Services include i componenti Predicato data, Predicato testo completo, Predicato proprietà e Predicato tag. Questi componenti sono utilizzati per configurare la ricerca nel componente Ricerca e filtro.

Una volta abilitati in una pagina AEM siti, queste categorie di componenti sono disponibili per l’uso nel browser Componenti.

![componenti del portale AEM Forms nel browser](assets/component-categories.png)componenti **Figura:** *Categorie di componenti di Forms Portal*

## Componente Ricerca e filtro {#search-amp-lister-component}

Il componente Cerca e elenca, disponibile nella categoria di componenti Document Services, consente di elencare i moduli su una pagina e di implementare la ricerca nei moduli elencati. Il componente include due riquadri:

* Riquadro elenco in cui sono elencati i moduli.
* Riquadro di ricerca in cui si aggiunge la funzionalità di ricerca.

È possibile trascinare il componente Ricerca e filtro dalla categoria di componenti Document Services nel browser Componenti sulla pagina. Il componente, se aggiunto, è simile al seguente.

![Componente Search &amp; Lister in a page](assets/fp-grid-viw.png)**Figure:** *Componente Ricerca e filtro in una pagina con layout Griglia*

### Riquadro elenco {#list-pane}

Il riquadro Elenco è un&#39;area in cui sono elencati i moduli. Il componente Ricerca e filtro offre diverse opzioni di configurazione che è possibile utilizzare per controllare la visualizzazione dei moduli nel riquadro Elenco.

Per configurare il riquadro Elenco, toccate il componente Cerca e Archivia, quindi toccate ![settings_icon](assets/settings_icon.png). Viene visualizzata la finestra di dialogo **[!UICONTROL Modifica componente]** .

![Riquadro elenco in modalità](assets/edit-list.png)di modifica **Figura:** *Riquadro elenco in modalità di modifica*

La finestra di dialogo **[!UICONTROL Modifica]** include diverse schede che forniscono le opzioni di configurazione descritte nella tabella seguente. Al termine, toccate **[!UICONTROL OK]** per salvare la configurazione.

<table> 
 <tbody> 
  <tr> 
   <th>Scheda</th> 
   <th>Configurazione</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Cartelle risorse</strong></span></td> 
   <td>Aggiungi elemento</td> 
   <td>Configura le cartelle in cui vengono caricate le risorse tramite ’interfaccia utente di AEM Forms. Per impostazione predefinita, elenca tutte le risorse caricate. Per ulteriori informazioni 'interfaccia utente di AEM Forms, vedere <a href="/help/forms/using/introduction-managing-forms.md" target="_blank">Introduzione alla gestione dei moduli</a>.</td> 
  </tr> 
  <tr> 
   <td><p><span class="uicontrol"><strong>Visualizzazione</strong></span></p> </td> 
   <td>Testo titolo</td> 
   <td>Titolo del componente Ricerca e filtro. Il titolo predefinito è <strong>Forms Portal.</strong></td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Modello di layout</td> 
   <td>Layout delle risorse. </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Disattiva ricerca avanzata</td> 
   <td>Quando abilitata, nasconde l'icona di ricerca avanzata.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Disattiva ricerca testo</td> 
   <td>Quando questa opzione è attivata, nasconde la barra di ricerca full-text.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Risultato</strong></span></td> 
   <td>Numero Di Risultati Per Pagina</td> 
   <td>Configura il numero massimo di moduli da visualizzare su una pagina.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Testo risultati</td> 
   <td><p>Configura il testo dei risultati (ad esempio, 1-12 di 601 <strong>Risultati</strong>). The default value is <strong>Results</strong>.</p> <p>Ad esempio, se si specifica <strong>Forms </strong>in questo campo e si dispone di un totale di 601 moduli, il testo del risultato cambia da 1 a 12 di 601 <strong>Forms.</strong></p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Testo pagina</td> 
   <td><p>Configura il testo della pagina (ad esempio, <strong>Pagina </strong>1 di 51). The default value is <strong>Page</strong>.</p> <p>Ad esempio, se si specifica Modulo <strong>applicazione </strong>in questo campo e sono presenti 51 pagine, il testo della pagina diventa Modulo <strong>applicazione </strong>1 di 51.</p> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Di testo</td> 
   <td><p>Sostituisce la parola <strong>di</strong> con il testo specificato (Pagina 1 <strong>di </strong>51). The default value is <strong>of</strong>.</p> <p>Ad esempio, se specificate <strong>out </strong>in questo campo, il testo diventa Pagina 1 <strong>su </strong>51.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Collegamento modulo</strong></span></td> 
   <td>Tipo di rendering</td> 
   <td>Controlla l'elenco dei moduli in base al tipo di rendering specificato. Le opzioni disponibili sono PDF e HTML. Ad esempio, se selezionate solo HTML come tipo di rendering, gli PDF forms vengono filtrati.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Profilo HTML</td> 
   <td>Configura il profilo HTML da utilizzare per il rendering. Tutti i profili disponibili sono elencati nell'elenco a discesa.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Invia URL</td> 
   <td><p>Configura un servlet in cui vengono inviati i dati del modulo.</p> <p><strong>Nota:</strong> <em>È possibile specificare l'URL di invio di un modulo in più punti e il relativo ordine di precedenza è il seguente:</em></p> 
    <ol> 
     <li><em>L'URL di invio incorporato nel modulo (nel pulsante Invia) ha la priorità più alta.</em></li> 
     <li><em>L’URL di invio menzionato ’interfaccia utente di AEM Forms ha la seconda priorità.</em></li> 
     <li><em>L'URL di invio indicato nel portale dei moduli ha la priorità più bassa.</em></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Descrizione comandi per le azioni di rendering HTML</td> 
   <td>Configura il testo della descrizione comandi, che viene visualizzata quando si passa il puntatore su di essa <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> (icona HTML5).</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Descrizione comandi per le azioni di rendering PDF</td> 
   <td>Configura il testo della descrizione comandi, che viene visualizzata quando si passa il puntatore su di esso <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> (icona PDF).</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol"><strong>Stile</strong></span></td> 
   <td>Tipo di stile</td> 
   <td>Consente di specificare <strong>Nessuno stile, Stile</strong>predefinito o Stile <strong>personalizzato </strong>per elencare i moduli.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Percorso stile personalizzato</td> 
   <td>Se avete selezionato Personalizzato come Tipo di stile, individuate e specificate il percorso del CSS personalizzato, altrimenti selezionate Predefinito.</td> 
  </tr> 
 </tbody> 
</table>

### Riquadro di ricerca {#search-pane}

Il riquadro Ricerca consente di aggiungere i componenti Predicato data, Predicato testo completo, Predicato proprietà e Predicato tag dalla categoria Predicati di Document Services nella barra laterale AEM. Questi componenti implementano la funzionalità di ricerca che consente agli utenti di eseguire ricerche nei moduli elencati.

**Suggerimento:** *È possibile controllare l&#39;elenco dei moduli visualizzato nel portale dei moduli in base a criteri predefiniti e nascondere la funzionalità di ricerca per gli utenti finali. Per controllare l&#39;elenco dei moduli, utilizzare i componenti Predicate per applicare i filtri di ricerca. È inoltre possibile specificare i valori di filtro predefiniti e disabilitare la ricerca dalla scheda Visualizzazione della finestra di dialogo Modifica componente.*

![Pannello di ricerca con Data, Testo completo, Proprietà e Predicato](assets/search-with-predicates.png)**tag:** *Pannello di ricerca con indicazione data, testo completo, proprietà e tag*

#### Predicato data {#date-predicate}

Il componente Predicato data, se aggiunto, consente la ricerca nei moduli elencati modificati durante una durata specificata.

Per configurare il componente Predicato data:

1. Toccate il componente, quindi toccate ![settings_icon](assets/settings_icon.png). Viene visualizzata la finestra di dialogo Modifica.
1. Specificate quanto segue:

   * **[!UICONTROL Tipo:]** L’unica opzione disponibile è Data **[!UICONTROL ultima modifica]**.
   * **[!UICONTROL Testo:]** Etichetta o didascalia per il componente Predicato data. Il valore predefinito è Data **[!UICONTROL ultima modifica]**.
   * **[!UICONTROL Etichetta data inizio:]** Etichetta o didascalia del campo data di inizio.
   * **[!UICONTROL Etichetta data fine:]** Etichetta o didascalia per il campo data di fine.
   * **[!UICONTROL Nascondi:]** Per applicare il filtro data predefinito all&#39;elenco dei moduli.

1. Toccate **[!UICONTROL OK]**.

#### Predicato full-text {#full-text-predicate}

Il componente Predicato full-text implementa la ricerca full-text sui dati del modulo, ad esempio nome e descrizione. Gli utenti possono cercare qualsiasi stringa di testo per restituire moduli che contengono il testo nel nome o nella descrizione.

Per configurare il componente Predicato full-text:

1. Toccate il componente, quindi toccate ![settings_icon](assets/settings_icon.png). Viene visualizzata la finestra di dialogo Modifica.
1. Specificate il titolo nel campo Titolo **** principale.
1. Toccate **[!UICONTROL Ok]**.

#### Predicato proprietà {#properties-predicate}

Il componente Predicato proprietà implementa la ricerca nei moduli in base alle proprietà del modulo, quali titolo, autore e descrizione.

Per configurare il componente Predicato proprietà:

1. Toccate il componente, quindi toccate ![settings_icon](assets/settings_icon.png). Viene visualizzata la finestra di dialogo **** Modifica.
1. Nella scheda **[!UICONTROL Generale]** , specificate l&#39;etichetta di ricerca. The default value is **[!UICONTROL Properties]**.

1. Nella scheda **[!UICONTROL Opzioni]** , toccate **[!UICONTROL Aggiungi elemento]**.
1. Selezionare una proprietà dall&#39;elenco a discesa e specificare un&#39;etichetta di ricerca nel campo sotto l&#39;elenco a discesa.
1. Ripetere il passaggio 4 per aggiungere altre proprietà. È inoltre possibile specificare un valore di filtro predefinito per elencare i moduli in base ai criteri specificati e nascondere la proprietà di ricerca per gli utenti finali. Selezionare la casella di controllo Nascondi per una proprietà e specificare il valore del filtro predefinito.

   Ad esempio, se si desidera visualizzare i moduli che contengono &quot;Viaggio&quot; nei titoli, selezionare Nascondi accanto alla proprietà Titolo. Inoltre, specificate Viaggio nella casella di testo del valore del filtro predefinito.

1. Toccate **[!UICONTROL OK]**.

#### Predicato tag {#tags-predicate}

Il componente Predicato tag implementa la ricerca nei moduli in base ai tag definiti in Forms Manager.

Per configurare il componente Predicato tag:

1. Toccate il componente, quindi toccate ![settings_icon](assets/settings_icon.png). Viene visualizzata la finestra di dialogo **** Modifica.
1. Toccate il pulsante freccia giù accanto al campo Tag.
1. Selezionate i tag appropriati.
1. Toccate **[!UICONTROL OK]**.

I tag selezionati vengono visualizzati nel riquadro Ricerca insieme alle caselle di controllo per la selezione. Gli utenti ora possono limitare la ricerca in base ai tag.

## Elencare i moduli in una pagina {#list-forms-on-a-page-br}

Per elencare i moduli in una pagina, aggiungere il componente **[!UICONTROL Cerca e tieni]** traccia alla pagina e configurare il riquadro **** Elenco. Per consentire agli utenti finali di effettuare ricerche nei moduli con data, testo e tag, aggiungere un componente Riquadro **[!UICONTROL di]** ricerca.

Per collegare un modulo da un punto qualsiasi della pagina, utilizzare il componente Collegamento. Per ulteriori informazioni sul componente collegamento, consulta [Incorporamento del componente collegamento in una pagina](/help/forms/using/embedding-link-component-page.md).

Per elencare i moduli in stato bozza e quelli già inviati, utilizzare il componente **[!UICONTROL Bozze e invii]** . Per ulteriori informazioni, vedere [Personalizzazione di bozze e invii](/help/forms/using/draft-submission-component.md).

## Facilità di utilizzo dei dispositivi mobili {#mobile-device-friendliness}

Il componente Forms Portal Search &amp; Lister è compatibile con i dispositivi mobili e si adatta di conseguenza. Tutte e tre le viste predefinite: Griglia, Scheda, Pannello vengono presentati in base al dispositivo in cui viene aperto il sito, a condizione che anche la pagina Web si adatti. Il fatto è che Search &amp; Lister è solo un componente e non regola lo stile a livello di pagina.

L’immagine seguente mostra il componente Ricerca e filtro quando viene aperto su un dispositivo mobile:

![Screenshot del componente](assets/search_lister.png)Ricerca e Lister **Figura:** *Ricerca e filtro, componente*

## Personalizzazione di una pagina del portale moduli {#customizing-a-forms-portal-page-br}

È possibile personalizzare una pagina del portale dei moduli per fornire un aspetto distinto alla pagina. Potete inoltre aggiungere metadati per migliorare l&#39;esperienza di ricerca, modificare il layout della pagina e aggiungere stili CSS personalizzati. Per ulteriori informazioni, consultate [Personalizzazione dei modelli per i componenti](/help/forms/using/customizing-templates-forms-portal-components.md)di Forms Portal.

&#39;interfaccia utente di AEM Forms consente di aggiungere metadati personalizzati ai moduli. I metadati personalizzati sono utili per fornire agli utenti finali un&#39;esperienza di elenco e ricerca dei moduli. Per ulteriori informazioni sui metadati personalizzati, consultate [Personalizzazione dei modelli per i componenti](/help/forms/using/customizing-templates-forms-portal-components.md)di Forms Portal.

Dal portale dei moduli sono incluse le azioni di rendering. È possibile personalizzare il portale dei moduli per aggiungere ulteriori azioni. Per informazioni dettagliate, vedere [Aggiunta di un&#39;azione personalizzata agli elementi dell&#39;elenco dei moduli.](/help/forms/using/add-custom-action-form-lister.md)
