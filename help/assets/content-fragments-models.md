---
title: Modelli per frammenti di contenuto
seo-title: Content Fragment Models
description: I modelli per frammenti di contenuto vengono utilizzati per creare frammenti di contenuto con contenuto strutturato.
seo-description: Content Fragment Models are used to create content fragments with structured content.
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
exl-id: 39ed07ec-54a6-4387-8435-e891726c411c
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 61%

---

# Modelli per frammenti di contenuto {#content-fragment-models}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Alcune funzionalità dei frammenti di contenuto richiedono l’applicazione di [AEM 6.4 Service Pack 2 (6.4.2.0) o successivo](../release-notes/sp-release-notes.md).

I modelli per frammenti di contenuto definiscono la struttura del contenuto [frammenti di contenuto](content-fragments.md).

## Abilita modelli di frammenti di contenuto {#enable-content-fragment-models}

>[!CAUTION]
>
>Se non si abilita **[!UICONTROL Modelli per frammenti di contenuto]**, **[!UICONTROL Crea]** non sarà disponibile per la creazione di nuovi modelli.

Per abilitare i modelli di frammento di contenuto è necessario:

* Abilitare l’utilizzo di modelli di frammenti di contenuto nella gestione della configurazione
* Applicare la configurazione alla cartella Risorse

### Abilitare i modelli di frammenti di contenuto in Configuration Manager {#enable-content-fragment-models-in-configuration-manager}

A [creare un nuovo modello di frammento di contenuto](#creating-a-content-fragment-model) voi **deve** per prima cosa attivali utilizzando Configuration Manager:

1. Accedi a **[!UICONTROL Strumenti]**, **[!UICONTROL Generali]**, quindi apri **[!UICONTROL Browser configurazioni]**.
   * Consulta la sezione [Documentazione del browser di configurazione](/help/sites-administering/configurations.md) per ulteriori informazioni.
1. Seleziona la posizione appropriata per il sito web.
1. Utilizza **[!UICONTROL Crea]** per aprire la finestra di dialogo, in cui:

   1. Specificare un **[!UICONTROL Titolo]**.
   1. Seleziona **[!UICONTROL Modelli per frammenti di contenuto]** per consentirne l&#39;uso.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Seleziona **[!UICONTROL Crea]** per salvare la definizione.

### Applica la configurazione alla cartella Risorse {#apply-the-configuration-to-your-assets-folder}

Quando la configurazione **[!UICONTROL globale]** è abilitato per i modelli di frammenti di contenuto, quindi tutti i modelli creati dagli utenti possono essere utilizzati in qualsiasi cartella Assets.

Per utilizzare altre configurazioni con una cartella Risorse simile, ovvero escludendo il formato globale, è necessario definire la connessione. Questa operazione viene eseguita dalla voce **[!UICONTROL Configurazione]** della scheda **[!UICONTROL Cloud Services]** della finestra **[!UICONTROL Proprietà cartella]** della cartella specifica.

## Creazione di un modello di frammento di contenuto {#creating-a-content-fragment-model}

1. Passa a **[!UICONTROL Strumenti]**, **[!UICONTROL Risorse]**, quindi apri **[!UICONTROL Modelli per frammenti di contenuto]**.
1. Passa alla cartella appropriata [configurazione](#enable-content-fragment-models).
1. Utilizza **[!UICONTROL Crea]** per aprire la procedura guidata.

   >[!CAUTION]
   >
   >Se l’[utilizzo di modelli per frammenti di contenuto non è stato abilitato](#enable-content-fragment-models), l’opzione **Crea** non sarà disponibile.

1. Specifica il **[!UICONTROL Titolo modello]**. Se necessario, puoi anche aggiungere una **[!UICONTROL Descrizione]**.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Utilizza **[!UICONTROL Crea]** per salvare il modello vuoto. Un messaggio indica il successo dell’azione: puoi selezionare **[!UICONTROL Apri]** per modificare immediatamente il modello, oppure **[!UICONTROL Fine]** per tornare alla console.

## Definizione del modello per frammenti di contenuto {#defining-your-content-fragment-model}

Il modello per frammenti di contenuto definisce in modo efficace la struttura dei frammenti di contenuto risultanti. Utilizzando l&#39;editor modelli è possibile aggiungere e configurare i campi richiesti:

>[!CAUTION]
>
>La modifica di un modello per frammento di contenuto esistente può avere un impatto sui frammenti dipendenti.

1. Passa a **[!UICONTROL Strumenti]**, **[!UICONTROL Risorse]**, quindi apri **[!UICONTROL Modelli per frammenti di contenuto]**.

1. Passa alla cartella contenente il modello per frammenti di contenuto.
1. Apri il modello che desideri **[!UICONTROL modificare]** utilizzando l’azione rapida oppure selezionando il modello e quindi l’azione dalla barra degli strumenti.

   Una volta aperto, l’editor modelli mostra:

   * a sinistra: campi già definiti
   * a destra: **[!UICONTROL Tipi di dati]** disponibili per la creazione di campi, oltre alle **[!UICONTROL Proprietà]** da utilizzare dopo la creazione.

   >[!NOTE]
   >
   >Quando un campo è **Obbligatorio**, **Etichetta** indicato nel riquadro a sinistra sarà contrassegnato con un asterisco (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **Per aggiungere un campo**

   * Trascina un tipo di dati obbligatorio nella posizione desiderata per un campo:

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * Una volta aggiunto un campo al modello, il pannello di destra visualizza le **Proprietà** che possono essere definite per quel particolare tipo di dati. Qui puoi definire ciò che è necessario per quel campo. Ad esempio:

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **Per rimuovere un campo**

   Seleziona il campo richiesto, quindi tocca o fai clic sull’icona del cestino. Viene richiesto di confermare l’operazione.

   ![cf-32](assets/cf-32.png)

1. Dopo aver aggiunto tutti i campi obbligatori e definito le proprietà, utilizza **[!UICONTROL Salva]** per mantenere la definizione. Ad esempio:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Eliminazione di un modello per frammenti di contenuto {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>L’eliminazione di un modello per frammenti di contenuto può avere un impatto sui frammenti dipendenti.

Per eliminare un modello per frammenti di contenuto:

1. Passa a **[!UICONTROL Strumenti]**, **[!UICONTROL Risorse]**, quindi apri **[!UICONTROL Modelli per frammenti di contenuto]**.

1. Passa alla cartella contenente il modello per frammenti di contenuto.
1. Seleziona il modello e poi **[!UICONTROL Elimina]** dalla barra degli strumenti.

   >[!NOTE]
   >
   >Se ci sono riferimenti al modello, viene visualizzato un avviso. Agisci di conseguenza.

## Pubblicazione di un modello per frammenti di contenuto {#publishing-a-content-fragment-model}

I modelli per frammenti di contenuto devono essere pubblicati quando/prima che vengano pubblicati eventuali frammenti di contenuto dipendenti.

Per pubblicare un modello per frammenti di contenuto:

1. Passa a **[!UICONTROL Strumenti]**, **[!UICONTROL Risorse]**, quindi apri **[!UICONTROL Modelli per frammenti di contenuto]**.

1. Passa alla cartella contenente il modello per frammenti di contenuto.
1. Seleziona il modello e poi **[!UICONTROL Pubblica]** dalla barra degli strumenti.

   >[!NOTE]
   >
   >Se pubblichi un frammento di contenuto per il quale il modello non è ancora stato pubblicato, questo sarà segnalato in un elenco di selezione e il modello verrà pubblicato con il frammento.
