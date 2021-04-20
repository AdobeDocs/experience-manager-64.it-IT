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
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Progettazione di moduli HTML5 accessibili {#designing-accessible-html-forms}

I moduli HTML5 utilizzano lo standard di accessibilità ARIA HTML5 per generare moduli HTML con accesso facilitato. Questi moduli supportano la navigazione a schede (ad eccezione di Mozilla FireFox) e sono certificati compatibili con gli assistenti vocali comuni. Per generare un modulo HTML5 con buone funzioni di accessibilità, progettare il modello di modulo XFA in base ad alcune [linee guida di progettazione di base](/help/forms/using/best-practices-for-html5-forms.md). Le linee guida di progettazione includono la configurazione dell’ordine di tabulazione corretto e la fornitura del contenuto di testo parlato per ciascun controllo del modulo. AEM Forms Designer supporta l’impostazione di questi attributi per la generazione di moduli PDF e HTML5 accessibili.

*Nota:la navigazione a schede non include campi protetti, ad esempio campi di calcolo che visualizzano la somma dei valori. Per consentire all’assistente vocale di leggere il valore di un campo protetto, posizionare un campo di sola lettura vuoto sopra o accanto al campo protetto. Assegnare il valore del campo protetto al nuovo campo di sola lettura. L&#39;assistente vocale o la navigazione a schede può scegliere questo campo di sola lettura e parlare il valore del campo protetto.*

AEM Forms Designer include diverse opzioni di testo parlato che possono essere passate agli assistenti vocali. Per ciascun oggetto di un modulo, l’utente può specificare una delle diverse impostazioni per il testo dell’assistente vocale:

* Testo personalizzato dell’assistente vocale, che può essere impostato utilizzando la palette Accessibilità. Gli autori possono annotare i nomi dei pulsanti e dei campi e il loro scopo.
* Le descrizioni comandi possono essere impostate nella palette Accessibilità.
* Sottotitoli per i campi del modulo.
* Nomi degli oggetti, come specificato nell’opzione Nome della scheda Binding.

![accessibilità](assets/accessibility.png)

Quando in un controllo Form sono disponibili più opzioni quali la descrizione comandi, il testo del Reader dello schermo e la didascalia, il Reader dello schermo utilizza solo una di queste proprietà. L’ordine predefinito è Testo personalizzato Reader schermo, descrizione comandi, Didascalia e Nome. È possibile ignorare l’ordine predefinito utilizzando l’opzione Reader schermata **Precedenza** nella palette Accessibilità.
