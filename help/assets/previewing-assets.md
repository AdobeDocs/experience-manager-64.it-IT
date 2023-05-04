---
title: Anteprima delle risorse Dynamic Media
seo-title: Previewing Dynamic Media assets
description: Scopri come visualizzare in anteprima le risorse in Dynamic Media
seo-description: Learn how to preview assets in Dynamic Media
uuid: f0ff2fc4-a263-4dbe-ba46-b07077b49ae0
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 77296bff-8429-4240-af93-26076ae431ec
exl-id: ec05569a-6449-4430-9b9f-7ab051f44970
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 5%

---

# Anteprima delle risorse Dynamic Media {#previewing-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile utilizzare **[!UICONTROL Anteprima]** per vedere l’aspetto di una risorsa digitale Dynamic Media quando viene visualizzata da un cliente nel proprio browser web. Il visualizzatore predefinito incorporato per più dispositivi assegnato alla risorsa viene utilizzato per **[!UICONTROL Anteprima]**.

Un visualizzatore è una raccolta di varie impostazioni o &quot;predefiniti&quot;, come le dimensioni dello schermo del visualizzatore, il comportamento dello zoom, le combinazioni di colori, i bordi, i font e così via, che determinano il modo in cui gli utenti visualizzano le risorse multimediali sullo schermo del computer e sui dispositivi mobili.

Oltre a utilizzare la funzione di anteprima dedicata per video, set 360 gradi e set di immagini, puoi anche visualizzare in anteprima una risorsa utilizzando i predefiniti visualizzatore che hai creato. Oppure, utilizza i predefiniti immagine per visualizzare in anteprima le rappresentazioni delle immagini.

* [Applicazione dei predefiniti per immagini](image-presets.md)
* [Applicazione dei predefiniti per visualizzatori](viewer-presets.md)

>[!NOTE]
>
>Quando ti trovi su una pagina web (Sites) in AEM, non puoi visualizzare in anteprima le risorse in modalità **[!UICONTROL Modifica]**. Per passare alla modalità **[!UICONTROL Anteprima]**, nell’angolo in alto a destra fai clic su **Anteprima**.

**Per visualizzare in anteprima le risorse**:

