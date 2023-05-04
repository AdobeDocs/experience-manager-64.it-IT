---
title: Aggiunta di informazioni dai dati utente ai metadati di invio del modulo
seo-title: Adding information from user data to form submission metadata
description: Scopri come aggiungere informazioni ai metadati di un modulo inviato con i dati forniti dall’utente.
seo-description: Learn how to add information to metadata of a submitted form with user provided data.
uuid: b33ad1c8-d6c9-421d-8a3a-a29d17acfb18
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 93961c9c-b46c-4233-b070-7343245255d1
feature: Adaptive Forms
exl-id: 7e3e9db6-13da-49b4-a9f9-79e76be9ea19
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 1%

---

# Aggiunta di informazioni dai dati utente ai metadati di invio del modulo {#adding-information-from-user-data-to-form-submission-metadata}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile utilizzare i valori immessi in un elemento del modulo per calcolare i campi di metadati di una bozza o di un invio di un modulo. I metadati consentono di filtrare il contenuto in base ai dati utente. Ad esempio, un utente immette John Doe nel campo nome del modulo. È possibile utilizzare queste informazioni per calcolare i metadati che possono categorizzare questo invio sotto le iniziali JD.

Per calcolare i campi di metadati con i valori immessi dall’utente, aggiungere elementi del modulo nei metadati. Quando un utente immette un valore in tale elemento, uno script utilizza il valore per calcolare le informazioni. Queste informazioni vengono aggiunte nei metadati. Quando aggiungi un elemento come campo di metadati, fornisci una chiave per esso. La chiave viene aggiunta come campo nei metadati e le informazioni calcolate vengono registrate su di essa.

Ad esempio, un&#39;impresa di assicurazione sanitaria pubblica un modulo. In questo modulo, un campo acquisisce l’età degli utenti finali. Il cliente desidera controllare tutti gli invii in una determinata fascia di età dopo che un certo numero di utenti ha inviato il modulo. Anziché esaminare tutti i dati che si complicano con l’aumento del numero di moduli, i metadati aggiuntivi consentono al cliente. L’autore del modulo può configurare quali proprietà/dati compilati dall’utente finale vengono memorizzati al livello superiore in modo da semplificare la ricerca. I metadati aggiuntivi sono informazioni compilate dall’utente memorizzate al livello superiore del nodo di metadati, come configurato dall’autore.

Considerare un altro esempio di modulo che acquisisce l’ID e-mail e il numero di telefono. Quando un utente visita il modulo in modo anonimo e lo abbandona, l’autore può configurare il modulo per il salvataggio automatico dell’ID e-mail e del numero di telefono. Questo modulo viene salvato automaticamente e il numero di telefono e l’ID e-mail vengono memorizzati nel nodo di metadati della bozza. Un caso d’uso di questa configurazione è il dashboard di gestione dei lead.

## Aggiunta di elementi modulo ai metadati {#adding-form-elements-to-metadata}

Per aggiungere un elemento nei metadati, effettua le seguenti operazioni:

1. Apri il modulo adattivo in modalità di modifica.

   Per aprire il modulo in modalità di modifica, nel gestore moduli selezionare il modulo e toccare **Apri**.

1. In modalità di modifica, seleziona un componente, tocca ![a livello di campo](assets/field-level.png) > **Contenitore di moduli adattivi**, quindi tocca ![cmppr](assets/cmppr.png).
1. Nella barra laterale, fai clic su **Metadati**.
1. Nella sezione Metadati , fai clic su **Aggiungi**.
1. Utilizzare il campo Valore della scheda Metadati per aggiungere script. Gli script aggiunti raccolgono i dati dagli elementi del modulo e calcolano i valori inviati ai metadati.

   Ad esempio: **true** è registrato nei metadati se l’età immessa è superiore a 21 anni, e **false** viene registrato se è inferiore a 21. Immetti il seguente script nella scheda Metadati :

   `(agebox.value >= 21) ? true : false`

   ![Script metadati](assets/add-element-metadata.png)
   **Figura:** *Script immesso nella scheda Metadati*

1. Fai clic su **OK**.

Dopo che un utente immette i dati nell’elemento selezionato come campo di metadati, le informazioni calcolate vengono registrate nei metadati. Puoi visualizzare i metadati nell’archivio configurato per memorizzare i metadati.

## Visualizzazione dei metadati aggiornati di invio del modulo: {#seeing-updated-form-nbsp-submission-metadata}

Per l&#39;esempio precedente, i metadati sono memorizzati nell&#39;archivio CRX. I metadati si presentano come segue:

![ingresso metadata](assets/metadata-entry.png)

Se aggiungi un elemento casella di controllo nei metadati, i valori selezionati vengono memorizzati come stringa separata da virgole. Ad esempio, è possibile aggiungere un componente casella di controllo nel modulo e specificarne il nome come `checkbox1`. Nelle proprietà del componente della casella di controllo è possibile aggiungere le voci Patente di guida, Numero di previdenza sociale e Passaporto per i valori 0, 1 e 2.

![Memorizzazione di più valori da una casella di controllo](assets/checkbox-metadata.png)

È possibile selezionare un contenitore di moduli adattivi e aggiungere una chiave di metadati nelle proprietà del modulo `cb1` quali negozi `checkbox1.value`e pubblicare il modulo. Quando un cliente compila il modulo, seleziona le opzioni Passport e Social Security Number nel campo della casella di controllo. I valori 1 e 2 sono memorizzati come 1, 2 nel campo cb1 dei metadati di invio.

![Voce di metadati per più valori selezionati in un campo casella di controllo](assets/metadata-entry-1.png)

>[!NOTE]
>
>L&#39;esempio precedente è solo a scopo di apprendimento. Verifica di cercare i metadati nella posizione corretta configurata nell’implementazione AEM Forms.
