---
title: Impostazione delle opzioni di internazionalizzazione
seo-title: Setting internationalization options
description: Scopri come specificare le impostazioni internazionali utilizzate per il rendering dei moduli e come specificare il set di caratteri utilizzato per codificare il flusso di output.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 4%

---

# Impostazione delle opzioni di internazionalizzazione{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Specificare le impostazioni internazionali utilizzate per il rendering dei moduli {#specify-the-locale-used-to-render-forms}

È possibile specificare le impostazioni internazionali utilizzate per il rendering di un modulo PDF. I campi di un modulo PDF utilizzano le impostazioni internazionali specificate per visualizzare i dati. Ad esempio, se le impostazioni internazionali sono impostate su Tedesco, per i valori numerici il modulo utilizza separatori decimali tedeschi. Le impostazioni internazionali vengono inoltre utilizzate per inviare messaggi di convalida ai dispositivi client, come i browser web, come parte delle trasformazioni di HTML.

1. Nella console di amministrazione, fai clic su Servizi > Forms.
1. In Internazionalizzazione, nell’elenco Lingua, selezionare le impostazioni internazionali utilizzate per eseguire il rendering di un modulo. Il valore predefinito è Inglese (Stati Uniti).
1. Fai clic su Salva.

## Specifica il set di caratteri utilizzato per codificare il flusso di output {#specify-the-character-set-used-to-encode-the-output-stream}

1. In Internazionalizzazione, selezionare un set di caratteri dall’elenco Set di caratteri. Questa impostazione dipende dall’API utilizzata, renderHTMLForm o renderPDFForm. Per specificare un set di caratteri diverso da quelli elencati, selezionare Personalizzato e specificare un valore di codifica nella casella visualizzata.

   Per le trasformazioni di HTML, i moduli AEM supportano i valori di codifica dei caratteri definiti dal `java.nio.charset` pacchetto. Se sFormPreference è PDFForm, sono supportati solo set di caratteri specifici. Il set di caratteri deve essere un nome canonico valido. Il valore predefinito è ISO-8859-1.

1. Fai clic su Salva.