1. Da **Adobe Experience Manager**, sul **[!UICONTROL Navigazione]** pagina, tocca **[!UICONTROL Risorsa]s**, quindi **[!UICONTROL File]** per accedere alle risorse.
1. Vicino all’angolo superiore destro della pagina, dal **[!UICONTROL Visualizza]** elenco a discesa, tocca **[!UICONTROL Vista a elenco]**.
1. (Facoltativo) Utilizza il **[!UICONTROL Tipo]** per ordinare le risorse in base al tipo da visualizzare in anteprima.
1. Sotto la **[!UICONTROL Titolo]** fai clic sul nome del titolo (non sulla miniatura) della risorsa da visualizzare in anteprima.
1. A seconda del tipo di risorsa su cui hai fatto clic, effettua una delle seguenti operazioni:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo di risorsa toccato</strong><br /> </td> 
   <td><strong>In grado di visualizzare in anteprima la risorsa in un rendering specifico?</strong></td> 
   <td><strong>In grado di visualizzare in anteprima la risorsa in un particolare visualizzatore?</strong></td> 
  </tr>
  <tr>
   <td><p>Immagine</p> </td> 
   <td>Sì</td> 
   <td>Sì</td> 
   <td><p><strong>Visualizzazione in anteprima della risorsa in un rendering specifico</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Rendering </strong>dall’elenco, selezionare un rendering specifico da visualizzare in anteprima.</li> 
    </ul> <p><strong>Per visualizzare in anteprima la risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Visualizzatori</strong> dall’elenco, seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Utilizza la <strong>+</strong> e <strong>- </strong>per aumentare o diminuire lo zoom dell’immagine selezionata, rispettivamente. Fai clic su <strong>Reimposta</strong> per ripristinare l'immagine allo zoom originale.<br /> Se utilizzi un dispositivo mobile, tocca due volte l’immagine per ingrandire di passaggio. Quando raggiungete lo zoom massimo, toccate nuovamente l’immagine per ripristinare lo stato di zoom. Trascina l’immagine per eseguire il panning.</p> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.<br /> </p> </td> 
  </tr>
  <tr>
   <td>File multimediali</td> 
   <td>Sì</td> 
   <td>Sì</td> 
   <td><p><strong>Visualizzazione in anteprima della risorsa in un rendering specifico</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Rendering </strong>dall’elenco, selezionare un rendering specifico da visualizzare in anteprima.</li> 
    </ul> <p>Selezionando un rendering video a risoluzione più elevata per l'anteprima, il video potrebbe apparire troncato. Questo perché l’anteprima del rendering mostra la risoluzione esatta che i clienti vedranno, il tutto nel contesto del visualizzatore incorporato utilizzato per l’anteprima.</p> <p>Quando visualizzi l’anteprima di un set di video adattivo a livello di risorsa, le rappresentazioni vengono raggruppate in un’unica esperienza di riproduzione. In altre parole, il video adattivo viene ridimensionato correttamente per la visualizzazione e la riproduzione utilizzando la migliore risoluzione nel contesto del dispositivo di visualizzazione e della velocità di connessione.<br /> </p> <p><strong>Per visualizzare in anteprima una risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Visualizzatori</strong> dall’elenco, seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.</p> </td> 
  </tr>
  <tr>
   <td>Set immagini</td> 
   <td>No</td> 
   <td>Sì</td> 
   <td><p><strong>Per visualizzare in anteprima una risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Visualizzatori</strong> dall’elenco, seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Utilizza la <strong>+</strong> e <strong>- </strong>per aumentare o diminuire lo zoom dell’immagine selezionata, rispettivamente. Fai clic su <strong>Reimposta</strong> per ripristinare l'immagine allo zoom originale.<br /> Se utilizzi un dispositivo mobile, tocca due volte l’immagine per ingrandire di passaggio. Quando raggiungete lo zoom massimo, toccate nuovamente l’immagine per ripristinare lo stato di zoom. Trascina l’immagine per eseguire il panning.</p> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.</p> </td> 
  </tr>
  <tr>
   <td>Set 360 gradi</td> 
   <td>No</td> 
   <td>Sì</td> 
   <td><p><strong>Per visualizzare in anteprima una risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Visualizzatori</strong> dall’elenco, seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Utilizza la <strong>+</strong> e <strong>- </strong>per aumentare o diminuire lo zoom dell’immagine selezionata, rispettivamente. Fai clic su <strong>Reimposta</strong> per ripristinare l'immagine allo zoom originale.<br /> Se utilizzi un dispositivo mobile, tocca due volte l’immagine per ingrandire di passaggio. Quando raggiungete lo zoom massimo, toccate nuovamente l’immagine per ripristinare lo stato di zoom. Trascina l’immagine per eseguire il panning.</p> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.</p> </td> 
  </tr>
  <tr>
   <td>Set di file multimediali diversi</td> 
   <td>No</td> 
   <td>Sì</td> 
   <td><p><strong>Per visualizzare in anteprima una risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Fai clic su <strong>Visualizzatori</strong> dall’elenco, seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Utilizza la <strong>+</strong> e <strong>- </strong>per aumentare o diminuire lo zoom dell’immagine selezionata, rispettivamente. Fai clic su <strong>Reimposta</strong> per ripristinare l'immagine allo zoom originale.<br /> Se utilizzi un dispositivo mobile, tocca due volte l’immagine per ingrandire di passaggio. Quando raggiungete lo zoom massimo, toccate nuovamente l’immagine per ripristinare lo stato di zoom. Trascina l’immagine per eseguire il panning.</p> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.</p> </td> 
  </tr>
  <tr>
   <td>Set carosello</td> 
   <td>No</td> 
   <td>Sì</td> 
   <td><p><strong>Per visualizzare in anteprima una risorsa in un particolare visualizzatore</strong></p> 
    <ul> 
     <li>Fai clic sull’icona nell’angolo in alto a sinistra della pagina per visualizzare l’elenco a discesa. Seleziona un visualizzatore da applicare alla risorsa.</li> 
    </ul> <p>Per abilitare o disabilitare i predefiniti visualizzatore nell’interfaccia utente, vedi <a href="/help/assets/managing-viewer-presets.md">Gestione dei predefiniti per visualizzatori</a>.</p> </td> 
  </tr>
 </tbody>
</table>
