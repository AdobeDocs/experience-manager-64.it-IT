---
title: Informazioni sulla struttura delle cartelle
seo-title: Understanding the folder structure
description: Informazioni sulla struttura delle cartelle del codice sorgente dell’area di lavoro di AEM Forms da personalizzare.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# Informazioni sulla struttura delle cartelle {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I componenti dell’area di lavoro di AEM Forms sono progettati sull’architettura MVC utilizzando Backbone. Ogni componente ha un file per:

* Modello, che contiene la logica di business.
* Modello, ovvero un file HTML contenente i controlli dell’interfaccia.
* Visualizza, che funge da classe Controller in Modello.

Le risorse per tutti i componenti vengono posizionate nella struttura di cartelle descritta di seguito. Per accedere alle risorse, accedi a CRXDE Lite e sfoglia fino a `/libs/ws/js/runtime/`.

**modelli** Contiene modelli di dorsale.

**visualizzazioni** Contiene le visualizzazioni della spina dorsale.

**modelli** Contiene solo i modelli di HTML per i componenti.

**rotte** Contiene percorsi universali. La cartella Templates all&#39;interno delle route contiene il codice HTML e i riferimenti ai componenti.

**servizi** Contiene l’interfaccia del servizio per chiamare le API del server Adobe Experience Manager sull’endpoint REST.

**util** Contiene utilità generiche utilizzabili da più componenti.
