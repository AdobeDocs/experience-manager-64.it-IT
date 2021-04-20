---
title: Supporto di nuove impostazioni internazionali per la localizzazione di moduli adattivi
seo-title: Supporto di nuove impostazioni internazionali per la localizzazione di moduli adattivi
description: AEM Forms consente di aggiungere nuove impostazioni internazionali per la localizzazione di moduli adattivi. Le impostazioni internazionali supportate per impostazione predefinita sono inglese, francese, tedesco e giapponese.
seo-description: AEM Forms consente di aggiungere nuove impostazioni internazionali per la localizzazione di moduli adattivi. Le impostazioni internazionali supportate per impostazione predefinita sono inglese, francese, tedesco e giapponese.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Adaptive Forms
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---


# Supporto di nuove impostazioni internazionali per la localizzazione di moduli adattivi {#supporting-new-locales-for-adaptive-forms-localization}

## Informazioni sui dizionari locali {#about-locale-dictionaries}

La localizzazione dei moduli adattivi si basa su due tipi di dizionari locali:

**Dizionario specifico per il moduloContiene le stringhe utilizzate nei moduli adattivi.** Ad esempio, etichette, nomi di campo, messaggi di errore, descrizioni della guida e così via. È gestito come un set di file XLIFF per ogni impostazione internazionale ed è possibile accedervi in https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Dizionari globaliCi sono due dizionari globali, gestiti come oggetti JSON, nella libreria client AEM.** Questi dizionari contengono messaggi di errore predefiniti, nomi di mese, simboli di valuta, pattern di data e ora e così via. Puoi trovare questi dizionari in CRXDe Lite su /libs/fd/xfaforms/clientlibs/I18N. Queste posizioni contengono cartelle separate per ogni impostazione internazionale. Poiché i dizionari globali di solito non vengono aggiornati frequentemente, mantenere file JavaScript separati per ogni impostazione internazionale consente ai browser di memorizzarli nella cache e di ridurre l’utilizzo della larghezza di banda della rete quando si accede a diversi moduli adattivi sullo stesso server.

### Funzionamento della localizzazione dei moduli adattivi {#how-localization-of-adaptive-form-works}

Quando viene eseguito il rendering di un modulo adattivo, identifica le impostazioni internazionali richieste esaminando i seguenti parametri nell’ordine specificato:

* Parametro della richiesta `afAcceptLang`

   Per ignorare le impostazioni internazionali del browser degli utenti, è possibile trasmettere il parametro della richiesta `afAcceptLang` per forzare le impostazioni internazionali. Ad esempio, con il seguente URL verrà eseguito il rendering del modulo nelle impostazioni internazionali giapponesi:

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* Le impostazioni internazionali del browser impostate per l’utente, specificate nella richiesta utilizzando l’intestazione `Accept-Language` .

* Impostazione della lingua dell’utente specificata in AEM.

Una volta identificate le impostazioni internazionali, i moduli adattivi selezionano il dizionario specifico per il modulo. Se non viene trovato il dizionario specifico per il modulo per le impostazioni internazionali richieste, viene utilizzato il dizionario inglese (en).

Se non esiste una libreria client per le impostazioni internazionali richieste, cerca in una libreria client il codice della lingua presente nelle impostazioni internazionali. Ad esempio, se le impostazioni internazionali richieste sono `en_ZA` (Inglese sudafricano) e la libreria client per `en_ZA` non esiste, il modulo adattivo utilizzerà la libreria client per la lingua `en` (Inglese), se esiste. Tuttavia, se non ne esiste nessuna, il modulo adattivo utilizza il dizionario per le impostazioni internazionali `en`.

## Aggiunta del supporto per la localizzazione per le impostazioni locali non supportate {#add-localization-support-for-non-supported-locales}

AEM Forms supporta attualmente la localizzazione di contenuti di moduli adattivi nelle impostazioni internazionali: inglese (en), spagnolo (es), francese (fr), italiano (it), tedesco (de), giapponese (ja), portoghese-brasiliano (pt-BR, cinese- (zh-CN), cinese-Taiwan (zh-TW) e coreano (ko-KR).

Per aggiungere il supporto per una nuova impostazione internazionale in fase di esecuzione dei moduli adattivi:

1. [Aggiungere un’impostazione internazionale al servizio GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Aggiungere una libreria client XFA per le impostazioni internazionali](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Aggiungere una libreria client per moduli adattivi per le impostazioni internazionali](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Aggiungere supporto per le impostazioni internazionali del dizionario](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Riavvia il server](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Aggiungere un’impostazione internazionale al servizio Guide Localization {#add-a-locale-to-the-guide-localization-service-br}

1. Passa a `https://[server]:[port]/system/console/configMgr`.
1. Fai clic su per modificare il componente **Servizio di localizzazione guida** .
1. Aggiungi le impostazioni internazionali da aggiungere all’elenco delle impostazioni internazionali supportate.

![GuideLocalizationService](assets/configservice.png)

### Aggiungi la libreria client XFA per un&#39;impostazione internazionale {#add-xfa-client-library-for-a-locale-br}

Crea un nodo di tipo `cq:ClientLibraryFolder` in `etc/<folderHierarchy>`, con categoria `xfaforms.I18N.<locale>` e aggiungi i seguenti file alla libreria client:

* **I18N.** jsdefinition  `xfalib.locale.Strings` per  `<locale>` come definito in  `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.** txtcontenenti quanto segue:

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Aggiungere una libreria client per moduli adattivi per le impostazioni locali {#add-adaptive-form-client-library-for-a-locale-br}

Crea un nodo di tipo `cq:ClientLibraryFolder` in `etc/<folderHierarchy>`, con categoria come `guides.I18N.<locale>` e dipendenze come `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` e `guide.common`. &quot;

Aggiungi i seguenti file alla libreria client:

* **i18n.** jsdefinition  `guidelib.i18n`, con pattern di &quot;calendarSymSymbol&quot;,  `datePatterns`,  `timePatterns`,  `dateTimeSymbols`,  `numberPatterns`,  `numberSymbols`,  `currencySymbols`,  `typefaces` per le specifiche XFA descritte in  `<locale>` Impostazioni internazionali specifiche [ ](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). Puoi anche vedere come viene definito per altre impostazioni internazionali supportate in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.** jsdefinition  `guidelib.i18n.strings` e  `guidelib.i18n.LogMessages` per  `<locale>` come definito in  `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.** txtcontenenti quanto segue:

```
i18n.js
LogMessages.js
```

### Aggiungi il supporto delle impostazioni internazionali per il dizionario {#add-locale-support-for-the-dictionary-br}

Esegui questo passaggio solo se il `<locale>` che stai aggiungendo non è compreso tra `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Crea un nodo `nt:unstructured` `languages` in `etc`, se non è già presente.

1. Aggiungi una proprietà stringa con più valori `languages` al nodo, se non è già presente.
1. Aggiungi i valori `<locale>` predefiniti delle impostazioni internazionali `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, se non già presenti.

1. Aggiungi `<locale>` ai valori della proprietà `languages` di `/etc/languages`.

Il simbolo `<locale>` verrà visualizzato in `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Riavvia il server {#restart-the-server}

Riavvia il server AEM per rendere effettive le impostazioni internazionali aggiunte.

## Librerie di esempio per aggiungere supporto per lo spagnolo {#sample-libraries-for-adding-support-for-spanish}

Librerie client di esempio per aggiungere supporto per lo spagnolo

[Ottieni file](assets/sample.zip)
