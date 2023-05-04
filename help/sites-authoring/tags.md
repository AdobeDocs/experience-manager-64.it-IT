---
title: Utilizzo dei tag
seo-title: Using Tags
description: I tag sono un metodo semplice e veloce per classificare i contenuti di un sito web
seo-description: Tags are a quick and easy method of classifying content within a website
uuid: a91f8724-fc35-4f40-b21c-bee90429765b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: d0b0e47b-e68d-407d-9d06-deca2039dede
exl-id: 846a925a-673e-4051-a673-1a9236701f0a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 31%

---

# Utilizzo dei tag   {#using-tags}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I tag sono un metodo semplice e veloce per classificare i contenuti di un sito web. I tag possono essere considerati parole chiave o etichette da allegare a una pagina, a una risorsa o ad altro contenuto per consentire la ricerca di tale contenuto e del relativo contenuto.

* Vedi [Amministrazione dei tag](/help/sites-administering/tags.md) per informazioni sulla creazione e la gestione dei tag e sui tag di contenuto applicati.
* Per informazioni sul framework dei tag e sull’inclusione e l’estensione dei tag in applicazioni personalizzate, vedi [Tagging per sviluppatori](/help/sites-developing/tags.md).

## Dieci motivi per utilizzare l’assegnazione tag {#ten-reasons-to-use-tagging}

1. Organizzazione dei contenuti : L’assegnazione tag semplifica il lavoro degli autori, che possono organizzare rapidamente i contenuti con il minimo sforzo.

1. Organizzazione dei tag : mentre i tag organizzano il contenuto, le tassonomie o i namespace gerarchici consentono di organizzare i tag.

1. Tag profondamente organizzati : grazie alla possibilità di creare tag e tag secondari, è possibile creare tassonomie complete che includono termini, termini secondari e le loro relazioni. In questo modo è possibile creare una seconda (o terza) gerarchia di contenuti parallela a quella ufficiale.

1. Assegnazione tag controllata : l’assegnazione tag può essere controllata applicando autorizzazioni ai tag e/o ai namespace per controllare la creazione e l’applicazione dei tag.

1. Assegnazione di tag flessibile : I tag hanno nomi e facce diversi: tag, termini di tassonomia, categorie, etichette e molto altro. Sono flessibili dal punto di vista del modello di contenuto e della modalità di utilizzo. Possono essere ad esempio utilizzati per sintetizzare le caratteristiche demografiche del target, suddividere in categorie e classificare i contenuti o creare una gerarchia di contenuti secondaria.

1. Ricerca migliorata : il componente di ricerca predefinito in AEM include i tag creati e applicati a cui è possibile applicare filtri per limitare i risultati a quelli pertinenti.

1. Abilitazione SEO : I tag applicati come proprietà della pagina vengono visualizzati automaticamente nei metatag della pagina, rendendola visibile ai motori di ricerca.

1. Sofisticazione semplice : I tag possono essere creati semplicemente da una parola e premendo un pulsante. In seguito, è possibile aggiungere un titolo, una descrizione ed etichette illimitate per fornire ulteriore semantica al tag.

1. Coerenza di base : il sistema di assegnazione tag è un componente di base di AEM e viene utilizzato da tutte le funzionalità di AEM per la classificazione dei contenuti. Inoltre, per gli sviluppatori è disponibile l’API di assegnazione tag che consente di creare applicazioni abilitate per l’assegnazione tag con accesso alle stesse tassonomie.

1. Struttura e flessibilità combinate: AEM è ideale per lavorare con informazioni strutturate, grazie alla nidificazione di pagine e percorsi. È altrettanto potente quando si lavora con informazioni non strutturate, a causa della ricerca full-text integrata. L’assegnazione tag combina i punti di forza sia della struttura che della flessibilità.

Durante la progettazione della struttura del contenuto per un sito e dello schema di metadati per le risorse, considera l’approccio leggero e accessibile fornito dall’assegnazione di tag.

## Applicazione dei tag   {#applying-tags}

Nell’ambiente di authoring gli autori possono applicare i tag accedendo alle proprietà della pagina e immettendo uno o più tag nel campo **Tag/Parole chiave**.

Da applicare [tag predefiniti](/help/sites-administering/tags.md), nella **Proprietà pagina** utilizza la finestra **Tag** e **Seleziona tag** finestra. La scheda **Tag standard** è il namespace predefinito, il che significa che non esiste una `namespace-string:` aggiunta come prefisso alla tassonomia.

![chlimage_1-92](assets/chlimage_1-92.png)

### Pubblicazione dei tag {#publishing-tags}

Come per le pagine, è possibile eseguire le seguenti operazioni su tag e namespace:

**Attiva**

* Consente di attivare singoli tag.

   Come per le pagine, è necessario attivare i nuovi tag creati prima che siano disponibili nell’ambiente di pubblicazione.

>[!NOTE]
>
>Quando si attiva una pagina, si apre automaticamente una finestra di dialogo che consente di attivare i tag non attivati appartenenti alla pagina.

**Disattiva**

* Consente di disattivare i tag selezionati.

## Tag cloud {#tag-clouds}

I tag cloud mostrano un insieme di tag relativi alla pagina corrente, all’intero sito web o ai contenuti maggiormente utilizzati. I tag cloud sono uno strumento per evidenziare i problemi che sono (o sono stati) di interesse per l’utente. Le dimensioni del testo utilizzato per visualizzare il tag variano in relazione all’uso.

La [Tag Cloud](/help/sites-authoring/default-components-foundation.md#tag-cloud) viene utilizzato per aggiungere un tag cloud a una pagina.

## Ricerca di tag {#searching-on-tags}

È possibile cercare i tag sia nell’ambiente di authoring che in quello di pubblicazione.

### Utilizzo del componente Ricerca {#using-search-component}

Aggiunta di un [Componente di ricerca](/help/sites-authoring/default-components-foundation.md#search) In una pagina è disponibile una funzionalità di ricerca che include i tag e può essere utilizzata sia nell’ambiente di authoring che in quello di pubblicazione.

![chlimage_1-93](assets/chlimage_1-93.png)
