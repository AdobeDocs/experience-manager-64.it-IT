---
title: Utilizzare i profili di metadati per applicare i metadati predefiniti a tutte le risorse di una cartella
description: Informazioni sui profili di metadati per le risorse. Scopri come creare un profilo di metadati e applicarlo alle risorse delle cartelle.
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 17%

---


# Profili metadati {#metadata-profiles}

Un profilo di metadati consente di applicare metadati predefiniti alle risorse all’interno di una cartella. Crea un profilo metadati e applicalo a una cartella. Qualsiasi risorsa da caricare successivamente nella cartella eredita i metadati predefiniti configurati nel profilo metadati.

## Aggiungere un profilo di metadati {#adding-a-metadata-profile}

1. Tocca o fai clic sul logo AEM e passa a **[!UICONTROL Strumenti > Risorse > Profili metadati]**, quindi tocca **[!UICONTROL Crea]**.
1. Inserisci un titolo per il profilo metadati, ad esempio Metadati campione, e fai clic su **[!UICONTROL Invia]**. Viene visualizzato il **[!UICONTROL Modifica modulo]** per il profilo metadati.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Fai clic su un componente e configurane le proprietà nella scheda **[!UICONTROL Impostazioni]** . Ad esempio, fai clic sul componente **[!UICONTROL Descrizione]** e modificane le proprietà.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Modifica le seguenti proprietà per il componente **[!UICONTROL Descrizione]** :

   * **[!UICONTROL Etichetta]** campo: Nome visualizzato della proprietà metadati. È solo per il riferimento utente.
   * **[!UICONTROL Mappa su proprietà]**: Il valore di questa proprietà fornisce il percorso/nome relativo al nodo della risorsa in cui viene salvata nell’archivio. Il valore deve sempre iniziare con `./` perché indica che il percorso si trova sotto il nodo della risorsa.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   Il valore specificato per **[!UICONTROL Mappa su proprietà]** viene memorizzato come proprietà sotto il nodo di metadati della risorsa. Ad esempio, se specifichi: `/jcr:content/metadata/dc:desc` come nome di  **[!UICONTROL Mappa su proprietà]**, AEM Assets memorizza il valore  `dc:desc` nel nodo di metadati della risorsa.

   * **[!UICONTROL Valore]** predefinito: Utilizzare questa proprietà per aggiungere un valore predefinito per il componente metadati. Ad esempio, se specifichi &quot;La mia descrizione&quot;, questo valore viene assegnato alla proprietà `dc:desc` nel nodo di metadati della risorsa.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Aggiunta di un valore predefinito a una nuova proprietà di metadati (che non esiste già in . `/jcr:content/metadata` node) non visualizza la proprietà e il relativo valore nella pagina  **** Proprietà della risorsa per impostazione predefinita. Per visualizzare la nuova proprietà nella pagina [!UICONTROL Proprietà] della risorsa, modifica il modulo schema corrispondente.

1. (Facoltativo) Aggiungi altri componenti alla scheda **[!UICONTROL Modifica modulo]** dalla scheda **[!UICONTROL Genera modulo]** e configurane le proprietà nella scheda **[!UICONTROL Impostazioni]** . Le seguenti proprietà sono disponibili dalla scheda **[!UICONTROL Genera modulo]**:

