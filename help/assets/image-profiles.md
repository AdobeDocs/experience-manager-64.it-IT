---
title: Profili immagine Dynamic Media
seo-title: Dynamic Media image profiles
description: Crea profili immagine contenenti impostazioni per maschera non affilata, ritaglio avanzato, campione avanzato o entrambi, quindi applica il profilo a una cartella di risorse immagine.
seo-description: Create image profiles that contain settings for unsharp mask, and smart crop or smart swatch, or both, then apply the profile to a folder of image assets.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
exl-id: 895103c8-df58-40f0-85d6-e29637edce53
feature: Image Profiles
role: Admin,User
source-git-commit: 77b2643c91092a9a08b67fb5ad06a96a79f4deea
workflow-type: tm+mt
source-wordcount: '2729'
ht-degree: 12%

---

# Profili immagine Dynamic Media {#image-profiles}

Quando carichi le immagini, puoi ritagliare automaticamente l’immagine al momento del caricamento applicando un profilo immagine alla cartella.

>[!NOTE]
>
>Smart Crop è disponibile solo in modalità Dynamic Media - Scene7.

>[!IMPORTANT]
>
>I profili immagine non sono applicabili ai file PDF, animated GIF o INDD (Adobe InDesign).


## Opzioni di ritaglio {#crop-options}

Quando implementi il ritaglio avanzato sulle immagini, Adobe consiglia la seguente best practice e applica il seguente limite:

| Tipo di limite | Best practice | Limite imposto | Modifica del limite il 31 dicembre 2022 |
| --- | --- | --- | --- |
| Numero di ritagli avanzati per immagine | 5 | 100 | 20 |

Vedi anche [Limiti Dynamic Media](/help/assets/limitations.md).

<!-- CQDOC-16069 for paragraph directly below -->

Le coordinate di ritaglio avanzato dipendono dalle proporzioni. In altre parole, per le varie impostazioni di ritaglio avanzato in un profilo immagine, se le proporzioni sono le stesse per le dimensioni aggiunte nel profilo immagine, le stesse proporzioni vengono inviate a Dynamic Media. Per questo motivo, l’Adobe consiglia di utilizzare la stessa area di ritaglio. In questo modo non vi sarà alcun impatto sulle diverse dimensioni utilizzate nel profilo immagine.

Tieni presente che ogni generazione di ritaglio avanzato creata richiede un’elaborazione aggiuntiva. Ad esempio, l’aggiunta di più di cinque rapporti di formato Ritaglio avanzato può causare un tasso di inserimento delle risorse lento. Può anche causare un aumento del carico sui sistemi. Poiché è possibile applicare Smart Crop a livello di cartella, Adobe consiglia di utilizzarlo nelle cartelle *only* dove è necessario.

