---
title: Soglia massima cursori aperti del database di Oracle
seo-title: Oracle database maximum open cursors threshold
description: Scopri come configurare un valore massimo per i cursori aperti in Oracle.
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 6%

---

# Soglia massima cursori aperti del database di Oracle {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per configurare un valore massimo per i cursori aperti in Oracle, potrebbe essere necessario impostare questo valore su un numero appropriato per l&#39;applicazione. È evidente che sotto un carico moderato, i cursori medi aperti erano 2700. Si consiglia di iniziare con un limite superiore di 3000. Per ulteriori informazioni, consulta [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