| Componente | Proprietà |
|---|---|
| [!UICONTROL Intestazione sezione] | Etichetta campo, <br> descrizione |
| [!UICONTROL Testo su riga singola] | Etichetta campo <br> Mappa su proprietà, <br> Valore predefinito |
| [!UICONTROL Testo con più valori] | Etichetta campo <br> Mappa su proprietà, <br> Valore predefinito |
| [!UICONTROL Numero] | Etichetta campo <br> Mappa su proprietà, <br> Valore predefinito |
| [!UICONTROL Data] | Etichetta campo <br> Mappa su proprietà, <br> Valore predefinito |
| [!UICONTROL Tag standard] | Etichetta campo <br> Mappa su proprietà, <br> Valore predefinito, <br> Descrizione |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Fare clic su **[!UICONTROL Fine]**. Il profilo metadati viene aggiunto all’elenco dei profili nella pagina **[!UICONTROL Profili metadati]** .

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Copiare un profilo di metadati {#copying-a-metadata-profile}

1. Dalla pagina **[!UICONTROL Profili metadati]** , seleziona un profilo per crearne una copia.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Fai clic su **[!UICONTROL Copia]** nella barra degli strumenti.
1. Nella finestra di dialogo **[!UICONTROL Copia profilo metadati]**, immetti un titolo per la nuova copia del profilo.
1. Fate clic su **[!UICONTROL Copia]**. Una copia del profilo viene visualizzata nell’elenco dei profili nella pagina **[!UICONTROL Profili metadati]** .

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Eliminare un profilo di metadati {#deleting-a-metadata-profile}

1. Dalla pagina **[!UICONTROL Profili metadati]** , seleziona un profilo da eliminare.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Fai clic su **[!UICONTROL Elimina profili metadati]** nella barra degli strumenti.
1. Nella finestra di dialogo, fare clic su **[!UICONTROL Elimina]** per confermare l&#39;operazione di eliminazione. Il profilo metadati viene eliminato dall’elenco.

## Applicare un profilo di metadati alle cartelle {#applying-a-metadata-profile-to-folders}

Quando assegni un profilo di metadati a una cartella, tutte le sottocartelle ereditano automaticamente il profilo dalla relativa cartella padre. Ciò significa che puoi assegnare un solo profilo di metadati a una cartella. Considera attentamente la struttura delle cartelle in cui caricare, archiviare, utilizzare e archiviare le risorse.

Se hai assegnato un profilo di metadati diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse della cartella esistenti in precedenza rimangono invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell&#39;interfaccia utente in base al nome del profilo visualizzato nel nome della scheda.

![chlimage_1-489](assets/chlimage_1-489.png)

Puoi applicare i profili di metadati a cartelle specifiche o globalmente a tutte le risorse.

### Applicare profili di metadati a cartelle specifiche {#applying-metadata-profiles-to-specific-folders}

Puoi applicare un profilo di metadati a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili di metadati alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicare profili di metadati alle cartelle dall&#39;interfaccia utente Profili {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tocca il logo AEM e passa a **[!UICONTROL Strumenti > Risorse > Profili metadati]**.
1. Seleziona il profilo di metadati da applicare a una o più cartelle.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Tocca **[!UICONTROL Applica profilo metadati a cartelle]** e seleziona una o più cartelle da utilizzare per ricevere le risorse appena caricate, quindi tocca **[!UICONTROL Fine]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicare profili di metadati alle cartelle da Proprietà {#applying-metadata-profiles-to-folders-from-properties}

1. Nella barra a sinistra, tocca **[!UICONTROL Risorse]**, quindi individua la cartella a cui desideri applicare un profilo di metadati.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.

1. Seleziona la scheda **[!UICONTROL Profili metadati]** e seleziona il profilo dal menu a discesa, quindi fai clic su **[!UICONTROL Salva]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

### Applicare un profilo di metadati a livello globale {#applying-a-metadata-profile-globally}

Oltre ad applicare un profilo a una cartella, puoi anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse in una cartella sia applicato il profilo selezionato. Per applicare un profilo di metadati a livello globale, effettua le seguenti operazioni:

1. Effettua una delle operazioni seguenti:

   * Passa a `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` e applica il profilo appropriato, quindi tocca o fai clic su **[!UICONTROL Salva]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Passa a CRXDE Lite al seguente nodo: `/content/dam/jcr:content`. Aggiungi la proprietà `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` e tocca **[!UICONTROL Salva tutto]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Rimuovere un profilo di metadati dalle cartelle {#removing-a-metadata-profile-from-folders}

Quando rimuovi un profilo di metadati da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla relativa cartella principale. Tuttavia, l’elaborazione dei file che si è verificata all’interno delle cartelle rimane intatta.

Puoi rimuovere un profilo di metadati da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come rimuovere i profili di metadati dalle cartelle con entrambe le soluzioni.

### Rimuovere i profili di metadati dalle cartelle tramite l’interfaccia utente Profiles {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Per rimuovere un profilo di metadati dalle cartelle tramite l’interfaccia utente Profiles , effettua le seguenti operazioni:

1. Tocca il logo AEM e passa a **[!UICONTROL Strumenti > Risorse > Profili metadati]**.
1. Seleziona il profilo di metadati da rimuovere da una o più cartelle.
1. Tocca **[!UICONTROL Rimuovi profilo metadati da cartelle]** e seleziona una o più cartelle da cui vuoi rimuovere un profilo, quindi tocca **[!UICONTROL Fine]**.

   Puoi confermare che il profilo di metadati non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimuovere i profili di metadati dalle cartelle tramite Proprietà {#removing-metadata-profiles-from-folders-via-properties}

1. Tocca il logo AEM e naviga **[!UICONTROL Risorse]**, quindi alla cartella da cui vuoi rimuovere un profilo di metadati.
1. Sulla cartella, tocca il segno di spunta per selezionarlo, quindi tocca **[!UICONTROL Proprietà]**.
1. Seleziona la scheda **[!UICONTROL Profili metadati]** , quindi seleziona **[!UICONTROL Nessuno]** dal menu a discesa. Tocca **[!UICONTROL Salva]**.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.