Potete scegliere tra due opzioni di ritaglio immagine. È inoltre disponibile un’opzione per automatizzare la creazione di campioni di colore e immagine.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opzione</strong></td> 
   <td><strong>Quando utilizzare</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>Ritaglio pixel</td> 
   <td>Le immagini ritagliate in blocco in base solo alle dimensioni.</td> 
   <td><p>Per utilizzare questa opzione, seleziona <strong>Ritaglio pixel</strong> dall’elenco a discesa Opzioni di ritaglio .</p> <p>Per ritagliare dai lati di un’immagine, immetti il numero di pixel da ritagliare da qualsiasi lato o lato dell’immagine. La quantità di immagine ritagliata dipende dall’impostazione ppi (pixel per pollice) nel file di immagine.</p> <p>Il rendering di un ritaglio pixel del profilo immagine avviene nel modo seguente:<br /> </p> 
    <ul> 
     <li>I valori sono Superiore, Inferiore, Sinistra e Destra.</li> 
     <li>In alto a sinistra è considerato 0,0 e il ritaglio dei pixel viene calcolato da lì.</li> 
     <li>Punto iniziale di ritaglio: La sinistra è X e la parte superiore è Y</li> 
     <li>Calcolo orizzontale: dimensione pixel orizzontale dell'immagine originale meno sinistro e quindi meno destro.</li> 
     <li>Calcolo verticale: altezza pixel verticale meno superiore, quindi meno inferiore.</li> 
    </ul> <p>Ad esempio, supponiamo di avere un'immagine di 4000 x 3000 pixel. I valori vengono utilizzati: Top=250, Bottom=500, Left=300, Right=700.</p> <p>Dall’alto a sinistra (300.250) ritagliare utilizzando lo spazio di riempimento di (4000-300-700, 3000-250-500, o 3000.2250).</p> </td> 
  </tr> 
  <tr> 
   <td>Ritaglio avanzato</td> 
   <td>Ritaglio in serie di immagini in base al loro punto focale visivo.</td> 
   <td><p>Smart Crop utilizza la potenza dell'intelligenza artificiale in Adobe Sensei per automatizzare rapidamente il ritaglio delle immagini in blocco. Smart Crop rileva e ritaglia automaticamente il punto focale in qualsiasi immagine per catturare il punto di interesse desiderato, indipendentemente dalle dimensioni dello schermo.</p> <p>Per utilizzare il ritaglio avanzato, seleziona <strong>Ritaglio avanzato</strong> dall’elenco a discesa Opzioni di ritaglio , a destra di Ritaglio immagine reattivo, abilita (attiva) la funzione.</p> <p>Le dimensioni predefinite dei punti di interruzione di grandi, medi e piccoli coprono in genere l'intera gamma di dimensioni che la maggior parte delle immagini vengono utilizzate su dispositivi mobili e tablet, desktop e banner. Se lo desideri, puoi modificare i nomi predefiniti di Grande, Medio e Piccolo.</p> <p>Per aggiungere altri punti di interruzione, fai clic su <strong>Aggiungi ritaglio</strong>; per eliminare un ritaglio, fai clic sull’icona Garbage Can .</p> </td> 
  </tr> 
  <tr> 
   <td>Campione immagine e colore</td> 
   <td>Generare in blocco un campione immagine per ogni immagine.</td> 
   <td><p><strong>Nota</strong>: Lo Smart Swatch non è supportato in Dynamic Media Classic.</p> <p>Individua e genera automaticamente campioni di alta qualità dalle immagini dei prodotti che mostrano colore o texture.</p> <p>Per utilizzare Colore e Campione immagine, selezionare <strong>Ritaglio avanzato</strong> dall’elenco a discesa Opzioni di ritaglio, quindi a destra di Colore e Campione immagine, abilita (attiva) la funzione. Immettere un valore in pixel nelle caselle di testo Larghezza e Altezza.</p> <p>Mentre tutti i ritagli immagine sono disponibili nella barra Rendering , i campioni vengono utilizzati solo tramite la funzione Copia URL . Per eseguire il rendering del campione sul sito, è necessario utilizzare il proprio componente di visualizzazione. (L'eccezione è rappresentata dai banner a carosello. Dynamic Media fornisce il componente di visualizzazione per il campione utilizzato nei banner a carosello.)</p> <p><strong>Utilizzo dei campioni immagine</strong></p> <p>L’URL per i campioni immagine è semplice. Questo è:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>dove <code>:Swatch</code> viene aggiunto alla richiesta di risorse.</p> <p><strong>Utilizzo dei campioni colore</strong></p> <p>Per utilizzare i campioni colore, effettuate una <code>req=userdata</code> richiedere quanto segue:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Ad esempio, di seguito è riportata una risorsa campione in Dynamic Media Classic:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>ed ecco il corrispondente della risorsa campione <code>req=userdata</code> URL:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>La <code>req=userdata</code> la risposta è la seguente:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>Puoi anche richiedere un <code>req=userdata</code> risposta in formato XML o JSON, come nei seguenti esempi URL:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Maschera di contrasto {#unsharp-mask}

Utilizzate **Maschera definizione dettagli** per ottimizzare un effetto filtro di nitidezza sull&#39;immagine ricampionata verso il basso finale. Puoi controllare l’intensità dell’effetto, il raggio in pixel e una soglia di contrasto da ignorare. L’effetto utilizza le stesse opzioni del filtro “Maschera definizione dettagli” di Adobe Photoshop.

>[!NOTE]
>
>Maschera definizione dettagli viene applicata solo alle rappresentazioni ridimensionate all’interno del PTIFF (TIFF piramidale) che vengono sottoposte a sottocampionamento superiore al 50%. Ciò significa che le rappresentazioni di grandi dimensioni all’interno del PTIFF non sono influenzate da una maschera di contrasto, mentre le rappresentazioni di dimensioni più piccole, come le miniature, vengono modificate (e mostreranno la maschera di contrasto).

In **Maschera definizione dettagli**, sono disponibili le seguenti opzioni di filtro:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Opzione</strong></td> 
   <td><strong>Descrizione</strong></td> 
  </tr> 
  <tr> 
   <td>Quantità</td> 
   <td>Controlla la quantità di contrasto applicata ai pixel del bordo. Il valore predefinito è 1,75. Per le immagini ad alta risoluzione, è possibile aumentarlo fino a 5. Considera Importo come una misura dell'intensità del filtro. L'intervallo è compreso tra 0 e 5.</td> 
  </tr> 
  <tr> 
   <td>Raggio</td> 
   <td>Determina quanti pixel attorno al bordo vengono interessati dalla nitidezza. Per le immagini ad alta risoluzione, inserite un valore da 1 a 2. Un valore basso agisce solo sui pixel del bordo; un valore più elevato agisce su una fascia più ampia di pixel. Il valore adatto dipende dalle dimensioni dell'immagine. Il valore predefinito è 0,2. Intervallo compreso tra 0 e 250.</td> 
  </tr> 
  <tr> 
   <td>Soglia</td> 
   <td><p>Determina l'intervallo di contrasto da ignorare quando viene applicato il filtro Maschera definizione dettagli. In altre parole, questa opzione determina la differenza tra i pixel da rendere più nitidi rispetto all’area circostante, prima che vengano considerati pixel del bordo e resi più nitidi. Per evitare di introdurre rumore, prova con valori compresi tra 0 e 255.</p> </td> 
  </tr> 
 </tbody> 
</table>

La nitidezza è descritta in [Nitidezza delle immagini](/help/assets/assets/sharpening_images.pdf).

## Creazione di profili immagine Dynamic Media {#creating-image-profiles}

Per definire parametri di elaborazione avanzati per altri tipi di risorse, consulta [Configurazione dell’elaborazione delle risorse](config-dms7.md#configuring-asset-processing).

**Creazione di profili immagine Dynamic Media**:

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Strumenti > Risorse > Profili immagine]**.
1. Tocca **[!UICONTROL Crea]** per aggiungere un nuovo profilo immagine.
1. Inserisci un nome di profilo e valori per maschera non affilata, ritaglio o campione o entrambi.

   È utile utilizzare un nome di profilo specifico per lo scopo a cui è destinato. Ad esempio, se desideri creare un profilo che generi solo i campioni, ovvero se il ritaglio avanzato è disattivato e se il campione colore e immagine è attivato (attivato), puoi utilizzare il nome del profilo &quot;Campioni avanzati&quot;.

   Consulta anche la sezione [Opzioni di ritaglio avanzato e campione avanzato](#crop-options) e [Maschera definizione dettagli](#unsharp-mask).

   ![coltura](assets/crop.png)

1. Tocca **[!UICONTROL Salva]**. Il nuovo profilo creato viene visualizzato nell’elenco dei profili disponibili.

## Modifica o eliminazione dei profili immagine di Dynamic Media {#editing-or-deleting-image-profiles}

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Strumenti > Risorse > Profili immagine]**.
1. Seleziona il profilo immagine da modificare o rimuovere. Per modificarlo, seleziona **[!UICONTROL Modifica profilo elaborazione immagine]**. Per rimuoverlo, seleziona **[!UICONTROL Elimina profilo elaborazione immagine]**.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. In caso di modifica, salva le modifiche. Se si esegue l’eliminazione, confermare la rimozione del profilo.

## Applicazione di un profilo immagine Dynamic Media alle cartelle {#applying-an-image-profile-to-folders}

Quando assegni un profilo immagine a una cartella, tutte le sottocartelle ereditano automaticamente il profilo dalla relativa cartella principale. Ciò significa che puoi assegnare un solo profilo immagine a una cartella. Considera attentamente la struttura delle cartelle in cui caricare, archiviare, utilizzare e archiviare le risorse.

Se hai assegnato un profilo immagine diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse della cartella esistenti in precedenza rimangono invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell’interfaccia utente in base al nome del profilo visualizzato nella scheda.

Quando aggiungi il ritaglio avanzato a un profilo immagine esistente, devi riattivare il [Flusso di lavoro Aggiorna risorsa DAM](assets-workflow.md) se desideri generare colture per le risorse esistenti nell’archivio risorse.

Puoi applicare i profili immagine a cartelle specifiche o globalmente a tutte le risorse.

### Applicazione dei profili immagine Dynamic Media a cartelle specifiche {#applying-image-profiles-to-specific-folders}

Puoi applicare un profilo immagine a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili immagine alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili immagine Dynamic Media alle cartelle dall’interfaccia utente Profili {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Strumenti > Risorse > Profili immagine]**.
1. Seleziona il profilo immagine da applicare a una o più cartelle.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tocca **[!UICONTROL Applica profilo di elaborazione alle cartelle]** e seleziona una o più cartelle da utilizzare per ricevere le risorse appena caricate, quindi tocca o fai clic su **[!UICONTROL Applica]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili immagine Dynamic Media alle cartelle da Proprietà {#applying-image-profiles-to-folders-from-properties}

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Risorse]**. Quindi passa alla cartella principale della cartella a cui desideri applicare un profilo immagine.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.
1. Tocca la scheda **[!UICONTROL Profili immagine]**. Seleziona il profilo dall’elenco a discesa **[!UICONTROL Nome profilo]**, quindi tocca **[!UICONTROL Salva e chiudi]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Applicazione globale di un profilo immagine Dynamic Media {#applying-an-image-profile-globally}

Oltre ad applicare un profilo a una cartella, puoi anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse in una cartella sia applicato il profilo selezionato.

**Applicazione globale di un profilo immagine Dynamic Media**:

1. Effettua una delle operazioni seguenti:

   * Passa a **https://&lt;aem server=&quot;&quot;>/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam** e applica il profilo appropriato e tocca **Salva**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Passa a CRXDE Lite al seguente nodo: `/content/dam/jcr:content`.

      Aggiungi la proprietà `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` e toccare **[!UICONTROL Salva tutto]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Modifica del ritaglio avanzato o del campione avanzato di una singola immagine {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!NOTE]
>
>Smart Crop è disponibile solo in modalità Dynamic Media - Scene7.

È possibile riallineare o ridimensionare manualmente la finestra di ritaglio avanzato di un’immagine per perfezionarne ulteriormente il punto focale.

Dopo aver modificato e salvato un ritaglio avanzato, la modifica viene propagata ovunque si utilizzi il ritaglio per le immagini specifiche.

Se necessario, potete eseguire nuovamente il ritaglio avanzato per generare di nuovo il raccolto aggiuntivo.

Vedi anche [Modifica del ritaglio avanzato o del campione avanzato di più immagini](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Per modificare il ritaglio avanzato o il campione avanzato di una singola immagine**:

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Risorse]**, quindi alla cartella a cui è applicato un profilo immagine di ritaglio avanzato o campione avanzato.

1. Tocca la cartella per aprirne il contenuto.
1. Toccate l’immagine di cui desiderate regolare il ritaglio avanzato o il campione avanzato.
1. Nella barra degli strumenti, tocca **[!UICONTROL Ritaglio avanzato]**.

1. Effettua una delle operazioni seguenti:

   * Nell’angolo in alto a destra della pagina, trascinate la barra di scorrimento verso sinistra o verso destra per aumentare o diminuire rispettivamente la visualizzazione dell’immagine.
   * Sull&#39;immagine, trascinate una maniglia d&#39;angolo per regolare le dimensioni dell&#39;area visibile del ritaglio o del campione.
   * Sull’immagine, trascinate la casella o il campione in una nuova posizione. È possibile modificare solo i campioni immagine; i campioni colore sono statici.
   * Sopra l’immagine, tocca  **[!UICONTROL Ripristina]** per annullare tutte le modifiche e ripristinare il ritaglio o il campione originale.

1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]**, quindi tocca **[!UICONTROL Chiudi]** per tornare alla cartella delle risorse.

## Modifica del ritaglio avanzato o del campione avanzato di più immagini {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Dopo aver applicato un profilo immagine contenente Smart Crop a una cartella, a tutte le immagini in essa contenute viene applicato un ritaglio. Se lo desideri, puoi *manuale* riallineare o ridimensionare la finestra di ritaglio avanzato in più immagini per perfezionare ulteriormente il punto focale.

Dopo aver modificato e salvato un ritaglio avanzato, la modifica viene propagata ovunque si utilizzi il ritaglio per le immagini specifiche.

Se necessario, potete eseguire nuovamente il ritaglio avanzato per generare di nuovo il raccolto aggiuntivo.

**Per modificare il ritaglio avanzato o il campione avanzato di più immagini**:

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Risorse]**, quindi a una cartella a cui è applicato un profilo immagine di ritaglio avanzato o campione avanzato.
1. Nella cartella, tocca **[!UICONTROL Altre azioni]** icona (..), quindi tocca **[!UICONTROL Ritaglio avanzato]**.

