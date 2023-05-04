---
title: Convenzioni di denominazione
seo-title: Naming Conventions
description: I nodi nell’archivio sono soggetti a denominazioni convenzionali del Java Content Repository
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
exl-id: 741043c7-2ebb-455d-8163-a246b874a7b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 9%

---

# Convenzioni di denominazione{#naming-conventions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I nodi nell&#39;archivio sono soggetti a convenzioni di denominazione [Archivio dei contenuti Java](/help/sites-developing/the-basics.md#java-content-repository). Tuttavia AEM impone ulteriori convenzioni per il nome dei nodi di pagina.

## Convenzioni di denominazione per le pagine {#naming-conventions-for-pages}

Queste convenzioni di denominazione sono implementate a vari livelli:

* JcrUtil: l&#39;attuazione AEM [Utilità JCR](#jcr-utilities).
* PageManager: la [Gestione pagine](#page-manager) fornisce metodi per le operazioni a livello di pagina.
* A seconda dell’interfaccia in uso:

   * [Interfaccia standard con funzionalità touch](#standard-ui)
   * [Interfaccia classica](#classic-ui)

### Utilità JCR {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) è l’implementazione AEM delle utility JCR. Di particolare interesse per la convalida dei nomi sono le mappature dei caratteri che controlla e le seguenti convalide:

* `isValidName`

   * Controlla se il nome non è vuoto e contiene solo caratteri validi.
   * Può essere utilizzato per verificare se un nome proposto è valido.

* `createValidName`

   * Questo crea un&#39;etichetta valida da una stringa arbitraria.
   * Può essere utilizzato per creare un nome da un titolo.

### Gestione pagine {#page-manager}

[PageManager](https://helpx.adobe.com/it/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) fornisce metodi per le operazioni a livello di pagina, in base a [JCRUtil](#jcr-utilities).

### Interfaccia standard {#standard-ui}

Interfaccia touch standard:

* Convalida il nome in base alle restrizioni imposte da PageManager quando:

   * viene fornito un titolo di pagina per la conversione nel nome del nodo
   * viene fornito un nome di nodo esplicito

### Interfaccia classica {#classic-ui}

L’interfaccia classica impone restrizioni più restrittive:

* Convalida il nome quando un nome di nodo esplicito è presente quando:

   * viene fornito un titolo di pagina per la conversione nel nome del nodo
   * viene fornito un nome di nodo esplicito

* Caratteri validi (solo questi caratteri sono effettivamente validi quando una pagina viene creata dall’interno dell’interfaccia classica, anche se `PageManagerImpl` consentirebbe caratteri aggiuntivi):

   * da &quot;a&quot; a &quot;z&quot;
   * Da &quot;A&quot; a &quot;Z&quot;
   * Da &quot;0&quot; a &quot;9&quot;
   * _ (trattino basso)
   * `-` (trattino/segno meno)
