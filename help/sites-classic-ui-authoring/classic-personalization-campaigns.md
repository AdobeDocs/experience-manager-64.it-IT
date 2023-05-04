---
title: Campaign Management
seo-title: Campaign Management
description: La gestione delle campagne offre agli esperti di marketing digitale l’opportunità di distribuire contenuti personalizzati e creare esperienze dedicate ai visitatori. Ti consente di orchestrare le campagne di marketing attraverso il web, l’e-mail e i servizi mobili, per coinvolgere in tal modo i visitatori.
seo-description: Campaign management provides digital marketers the opportunity to deliver personalized content and so create dedicated experiences for visitors. It allows you to orchestrate your marketing campaigns across the web, email and mobile services and so engage your visitors.
uuid: 202d614b-a607-45de-8c24-1ee66b230315
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e8b70971-4f23-45f8-8c23-e147413243c2
exl-id: 2980ec6d-cdd4-4fbd-b4a4-5e45e4508903
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 3%

---

# Campaign Management{#campaign-management}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La gestione delle campagne offre agli esperti di marketing digitale l’opportunità di distribuire contenuti personalizzati e creare esperienze dedicate ai visitatori.

Ti consente di orchestrare le campagne di marketing attraverso il web, l’e-mail e i servizi mobili, per coinvolgere in tal modo i visitatori. Puoi creare contenuti, segmentare i visitatori, inviare e promuovere contenuti mirati per specifici profili utente e gestire le campagne su più canali.

Questo documento descrive i vari elementi che compongono le campagne. Informazioni più dettagliate sono disponibili nei seguenti documenti:

* [Teaser e strategie](/help/sites-classic-ui-authoring/classic-personalization-campaigns-teasers-strategy.md)
* [Marketing e-mail](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email.md)
* [Pagine di destinazione](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)
* [Offerte Target](/help/sites-classic-ui-authoring/classic-personalization-campaigns-target-offers.md)
* [Utilizzo di Marketing Campaign Manager](/help/sites-classic-ui-authoring/classic-personalization-campaigns-mktg-manager.md)
* [Segmentazione](/help/sites-classic-ui-authoring/classic-personalization-campaigns-segmentation.md)
* [Impostazione della campagna](/help/sites-classic-ui-authoring/classic-personalization-campaigns-setting-up-your.md)

La gestione delle campagne è composta da vari elementi:

* **Marchi**
In AEM, i marchi sono l’unità di livello superiore e costituiscono una raccolta di 
**Campagne**.

* **Campagne**
Una campagna è una raccolta individuale 
**Esperienze**.

* **Esperienze**
Le esperienze sono composte di contenuti mirati, presentati al visitatore all’indirizzo 
**Punti di contatto**. Sono disponibili diversi tipi di esperienza:

   * **Teaser**
      [Pagine/paragrafi teaser](#teasers) sono utilizzati per indirizzare un visitatore specifico **Segmenti** a contenuti incentrati sui loro interessi.

      Le pagine teaser possono:

      * presentare al visitatore una serie di opzioni tra cui scegliere
      * mostrare un solo paragrafo teaser basato sul segmento di visitatori specifico; ad esempio, il paragrafo teaser visualizzato potrebbe dipendere dall’età del visitatore.

      In genere, una pagina teaser è un’azione temporanea che durerà per un determinato periodo di tempo, fino a quando non viene sostituita dalla pagina teaser successiva.

   * **Newsletter**

      [Comunicazioni e-mail](#emailmarketing) sono utilizzati per coinvolgere gli utenti e incoraggiarli a visitare il tuo sito web. In genere si tratta di newsletter, inviate al **Lead** (solitamente raggruppati in **Elenchi**). **Nota:** Adobe non prevede ulteriori miglioramenti di questa funzionalità. Si raccomanda di [sfruttare Adobe Campaign e l’integrazione con AEM](/help/sites-administering/campaign.md).

   * **Adobe Target**

      Questo consente l’integrazione con Adobe Target (precedentemente Test&amp;Target), che offre agli addetti al marketing uno strumento di ottimizzazione per la conversione da siti web, con le funzionalità necessarie per rendere continuamente i contenuti online e le offerte più rilevanti per i loro clienti, con conseguente miglioramento della conversione da visitatore a cliente. Adobe Target offre un’interfaccia intuitiva per la progettazione e l’esecuzione di test, la creazione di segmenti di pubblico e il targeting dei contenuti, il tutto da una singola applicazione.


* **Punti di contatto**

   Questi sono i punti di contatto tra il visitatore e la campagna. I punti di contatto sono collegati alle esperienze create.

   Ad esempio, per i teaser si tratta della pagina di contenuto in cui si trova il paragrafo teaser, mentre per una newsletter si tratta della mailing list.

* **Lead**

   Le informazioni raccolte sui visitatori e su come contattarli costituiscono la base dei lead. **Nota:** Adobe non prevede ulteriori miglioramenti di questa funzionalità.

   Si raccomanda di [sfruttare Adobe Campaign e l’integrazione con AEM](/help/sites-administering/campaign.md).

* **Elenchi**

   I lead sono solitamente raggruppati in elenchi in modo da poter intraprendere azioni collettive su di essi. Nota: **Nota:** Adobe non prevede ulteriori miglioramenti di questa funzionalità.

   Si raccomanda di [sfrutta Adobe Campaign e l’integrazione con AEM.](/help/sites-administering/campaign.md)

* **Segmenti**

   I visitatori del sito hanno interessi e obiettivi diversi quando accedono a un sito. L’analisi in base a fattori come l’attività sul sito web, le informazioni sul profilo registrate e l’attività su altri siti web ti aiuta a definire i segmenti. Il contenuto può quindi essere mirato in modo specifico alle esigenze e agli interessi del visitatore in base ai segmenti a cui corrispondono.

* **MCM**

   La console Marketing Campaign Manager (MCM) consente di accedere a tutte le funzionalità necessarie per creare e controllare campagne, marchi, esperienze, punti contatto, lead, elenchi, segmenti e rapporti.

   È accessibile da varie posizioni (etichettate come **Campagne**) o con, ad esempio, l’URL:

   `http://localhost:4502/libs/mcm/content/admin.html`
