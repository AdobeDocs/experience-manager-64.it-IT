---
title: Diagnostica ContextHub
seo-title: ContextHub Diagnostics
description: ContextHub fornisce una pagina di diagnostica in cui puoi visualizzare una panoramica del framework ContextHub
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Diagnostica ContextHub {#contexthub-diagnostics}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

ContextHub fornisce una pagina di diagnostica in cui puoi visualizzare una panoramica del framework ContextHub. Per aprire la pagina, passa alla pagina `contexthub.diagnostics.html` pagina dell’istanza di authoring AEM, ad esempio:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

La pagina Diagnostica ContextHub fornisce informazioni sugli archivi e sui moduli di interfaccia utente creati, sulle cartelle della libreria client caricate e sui collegamenti a pagine utili.

>[!NOTE]
>
>Per poter restituire le informazioni di diagnostica, è necessario attivare la modalità di debug, altrimenti la pagina di diagnostica sarà vuota. Vedi [presente documento](/help/sites-administering/contexthub-config.md#debugging-contexthub) per informazioni dettagliate su come abilitare la modalità di debug.

>[!NOTE]
>
>Per le configurazioni ContextHub ancora presenti nei percorsi legacy, il percorso della pagina di diagnostica è `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Negozi {#stores}

Nella sezione Stores sono elencati tutti gli archivi ContextHub configurati. Ogni voce dell&#39;elenco è costituita dalle seguenti informazioni:

* **Titolo:** La [tipo di archivio](/help/sites-developing/ch-samplestores.md) su cui si basa il negozio.
* **percorso:** Percorso del nodo del repository che contiene la configurazione.
* **resourceType:** Percorso del nodo del repository in cui è definito il tipo di archivio.
* **clientlibs:** Le categorie delle librerie client caricate che implementano il tipo di archivio.

## Moduli {#modules}

La sezione Moduli elenca tutti i moduli dell’interfaccia utente di ContextHub configurati. Ogni voce dell&#39;elenco è costituita dalle seguenti informazioni:

* **Titolo:** La [Tipo di modulo interfaccia utente](/help/sites-developing/ch-samplemodules.md) su cui si basa il modulo dell’interfaccia utente.
* **percorso:** Percorso del nodo del repository che contiene la configurazione.
* **resourceType:** Percorso del nodo del repository in cui è definito il tipo di modulo dell&#39;interfaccia utente.
* **clientlibs:** Le categorie delle librerie client caricate che implementano il tipo di modulo dell’interfaccia utente.

## Clientlibs {#clientlibs}

La sezione Clientlibs elenca tutte le cartelle della libreria client caricate da ContextHub. Le librerie client sono suddivise in categorie:

* **kernel.js:** Librerie client che implementano il framework ContextHub, il motore dei segmenti e i tipi di archivio.
* **ui.js:** Librerie client che implementano i tipi di moduli di interfaccia utente e interfaccia utente di ContextHub.
* **style.css:** File CSS caricati dalle librerie client.

## URL {#urls}

La sezione URL contiene collegamenti alle funzioni di ContextHub:

* **Editor di configurazione:** Apre la [Pagina Configurazione ContextHub](/help/sites-administering/contexthub-config.md) dove puoi configurare negozi, modalità di interfaccia utente e moduli di interfaccia utente.

* **Configurazione dei moduli ContextHub:** Apre il file /etc/cloudsettings/default/contexthub.config.kernel.js, che contiene la rappresentazione dell&#39;oggetto Javascript delle configurazioni dell&#39;archivio ContextHub.
* **Configurazione dell’interfaccia utente di ContextHub:** Apre il file /etc/cloudsettings/default/contexthub.config.ui.js , che contiene la rappresentazione dell’oggetto Javascript delle configurazioni della modalità di interfaccia utente ContextHub.
* **kernel.js:** Apre il file /etc/cloudsettings/default/contexthub.kernel.js , che contiene il codice sorgente delle librerie client che implementano il framework ContextHub, il motore dei segmenti e i tipi di archivio.
* **ui.js:** Apre il file /etc/cloudsettings/default/contexthub.ui.js , che contiene il codice sorgente delle librerie client che implementano i tipi di interfaccia utente e moduli di interfaccia utente di ContextHub.
* **style.css:** Apre il file /etc/cloudsettings/default/contexthub.styles.css , che contiene gli stili CSS per i moduli di interfaccia utente e interfaccia utente di ContextHub.
