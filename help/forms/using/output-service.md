---
title: Servizio di output
seo-title: Output Service
description: Descrive il servizio di output, che fa parte di AEM Document Services
seo-description: Describes Output Service, which is part of AEM Document Services
uuid: acd64bbb-91df-49bc-9216-2e860812bbe9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 8b96ba2d-007e-472a-875f-2caedd35ecf4
exl-id: ccc291fc-f4c5-4d14-816a-c57f56a95663
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 3%

---

# Servizio di output {#output-service}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Il servizio di output è un servizio OSGi che fa parte di AEM Document Services. Il servizio di output supporta vari formati di output e funzioni di progettazione dell’output di AEM Forms Designer. Il servizio di output può convertire modelli XFA e dati XML per generare documenti di stampa in vari formati.

Il servizio di output consente di creare applicazioni che consentono di:

* Generare documenti modulo finali compilando i file modello con dati XML.
* Genera moduli di output in vari formati, inclusi flussi di stampa non interattivi PDF, PostScript, PCL e ZPL.
* Genera PDF di stampa da PDF modulo XFA.
* Genera in blocco documenti PDF, PostScript, PCL e ZPL unendo più set di dati con i modelli forniti.

>[!NOTE]
>
>Il servizio di output è un&#39;applicazione a 32 bit. Su Microsoft Windows, un&#39;applicazione a 32 bit può utilizzare un massimo di 2 GB di memoria. Il limite si applica anche al servizio di output.

## Creazione di documenti modulo non interattivi {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

In genere si creano modelli con AEM Forms Designer. La `generatePDFOutput` e `generatePrintedOutput` Le API del servizio Output consentono di convertire direttamente questi modelli in vari formati, tra cui PDF, PostScript, ZPL e PCL.

La `generatePDFOutput` l&#39;operazione genera PDF mentre il `generatePrintedOutput` Questa operazione genera i formati PostScript, ZPL e PCL. Il primo parametro di entrambe le operazioni accetta il nome del file modello (ad esempio `ExpenseClaim.xdp`) o un oggetto Document contenente il modello. Quando specifichi il nome del file modello, specifica anche la directory principale del contenuto come percorso della cartella che contiene il modello. È possibile specificare la directory principale del contenuto utilizzando `PDFOutputOptions` o `PrintedOutputOptions` parametro . Consulta Javadoc per i dettagli di altre opzioni che puoi specificare utilizzando questi parametri.

Il secondo parametro accetta un documento XML unito al modello durante la generazione del documento di output.

La `generatePDFOutput` può inoltre accettare un modulo PDF basato su XFA come input e restituire una versione non interattiva del modulo PDF come output.

## Generazione di documenti modulo non interattivi {#generating-non-interactive-form-documents}

Considerare uno scenario in cui si dispone di uno o più modelli e più record di dati XML per ciascun modello.

Utilizza la `generatePDFOutputBatch` e `generatePrintedOutputBatch` operazioni del servizio Output per generare un documento di stampa per ogni record.

È inoltre possibile combinare i record in un unico documento. Entrambe le operazioni richiedono quattro parametri.

Il primo parametro è una mappa che contiene una stringa arbitraria come chiave e il nome del file modello come valore.

Il secondo parametro è una mappa diversa il cui valore è un oggetto Document che contiene dati XML. La chiave è la stessa specificata per il primo parametro.

Il terzo parametro per `generatePDFOutputBatch` o `generatePrintedOutputBatch` è di tipo `PDFOutputOptions` o `PrintedOutputOptions` rispettivamente.

I tipi di parametri sono gli stessi dei tipi dei parametri per `generatePDFOutput` e `generatePrintedOutput` e hanno lo stesso effetto.

Il quarto parametro è di tipo `BatchOptions`, che consente di specificare se è possibile generare un file separato per ogni record. Il valore predefinito di questo parametro è false.

Entrambi `generatePrintedOutputBatch` e `generatePDFOutputBatch` restituisce un valore di tipo `BatchResult`. Il valore contiene un elenco di documenti generati. Contiene inoltre un documento con metadati in formato XML contenente informazioni relative a ciascun documento generato.
