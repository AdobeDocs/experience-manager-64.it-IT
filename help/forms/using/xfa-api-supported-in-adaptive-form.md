---
title: Supporto XFA nei moduli adattivi basati su XDP
seo-title: XFA support in XDP-based adaptive forms
description: Elenca gli eventi XFA supportati, le proprietà, gli script e la convalida nei moduli adattivi.
seo-description: Lists supported XFA events, properties, scripts, and validation in adaptive forms.
uuid: 2f976de3-2cdf-4bbb-acd1-048a498930f0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: eaf60421-097e-4feb-b661-433a512470ab
feature: Adaptive Forms
exl-id: 86596819-8108-409e-af14-4634e8a1959d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 6%

---

# Supporto XFA nei moduli adattivi basati su XDP {#xfa-support-in-xdp-based-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

I moduli adattivi supportano vari eventi, proprietà, script e convalide XFA definiti in un file XDP, tra cui:

* Esecuzione di script definiti su eventi nel file XDP.
* Acquisizione dei valori predefiniti e delle proprietà comportamentali per i campi nel file XDP.
* Esecuzione degli script di convalida definiti nel file XDP.

Quando si crea un modulo adattivo basato su un file XDP, le proprietà, gli eventi e le convalide vengono compilati automaticamente nell’interfaccia utente di creazione del modulo. Tuttavia, gli autori dei moduli possono ignorare alcuni di questi elementi per creare un’esperienza alternativa.

Questo articolo elenca gli eventi, le proprietà e le convalide XFA supportati nei moduli adattivi e spiega come sostituirli nei moduli adattivi.

## Elementi XFA supportati e loro mappatura nei moduli adattivi {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Campi {#fields}

Quando si crea un modulo adattivo utilizzando un file XDP, è possibile trascinare un campo XFA nel modulo adattivo. La tabella seguente elenca il modo in cui i campi XFA vengono mappati ai campi del modulo adattivo.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Campo o contenitore XFA</strong></p> </td> 
   <td><p><strong>Componente modulo adattivo corrispondente</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Pulsante </p> </td> 
   <td><p>Pulsante</p> </td> 
  </tr>
  <tr>
   <td><p>Casella di controllo </p> </td> 
   <td><p>Casella di controllo</p> </td> 
  </tr>
  <tr>
   <td><p>Casella di riepilogo </p> </td> 
   <td><p>Elenco a discesa</p> </td> 
  </tr>
  <tr>
   <td><p>Campo data/ora </p> </td> 
   <td><p>Selettore data</p> </td> 
  </tr>
  <tr>
   <td><p>Firma</p> </td> 
   <td><p>Firma a mano</p> </td> 
  </tr>
  <tr>
   <td><p>Campo numerico </p> </td> 
   <td><p>Casella numerica</p> </td> 
  </tr>
  <tr>
   <td><p>Campo decimale</p> </td> 
   <td><p>Casella numerica</p> </td> 
  </tr>
  <tr>
   <td><p>Campo testo </p> </td> 
   <td><p>Casella di testo</p> </td> 
  </tr>
  <tr>
   <td><p>Campo password </p> </td> 
   <td><p>Casella password</p> </td> 
  </tr>
  <tr>
   <td><p>Immagine</p> </td> 
   <td><p>Immagine</p> </td> 
  </tr>
  <tr>
   <td><p>Testo</p> </td> 
   <td><p>Testo</p> </td> 
  </tr>
  <tr>
   <td><p>Sottomodulo </p> </td> 
   <td><p>Pannello</p> </td> 
  </tr>
  <tr>
   <td><p>Area (gruppo)</p> </td> 
   <td><p>Pannello</p> </td> 
  </tr>
  <tr>
   <td><p>Set sottomodulo </p> </td> 
   <td><p>Pannello</p> </td> 
  </tr>
 </tbody>
</table>

### Proprietà {#properties}