1. Sulla **[!UICONTROL Modifica ritaglio avanzato]** eseguire una delle operazioni seguenti:

   * Regola le dimensioni di visualizzazione delle immagini sulla pagina.

      A destra dell’elenco a discesa Nome punto di interruzione , trascina la barra di scorrimento a sinistra o a destra per modificare le dimensioni della visualizzazione dell’immagine visualizzabile.

      ![edit_smart_crop-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtra l’elenco delle immagini visualizzabili in base ai nomi dei punti di interruzione. Nell’esempio seguente, le immagini vengono filtrate sul nome del punto di interruzione &quot;Medium&quot;.

      Seleziona un nome di punto di interruzione dall’elenco a discesa nell’angolo in alto a destra della pagina per filtrare le immagini visualizzate. (Vedi l&#39;immagine qui sopra).

      ![edit_smart_crop-elenco a discesa](assets/edit_smart_crops-dropdownlist.png)

   * Ridimensiona la casella di ritaglio avanzato. Effettua una delle seguenti operazioni:

      * Se l’immagine presenta solo un ritaglio avanzato o un campione avanzato, trascinate sull’immagine la maniglia d’angolo della casella di ritaglio per regolare le dimensioni dell’area visibile del ritaglio.
      * Se l’immagine presenta sia un ritaglio avanzato che un campione avanzato, trascinate sull’immagine la maniglia d’angolo della casella di ritaglio per regolare le dimensioni dell’area visibile del ritaglio. Oppure, tocca o fai clic sul campione avanzato sotto l’immagine (i campioni colore sono statici), quindi trascina la maniglia d’angolo della casella di ritaglio per regolare le dimensioni dell’area visibile del campione.

      ![Ridimensionamento del ritaglio avanzato di un’immagine.](assets/edit_smart_crops-resize.png)

   * Spostate la casella di ritaglio avanzato. Effettua una delle seguenti operazioni:

      * Se l’immagine dispone solo di un ritaglio avanzato o di un campione avanzato, trascinate la casella di ritaglio in una nuova posizione.
      * Se l’immagine presenta sia un ritaglio avanzato che un campione avanzato, trascinate la casella di ritaglio avanzato in una nuova posizione. Oppure, tocca il campione avanzato sotto l’immagine (i campioni colore sono statici), quindi trascina la casella di ritaglio campione avanzato in una nuova posizione.

      ![edit_smart_crop-move](assets/edit_smart_crops-move.png)

   * Annulla tutte le modifiche e ripristina il ritaglio avanzato o il campione avanzato originale (applicabile solo alla sessione di modifica corrente).

      Tocca **[!UICONTROL Ripristina]** sopra l&#39;immagine.

      ![edit_smart_crop-revert](assets/edit_smart_crops-revert.png)



1. Nell’angolo in alto a destra della pagina, tocca **[!UICONTROL Salva]**. quindi tocca **[!UICONTROL Chiudi]** per tornare alla cartella delle risorse.

## Rimozione di un profilo immagine dalle cartelle {#removing-an-image-profile-from-folders}

Quando rimuovi un profilo immagine da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla relativa cartella principale. Tuttavia, l’elaborazione dei file che si è verificata all’interno delle cartelle rimane intatta.

Puoi rimuovere un profilo immagine da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come rimuovere i profili immagine dalle cartelle con entrambe le soluzioni.

### Rimozione di profili immagine Dynamic Media dalle cartelle tramite l’interfaccia utente Profili {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Tocca il logo AEM e naviga fino a **[!UICONTROL Strumenti > Risorse > Profili immagine]**.
1. Seleziona il profilo immagine da rimuovere da una o più cartelle.
1. Tocca **[!UICONTROL Rimuovi profilo elaborazione da cartelle]** e seleziona una o più cartelle da cui vuoi rimuovere il profilo, infine tocca **[!UICONTROL Rimuovi]**.

   Puoi confermare che il profilo immagine non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimozione di profili immagine Dynamic Media dalle cartelle tramite Proprietà {#removing-image-profiles-from-folders-via-properties}

1. Tocca il logo AEM e naviga **[!UICONTROL Risorse]** e quindi alla cartella da cui si desidera rimuovere un profilo immagine.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.
1. Seleziona la **[!UICONTROL Profili immagine]** scheda .
1. Da **[!UICONTROL Nome profilo]** elenco a discesa, seleziona **[!UICONTROL Nessuno]**, quindi tocca **[!UICONTROL Salva e chiudi]**.

   Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.
