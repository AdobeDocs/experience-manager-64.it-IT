---
title: 'Gestisci le risorse in [!DNL Adobe Experience Manager Assets]. [!DNL Adobe Stock] '
description: Cerca, recupera, rilascia la licenza e gestisci [!DNL Adobe Stock] risorse all’interno di [!DNL Adobe Experience Manager]. Utilizza le risorse con licenza come qualsiasi altra risorsa digitale.
contentOwner: AG
feature: Search,Adobe Stock
role: User,Admin
exl-id: f360abaf-a812-46ed-a160-ff569b6bec1c
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 13%

---

# Utilizzare le risorse [!DNL Adobe Stock] in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

Le organizzazioni possono integrare il proprio piano [!DNL Adobe Stock] enterprise con [!DNL Experience Manager Assets] per garantire che le risorse concesse in licenza siano ampiamente disponibili per i loro progetti creativi e di marketing, con le potenti funzionalità di gestione delle risorse di [!DNL Experience Manager].

[!DNL Adobe Stock]Il servizio offre a designer e aziende l’accesso a milioni di foto, immagini vettoriali, illustrazioni, video, modelli e risorse 3D di alta qualità, curate ed esenti da royalty, per qualsiasi progetto creativo. [!DNL Experience Manager] gli utenti possono trovare, visualizzare in anteprima e concedere in licenza rapidamente  [!DNL Adobe Stock] le risorse salvate in  [!DNL Experience Manager] senza uscire dall’ [!DNL Experience Manager] interfaccia.

## Prerequisiti {#prerequisites}

L&#39;integrazione richiede un [piano Adobe Stock aziendale](https://stockenterprise.adobe.com/) e [!DNL Experience Manager] 6.4 con almeno Service Pack 2 implementato. Per i dettagli del service pack [!DNL Experience Manager] 6.4, consulta le seguenti [note sulla versione](/help/release-notes/sp-release-notes.md).

## Integrare [!DNL Experience Manager] e [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

Per consentire la comunicazione tra [!DNL Experience Manager] e [!DNL Adobe Stock], crea una configurazione IMS e una configurazione [!DNL Adobe Stock] in [!DNL Experience Manager].

>[!NOTE]
>
>Solo gli amministratori [!DNL Experience Manager] e gli amministratori [!DNL Admin Console] di un&#39;organizzazione possono eseguire l&#39;integrazione in quanto richiede i privilegi di amministratore.

### Creare una configurazione IMS {#create-an-ims-configuration}

