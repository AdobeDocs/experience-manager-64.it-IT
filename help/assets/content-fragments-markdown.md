---
title: Markdown
seo-title: Markdown
description: Durante l’authoring, l’editor per frammenti di contenuto utilizza la sintassi markdown per consentire di scrivere facilmente il contenuto.
seo-description: When you are authoring, the content fragment editor uses markdown syntax to allow you to easily write content.
uuid: 12b185a5-3d87-4d7c-8d09-8cc2726009a8
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: bde54663-9050-4a5a-93cb-7cd84ac7f071
exl-id: 209f0e02-b883-4104-8358-01cab15e5db2
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 86%

---

# Markdown {#markdown}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](/help/release-notes/sp-release-notes.md).

Quando sei [authoring](content-fragments-variations.md#authoring-your-content), l’editor dei frammenti di contenuto utilizza *markdown* sintassi per consentire di scrivere facilmente il contenuto:

![editor markdown](/help/assets/assets/cfm-6420-08.png)

Puoi definire:

* [Notazione intestazione](/help/assets/content-fragments-markdown.md#heading-notation)
* [Paragrafi e interruzioni di riga](/help/assets/content-fragments-markdown.md#paragraphs-and-line-breaks)
* [Collegamenti](/help/assets/content-fragments-markdown.md#links)
* [Immagini](/help/assets/content-fragments-markdown.md#images)
* [Citazioni](/help/assets/content-fragments-markdown.md#block-quotes)
* [Elenchi](/help/assets/content-fragments-markdown.md#lists)
* [Enfasi](/help/assets/content-fragments-markdown.md#emphasis)
* [Blocchi di codice](/help/assets/content-fragments-markdown.md#code-blocks)
* [Escape barra rovesciata](/help/assets/content-fragments-markdown.md#backslash-escapes)

## Notazione intestazione {#heading-notation}

Per creare un’intestazione inserendo un hashtag (#) davanti al titolo. Un singolo hashtag (#) viene utilizzato per un titolo H1, due hashtag (##) per H2 e così via. Puoi utilizzare fino a 6 hashtag. Esempio:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

In alternativa, è possibile creare un H1 sottolineando il testo con alcuni segni di uguale e creare un H2 sottolineando il testo con i segni meno. Esempio:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Paragrafi e interruzioni di riga {#paragraphs-and-line-breaks}

Un paragrafo è costituito semplicemente da una o più righe di testo consecutive, separate da una o più righe vuote. Una riga vuota è una riga contenente solo spazi o tabulazioni. Il rientro dei paragrafi normali non deve essere applicato con spazi o tabulazioni.

Un’interruzione di riga viene creata chiudendo una riga con due o più spazi e quindi premendo Invio.

## Collegamenti {#links}

Puoi creare collegamenti in linea e di riferimento.

In entrambi gli stili, il testo del collegamento è delimitato da parentesi quadre `[]`.

Di seguito sono riportati alcuni esempi di collegamenti in linea:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Un collegamento di riferimento ha la seguente sintassi:

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Immagini {#images}

La sintassi per le immagini è simile a quella dei collegamenti. Puoi creare immagini in linea e di riferimento.

Ad esempio, un’immagine in linea ha la seguente sintassi:

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

La sintassi include:

* Un punto esclamativo: !;
* seguito da un set di parentesi quadre, contenenti il testo dell’attributo “alt” relativo all’immagine;
* seguito da un set di parentesi, contenenti l’URL o il percorso dell’immagine, oltre a un attributo facoltativo del titolo racchiuso tra virgolette doppie o singole.

Un’immagine stile di riferimento ha la seguente sintassi:

    `![Alt text][id]`

Dove “id” è il nome di un riferimento immagine definito. I riferimenti a immagini sono definiti utilizzando una sintassi identica ai riferimenti di collegamento:

    `[id]: url/to/image "Optional title attribute"`

## Citazioni {#block-quotes}

Puoi citare il testo aggiungendo il simbolo > prima del testo. Esempio:

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

Puoi anche aggiungere citazioni nidificate. Esempio:

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Elenchi {#lists}

Puoi creare elenchi ordinati e non ordinati.

Per creare un elenco non ordinato, utilizza il simbolo &amp;ast; davanti agli elementi dell’elenco. Esempio:

    `* item in list`

    `* item in list`

    `* item in list`

Per creare un elenco ordinato, aggiungi i numeri, seguiti da un punto, davanti a ogni elemento dell’elenco. Esempio:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Enfasi {#emphasis}

Puoi aggiungere al testo lo stile corsivo o grassetto.

Per aggiungere il corsivo, procedi come segue:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

Puoi applicare il grassetto con la seguente procedura:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Per indicare un’estensione del codice, inseriscila tra apici inversi (&grave;). A differenza di un blocco di codice preformattato, un’estensione del codice indica il codice all’interno di un paragrafo normale.

Esempio:

    ``Use the `printf()` function.``

## Blocchi di codice {#code-blocks}

I blocchi di codice vengono generalmente utilizzati per illustrare il codice sorgente. Puoi creare blocchi di codice applicando un rientro al codice utilizzando una tabulazione o un minimo di 4 spazi. Esempio:

    `This is a normal paragraph.`

        `This is a code block.`

## Escape barra rovesciata {#backslash-escapes}

Puoi utilizzare gli escape barra rovesciata per generare caratteri letterali che hanno un significato speciale nella sintassi di formattazione. Ad esempio, se desideri racchiudere una parola tra asterischi letterali (invece di un tag &lt;em> HTML), puoi utilizzare le barre rovesciate prima degli asterischi, come segue:

    `\\*literal asterisks\\*`

Gli escape barre rovesciate sono disponibili per i seguenti caratteri:

    ` \ backslash`

    `` ` backtick``

    ` * asterisk`

    ` _ underscore`

    ` {} curly braces`

    ` [] square brackets`

    ` () parentheses`

    ` # hash mark`

    ` + plus sign`

    ` - minus sign (hyphen)`

    ` . dot`
