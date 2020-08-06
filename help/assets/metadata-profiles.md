---
title: Utilizzare i profili di metadati per applicare i metadati predefiniti a tutte le risorse di una cartella
description: Informazioni sui profili di metadati per le risorse. Scoprite come creare un profilo di metadati e applicarlo alle risorse delle cartelle.
contentOwner: AG
translation-type: tm+mt
source-git-commit: af1955ab1fdcf16dd9a9d3ad36336e6c1aac9312
workflow-type: tm+mt
source-wordcount: '1232'
ht-degree: 17%

---


# Profili metadati {#metadata-profiles}

Un profilo di metadati consente di applicare i metadati predefiniti alle risorse all’interno di una cartella. Create un profilo di metadati e applicatelo a una cartella. Le risorse che successivamente caricate nella cartella ereditano i metadati predefiniti configurati nel profilo di metadati.

## Aggiunta di un profilo di metadati {#adding-a-metadata-profile}

1. Toccate o fate clic sul logo AEM e accedete a **[!UICONTROL Strumenti > Risorse > Profili]** metadati, quindi toccate **[!UICONTROL Crea]**.
1. Immettete un titolo per il profilo di metadati, ad esempio Metadati di esempio, e fate clic su **[!UICONTROL Invia]**. Viene visualizzato **[!UICONTROL Modifica modulo]** per il profilo metadati.

   ![chlimage_1-480](assets/chlimage_1-480.png)

