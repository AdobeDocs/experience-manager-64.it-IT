---
title: Diagnostica ContextHub
seo-title: Diagnostica ContextHub
description: ContextHub fornisce una pagina di diagnostica in cui potete vedere una panoramica del framework ContextHub
seo-description: ContextHub fornisce una pagina di diagnostica in cui potete vedere una panoramica del framework ContextHub
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Diagnostica ContextHub {#contexthub-diagnostics}

ContextHub fornisce una pagina di diagnostica in cui potete vedere una panoramica del framework ContextHub. Per aprire la pagina, passate alla pagina `contexthub.diagnostics.html` dell’istanza di authoring AEM, ad esempio:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

La pagina Diagnostica ContextHub fornisce informazioni sugli store e sui moduli dell&#39;interfaccia utente creati, sulle cartelle della libreria client che vengono caricate e sui collegamenti alle pagine utili.

>[!NOTE]
>
>Per poter restituire le informazioni diagnostiche, è necessario abilitare la modalità di debug, altrimenti la pagina di diagnostica sarà vuota. Per informazioni su come abilitare la modalità di debug, vedere [questo documento](/help/sites-administering/contexthub-config.md#debugging-contexthub).

>[!NOTE]
>
>Per le configurazioni ContextHub ancora presenti nei percorsi legacy, la posizione della pagina di diagnostica è `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Negozi {#stores}

Nella sezione Store sono elencati tutti gli store ContextHub configurati. Ogni elemento dell&#39;elenco è costituito dalle seguenti informazioni:

* **Titolo:** Il tipo di  [store ](/help/sites-developing/ch-samplestores.md) su cui si basa lo store.
* **percorso:** percorso del nodo del repository che contiene la configurazione.
* **resourceType:** il percorso del nodo del repository in cui è definito il tipo di archivio.
* **clientlibs:** Le categorie delle librerie client caricate che implementano il tipo di store.

## Moduli {#modules}

Nella sezione Moduli sono elencati tutti i moduli di interfaccia utente ContextHub configurati. Ogni elemento dell&#39;elenco è costituito dalle seguenti informazioni:

* **Titolo:** Tipo di modulo  [interfaccia ](/help/sites-developing/ch-samplemodules.md) basato sul modulo dell’interfaccia utente.
* **percorso:** percorso del nodo del repository che contiene la configurazione.
* **resourceType:** percorso del nodo del repository in cui è definito il tipo di modulo dell&#39;interfaccia utente.
* **clientlibs:** le categorie delle librerie client caricate che implementano il tipo di modulo dell&#39;interfaccia utente.

## Clientlibs {#clientlibs}

Nella sezione Clientlibs sono elencate tutte le cartelle della libreria client caricate da ContextHub. Le librerie client sono suddivise in categorie:

* **kernel.js:librerie** client che implementano il framework ContextHub, il motore del segmento e i tipi di store.
* **ui.js:librerie** client che implementano l&#39;interfaccia utente e i tipi di moduli dell&#39;interfaccia utente ContextHub.
* **style.css:file** CSS caricati dalle librerie client.

## URL {#urls}

La sezione URL contiene collegamenti alle funzioni ContextHub:

* **Editor di configurazione:** apre la  [pagina Configurazione ](/help/sites-administering/contexthub-config.md) ContextHub in cui è possibile configurare store, modalità di interfaccia utente e moduli di interfaccia utente.

* **Configurazione dei moduli ContextHub:** apre il file /etc/cloudsettings/default/contexthub.config.kernel.js, che contiene la rappresentazione oggetto Javascript delle configurazioni dell&#39;archivio ContextHub.
* **Configurazione dell’interfaccia utente ContextHub:** apre il file /etc/cloudsettings/default/contexthub.config.ui.js, che contiene la rappresentazione oggetto Javascript delle configurazioni della modalità di interfaccia ContextHub.
* **kernel.js:** apre il file /etc/cloudsettings/default/contexthub.kernel.js, che contiene il codice sorgente delle librerie client che implementano il framework ContextHub, il motore del segmento e i tipi di store.
* **ui.js:** apre il file /etc/cloudsettings/default/contexthub.ui.js, che contiene il codice sorgente delle librerie client che implementano l&#39;interfaccia utente e i tipi di moduli dell&#39;interfaccia utente ContextHub.
* **style.css:** apre il file /etc/cloudsettings/default/contexthub.styles.css, che contiene gli stili CSS per i moduli dell&#39;interfaccia utente e dell&#39;interfaccia utente ContextHub.
