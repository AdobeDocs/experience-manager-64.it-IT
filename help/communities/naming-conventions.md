---
title: Convenzioni di denominazione
seo-title: Naming Conventions
description: Trattini nel nome del pacchetto Java
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: f5a63642-9f2c-436f-bd40-4459545a0ddf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Convenzioni di denominazione {#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Trattini nel nome del pacchetto Java {#hyphens-in-java-package-name}

Quando crei una posizione per una classe Java, tieni presente che il nome del pacchetto deve corrispondere a quello della posizione della cartella dell’archivio con eventuali trattini nel percorso correttamente preceduti da escape.

L’utilizzo dei trattini nei nomi degli elementi dell’archivio è una pratica consigliata nello sviluppo AEM , ma i trattini non sono consentiti nei nomi dei pacchetti Java.

La piattaforma CRX sottostante deve essere in grado di distinguere tra un underscore effettivo &quot;_&quot; e un trattino &quot;-&quot;. Pertanto, in JCR, il trattino deve essere sostituito con il suo valore unicode (u002d) ed essere escape con un carattere di sottolineatura &quot;_&quot;.

Ad esempio, se il percorso del repository è **/apps/my-example/component/info/Info.java**, il nome del pacchetto deve essere `java package apps.my_002dexample.component.info;`

Tenere presente che un carattere di sottolineatura deve essere ugualmente escape, in modo che `_` diventa `_005f`.
