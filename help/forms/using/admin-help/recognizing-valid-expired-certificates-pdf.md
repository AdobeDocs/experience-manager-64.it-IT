---
title: Riconoscere certificati validi e scaduti nei documenti PDF
seo-title: Recognizing valid and expired certificates in PDF documents
description: Scopri come riconoscere i certificati validi e scaduti nei documenti PDF.
seo-description: Learn how to recognize valid and expired certificates in PDF documents.
uuid: ceeff57a-586f-4f7b-852f-2a637f003d7e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4559218a-65ba-4577-ad26-7721e28971bc
exl-id: 6e2c109c-381f-455d-bd1d-b08c37c0bd67
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# Riconoscere certificati validi e scaduti nei documenti PDF {#recognizing-valid-and-expired-certificates-in-pdf-documents}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando un documento PDF con diritti di utilizzo applicati da Estensioni Reader viene aperto in Adobe Reader, viene visualizzata una barra di stato che descrive i diritti di utilizzo specifici attivati nel documento PDF.

Quando il certificato digitale che specifica i diritti di utilizzo per un documento PDF scade e il documento PDF viene aperto in Adobe Reader, viene visualizzata una finestra di dialogo in cui viene comunicato all’utente che il documento PDF dispone di diritti di utilizzo, ma tali diritti sono disabilitati. Anche se il messaggio indica che il documento PDF è stato modificato o alterato, non necessariamente questo accade. Adobe Reader visualizza questo messaggio alla scadenza di un certificato o alla modifica di un documento. In Adobe Reader 7.0.x o versione successiva, non è possibile determinare quale caso è attualmente il problema.

Dopo aver chiuso la finestra di dialogo, Adobe Reader apre il documento PDF. I diritti di utilizzo applicati utilizzando le estensioni Acrobat Reader DC non sono disponibili, come previsto. Se il documento PDF è un modulo interattivo, i campi del modulo sono bloccati e l’utente non può modificare i dati del modulo.
