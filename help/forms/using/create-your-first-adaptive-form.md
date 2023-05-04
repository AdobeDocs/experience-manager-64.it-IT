---
title: Creare il primo modulo adattivo
seo-title: Create your first adaptive form
description: Scopri come creare moduli interattivi, di classe aziendale e reattivi.
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 1%

---

# Creare il primo modulo adattivo {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Introduzione {#introduction}

Stai cercando un mobile-friendly **esperienza dei moduli** che semplifica l&#39;iscrizione, aumenta l&#39;impegno e riduce i tempi di consegna, **moduli adattivi** È una vestibilità perfetta per te. I moduli adattivi offrono un’esperienza mobile, automatizzata e con moduli compatibili con le analisi. È possibile creare facilmente moduli di natura reattiva e interattiva, utilizzare processi automatizzati per ridurre le attività amministrative e ripetitive e utilizzare l’analisi dei dati per migliorare e personalizzare l’esperienza dei clienti con i moduli.

Questa esercitazione fornisce un framework end-to-end per creare un modulo adattivo. L’esercitazione è organizzata in un caso d’uso e in più guide. Ogni guida è utile per apprendere e aggiungere nuove funzioni al modulo adattivo creato in questa esercitazione. Hai un modulo adattivo funzionante dopo ogni guida. È disponibile la guida per la creazione di un modulo adattivo . Le guide successive saranno presto disponibili. Al termine di questa esercitazione, potrai:

* Creare un modello di dati modulo adattivo e modulo.
* Assegna uno stile al modulo adattivo.
* Utilizza l’editor di regole del modulo adattivo per creare regole aziendali.
* Test e pubblicazione di un modulo adattivo.

![creazione-adattamento-modulo-workflow](assets/create-daptive-form-workflow.png)

Il percorso inizia con l’apprendimento del caso d’uso:

Un sito web offre una gamma di prodotti per diversi clienti. I clienti navigano nel portale, selezionano e ordinano i prodotti. Ogni cliente crea un account e fornisce indirizzi di spedizione e fatturazione. Una cliente esistente, Sara Rose, sta cercando di aggiungere il suo indirizzo di spedizione al sito web. Il sito web fornisce un modulo online per aggiungere e aggiornare gli indirizzi di spedizione.

Il sito web viene eseguito su Adobe Experience Manager (AEM) e utilizza AEM Forms per l’acquisizione e l’elaborazione dei dati. Il modulo di aggiunta e aggiornamento dell’indirizzo è un modulo adattivo. Il sito web memorizza i dettagli dei clienti in un database. Utilizzano il modulo di aggiunta e aggiornamento dell’indirizzo per recuperare e visualizzare gli indirizzi disponibili. Utilizzano anche il modulo adattivo per accettare indirizzi nuovi e aggiornati.

### Prerequisito {#prerequisite}

* Imposta un&#39;istanza di authoring AEM.
* Installa [Componente aggiuntivo AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) sull’istanza di authoring.
* Ottenere il driver del database JDBC (file JAR) dal provider del database. Gli esempi nell&#39;esercitazione sono basati sul database MySQL e utilizzano Oracle [Driver del database JDBC MySQL](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Imposta un database contenente i dati del cliente con i campi visualizzati di seguito. Un database non è essenziale per creare un modulo adattivo. Questa esercitazione utilizza un database per visualizzare il modello dati del modulo e le funzionalità di persistenza di AEM Forms.

![adaptiveformdata](assets/adaptiveformdata.png)

## Passaggio 1: Creare un modulo adattivo {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

I moduli adattivi sono di nuova generazione, coinvolgenti, reattivi, dinamici e adattivi in natura. Utilizzando i moduli adattivi, puoi fornire esperienze personalizzate e mirate. AEM Forms fornisce un editor WYSIWYG con trascinamento per creare moduli adattivi. Per ulteriori informazioni sui moduli adattivi, consulta [Introduzione alla creazione di moduli adattivi](/help/forms/using/introduction-forms-authoring.md).

