---
title: Applicazione Sandbox iniziale
seo-title: Initial Sandbox Application
description: Creare modelli, componenti e script
seo-description: Create template, component, and script
uuid: b0d03376-d8bc-4e98-aea2-a01744c64ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f74d225e-0245-4d5a-bb93-0ee3f31557aa
exl-id: 3da30cb4-39b2-4495-9e8b-93567b73b644
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 4%

---

# Applicazione Sandbox iniziale {#initial-sandbox-application}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In questa sezione verrà creato quanto segue:

* La **[template](#createthepagetemplate)** che verrà utilizzato per creare pagine di contenuto nel sito web di esempio
* La **[componente e script](#create-the-template-s-rendering-component)** che verrà utilizzato per il rendering delle pagine del sito web

## Creare il modello di contenuto {#create-the-content-template}

Un modello definisce il contenuto predefinito di una nuova pagina. I siti web complessi possono utilizzare diversi modelli per la creazione di diversi tipi di pagine nel sito. Inoltre, il set di modelli può diventare un blueprint utilizzato per il rollout delle modifiche a un cluster di server.

In questo esercizio, tutte le pagine sono basate su un modello semplice.

1. Nel riquadro Esplora risorse di CRXDE Lite

   * select `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Crea > Crea modello]**

1. Nella finestra di dialogo Crea modello, digita i seguenti valori e fai clic su **[!UICONTROL Successivo]**:

   * Etichetta: `playpage`
   * Titolo: `An SCF Sandbox Play Template`
   * Descrizione: `An SCF Sandbox template for play pages`
   * Tipo risorsa: `an-scf-sandbox/components/playpage`
   * Classifica: &lt;leave as=&quot;&quot; default=&quot;&quot;>

   Etichetta utilizzata per il nome del nodo.

   Il tipo di risorsa viene visualizzato nella sezione `playpage`nodo jcr:content come proprietà `sling:resourceType`. Identifica il componente (risorsa) che esegue il rendering del contenuto quando richiesto da un browser.

   In questo caso, tutte le pagine create utilizzando il `playpage`viene eseguito il rendering del modello dal `an-scf-sandbox/components/playpage` componente. Per convenzione, il percorso del componente è relativo, consentendo a Sling di cercare la risorsa per prima nella `/apps` e, se non trovato, nella cartella `/libs` cartella.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Se utilizzi copia/incolla, assicurati che il valore Tipo di risorsa non contenga spazi iniziali o finali.

   Fai clic su **[!UICONTROL Avanti]**.

1. Per &quot;Percorsi consentiti&quot; si intendono i percorsi delle pagine che utilizzano questo modello, in modo che il modello sia elencato per **[!UICONTROL Nuova pagina]** finestra di dialogo.

   Per aggiungere un percorso, fai clic sul pulsante più `+` e tipo `/content(/.&ast;)?` nella casella di testo visualizzata. Se utilizzi copia/incolla, assicurati che non vi siano spazi iniziali o finali.

   Nota: Il valore della proprietà percorso consentita è un *espressione regolare.* Le pagine di contenuto con un percorso che corrisponde all’espressione possono utilizzare il modello . In questo caso, l’espressione regolare corrisponde al percorso del **/content** e tutte le relative sottopagine.

   Quando un autore crea una pagina qui sotto `/content`, `playpage`il modello denominato &quot;An SCF Sandbox Page Template&quot; viene visualizzato in un elenco di modelli disponibili da utilizzare.

   Una volta creata la pagina principale dal modello, l’accesso al modello potrebbe essere limitato a questo sito web modificando la proprietà per includere il percorso principale nell’espressione regolare, ovvero

   `/content/an-scf-sandbox(/.&ast;)?`

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Fai clic su **[!UICONTROL Avanti]**.

   Fai clic su **[!UICONTROL Successivo]** in **[!UICONTROL Genitori consentiti]** pannello.

   Fai clic su **[!UICONTROL Successivo]** in **[!UICONTROL Bambini consentiti]** pannelli.

   Fai clic su **[!UICONTROL OK]**.

1. Dopo aver fatto clic su OK e aver completato la creazione del modello, si noteranno triangoli rossi negli angoli dei valori della scheda Proprietà per il nuovo modello `playpage`modello. Questi triangoli rossi indicano le modifiche che non sono state salvate.

   Fai clic su **[!UICONTROL Salva tutto]** per salvare il nuovo modello nel repository.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### Creare il componente di rendering del modello {#create-the-template-s-rendering-component}

Crea il *component* che definisce il contenuto ed esegue il rendering delle pagine create in base al [modello di playpage](#createthepagetemplate).

1. In CRXDE Lite, fai clic con il pulsante destro del mouse su **`/apps/an-scf-sandbox/components`** e fai clic su **[!UICONTROL Crea > Componente]**.
1. Impostando il nome del nodo (Etichetta) su *playpage*, il percorso del componente è

   `/apps/an-scf-sandbox/components/playpage`

   che corrisponde al tipo di risorsa del modello di playpage (facoltativamente meno il valore iniziale **`/apps/`** parte del percorso).

   In **[!UICONTROL Crea componente]** digitare i seguenti valori di proprietà nella finestra di dialogo:

   * Etichetta: **playpage**
   * Titolo: **Componente di riproduzione sandbox SCF**
   * Descrizione: **È il componente che esegue il rendering del contenuto per una pagina Sandbox SCF.**
   * Super Type: *&lt;leave blank=&quot;&quot;>*
   * Gruppo:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Fai clic su **[!UICONTROL Successivo]** fino al **[!UICONTROL Bambini consentiti]** viene visualizzato il pannello della finestra di dialogo

   * Fai clic su **[!UICONTROL OK]**
   * Fai clic su **[!UICONTROL Salva tutto]**

1. Verifica che il percorso del componente e il resourceType per il modello corrispondano.

   >[!CAUTION]
   >
   >La corrispondenza tra il percorso del componente playpage e la proprietà sling:resourceType del modello playpage è fondamentale per il corretto funzionamento del sito web.

   ![chlimage_1-79](assets/chlimage_1-79.png)
