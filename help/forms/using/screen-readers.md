---
title: assistenti vocali per moduli HTML5
seo-title: Screen readers for HTML5 forms
description: Elenca gli assistenti vocali supportati con i moduli HTML5.
seo-description: Lists the screen readers supported with HTML5 forms.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: c27eb771-d390-4534-8e67-f1277550e760
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---

# assistenti vocali per moduli HTML5 {#screen-readers-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I componenti dei moduli di HTML5 eseguono il rendering del modello di modulo XFA in un formato HTML5. Tutti i browser standard che supportano HTML5 possono eseguire il rendering di questi moduli. Per supportare un’esperienza di acquisizione dati simile in PDF e HTML5 forms, il layout dei PDF forms viene mantenuto nei moduli HTML5.

I moduli di HTML5 utilizzano costrutti standard di HTML che consentono l’utilizzo di normali strumenti di accesso facilitato per HTML con questi moduli. Se un modulo è progettato in base alle best practice per i moduli con accesso facilitato, funziona con qualsiasi assistente vocale supportato. Inoltre, tali moduli sono abilitati per la navigazione da tastiera.

## Standard di accessibilità {#accessibility-standards}

I moduli di HTML5 sono conformi alla sezione 508 per l’accessibilità, con eccezioni note. Vedi [VPAT per moduli HTML5](https://www.adobe.com/content/dam/cc1/en/accessibility/compliance/pdfs/adobe-livecycle-es4-section-508-vpat-portfolio.pdf) per i dettagli.

## assistenti vocali certificati per moduli HTML5 {#certified-screen-readers-for-html-forms}

* JAWS 14.0 su Microsoft Windows
* VoiceOver su Mac OS X e iPad

### JAWS {#jaws}

Tutte le sequenze di tasti e le scelte rapide predefinite funzionano per i moduli di HTML5. Per ulteriori informazioni sull&#39;utilizzo di JAWS, visita [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/products/software/jaws/).

### VoiceOver {#voiceover}

I moduli di HTML5 supportano tutti i tasti e i gesti predefiniti di Voice over. Per ulteriori informazioni sulla configurazione e sull&#39;utilizzo di VoiceOver, vedi [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Problemi noti {#known-issues}

* **(Solo Internet Explorer 9)** Nei moduli di HTML5, le pagine vengono caricate su richiesta (in modo dinamico). Il caricamento della pagina su richiesta causa problemi con il funzionamento degli assistenti vocali. Quando l’assistente vocale si trova sull’ultimo campo della pagina e l’utente preme il tasto Tab, anziché impostare lo stato attivo sul primo campo della pagina successiva, l’assistente vocale torna a essere attivo sul primo campo della prima pagina del modulo.
* **(Solo Internet Explorer 9)** Il controllo Selezione data nei moduli di HTML5 non è completamente accessibile tramite tastiera. Nel controllo Selettore data, se si premono più volte i tasti Su/Giù, il controllo Selettore data si chiude e lo stato attivo si sposta al campo successivo/ultimo.

* VoiceOver non è in grado di rilevare i tasti freccia nel widget data su iPad safari.
