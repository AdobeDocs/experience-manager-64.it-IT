---
title: 'Differenza tra le funzioni dei moduli HTML5 e dei moduli PDF '
seo-title: 'Differenza tra le funzioni dei moduli HTML5 e dei moduli PDF '
description: Funzionalità supportate nei moduli HTML5 e PDF
seo-description: Funzionalità supportate nei moduli HTML5 e PDF
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Differenza tra le funzioni dei moduli HTML5 e dei moduli PDF {#feature-differentiation-between-html-forms-and-pdf-forms}

La tabella seguente specifica la funzione di supporto fornita per i moduli HTML5 e PDF:

<table> 
 <tbody>
  <tr>
   <th>Funzione</th> 
   <th>Moduli HTML5</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Codici a barre<br /> </td> 
   <td>Non disponibile a livello di interfaccia utente. </td> 
   <td>Supportato</td> 
  </tr>
  <tr>
   <td>Campo firma<br /> </td> 
   <td><strong>Le firme</strong> digitali non sono supportate, ma è stato aggiunto un nuovo campo <strong>Firma</strong> scarabocchio per le firme cartacee. È possibile creare uno script per la firma sul modulo utilizzando il campo <strong>Firma</strong> scarabocchio. La firma viene salvata nel modulo come immagine. È possibile salvare le informazioni sulla geolocalizzazione nel campo <strong>Firma</strong> scarabocchio.</td> 
   <td>Campo firma disponibile per <strong>Digital Signatures</strong>.</td> 
  </tr>
  <tr>
   <td>Unione dati</td> 
   <td>Supportato</td> 
   <td>Supportato</td> 
  </tr>
  <tr>
   <td>Immagini</td> 
   <td>Lo schema URI dati viene utilizzato per visualizzare le immagini. Tutte le versioni moderne dei browser supportano questo schema, ma esistono differenze nella gamma di formati di immagine supportati da ciascun browser.<br /> </td> 
   <td>Sono supportati i formati .gif, .png, .jpeg, .bmp e .tiff.</td> 
  </tr>
  <tr>
   <td>Paginazione<br /> </td> 
   <td><p>Un modulo HTML5 è suddiviso in pannelli e caselle per conferirgli un aspetto simile ai moduli PDF. Le dimensioni della pagina vengono calcolate in modo dinamico. Se tutti i contenuti di una pagina in un modulo HTML5 vengono eliminati o contrassegnati come nascosti, la pagina vuota viene nascosta e non viene visualizzato uno spazio vuoto (spazio vuoto) tra le pagine sopra e sotto la pagina vuota.</p> <p>Se l'unione dei dati o gli script aggiungono contenuto a una pagina, la lunghezza della pagina si espande per adattarsi al contenuto appena aggiunto. Al modulo non vengono aggiunte nuove pagine per contenere il contenuto appena aggiunto. </p> <p><strong>Nota:</strong> Quando tutti i contenuti di una pagina in un modulo HTML5 vengono eliminati o contrassegnati come nascosti, la pagina vuota (spazio vuoto) rimane visibile tra la prima e la seconda pagina, ma non tra le altre.</p> </td> 
   <td>L'impaginazione in PDF dipende dal contenuto dei dati unito o contenuto utente e il conteggio delle pagine viene aumentato o ridotto in base a tale contenuto.</td> 
  </tr>
  <tr>
   <td>Intestazioni/Piè di pagina </td> 
   <td>Supportato. <br /> <br /> Poiché i moduli mobili HTML5 non supportano le interruzioni di pagina, le intestazioni e i piè di pagina vengono visualizzati solo una volta. Tuttavia, è possibile impostarle nel layout in modo che vengano visualizzate in più posizioni nell'anteprima dei moduli per dispositivi mobili.<br /> </td> 
   <td>Supportato.</td> 
  </tr>
  <tr>
   <td>Widget personalizzati</td> 
   <td>È possibile personalizzare i widget per migliorare l'esperienza utente sui dispositivi mobili.<br /> </td> 
   <td>Tutti i widget sono bloccati e non è possibile collegare alcun widget personalizzato.<br /> </td> 
  </tr>
  <tr>
   <td>API script XFA</td> 
   <td>Supporta i costrutti di script XFA più comunemente utilizzati. Per un elenco dettagliato dei costrutti supportati, vedere <a href="/help/forms/using/scripting-support.md">Supporto</a>script.</td> 
   <td>Supporta tutti i costrutti di script XFA.</td> 
  </tr>
  <tr>
   <td>API di Acrobat Script </td> 
   <td>I moduli HTML5 supportano le API più utilizzate. Per informazioni dettagliate, vedere <a href="/help/forms/using/scripting-support.md">Supporto</a>per gli script.</td> 
   <td>Se il file PDF viene aperto in Acrobat o Reader, supporta anche tutte le API di script fornite da Acrobat.</td> 
  </tr>
  <tr>
   <td>Supporto delle lingue da destra a sinistra </td> 
   <td>Supportato</td> 
   <td>Supportato</td> 
  </tr>
 </tbody>
</table>

Seguire le procedure ottimali per abilitare un modello di modulo per le rappresentazioni HTML5 e assicurarsi che il comportamento e l&#39;aspetto dei moduli HTML5 e dei PDF basati su XFA siano coerenti. Per un elenco dettagliato delle procedure ottimali, vedere Procedure [consigliate per progettare un modulo HTML5.](/help/forms/using/best-practices-for-html5-forms.md)