La tabella seguente acquisisce il comportamento dei vari script XFA definiti nei file XDP nei moduli adattivi.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Proprietà dei componenti XFA</strong></p> </td> 
   <td><p><strong>Comportamento corrispondente nei moduli adattivi</strong></p> </td> 
  </tr>
  <tr>
   <td><p>somExpression </p> </td> 
   <td><p>Mappata alla proprietà Bind reference (bindRef) in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>presenza </p> </td> 
   <td><p>Mappata alla proprietà visibile in modulo adattivo. È possibile sostituirlo utilizzando l’espressione Visibility.</p> </td> 
  </tr>
  <tr>
   <td><p>accesso </p> </td> 
   <td><p>Mappata alla proprietà abilitata in modulo adattivo. È possibile sostituirlo utilizzando l'espressione Access.</p> </td> 
  </tr>
  <tr>
   <td><p>Accessibilità: ruolo </p> </td> 
   <td><p>Mappata alla proprietà role in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>Accessibilità: speakPriority </p> </td> 
   <td><p>Mappata alla proprietà speakPriority in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>Accessibilità: speakText</p> </td> 
   <td><p>Mappata al testo di accessibilità personalizzato in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>Accessibilità: toolTip </p> </td> 
   <td><p>Mappata alla proprietà short description in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>didascalia<em> (tutti i tipi di campo)</em></p> </td> 
   <td><p>Mappata alla proprietà Titolo in modulo adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>displayFormat<em> (tutti i tipi di campo)</em></p> </td> 
   <td><p>Mappata al pattern di visualizzazione in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>rawValue<em> (tutti i tipi di campo)</em></p> </td> 
   <td><p>Mappata alla proprietà value in Modulo adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>items<em> (Casella Di Riepilogo, Casella Di Controllo)</em></p> </td> 
   <td><p>Mappata alla proprietà options in forma adattiva. È possibile sostituirlo utilizzando l'espressione Options.</p> </td> 
  </tr>
  <tr>
   <td><p>maxChar<em> (Campo di testo)</em></p> </td> 
   <td><p>Mappata alla proprietà Numero massimo di caratteri consentiti in modulo adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>multilingue<em> (Campo di testo)</em></p> </td> 
   <td><p>Mappata alla proprietà Consenti righe multiple in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>fracDigit<em> (Campo numerico, Campo decimale)</em></p> </td> 
   <td><p>Mappata alla proprietà Frac cifre in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>leadDigit<em> (Campo numerico, Campo decimale)</em></p> </td> 
   <td><p>Mappata alla proprietà Cifre lead in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>multiSelect<em> (Casella di riepilogo)</em></p> </td> 
   <td><p>Mappata alla proprietà Permette più selezioni in forma adattiva.</p> </td> 
  </tr>
 </tbody>
</table>

### Script {#scripts}

La tabella seguente acquisisce il comportamento dei vari script XFA definiti nel file XDP nei moduli adattivi.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Eventi script XFA</strong></p> </td> 
   <td><p><strong>Comportamento corrispondente nei moduli adattivi</strong></p> </td> 
  </tr>
  <tr>
   <td><p>initialize </p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>calculate</p> </td> 
   <td><p>Mappata all’espressione Calculate in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>validate </p> </td> 
   <td><p>Mappata all'espressione Validation in forma adattiva.</p> </td> 
  </tr>
  <tr>
   <td><p>validationState </p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.<br /> </p> </td> 
  </tr>
  <tr>
   <td><p>uscire </p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>fai clic su (campi pulsante)</p> </td> 
   <td><p>Mappata all’espressione Click del pulsante.</p> </td> 
  </tr>
  <tr>
   <td><p>Supporto per script sul lato server</p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>Supporto per i servizi web</p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.</p> </td> 
  </tr>
  <tr>
   <td><p>Modifica (campo scarabocchio, pulsante di scelta, casella di controllo)</p> </td> 
   <td><p>Questo script viene eseguito in fase di runtime e non può essere ignorato in formato adattivo.</p> </td> 
  </tr>
 </tbody>
</table>

### Convalida {#validations}

Nella tabella seguente viene illustrato come le convalide XFA vengono associate alle convalide nei moduli adattivi.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Convalida XFA</strong></p> </td> 
   <td><p><strong>Convalida corrispondente nel modulo adattivo</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Pattern di convalida (formatTest)</p> </td> 
   <td><p>validatePictureClause</p> </td> 
  </tr>
  <tr>
   <td><p>Messaggio pattern convalida (formatTestMessage)</p> </td> 
   <td><p>validatePictureMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Obbligatorio (nullTest )</p> </td> 
   <td><p>obbligatorio </p> </td> 
  </tr>
  <tr>
   <td><p>Messaggio vuoto (nullTestMessage) </p> </td> 
   <td><p>mandatoryMessage</p> </td> 
  </tr>
  <tr>
   <td><p>Convalida script (scriptTest)</p> </td> 
   <td><p>validateExp</p> </td> 
  </tr>
  <tr>
   <td><p>Messaggio script convalida (scriptTestMessage)</p> </td> 
   <td><p>validateMessage</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Non è possibile ignorare la proprietà obbligatoria per i pulsanti di scelta modulo adattivo e il gruppo di caselle di controllo associati ai pulsanti di controllo XFA.
