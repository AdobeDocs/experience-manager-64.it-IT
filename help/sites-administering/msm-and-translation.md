---
title: Amministrazione di siti web
seo-title: Website Administration
description: Scopri come gestire i siti web multilingue in AEM.
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: e8f83d21-b55e-4415-a581-8df1b71a84b1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 41%

---

# Amministrazione di siti web{#website-administration}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per la gestione di siti web e pagine sono disponibili i seguenti strumenti di amministrazione:

* Multi Site Manager (MSM) consente di utilizzare lo stesso contenuto del sito in più posizioni, consentendo al contempo le varianti:

   * [Riutilizzo del contenuto: Multi-Site Manager e Live Copy](/help/sites-administering/msm.md)

* La traduzione automatizzata consente di automatizzare la traduzione del contenuto della pagina, delle risorse e dei contenuti generati dagli utenti per creare e gestire siti web multilingue:

   * [Traduzione di contenuti per siti multilingue](/help/sites-administering/translation.md)

* Queste due funzioni possono essere combinate per gestire i siti web che sono entrambi [Multinazionale e multilingue](#multinational-and-multilingual-sites).

## Siti multinazionali e multilingue {#multinational-and-multilingual-sites}

Puoi creare contenuti per siti multinazionali e multilingue in modo efficiente tramite l’utilizzo combinato di Multi Site Manager e del flusso di lavoro di traduzione. Crea un sito master in una lingua, per un paese specifico, quindi utilizza tale contenuto come base per gli altri siti, utilizzando la traduzione, se necessario:

* [Tradurre](/help/sites-administering/translation.md) il sito master in lingue diverse.

* Utilizza [Multi Site Manager](/help/sites-administering/msm.md) per:

   * Riutilizza i contenuti del sito principale e le traduzioni per creare siti per altri paesi e culture.
   * Assicurati di limitare l&#39;utilizzo di Multi Site Manager ai contenuti in una lingua, ad esempio master inglese -> filiali in lingua inglese in siti di paese, master francese -> filiali in lingua francese in siti di paese.
   * Se necessario, scollega gli elementi delle Live Copy per aggiungere i dettagli di localizzazione.

Il diagramma seguente illustra l’intersezione dei concetti principali (ma non tutti i livelli/elementi coinvolti):

![chlimage_1-71](assets/chlimage_1-71.png)

>[!NOTE]
>
>In questo scenario (e simili) MSM non gestisce le diverse versioni linguistiche in quanto tali.
>
>* [MSM](/help/sites-administering/msm.md) gestisce la distribuzione dei contenuti tradotti da un blueprint (ad esempio un master globale) alle Live Copy (ad esempio i siti locali), entro i limiti di una lingua.
>* Le capacità di integrazione delle [traduzioni](/help/sites-administering/translation.md) di AEM, in collaborazione con servizi di gestione della localizzazione di terze parti, gestiscono le lingue e traducono i contenuti in diverse lingue.
>
>Per casi di utilizzo più avanzati, MSM può essere utilizzato anche tra le lingue master.

>[!NOTE]
>
>Per tutti i casi d’uso si consiglia di leggere le seguenti best practice:
>
>* [Best practice per MSM](/help/sites-administering/msm-best-practices.md); in particolare:
   >
   >   * [Crea sito](/help/sites-administering/msm-best-practices.md#create-site)
   >   * [Siti Web MSM e multilingue](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Best practice per la traduzione](/help/sites-administering/tc-bp.md)

