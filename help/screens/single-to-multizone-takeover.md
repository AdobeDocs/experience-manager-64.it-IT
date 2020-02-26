---
title: Acquisizione da una zona a più zone
seo-title: Acquisizione da una singola zona a più zone
description: 'Segui questa pagina per saperne di più sulla creazione di una singola area con più aree in un progetto AEM Screens.  '
seo-description: 'Segui questa pagina per saperne di più sulla creazione di una singola area con più aree in un progetto AEM Screens.    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Acquisizione da una zona a più zone {#single-zoneto-multizone}

## Descrizione di un caso d’uso {#use-case-description}

In questa sezione viene illustrato un esempio di utilizzo che mette in evidenza come impostare un canale di layout con più zone che si alterna con un canale di layout a una singola area. Ogni canale dispone di risorse immagine/video in sequenza.

### Premesse {#preconditions}

Prima di iniziare questo caso di utilizzo, accertatevi di comprendere come:

* **[Creare e gestire canali](/help/screens/managing-channels.md)**
* **[Creare e gestire le posizioni](/help/screens/managing-locations.md)**
* **[Creare e gestire le pianificazioni](/help/screens/managing-schedules.md)**
* **[Registrazione dispositivo](/help/screens/device-registration.md)**

### Attori primari {#primary-actors}

Autori contenuto

## Impostazione del progetto {#setting-up-the-project}

Per impostare un progetto, effettuate le seguenti operazioni:

1. Crea un progetto AEM Screens denominato **ZonesDemo**, come illustrato di seguito.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e la gestione di progetti in AEM Screens, consultate [Creazione di un progetto](/help/screens/creating-a-screens-project.md).

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **Creazione di un canale di sequenza con un’immagine**

   1. Selezionate la cartella **Canali** e fate clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.
   1. Selezionate Canale **** sequenza dalla procedura guidata e create il canale denominato **FullScreenOne**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. Selezionate il canale e fate clic su **Modifica** dalla barra delle azioni per aprire l’editor e trascinate e rilasciate un’immagine su tale canale, come illustrato di seguito.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **Creazione di un canale 2X2 con quattro immagini**

   1. Selezionate la cartella **Canali** e fate clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.

   1. Selezionate il modello **2X2 Split Screen Channel** (Canale **diviso schermo) dalla procedura guidata e create il canale denominato** TwobyTwoChannel.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. Selezionate il canale e fate clic su **Modifica** nella barra delle azioni per aprire l’editor e trascinate e rilasciate quattro immagini (quattro aree diverse) su tale canale, come mostrato di seguito.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **Creazione di un canale per schermo diviso 1X2 con due immagini**

   1. Selezionate la cartella **Canali** e fate clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.

   1. Selezionate il modello **1X2 Split Screen Channel** (Canale **diviso schermo) dalla procedura guidata e create il canale denominato** OnebyTwoChannel.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. Selezionate il canale e fate clic su **Modifica** nella barra delle azioni per aprire l’editor e trascinate e rilasciate due immagini (due diverse zone) su tale canale, come mostrato di seguito.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **Creazione di un canale con un solo video a schermo intero**

   1. Selezionate la cartella **Canali** e fate clic su **Crea** dalla barra delle azioni per aprire la procedura guidata per creare un canale.

   1. Selezionate il modello Canale **** sequenza dalla procedura guidata e create il canale denominato **FullScreensVideo**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. Selezionate il canale e fate clic su **Modifica** dalla barra delle azioni per aprire l’editor, quindi trascinate e rilasciate il componente video su tale canale, quindi aggiungete il video desiderato, come mostrato di seguito.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)

## Impostazione del canale di acquisizione per la transizione dalla zona singola alla zona multipla {#takeover-channel-setup}

1. **Modifica del canale di zona singola per il rilevamento di più zone**

   1. Selezionate il canale (**FullScreenOne)** creato al punto 1.
   1. Fai clic su **Modifica** nella barra delle azioni per aprire l&#39;editor. Trascinate nell’editor due componenti per canali e un componente video.
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **Compilazione dei componenti aggiunti al canale FullScreenOne**

   1. Selezionate il primo componente canale dall’editor di **FullScreenOne** e fate clic su **Configura** per puntare al canale creato nei passaggi precedenti. Aggiungete il percorso al canale in **Channel Path** sia ai componenti del canale che al componente video trascinate e rilasciate il video come mostrato di seguito.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **Impostazione della durata dei canali durante la transizione**

   >[!NOTE]
   >
   >Per impostazione predefinita, le risorse subiscono una transizione ogni 8 secondi, ma se desiderate che la transizione avvenga dopo una durata specifica, seguite il passaggio seguente.

   1. Selezionate il secondo componente canale dall’editor di **FullScreenOne** e fate clic su **Impostazioni** per configurare la durata del canale. Analogamente, impostate la durata del canale due, come mostrato di seguito.
In questo esempio, il tempo è impostato su 3 secondi.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## Anteprima del risultato {#previewing-result}

Potete fare clic su **Anteprima** dall’editor e verificare in che modo le risorse passeranno da un’area singola a più aree.

![](assets/SZ_MZvideo3.gif)
