---
title: Creazione di moduli adattivi con accesso facilitato
seo-title: Creazione di moduli adattivi con accesso facilitato
description: ' AEM Forms fornisce strumenti e consente di creare moduli adattivi con accesso facilitato e rispetta gli standard di accessibilità.'
seo-description: ' AEM Forms fornisce strumenti e consente di creare moduli adattivi con accesso facilitato e rispetta gli standard di accessibilità.'
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
translation-type: tm+mt
source-git-commit: 7e58d1d861f832d073fb178868804995ee8d855b
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---


# Creazione di moduli adattivi con accesso facilitato {#creating-accessible-adaptive-forms}

## Introduzione {#introduction}

Un modulo con accesso facilitato è un modulo utilizzabile da tutti, compresi gli utenti con esigenze particolari. Adobe Experience Manager (AEM) include una serie di funzioni e funzionalità che migliorano l&#39;usabilità dei moduli adattivi per gli utenti con capacità diverse. Questa soluzione consente inoltre agli autori di moduli di creare moduli adattivi con accesso facilitato.

La creazione dell&#39;accessibilità nei moduli adattivi non solo consente al pubblico di accedere al contenuto nel modo più ampio possibile, ma anche quando si forniscono documenti in aree geografiche in cui è richiesta la conformità agli standard di accessibilità.  Guida di AEM Forms agli sviluppatori di moduli conformi agli standard di accessibilità.

Durante la creazione di un modulo adattivo, per creare un modulo adattivo con accesso facilitato l’autore deve tenere conto dei seguenti punti:

* Fornire etichette corrette per i controlli modulo
* Specifica equivalenti di testo per le immagini
* Fornire un contrasto di colore sufficiente
* Verificare che i controlli modulo siano accessibili tramite tastiera

## Specificare le etichette corrette per i controlli modulo {#provide-proper-labels-for-form-controls}

L’etichetta o il titolo di un componente identifica il contenuto rappresentato dal componente modulo. Ad esempio, il testo &quot;Nome&quot; indica agli utenti che devono immettere il proprio nome in un campo di testo. Per essere accessibile dagli assistenti vocali, l&#39;etichetta è associata a un componente modulo a livello di programmazione. In alternativa, il controllo modulo è configurato con ulteriori informazioni di accesso facilitato.

L&#39;etichetta percepita dagli assistenti vocali non deve necessariamente corrispondere alla didascalia visiva. In alcuni casi, potrebbe essere necessario essere più specifici sullo scopo del controllo. Per ciascun oggetto campo di un modulo, le opzioni di accessibilità possono essere utilizzate per specificare ciò che l&#39;assistente vocale annuncia per identificare il campo modulo specifico.

Per utilizzare l&#39;opzione Accessibilità, procedere come segue:

1. Selezionate un componente e toccate ![cmppr](assets/cmppr.png).
1. Fare clic su **Accessibilità** nella barra laterale per scegliere l&#39;opzione di accessibilità desiderata.

### Opzioni di accessibilità nei componenti modulo {#accessibility-options-in-form-components}

![Opzioni di accessibilità nei componenti modulo](assets/accessibility-options.png)

**Gli autori di** TextForm personalizzati forniscono il contenuto dell&#39;opzione di accesso facilitato Campo di testo personalizzato. La tecnologia di supporto, ad esempio gli assistenti vocali, utilizza questo testo personalizzato. L’utilizzo dell’impostazione Titolo è l’opzione migliore nella maggior parte degli scenari. Valutare la possibilità di creare testo personalizzato dell&#39;Reader dello schermo solo quando si utilizza il Titolo o se non è possibile inserire una breve descrizione.

**Breve** descrizionePer la maggior parte dei componenti, la breve descrizione viene visualizzata in fase di esecuzione quando l&#39;utente passa il puntatore sul componente. Potete impostare questa opzione nel campo della descrizione breve, sotto l&#39;opzione di contenuto della guida.

**** Titolo: utilizzate questa opzione per consentire a  AEM Forms di utilizzare l&#39;etichetta visiva associata al campo modulo come testo dell&#39;assistente vocale.

