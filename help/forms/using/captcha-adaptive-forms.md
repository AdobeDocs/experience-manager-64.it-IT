---
title: Uso del CAPTCHA nei moduli adattivi
seo-title: Uso del CAPTCHA nei moduli adattivi
description: Scopri come configurare AEM servizio CAPTCHA o Google reCAPTCHA nei moduli adattivi.
seo-description: Scopri come configurare AEM servizio CAPTCHA o Google reCAPTCHA nei moduli adattivi.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---


# Uso del CAPTCHA nei moduli adattivi {#using-captcha-in-adaptive-forms}

CAPTCHA (Test di Turing Pubblico Completamente Automatizzato per dire Computer e Humans Apart) è un programma comunemente utilizzato nelle transazioni online per distinguere tra umani e programmi automatizzati o bot. Rappresenta una sfida e valuta la risposta dell&#39;utente per determinare se si tratta di un essere umano o un bot che interagisce con il sito. Impedisce all&#39;utente di procedere se il test non riesce e contribuisce a rendere sicure le transazioni online impedendo ai bot di pubblicare spam o scopi dannosi.

AEM Forms supporta il CAPTCHA nei moduli adattivi. Puoi utilizzare il servizio reCAPTCHA di Google per implementare CAPTCHA.

>[!NOTE]
>
>AEM Forms supporta solo reCaptcha v2. Qualsiasi altra versione non è supportata.
>
>Il CAPTCHA nei moduli adattivi non è supportato in modalità offline nell’app AEM Forms.

## Configurare il servizio ReCAPTCHA da Google {#google-recaptcha}

Gli autori di moduli possono utilizzare il servizio reCAPTCHA di Google per implementare il CAPTCHA nei moduli adattivi. Offre funzionalità CAPTCHA avanzate per proteggere il tuo sito. Per ulteriori informazioni sul funzionamento di reCAPTCHA, consulta [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![ricontcha](assets/recaptcha.png)

Per implementare il servizio reCAPTCHA in AEM Forms:

1. Ottenere [la coppia di chiavi API reCAPTCHA](https://www.google.com/recaptcha/admin) da Google. Include una chiave del sito e un segreto.
1. Crea un contenitore di configurazione per i servizi cloud.

   1. Vai a **[!UICONTROL Strumenti > Generale > Browser di configurazione]**.
      * Per ulteriori informazioni, consulta la [documentazione del browser di configurazione](/help/sites-administering/configurations.md) .
   1. Effettua le seguenti operazioni per abilitare la cartella globale per le configurazioni cloud o salta questo passaggio per creare e configurare un’altra cartella per le configurazioni del servizio cloud.

      1. Nel Browser configurazioni, seleziona la cartella **[!UICONTROL global]** e tocca **[!UICONTROL Properties]**.
      1. Nella finestra di dialogo Proprietà configurazione, abilita **[!UICONTROL Configurazioni cloud]**.
      1. Tocca **[!UICONTROL Salva e chiudi]** per salvare la configurazione e uscire dalla finestra di dialogo.
   1. Nel Browser configurazioni, tocca **[!UICONTROL Crea]**.
   1. Nella finestra di dialogo Crea configurazione , specifica un titolo per la cartella e abilita **[!UICONTROL Configurazioni cloud]**.
   1. Tocca **[!UICONTROL Crea]** per creare la cartella abilitata per le configurazioni del servizio cloud.


1. Configura il servizio cloud per reCAPTCHA.

   1. Sull&#39;istanza di authoring di AEM, vai a ![strumenti](assets/tools.png) > **Cloud Services**.
   1. Tocca **[!UICONTROL reCAPTCHA]**. Viene visualizzata la pagina Configurazioni . Seleziona il contenitore di configurazione creato nel passaggio precedente e tocca **[!UICONTROL Crea]**.
   1. Specifica nome, chiave del sito e chiave segreta per il servizio reCAPTCHA e tocca **[!UICONTROL Crea]** per creare la configurazione del servizio cloud.
   1. Nella finestra di dialogo Modifica componente , specifica il sito e le chiavi segrete ottenute nel passaggio 1. Tocca **[!UICONTROL Salva impostazioni]**, quindi tocca **[!UICONTROL OK]** per completare la configurazione.

   Una volta configurato il servizio reCAPTCHA, è disponibile per l’uso nei moduli adattivi. Per ulteriori informazioni, consulta [Uso del CAPTCHA nei moduli adattivi](#using-captcha).

## Utilizzare il CAPTCHA nei moduli adattivi {#using-captcha}

Per utilizzare il CAPTCHA nei moduli adattivi:

1. Apri un modulo adattivo in modalità di modifica.

   >[!NOTE]
   >
   >Assicurati che il contenitore di configurazione selezionato durante la creazione del modulo adattivo contenga il servizio cloud reCAPTCHA. È inoltre possibile modificare le proprietà del modulo adattivo per modificare il contenitore di configurazione associato al modulo.

1. Dal browser Componenti, trascina il componente **[!UICONTROL Captcha]** nel modulo adattivo.

   >[!NOTE]
   >
   >L’utilizzo di più componenti Captcha in un modulo adattivo non è supportato. Inoltre, si sconsiglia di utilizzare il CAPTCHA in un pannello contrassegnato per il caricamento lento o in un frammento.

   >[!NOTE]
   >
   >Captcha è sensibile al tempo e scade tra circa un minuto. Pertanto, si consiglia di posizionare il componente Captcha immediatamente prima del pulsante Invia nel modulo adattivo.

1. Seleziona il componente Captcha aggiunto e tocca ![cmppr](assets/cmppr.png) per modificarne le proprietà.
1. Specifica un titolo per il widget CAPTCHA. Il valore predefinito è **Captcha**. Selezionare **[!UICONTROL Nascondi titolo]** se non si desidera che il titolo venga visualizzato.
1. Dal menu a discesa **[!UICONTROL Servizio Captcha]** , seleziona **[!UICONTROL reCaptcha]** per abilitare il servizio reCAPTCHA se lo hai configurato come descritto in [Servizio ReCAPTCHA di Google](#google-recaptcha). Seleziona una configurazione dal menu a discesa Impostazioni . Inoltre, seleziona la dimensione come **[!UICONTROL Normale]** o **[!UICONTROL Compatta]** per il widget reCAPTCHA.

   >[!NOTE]
   >
   >Non selezionare **[!UICONTROL Predefinito]** dal menu a discesa del servizio Captcha perché il servizio AEM CAPTCHA predefinito è obsoleto.

1. Salva le proprietà.

Il servizio reCAPTCHA è abilitato nel modulo adattivo. Puoi visualizzare l’anteprima del modulo e vedere come funziona il CAPTCHA.
