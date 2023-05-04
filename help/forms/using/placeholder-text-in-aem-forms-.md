---
title: Testo segnaposto in AEM Forms
seo-title: Placeholder text in AEM Forms
description: Il testo segnaposto ha lo scopo di aiutare l’utente a inserire dati quando il controllo non ha alcun valore. Può trattarsi di un valore di esempio o di una breve descrizione del formato previsto.
seo-description: Placeholder text is intended to aid the user with data entry when the control has no value. It could be a sample value or a brief description of the expected format.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: Adaptive Forms
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 3%

---

# Testo segnaposto in AEM Forms {#placeholder-text-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il testo segnaposto rappresenta una parola o una frase breve. Ha lo scopo di aiutare l’utente a inserire dati quando il controllo non ha alcun valore. Un testo segnaposto può essere un valore di esempio o una breve descrizione del formato previsto. Il testo segnaposto viene visualizzato prima che l’utente immetta un valore e viene rimosso quando l’utente immette o seleziona un valore.

>[!NOTE]
>
>Il testo segnaposto, se specificato, deve avere un valore che non contenga nuovi caratteri di riga.

![Componente data con e senza testo segnaposto](assets/dat-picker-place-holder-text.png)

**A.** Componente data con testo segnaposto **B.** Componente data senza testo segnaposto

AEM Forms supporta il testo segnaposto per i campi Casella password, Selezione data, Casella numerica e Casella di testo.\
I testi segnaposto non sono supportati per il widget di data nativo di HTML5. Per specificare un testo segnaposto:

1. Fai clic con il pulsante destro del mouse su un componente che supporta il testo segnaposto e fai clic su **Modifica**. Viene visualizzata la finestra di dialogo Modifica componente.

1. Apri **Titolo e testo** scheda .
1. Specifica una parola o una frase breve nel **Casella di testo segnaposto**. Fai clic su **OK**.

>[!NOTE]
>
>Il testo segnaposto non è supportato in Microsoft Internet Explorer 9.
