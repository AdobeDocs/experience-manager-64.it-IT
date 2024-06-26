---
title: Specificare i font da incorporare
seo-title: Specify fonts to embed
description: Scopri come specificare i font da incorporare.
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 3%

---

# Specificare i font da incorporare{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile specificare i font sempre incorporati o mai incorporati nei moduli utilizzati da Output. L’incorporazione di font aumenta le dimensioni del file dei moduli. Incorpora font insoliti che gli utenti non hanno sul loro sistema e non incorporano font comuni che avranno installato.

>[!NOTE]
>
>Se per Output è stato specificato un file XCI personalizzato, l&#39;opzione di font da incorporare nel file XCI sostituisce queste impostazioni. (Vedi [Specificare le posizioni dei file per l&#39;output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Nella console di amministrazione, fai clic su Servizi > output.
1. Nella casella Incorpora sempre font digitare i nomi dei font da incorporare nei moduli, separati da virgole. I font specificati vengono incorporati nel modulo generato solo se utilizzati nel modulo. Questa impostazione viene ignorata se l’opzione di font da incorporare è stata attivata nel file XCI passato al servizio. In tal caso, tutti i font utilizzati in PDF sono sempre incorporati.
1. Nella casella Non incorporare font digitare i nomi dei font da non incorporare nei moduli, separati da virgole. I font specificati non sono incorporati in PDF, anche se sono utilizzati nel PDF generato. Questa impostazione viene ignorata se l’opzione di font da incorporare è stata disattivata nel file XCI passato al servizio. In tal caso, nessuno dei font utilizzati in PDF è incorporato.
1. Fai clic su Salva.
