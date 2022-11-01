---
title: Applicazione di firme elettroniche a un modulo utilizzando firme a mano libera
seo-title: Apply electronic signatures to a form using scribble signatures
description: Firma dei moduli tramite scarabocchio
seo-description: Signing forms using scribble
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
exl-id: a870c4b7-4040-4bd8-b477-286ebe6a4b01
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Applicazione di firme elettroniche a un modulo utilizzando firme a mano libera {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

È possibile utilizzare **Firma scarabocchio** componente e **Passaggio firma** componente per disegnare (scarabocchiare) la firma su un modulo adattivo. Il componente Passaggio firma visualizza una versione PDF del modulo adattivo. Per utilizzare il componente Passaggio firma è necessaria l’opzione Documento di record abilitata o i moduli adattivi basati su modelli di modulo.

Entrambi i componenti dispongono di una finestra, come illustrato di seguito, per firmare un modulo. Puoi anche fare clic sull’icona di geolocalizzazione ![aem_6_3_geolocalizzazione](assets/aem_6_3_geolocation.png) per aggiungere una geolocalizzazione alla firma.

![Finestra di dialogo dei segni di scorrimento](assets/scribble-signature.png)

## Configurare un modulo adattivo per l’utilizzo della firma digitale {#configure-an-adaptive-form-to-use-scribble-signature}

1. Crea un modulo adattivo basato su modello di modulo abilitato per l’opzione Documento di record. Per informazioni dettagliate, consulta [Creazione di un modulo adattivo](/help/forms/using/creating-adaptive-form.md).
1. Trascina e rilascia la **Firma scarabocchio** dal browser Componenti al modulo adattivo.
1. Tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del componente Firma digitale. Configura le proprietà del componente Firma digitale.
1. Trascina il componente Passaggio firma dal browser Componenti al modulo adattivo.

   >[!NOTE]
   >
   >Il componente Passaggio firma occupa la larghezza completa disponibile per il modulo. Si consiglia di non avere alcun altro componente nella sezione contenente il componente Passaggio firma.

1. Nel browser Contenuto, tocca **Contenitore modulo** e tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del contenitore Modulo adattivo. Passa a **Contenitore di moduli adattivi** > **Firma elettronica** e deselezionare la **Abilita Acrobat Sign** opzione . Tocca Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per salvare le modifiche.

   >[!NOTE]
   >
   >Quando si aggiunge un componente Passaggio firma a un modulo adattivo, l’opzione Abilita Acrobat Sign viene selezionata automaticamente.

1. Tocca **Configura** ![configurare](assets/configure.png) icona. Apre il browser delle proprietà e visualizza le proprietà del passaggio Firma. Configura le seguenti proprietà:

   * **Nome elemento**: Specifica il nome del componente.
   * **Titolo:** Specifica un titolo univoco del componente.
   * **Messaggio del modello:** Specificare il messaggio da visualizzare durante il caricamento del PDF firma. I servizi Acrobat Sign impiegano un po&#39; di tempo per preparare e caricare signature PDF.
   * **Servizio di firma:** Seleziona la **Firma scarabocchio** opzione .
   * **Classe CSS**: Specifica la classe CSS della libreria client, se presente. Si consiglia di utilizzare [temi](/help/forms/using/themes.md) e [stili in linea](/help/forms/using/inline-style-adaptive-forms.md) anziché CSS Class.

   Tocca Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per salvare le modifiche. La firma è configurata correttamente.

   Ora, quando si compila un modulo, viene visualizzata una versione PDF del modulo adattivo e vengono fornite le opzioni per firmare il documento PDF. Per informazioni dettagliate, consulta [Firma digitale di un modulo adattivo](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## Firma digitale di un modulo adattivo {#sign-an-adaptive-form-using-scribble-signature}

1. Dopo aver compilato un modulo adattivo e aver raggiunto la pagina Passaggio firma, viene visualizzata la schermata della firma.

   ![Schermata della firma per la pagina EchoSign](assets/esignscribblesign.jpg)

1. Fai clic su **[!UICONTROL Sign]**. Viene visualizzata la finestra di dialogo del segno di scarabocchio. Firma il modulo e fai clic su Fine ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) per salvare la firma.

   ![Finestra di dialogo dei segni di scorrimento](assets/scribblewidget.jpg)

1. Fare clic su completa per completare il processo di firma.

   ![Completare il processo di firma](assets/scribblecomplete.jpg)

Le firme vengono aggiunte al modulo e il controllo modulo si sposta nel pannello successivo.