**** Nome: è possibile specificare un valore nel campo Nome della scheda Binding. Il nome non può contenere spazi.

**** Nessuno: se si seleziona Nessuno, l&#39;oggetto modulo non ha un nome nel modulo pubblicato. Nessuna impostazione consigliata per i controlli modulo.

>[!NOTE]
>
>I pulsanti di scelta e le caselle di controllo possono avere solo due opzioni per l&#39;accessibilità, ovvero Testo personalizzato e Titolo.

>[!NOTE]
>
>Per i moduli adattivi basati su XFA, l&#39;opzione di accessibilità è ereditata dalle opzioni di accessibilità impostate in XDP. Le descrizioni comandi di XDP sono mappate sulla descrizione breve e la didascalia sono mappate su Titolo. Le altre opzioni funzionano allo stesso modo.

## Specifica equivalenti di testo per le immagini {#provide-text-equivalents-for-images}

Le immagini possono aiutare a migliorare la comprensione per alcuni utenti. Tuttavia, per gli utenti che utilizzano gli assistenti vocali, le immagini riducono l&#39;accessibilità del modulo. Se scegliete di utilizzare le immagini, fornite descrizioni testuali per tutte le immagini.

Assicurarsi che il testo descriva l&#39;oggetto e la sua funzione nel modulo. Un assistente vocale legge questo testo alternativo quando incontra un&#39;immagine. Un&#39;immagine deve sempre avere un testo alternativo specificato.

Selezionate un componente immagine e toccate ![cmppr](assets/cmppr.png). Nella barra laterale, in Proprietà, specificate il testo alternativo per un’immagine.

![Testo alternativo per un’immagine](assets/image-properties.png)

## Contrasto colore sufficiente {#provide-sufficient-color-contrast}

La progettazione dell&#39;accessibilità prevede la considerazione di ulteriori linee guida per l&#39;utilizzo del colore. Gli autori dei moduli possono utilizzare i colori per migliorare l&#39;aspetto dei moduli, evidenziando diversi componenti. Tuttavia, un uso improprio del colore può rendere un modulo difficile o impossibile da leggere da persone con capacità diverse.

Gli utenti con problemi di vista si affidano a un contrasto elevato tra il testo e lo sfondo per la lettura di contenuti digitali. Senza un contrasto sufficiente, un modulo può diventare difficile, se non impossibile, da leggere per alcuni utenti.

Si consiglia di utilizzare i colori di font e sfondo predefiniti, ossia il contenuto in nero su uno sfondo bianco. Se modificate i colori predefiniti, scegliete un colore di primo piano scuro su un colore di sfondo chiaro o viceversa.

Per ulteriori informazioni sulla modifica del contrasto dei colori e del tema per i moduli adattivi, vedere [Creazione di temi personalizzati per i moduli adattivi.](/help/forms/using/creating-custom-adaptive-form-themes.md)

## Verificare che i controlli modulo siano accessibili tramite tastiera {#ensure-that-form-controls-are-keyboard-accessible}

Un modulo con accesso facilitato può essere compilato completamente utilizzando solo la tastiera o un dispositivo di input equivalente. Gli utenti con mobilità ridotta o problemi di vista possono non avere altra scelta se non utilizzare la tastiera e molti utenti che possono utilizzare il mouse preferiscono l&#39;input della tastiera. Consentendo l&#39;uso dei vari metodi di immissione, non solo si creano moduli con accesso facilitato, ma si creano anche moduli più adatti alle preferenze di tutti gli utenti.

In  AEM Forms sono disponibili le seguenti scelte rapide da tastiera.

| Azione | Scelte rapide da tastiera |
|---|---|
| Spostare il cursore in avanti all&#39;interno di un modulo | Scheda |
| Spostare il cursore all&#39;indietro all&#39;interno di un modulo | Maiusc+Tab |
| Passa al pannello successivo | Alt+Freccia destra |
| Passa al pannello precedente | Alt+Freccia sinistra |
| Reimpostare i dati compilati in un modulo | Alt+R |
| Invio di un modulo | Alt+S | configuring-watched-folder-endpoints.md |