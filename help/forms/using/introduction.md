---
title: Introduzione ai moduli di HTML5
seo-title: Introduction to HTML5 forms
description: HTML5 forms è una nuova funzionalità del software Adobe Experience Manager 6.0 (AEM 6.0) che offre il rendering dei modelli di moduli XFA in formato HTML5.
seo-description: HTML5 forms is a new capability in Adobe Experience Manager 6.0 (AEM 6.0) software that offers rendering of XFA form templates in HTML5 format.
uuid: a68f1ca1-32dd-48f9-9359-8f09abd1c3de
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: b8cd2656-8bc2-4bd7-a3d6-dc76b0a2d429
feature: Mobile Forms
exl-id: c69b5ae6-c5c5-46df-8290-3e41470cd09e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Introduzione ai moduli di HTML5 {#introduction-to-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

HTML5 forms è una nuova funzionalità del software Adobe Experience Manager 6.0 (AEM 6.0) che offre il rendering dei modelli di moduli XFA in formato HTML5. Questa funzionalità consente di eseguire il rendering dei moduli su dispositivi mobili e browser desktop su cui non è supportato PDF basato su XFA. HTML5 forms supporta non solo le funzionalità esistenti dei modelli di modulo XFA, ma aggiunge anche nuove funzionalità per i dispositivi mobili, ad esempio la firma a mano libera.

HTML5 forms genera documenti basati su costrutti standard di HTML5. È possibile visualizzare i moduli di HTML5 in tutti i browser moderni che supportano HTML5. Non è necessario installare alcun plug-in browser aggiuntivo per i browser. Per ulteriori informazioni sui browser supportati, consulta [Piattaforme client supportate](https://adobe.com/go/learn_aemforms_supportedplatforms_63).

![](do-not-localize/mobile_form_on_an_ipad_date_14.png)

## Funzionalità chiave dei moduli HTML5 {#key-capabilities-of-html-forms-br}

* Esegue il rendering dei moduli XFA esistenti in HTML5 supportati su tutti i browser compatibili.
* Utilizza le funzionalità standard di progettazione dei moduli XFA per eseguire il targeting dei moduli per dispositivi mobili.
* Utilizza le funzionalità XFA dinamiche in formato HTML5.
* Utilizza un layout di testo SVG estremamente preciso (SVG 1.1) per adattarlo al layout di testo di PDF.
* Fornisce il supporto per JavaScript e FormCalc.
* assembla in modo dinamico i frammenti in moduli interattivi in base a eventi basati sui dati o all’input dell’utente.
* Fornisce il supporto per CSS personalizzati in modo che l’aspetto dei moduli corrisponda agli standard aziendali.
* Consente ai widget personalizzati di offrire un’esperienza di acquisizione dati avanzata.
* Fornisce supporto per l&#39;integrazione con le app web.

### Pubblicazione multicanale {#multichannel-publishing}

Gli sviluppatori di moduli possono utilizzare un modello XFA per eseguire il rendering dei moduli nei formati PDF e HTML5. Questa funzionalità è utile negli scenari in cui si dispone di un insieme di moduli XFA di grandi dimensioni che richiedono modifiche minime per adattarsi alle pratiche di progettazione dei moduli di HTML5. È possibile eseguire il rendering dei moduli XFA esistenti su HTML5 per eseguire il targeting su diversi dispositivi in cui PDF basato su XFA non è ancora supportato.

## Gestione dei moduli HTML5 {#manage-html-forms}

AEM inoltre fornisce una visualizzazione unificata per elencare e gestire tutti i modelli di modulo utilizzando l’interfaccia utente di AEM Forms. È possibile attivare, disattivare, pubblicare e visualizzare in anteprima i moduli. Per ulteriori informazioni, consulta [Introduzione alla gestione dei moduli](/help/forms/using/introduction-managing-forms.md).

### Personalizzazione Forms {#forms-customization}

HTML5 forms esegue il rendering dei modelli di modulo utilizzando costrutti standard di HTML5. Questo rende semplice personalizzare ed estendere i moduli in formato HTML5 utilizzando tecnologie web, principalmente CSS e JavaScript. È possibile personalizzare facilmente l’aspetto dei widget esistenti, creare widget personalizzati o utilizzare stili personalizzati nei moduli. Per ulteriori informazioni sulla creazione di widget personalizzati e sulla personalizzazione di widget esistenti, consulta [Plug-in di widget personalizzati con HTML5 forms](/help/forms/using/custom-widgets.md).
