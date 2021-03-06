---
title: Concetto di authoring
seo-title: Concetto di authoring
description: Concetti relativi all’authoring in AEM
seo-description: Concetti relativi all’authoring in AEM
uuid: 824c8b91-07c7-471b-b3aa-5a73d6d48414
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 72ee013a-7a60-41ee-9421-2846e4c6bc68
translation-type: tm+mt
source-git-commit: b009abd8b3d55bd7dd030d7b4828aec72d9fa9ff
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 86%

---


# Concetto di authoring e pubblicazione{#authoring}

AEM offre due ambienti:

* Autore
* Pubblicazione

Questi interagiscono tra di loro e consentono di rendere i contenuti disponibili nel sito web e accessibili ai visitatori.

L’ambiente di authoring fornisce le funzioni necessarie per creare, aggiornare e rivedere i contenuti prima che vengano pubblicati:

* L’autore crea e rivede i contenuti (che possono essere di diversi tipi, ad esempio pagine, risorse, pubblicazioni ecc.)
* destinati a essere pubblicati sul sito web.

![chlimage_1-289](assets/chlimage_1-289.png)

Nell’ambiente di authoring le funzioni di AEM sono accessibili tramite due interfacce utente. Nell’ambiente di pubblicazione vengono invece progettati l’aspetto e il comportamento dell’interfaccia presentata agli utenti.

## Ambiente di authoring {#author-environment}

L’autore utilizza il cosiddetto **[ambiente di authoring](/help/sites-authoring/home.md)**, che fornisce un’interfaccia, grafica o normale, di facile utilizzo per la creazione dei contenuti. In genere si trova dietro un firewall aziendale per la protezione dei dati e l’autore può accedervi mediante un account dotato delle autorizzazioni di accesso appropriate.

>[!NOTE]
>
>Per creare, modificare o pubblicare le risorse, è necessario utilizzare un account con diritti di accesso appropriati.

A seconda della configurazione dell’istanza in uso e dei diritti di accesso personali, è possibile eseguire varie attività sui contenuti, ad esempio:

* Generare nuovi contenuti o modificare contenuti esistenti su una pagina
* Utilizzare modelli predefiniti per creare nuove pagine di contenuti
* Creare, modificare e gestire le risorse e raccolte
* Creare, modificare e gestire le pubblicazioni
* Sviluppare campagne e relative risorse
* Creare e gestire siti di tipo Community
* Spostare, copiare ed eliminare contenuti, pagine, ecc.
* Pubblicare (o annullare la pubblicazione di) pagine, risorse, ecc.

Sono inoltre disponibili attività amministrative per la gestione dei contenuti:

* Flussi di lavoro che controllano la modalità di gestione dei cambiamenti, ad esempio per imporre la revisione prima della pubblicazione
* Progetti per la coordinazione di singole attività

>[!NOTE]
>
>Molte delle attività AEM possono inoltre essere [amministrate](/help/sites-administering/home.md) dall’ambiente di authoring.

## Ambiente di pubblicazione {#publish-environment}

Quando è pronto, il contenuto del sito AEM viene pubblicato nell&#39; **ambiente di pubblicazione**. Qui le pagine del sito web vengono rese disponibili al pubblico di destinazione in base all’aspetto dell’interfaccia progettata.

Solitamente, l’ambiente di pubblicazione si trova nella cosiddetta zona demilitarizzata. In altre parole, è accessibile da Internet ma non usufruisce più della protezione completa offerta dalla rete interna.

Quando il sito AEM è di tipo [community](/help/communities/overview.md) o include [componenti per community](/help/communities/author-communities.md), i visitatori del sito che hanno effettuato l’accesso (ossia i membri registrati della community) possono interagire con le funzioni Community. Ad esempio, possono pubblicare contenuti in un forum, inserire un commento o seguire altri membri. Ai membri possono essere concesse autorizzazioni per eseguire attività solitamente limitate all’ambiente dell’autore, ad esempio creare nuove pagine (gruppi community) o articoli di blog e moderare i post degli altri membri.

>[!NOTE]
>
>In alcuni casi esiste una sovrapposizione della terminologia utilizzata. Ad esempio:
>
>* **Pubblicare/Annullare la pubblicazione**
   >  Termini principali per le azioni che consentono di rendere o meno i contenuti disponibili al pubblico nell’ambiente di pubblicazione.
   >
   >
* **Attivare/Disattivare**
   >  Sinonimi di pubblicare/annullare la pubblicazione. Utilizzati più frequentemente nell’interfaccia classica.
   >
   >
* **Replicare/Replica**
   >  Si tratta dei termini tecnici utilizzati per indicare lo spostamento di dati (ad esempio contenuto di una pagina, file, codice, commenti degli utenti) da un ambiente all&#39;altro; ad esempio per la pubblicazione o la replica inversa dei commenti degli utenti.
>



## Dispatcher {#dispatcher}

Per ottimizzare le prestazioni dal punto di vista dei visitatori del sito web, vengono usati **[dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) che implementano funzioni di bilanciamento del carico e memorizzazione in cache.**
