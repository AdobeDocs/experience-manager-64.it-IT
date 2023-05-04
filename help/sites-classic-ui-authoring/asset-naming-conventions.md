---
title: Convenzioni di denominazione per il test delle risorse
seo-title: Naming conventions for assets
description: I nodi nell’archivio sono soggetti a denominazioni convenzionali del Java Content Repository. Tuttavia, Adobe Experience Manager impone ulteriori convenzioni per il nome dei nodi di risorsa.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: 3dc38c37-f2a0-44f5-90f6-fee8c6f84ff4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 6%

---

# Convenzioni di denominazione per il test delle risorse{#naming-conventions-for-assets-testing}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I nodi nell&#39;archivio sono soggetti a convenzioni di denominazione [Archivio dei contenuti Java](/help/sites-developing/the-basics.md#java-content-repository). Tuttavia, Adobe Experience Manager impone ulteriori convenzioni per il nome dei nodi di risorsa.

## Interfaccia classica {#classic-ui}

L’interfaccia classica impone restrizioni più restrittive:

* Convalida il nome della risorsa quando è presente un nome di nodo esplicito quando:

   * viene fornito un titolo della risorsa per la conversione nel nome del nodo
   * viene fornito un nome di nodo esplicito

* Caratteri validi (solo questi caratteri sono effettivamente validi quando una risorsa viene creata dall&#39;interfaccia classica):

   * da &quot;a&quot; a &quot;z&quot;
   * Da &quot;A&quot; a &quot;Z&quot;
   * Da &quot;0&quot; a &quot;9&quot;
   * _ (trattino basso)
   * `-` (trattino/segno meno)