1. Nell&#39;interfaccia utente [!DNL Experience Manager] , passa a **[!UICONTROL Strumenti]** > **[!UICONTROL Sicurezza]** > **[!UICONTROL Configurazioni Adobe IMS]**. Fai clic su **[!UICONTROL Crea]** e seleziona **[!UICONTROL Soluzione cloud]** > **[!UICONTROL Adobe Stock]**.
1. Riutilizzare un certificato esistente o selezionare **[!UICONTROL Crea nuovo certificato]**.
1. Fai clic su **[!UICONTROL Crea certificato]**. Una volta creata, scarica la chiave pubblica. Fai clic su **[!UICONTROL Avanti]**. Lascia aperta la schermata [!UICONTROL Configurazione account tecnico Adobe IMS] per fornire a breve i valori richiesti.
1. Accedi a [Adobe Developer Console](https://console.adobe.io). Assicurati che il tuo account disponga delle autorizzazioni di amministratore per l’organizzazione per la quale è richiesta l’integrazione.
1. Fai clic su **[!UICONTROL Crea nuovo progetto]** e fai clic su **[!UICONTROL Aggiungi API]**. Seleziona **[!UICONTROL Adobe Stock]** dall’elenco delle API disponibili. Selezionare [!UICONTROL OAUTH 2.0 Web].
1. Fornisci valori **[!UICONTROL URI di reindirizzamento predefiniti]** e **[!UICONTROL pattern URI di reindirizzamento]**. Fai clic su **[!UICONTROL Salva API configurata]**. Copia l&#39;ID e il segreto generati.
1. Nella schermata [!UICONTROL Configurazione account tecnico Adobe IMS], inserisci i valori nelle caselle **[!UICONTROL Titolo]**, **[!UICONTROL Server autorizzazioni]**, **[!UICONTROL Chiave API]**, **[!UICONTROL Segreto client]** e **[!UICONTROL Payload]**. Per informazioni dettagliate su questi valori, consulta [Avvio rapido autenticazione JWT](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL when the new URL is available. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### Crea la configurazione [!DNL Adobe Stock] in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. Nell&#39;interfaccia utente [!DNL Experience Manager] , passa a **[!UICONTROL Strumenti]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Fai clic su **[!UICONTROL Crea]** per creare una configurazione e associarla alla configurazione IMS esistente. Seleziona `PROD` come parametro di ambiente.
1. Nel campo **[!UICONTROL Percorso risorse in licenza]** , lascia una posizione invariata. Non modificare il percorso in cui memorizzare le risorse [!DNL Adobe Stock].
1. Completa la creazione aggiungendo tutte le proprietà richieste. Fai clic su **[!UICONTROL Salva e chiudi]**.
1. Aggiungi utenti o gruppi [!DNL Experience Manager], che possono concedere la licenza per le risorse.

>[!NOTE]
>
>Se sono presenti più configurazioni [!DNL Adobe Stock], seleziona la configurazione desiderata nel pannello Preferenze utente (**[!UICONTROL AEM]** > **[!UICONTROL Icona utente]** > **[!UICONTROL Preferenze utente]** > **[!UICONTROL Configurazione stock]**).

## Utilizzare e gestire le risorse [!DNL Adobe Stock] in [!DNL Experience Manager] {#usemanage}

Utilizzando questa funzionalità, le organizzazioni possono consentire agli utenti di utilizzare le risorse [!DNL Adobe Stock] in [!DNL Experience Manager Assets]. Dall’interno dell’interfaccia utente [!DNL Experience Manager], gli utenti possono cercare le risorse [!DNL Adobe Stock] e concedere in licenza le risorse richieste.

Una volta concessa la licenza a una risorsa [!DNL Adobe Stock] in [!DNL Experience Manager], questa può essere utilizzata e gestita come una tipica risorsa. In [!DNL Experience Manager], gli utenti possono cercare e visualizzare in anteprima le risorse; copiare e pubblicare le risorse; condividere le risorse su [!DNL Brand Portal]; accedere alle risorse e utilizzarle tramite l’app desktop [!DNL Experience Manager]; e così via.

![Cercare risorse Adobe Stock e filtrare i risultati dall’area di lavoro Adobe Experience Manager](assets/adobe-stock-search-results-workspace.png)

*Figura: Cerca  [!DNL Adobe Stock] risorse e filtra i risultati dall’ [!DNL Experience Manager] interfaccia.*

**A.**[!DNL Adobe Stock] Cerca risorse simili a quelle di chi è fornito l’ID **B.** Cerca risorse corrispondenti alla tua selezione di forma o orientamento. **C.** Cerca uno o più dei tipi di risorse supportati **D.** Apri o comprimi il riquadro Filtri **E.** Procurati la licenza relativa e salva la risorsa selezionata in [!DNL Experience Manager]**F.**[!DNL Experience Manager] Salva la risorsa in applicando la filigrana **G.**[!DNL Adobe Stock] Sul sito web di , esplora le risorse simili a quella selezionata **H.**[!DNL Adobe Stock] Visualizza le risorse selezionate sul sito web di **I.** Numero di risorse selezionate proveniente dai risultati della ricerca **J.** Passaggio tra la vista a schede e la vista a elenco

### Trovare risorse {#find-assets}

Gli utenti [!DNL Experience Manager] possono cercare le risorse in entrambi, [!DNL Experience Manager] e [!DNL Adobe Stock]. Quando il percorso di ricerca non è limitato a [!DNL Adobe Stock], vengono visualizzati i risultati di ricerca da [!DNL Experience Manager] e [!DNL Adobe Stock].

* Per cercare le risorse [!DNL Adobe Stock], fai clic su **[!UICONTROL Navigazione]** > **[!UICONTROL Risorse]** > **[!UICONTROL Ricerca in Adobe Stock]**.

* Per cercare le risorse tra [!DNL Adobe Stock] e [!DNL Experience Manager Assets], fai clic su Cerca ![icona_ricerca](assets/search_icon.png).

In alternativa, inizia a digitare `Location: Adobe Stock` nella barra di ricerca per selezionare le risorse [!DNL Adobe Stock]. [!DNL Experience Manager] offre funzionalità di filtro avanzate per le risorse ricercate, che consentono agli utenti di accedere rapidamente da zero alle risorse richieste utilizzando i filtri, ad esempio i tipi di risorse supportate, l’orientamento dell’immagine e lo stato con licenza.

>[!NOTE]
>
>Le risorse ricercate da [!DNL Adobe Stock] vengono solo visualizzate in [!DNL Experience Manager]. [!DNL Adobe Stock] le risorse vengono recuperate e memorizzate nell’ [!DNL Experience Manager] archivio solo dopo che un utente  [salva una ](/help/assets/aem-assets-adobe-stock.md#saveassets) risorsa o  [ne salva una](/help/assets/aem-assets-adobe-stock.md#licenseassets). Le risorse già memorizzate in [!DNL Experience Manager] vengono visualizzate ed evidenziate per semplificare il riferimento e l’accesso. Inoltre, le risorse [!DNL Stock] vengono salvate con alcuni metadati aggiuntivi per indicare l’origine come [!DNL Stock].

![Filtri di ricerca in risorse Adobe Stock Experienci Manager ed evidenziate nei risultati di ricerca](assets/aem-search-filters2.jpg)

*Figura: Ricerca filtri  [!DNL Experience Manager] e  [!DNL Adobe Stock] risorse evidenziate nei risultati della ricerca.*

### Salvare e visualizzare le risorse richieste {#saveassets}

Seleziona una risorsa da salvare in [!DNL Experience Manager]. Fai clic su [!UICONTROL Salva] nella barra degli strumenti nella parte superiore e fornisci il nome e la posizione della risorsa. Le risorse senza licenza vengono salvate localmente con una filigrana.

La prossima volta che cerchi le risorse, le risorse salvate vengono evidenziate con un contrassegno, per indicare che sono disponibili in [!DNL Experience Manager Assets].

>[!NOTE]
>
>Le risorse aggiunte di recente visualizzano un nuovo badge invece del badge License .

### Risorse di licenza {#licenseassets}

Gli utenti possono concedere in licenza le risorse [!DNL Adobe Stock] utilizzando la quota del proprio [!DNL Adobe Stock] piano aziendale. Quando si concede la licenza a una risorsa, questa viene salvata senza filigrana ed è disponibile per la ricerca e l’utilizzo in [!DNL Experience Manager Assets].

![Finestra di dialogo per concedere in licenza e salvare le risorse Adobe Stock in Experience Manager Assets](assets/aem-stock_licenseandsave.jpg)

*Figura: Finestra di dialogo per concedere in licenza e salvare  [!DNL Adobe Stock] le risorse in  [!DNL Experience Manager Assets].*

### Accedere a metadati e proprietà delle risorse {#access-metadata-and-asset-properties}

Gli utenti possono accedere ai metadati e visualizzarli in anteprima, comprese le proprietà dei metadati [!DNL Adobe Stock] per le risorse salvate in [!DNL Experience Manager], e aggiungere **[!UICONTROL Riferimenti di licenza]** per una risorsa. Tuttavia, gli aggiornamenti al riferimento di licenza non vengono sincronizzati tra il sito web [!DNL Experience Manager] e [!DNL Adobe Stock].

Gli utenti possono visualizzare le proprietà sia delle risorse con licenza che di quelle senza licenza.

![Visualizzare e accedere ai metadati e ai riferimenti di licenza delle risorse salvate](assets/metadata_properties.jpg)

*Figura: Visualizzare e accedere ai metadati e ai riferimenti di licenza delle risorse salvate.*

## Limitazioni note {#known-limitations}

* **L&#39;avviso dell&#39;immagine editoriale non viene visualizzato**: Quando si concede in licenza un&#39;immagine, gli utenti non possono verificare se un&#39;immagine è di utilizzo solo editoriale. Per evitare possibili abusi, gli amministratori possono disattivare l’accesso alle risorse editoriali dall’Admin Console.

* **Viene visualizzato** un tipo di licenza errato: È possibile che venga visualizzato un tipo di licenza errato in  [!DNL Experience Manager] per una risorsa. Gli utenti possono accedere al sito web [!DNL Adobe Stock] per visualizzare il tipo di licenza.

* **I campi e i metadati di riferimento non sono sincronizzati**: Quando un utente aggiorna un campo di riferimento della licenza, le informazioni di riferimento della licenza vengono aggiornate in  [!DNL Experience Manager] ma non sul  [!DNL Adobe Stock] sito web. Analogamente, se l&#39;utente aggiorna i campi di riferimento sul sito web [!DNL Adobe Stock], gli aggiornamenti non vengono sincronizzati in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Esercitazione video sull’ [!DNL Adobe Stock] utilizzo delle risorse con [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] aiuto per il piano aziendale](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-stock-enterprise.ug.html)
>* [[!DNL Adobe Stock] Domande frequenti](https://helpx.adobe.com/stock/faq.html)