Obiettivi:

* Creare un modulo adattivo che consenta a un cliente di aggiungere un indirizzo di spedizione
* Layout dei campi di un modulo adattivo per visualizzare e accettare le informazioni di un cliente
* Creare un’azione di invio per inviare un’e-mail contenente il contenuto del modulo
* Anteprima e invio di un modulo adattivo

[ ](create-adaptive-form.md)

## Passaggio 2: Crea modello dati modulo {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Un modello di dati modulo consente di collegare un modulo adattivo a diverse origini dati. Ad esempio, AEM profilo utente, servizi web RESTful, servizi web basati su SOAP, servizi OData e database relazionali. Un modello dati Modulo è uno schema di rappresentazione dei dati unificato delle entità e dei servizi aziendali disponibili nelle origini dati connesse. È possibile utilizzare il modello dati del modulo con un modulo adattivo per recuperare, aggiornare, eliminare e aggiungere dati alle origini dati connesse.

Obiettivi:

* Configurare l&#39;istanza di database del sito Web (database MySQL) come origini dati
* Creare il modello dati del modulo utilizzando il database MySQL come origine dati
* Aggiunta di oggetti del modello dati al modello dati del modulo
* Configurare i servizi di lettura e scrittura per il modello dati del modulo
* Verificare il modello dati del modulo e i servizi configurati con i dati di prova

[ ](create-form-data-model.md)

## Passaggio 3: Applicazione di regole ai campi del modulo adattivo {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

I moduli adattivi forniscono un editor per la scrittura di regole sugli oggetti modulo adattivi. Queste regole definiscono le azioni da eseguire sugli oggetti modulo in base a condizioni preimpostate, input dell’utente e azioni dell’utente sul modulo. Consente di garantire l’accuratezza e di accelerare l’esperienza di compilazione dei moduli.

Obiettivi:

* Creazione e applicazione di regole ai campi del modulo adattivo
* Utilizzare le regole per attivare i servizi del modello dati modulo per aggiornare i dati al database

## Passaggio 4: Personalizzare lo stile del modulo adattivo {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

I moduli adattivi forniscono temi e [editor](/help/forms/using/themes.md) per creare temi per i moduli adattivi. Un tema contiene dettagli di stile per componenti e pannelli e può essere riutilizzato in diversi moduli. Gli stili includono proprietà quali colori di sfondo, colori dello stato, trasparenza, allineamento e dimensioni. Quando si applica il tema al modulo, lo stile specificato si riflette sui componenti corrispondenti del modulo. I moduli adattivi supportano anche lo stile in linea per gli stili specifici di un modulo.

Obiettivi:

* Applicare un tema preconfigurato a un modulo adattivo
* Creare un tema per un modulo adattivo utilizzando l’editor di temi
* Utilizzare i font web in un tema personalizzato

[ ](style-your-adaptive-form.md)

## Passaggio 5: Test del modulo adattivo {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

I moduli adattivi sono parte integrante delle interazioni dei clienti. È importante testare i moduli adattivi con ogni modifica apportata. Il test di ogni campo di un modulo è noioso. AEM Forms fornisce un SDK (Calvin SDK) per automatizzare il test dei moduli adattivi. Calvin consente di automatizzare i test dei moduli adattivi nel browser web.

Obiettivi:

* Installa Calvin SDK
* Crea suite di test e casi di test per il modulo per l’indirizzo di modifica

Per informazioni sull&#39;SDK, vedi [Utilizzo di test automatici con AEM modulo adattivo](/help/forms/using/calvin.md).

## Passaggio 6: Pubblicare il modulo adattivo {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

È possibile pubblicare moduli adattivi come modulo autonomo (applicazione a pagina singola), incluso in AEM [pagina dei siti](/help/forms/using/embed-adaptive-form-aem-sites.md)o su un sito AEM utilizzando [Portale Forms](/help/forms/using/introduction-publishing-forms.md).

Obiettivi:

* Pubblicare il modulo adattivo come applicazione a pagina singola