1. Fate clic su un componente e configuratene le proprietà nella scheda **[!UICONTROL Impostazioni]** . Ad esempio, fare clic sul componente **[!UICONTROL Descrizione]** e modificarne le proprietà.

   ![chlimage_1-481](assets/chlimage_1-481.png)

   Modificate le seguenti proprietà per il componente **[!UICONTROL Descrizione]** :

   * **[!UICONTROL Etichetta]** campo: Nome visualizzato della proprietà metadata. È solo per il riferimento utente.
   * **[!UICONTROL Mappa su proprietà]**: Il valore di questa proprietà fornisce il percorso/nome relativo al nodo della risorsa in cui viene salvata nella directory archivio. Il valore deve sempre iniziare con `./` perché indica che il percorso si trova sotto il nodo della risorsa.

   ![chlimage_1-482](assets/chlimage_1-482.png)

   The value you specify for **[!UICONTROL Map to property]** is stored as a property under the asset&#39;s metadata node. Ad esempio, se specifichi: `/jcr:content/metadata/dc:desc` come nome della proprietà **** Mappa,  AEM Assets memorizza il valore `dc:desc` nel nodo di metadati della risorsa.

   * **[!UICONTROL Valore]** predefinito: Utilizzare questa proprietà per aggiungere un valore predefinito per il componente metadati. Ad esempio, se specificate &quot;Descrizione personale&quot;, questo valore viene assegnato alla proprietà `dc:desc` nel nodo di metadati della risorsa.

   ![chlimage_1-483](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Aggiunta di un valore predefinito a una nuova proprietà di metadati (che non esiste già in . `/jcr:content/metadata` node) per impostazione predefinita, la proprietà e il relativo valore non vengono visualizzati nella pagina **[!UICONTROL Proprietà]** della risorsa. Per visualizzare la nuova proprietà nella pagina [!UICONTROL Proprietà] della risorsa, modificate il modulo schema corrispondente.

1. (Optional) Add more components to the **[!UICONTROL Edit Form]** from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. Le seguenti proprietà sono disponibili dalla scheda **[!UICONTROL Genera modulo]**:

| Componente | Proprietà |
|---|---|
| [!UICONTROL Intestazione sezione] | Etichetta campo, <br> Descrizione |
| [!UICONTROL Testo su riga singola] | Etichetta campo, <br> Mappa su proprietà, Valore <br> predefinito |
| [!UICONTROL Testo con più valori] | Etichetta campo, <br> Mappa su proprietà, Valore <br> predefinito |
| [!UICONTROL Numero] | Etichetta campo, <br> Mappa su proprietà, Valore <br> predefinito |
| [!UICONTROL Data] | Etichetta campo, <br> Mappa su proprietà, Valore <br> predefinito |
| [!UICONTROL Tag standard] | Etichetta campo, <br> Mappa su proprietà, <br> Valore predefinito, <br> Descrizione |

![chlimage_1-484](assets/chlimage_1-484.png)

1. Fate clic su **[!UICONTROL Fine]**. Il profilo di metadati viene aggiunto all’elenco dei profili nella pagina **[!UICONTROL Profili]** metadati.

   ![chlimage_1-485](assets/chlimage_1-485.png)

## Copiare un profilo di metadati {#copying-a-metadata-profile}

1. Dalla pagina **[!UICONTROL Profili]** metadati, selezionate un profilo per copiarlo.

   ![chlimage_1-486](assets/chlimage_1-486.png)

1. Click **[!UICONTROL Copy]** from the toolbar.
1. Nella finestra di dialogo **[!UICONTROL Copia profilo]** metadati, immettete un titolo per la nuova copia del profilo.
1. Fate clic su **[!UICONTROL Copia]**. A copy of the profile appears in the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

   ![chlimage_1-487](assets/chlimage_1-487.png)

## Eliminare un profilo di metadati {#deleting-a-metadata-profile}

1. Nella pagina **[!UICONTROL Profili]** metadati, selezionate un profilo da eliminare.

   ![chlimage_1-488](assets/chlimage_1-488.png)

1. Fate clic su **[!UICONTROL Elimina profili]** metadati nella barra degli strumenti.
1. Nella finestra di dialogo, fare clic su **[!UICONTROL Elimina]** per confermare l&#39;operazione di eliminazione. Il profilo di metadati viene eliminato dall’elenco.

## Applicazione di un profilo di metadati alle cartelle {#applying-a-metadata-profile-to-folders}

Quando assegnate un profilo di metadati a una cartella, tutte le sottocartelle ereditano automaticamente il profilo dalla cartella principale. Questo significa che potete assegnare un solo profilo di metadati a una cartella. Considerate quindi attentamente la struttura delle cartelle in cui caricare, memorizzare, usare e archiviare le risorse.

Se avete assegnato un profilo di metadati diverso a una cartella, il nuovo profilo sostituisce il profilo precedente. Le risorse di cartella esistenti in precedenza restano invariate. Il nuovo profilo viene applicato alle risorse aggiunte successivamente alla cartella.

Le cartelle a cui è assegnato un profilo sono indicate nell&#39;interfaccia utente in base al nome del profilo visualizzato nel nome della scheda.

![chlimage_1-489](assets/chlimage_1-489.png)

Potete applicare i profili di metadati a cartelle specifiche o globalmente a tutte le risorse.

### Applicazione di profili di metadati a cartelle specifiche {#applying-metadata-profiles-to-specific-folders}

Puoi applicare un profilo di metadati a una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come applicare i profili di metadati alle cartelle con entrambe le soluzioni.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili di metadati alle cartelle dall&#39;interfaccia utente Profili {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selezionate il profilo di metadati da applicare a una o più cartelle.

   ![chlimage_1-490](assets/chlimage_1-490.png)

1. Tap **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and tap **[!UICONTROL Done]**. Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

#### Applicazione dei profili di metadati alle cartelle da Proprietà {#applying-metadata-profiles-to-folders-from-properties}

1. Nella barra a sinistra, toccate **[!UICONTROL Risorse]** , quindi individuate la cartella a cui desiderate applicare un profilo di metadati.
1. Sulla cartella, toccate il segno di spunta per selezionarlo, quindi toccate **[!UICONTROL Proprietà]**.

1. Select the **[!UICONTROL Metadata Profiles]** tab and select the profile from the drop-down menu and click **[!UICONTROL Save]**.

   ![chlimage_1-491](assets/chlimage_1-491.png)

   Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.

### Applicare un profilo di metadati a livello globale {#applying-a-metadata-profile-globally}

Oltre ad applicare un profilo a una cartella, potete anche applicarne uno a livello globale in modo che a qualsiasi contenuto caricato AEM risorse di qualsiasi cartella sia applicato il profilo selezionato. Per applicare un profilo di metadati a livello globale, effettuate le seguenti operazioni:

1. Effettua una delle operazioni seguenti:

   * Individuate `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` e applicate il profilo appropriato, quindi toccate o fate clic su **[!UICONTROL Salva]**.

      ![chlimage_1-492](assets/chlimage_1-492.png)

   * Passa al CRXDE Lite al seguente nodo: `/content/dam/jcr:content`. Aggiungete la proprietà `metadataProfile:/etc/dam/metadata/dynamicmedia/<name_of_metadata_profile>` e toccate **[!UICONTROL Salva tutto]**.

      ![chlimage_1-493](assets/chlimage_1-493.png)

## Rimozione di un profilo di metadati dalle cartelle {#removing-a-metadata-profile-from-folders}

Quando rimuovete un profilo di metadati da una cartella, tutte le sottocartelle ereditano automaticamente la rimozione del profilo dalla cartella principale. Tuttavia, l&#39;elaborazione dei file che si è verificata all&#39;interno delle cartelle rimane intatta.

Puoi rimuovere un profilo di metadati da una cartella direttamente dal menu **[!UICONTROL Strumenti]** oppure, se ti trovi nella cartella, da **[!UICONTROL Proprietà]**. Questa sezione descrive come rimuovere i profili di metadati dalle cartelle con entrambe le soluzioni.

### Rimozione di profili di metadati dalle cartelle tramite l&#39;interfaccia utente Profili {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

Per rimuovere un profilo di metadati dalle cartelle tramite l’interfaccia utente Profili, effettuate le seguenti operazioni:

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selezionate il profilo di metadati da rimuovere da una o più cartelle.
1. Tap **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from, then tap **[!UICONTROL Done]**.

   Potete confermare che il profilo di metadati non viene più applicato a una cartella perché il nome non viene più visualizzato sotto il nome della cartella.

### Rimozione di profili di metadati dalle cartelle tramite Proprietà {#removing-metadata-profiles-from-folders-via-properties}

1. Toccate il logo AEM e individuate le **[!UICONTROL risorse]** , quindi la cartella da cui desiderate rimuovere un profilo di metadati.
1. Sulla cartella, toccate il segno di spunta per selezionarlo, quindi toccate **[!UICONTROL Proprietà]**.
1. Selezionate la scheda Profili **** metadati, quindi selezionate **[!UICONTROL Nessuno]** dal menu a discesa. Toccate **[!UICONTROL Salva]**.

Le cartelle a cui è già stato assegnato un profilo sono indicate dalla visualizzazione del nome del profilo che è posto direttamente sotto il nome della cartella.
