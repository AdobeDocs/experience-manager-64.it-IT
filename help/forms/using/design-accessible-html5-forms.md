---
title: Progettazione di moduli HTML5 con accesso facilitato
seo-title: Progettazione di moduli HTML5 con accesso facilitato
description: I moduli HTML5 utilizzano lo standard di accessibilità ARIA HTML5. Questi moduli supportano la navigazione a schede e sono certificati compatibili con gli assistenti vocali comuni.
seo-description: I moduli HTML5 utilizzano lo standard di accessibilità ARIA HTML5. Questi moduli supportano la navigazione a schede e sono certificati compatibili con gli assistenti vocali comuni.
uuid: b7757079-5f06-4818-8488-11d67cbe3522
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: ccc59dd5-c0cf-415a-b71a-5bc0cf452ede
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Progettazione di moduli HTML5 con accesso facilitato {#designing-accessible-html-forms}

I moduli HTML5 utilizzano lo standard di accessibilità ARIA HTML5 per generare moduli HTML con accesso facilitato. Questi moduli supportano la navigazione a schede (ad eccezione di Mozilla FireFox) e sono certificati compatibili con gli assistenti vocali comuni. Per generare un modulo HTML5 con buone funzioni di accessibilità, progettare il modello di modulo XFA in base ad alcune linee guida [di progettazione](/help/forms/using/best-practices-for-html5-forms.md)di base. Le linee guida della progettazione includono la configurazione dell&#39;ordine di tabulazione corretto e la fornitura del contenuto di testo parlato per ciascun controllo modulo. AEM Forms Designer supporta l&#39;impostazione di questi attributi di controllo per la generazione di moduli PDF e HTML5 con accesso facilitato.

*Nota: la navigazione a schede non copre i campi protetti, ad esempio i campi di calcolo che mostrano la somma dei valori. Affinché l&#39;assistente vocale possa leggere il valore di un campo protetto, posizionare un campo di sola lettura vuoto sopra o accanto al campo protetto. Assegnare il valore del campo protetto al nuovo campo di sola lettura. L&#39;assistente vocale o la navigazione a schede possono selezionare questo campo di sola lettura e parlare come il valore del campo protetto.*

AEM Forms Designer offre diverse opzioni di testo parlato che possono essere trasmesse agli assistenti vocali. Per ciascun oggetto di un modulo, l&#39;utente può specificare una delle diverse impostazioni per il testo dell&#39;assistente vocale:

* Testo personalizzato dell&#39;assistente vocale, che può essere impostato utilizzando la palette Accessibilità. Gli autori possono annotare i nomi dei pulsanti e dei campi, nonché la loro funzione.
* Descrizioni comandi, che possono essere impostate nella palette Accessibilità.
* Didascalie per i campi del modulo.
* Nomi degli oggetti, come specificato nell&#39;opzione Nome della scheda Binding.

![accessibilità](assets/accessibility.png)

Quando più opzioni come la descrizione comandi, il testo dell&#39;assistente vocale e la didascalia sono disponibili in un controllo Modulo, l&#39;assistente vocale utilizza solo una di queste proprietà. L&#39;ordine predefinito è Testo personalizzato dell&#39;assistente vocale, descrizione comandi, didascalia e nome. You can override the default order using the Screen Reader **Precedence** option in the Accessibility palette.
