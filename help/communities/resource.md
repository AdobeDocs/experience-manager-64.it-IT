---
title: Creazione e assegnazione di risorse di abilitazione
seo-title: Creazione e assegnazione di risorse di abilitazione
description: Aggiunta di risorse di abilitazione
seo-description: Aggiunta di risorse di abilitazione
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 6%

---


# Creazione e assegnazione di risorse di abilitazione {#create-and-assign-enablement-resources}

## Aggiunta di una risorsa di abilitazione {#add-an-enablement-resource}

Per aggiungere una risorsa di abilitazione al nuovo sito community:

* Nell’istanza di creazione
   * Ad esempio, [http://localhost:4502/](Http://localhost:4503/)
* Accesso come amministratore di sistema
* Dalla navigazione globale, selezionare **Communities > [Resources](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* Selezionare il sito community in cui vengono aggiunte le risorse di abilitazione
   * Seleziona `Enablement Tutorial`
* Dal menu, selezionare ` Create`
* Selezionare **[!UICONTROL Resource]**

![chlimage_1-201](assets/chlimage_1-201.png)

### Informazioni di base {#basic-info}

Compila le informazioni di base per la risorsa:

* **[!UICONTROL Nome]** sito: impostato sul nome del sito community selezionato: Esercitazione di abilitazione
* **[!UICONTROL Nome &amp;risorsa;]**: Lezione di sci 1
* **[!UICONTROL Tag]**: Esercitazione: Sport / Sci
* **[!UICONTROL Mostra nel catalogo]**: Attivato
* **[!UICONTROL Descrizione]**: Scivolare sulla neve per principianti
* **[!UICONTROL Aggiungi immagine]**: Aggiungere un&#39;immagine per rappresentare la risorsa al membro nella visualizzazione Assegnazioni
   ![chlimage_1-202](assets/chlimage_1-202.png)
* Seleziona **[!UICONTROL Avanti]**

### Aggiungi contenuto {#add-content}

Anche se è possibile selezionare più risorse, ne è consentita solo una.

Selezionare `'+' icon`, nell&#39;angolo superiore destro, per iniziare il processo di scelta della risorsa identificando l&#39;origine.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

Carica una risorsa. Se una risorsa video, caricate un’immagine personalizzata da visualizzare prima dell’inizio della riproduzione del video oppure consentite la generazione di una miniatura dal video (potrebbe richiedere alcuni minuti - non è necessario attendere).

![chlimage_1-205](assets/chlimage_1-205.png)

* selezionare **[!UICONTROL Next]**

### Impostazioni {#settings}

* **[!UICONTROL Social]**
Settings (Impostazioni social network): lasciate le impostazioni predefinite per consentire agli utenti di esprimere commenti e valutazioni sulle risorse di abilitazione.
* **[!UICONTROL Data di scadenza]**

   *(Facoltativo)* È possibile selezionare una data entro la quale completare l&#39;assegnazione.
* **[!UICONTROL Autore risorse]**

   *(Facoltativo)* Lasciate vuoto.
* **[!UICONTROL Contatto &amp;risorse;]**

   *(Obbligatorio)* Utilizzate il menu a discesa per selezionare un membro  `Quinn Harper`.
* **[!UICONTROL Esperto risorse]**

   *(Facoltativo)* Lasciate vuoto.
   **Nota**: se gli utenti o i gruppi non sono visibili, accertatevi che siano stati aggiunti al  `Community Enable Members` gruppo e  ** salvati nell’istanza di pubblicazione.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* Seleziona **[!UICONTROL Avanti]**

### Assegnazioni {#assignments}

* **[!UICONTROL Aggiungi]**
assegnatariNon impostate perché la risorsa di abilitazione verrà aggiunta a un percorso di apprendimento. Se uno studente viene assegnato sia alla singola risorsa di abilitazione che a un percorso di apprendimento contenente la risorsa di abilitazione, lo studente verrà assegnato due volte alla risorsa di abilitazione.

![chlimage_1-207](assets/chlimage_1-207.png)

* Seleziona **[!UICONTROL Crea]**

![chlimage_1-208](assets/chlimage_1-208.png)

La creazione della risorsa è riuscita e torna alla console Risorse con la risorsa appena creata selezionata. Da questa console è possibile pubblicare, aggiungere utenti in formazione e modificare altre impostazioni.

Per caricare una nuova versione della risorsa di abilitazione, si consiglia di creare una nuova risorsa, quindi di annullare l’iscrizione dei membri dalla versione precedente e di iscriverli nella nuova versione.

### Pubblicare la risorsa {#publish-the-resource}

Prima che gli iscritti siano in grado di visualizzare il corso di aggiornamento assegnato, è necessario pubblicarlo:

* Selezionare l&#39;icona mondiale `Publish`

L&#39;attivazione viene confermata con un messaggio di riuscita:

![chlimage_1-209](assets/chlimage_1-209.png)

## Aggiungere una seconda risorsa di abilitazione {#add-a-second-enablement-resource}

Ripetete i passaggi descritti qui sopra per creare e pubblicare una seconda risorsa di abilitazione correlata dalla quale verrà creato un percorso di apprendimento.

![chlimage_1-210](assets/chlimage_1-210.png)

**** Pubblica la seconda risorsa.

Tornate all&#39;elenco delle risorse di Enablement Tutorial.

*Suggerimento: se entrambe le risorse non sono visibili, aggiorna la pagina.*

![chlimage_1-211](assets/chlimage_1-211.png)

## Aggiungere un percorso di apprendimento {#add-a-learning-path}

Un percorso di apprendimento è un gruppo logico di risorse di abilitazione che formano un corso.

* Dalla console Risorse, selezionare `+ Create`
* Selezionare **[!UICONTROL Percorso di apprendimento]**

![chlimage_1-212](assets/chlimage_1-212.png)

Aggiungete **[!UICONTROL Informazioni di base]**:

* **[!UICONTROL Nome]** percorso di apprendimento: Lezioni di sci
* **[!UICONTROL Tag]**: Esercitazione: Sci
* **[!UICONTROL Mostra nel catalogo]**: lasciate deselezionata
* **[!UICONTROL Caricare un’]** immagine per rappresentare il percorso di apprendimento nella console Risorse

![chlimage_1-213](assets/chlimage_1-213.png)

* Seleziona **[!UICONTROL Avanti]**

Saltate il pannello successivo in quanto non sono disponibili percorsi di apprendimento preliminari da aggiungere.

* Seleziona **[!UICONTROL Avanti]**

Nel pannello Aggiungi risorse

* Selezionare `+ Add Resources` per selezionare le 2 risorse di lezione da aggiungere al percorso di apprendimento

   Nota: È possibile selezionare solo **risorse pubblicate**.

>[!NOTE]
>
>Potete selezionare solo le risorse disponibili allo stesso livello del percorso di apprendimento. Ad esempio, per un percorso di apprendimento creato in un gruppo sono disponibili solo le risorse a livello di gruppo; per un percorso di apprendimento creato in un sito community, le risorse in tale sito sono disponibili per l&#39;aggiunta al percorso di apprendimento.

* Seleziona **[!UICONTROL Invia]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* Seleziona **[!UICONTROL Avanti]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL Aggiungi]**
assegnatariUtilizzate il menu a discesa per selezionare 
`Community Ski Class` che devono includere membri  `Riley Taylor` e  `Sidney Croft.`

* **[!UICONTROL &amp;Apprendimento percorso contatto;]**

   *(Obbligatorio)* Utilizzate il menu a discesa per selezionare un membro  `Quinn Harper`.

* Seleziona **[!UICONTROL Crea]**

![chlimage_1-217](assets/chlimage_1-217.png)

La creazione corretta del percorso di apprendimento torna alla console Risorse con il nuovo percorso di apprendimento selezionato. Da questa console è possibile pubblicare, aggiungere utenti in formazione e modificare altre impostazioni.

**Pubblicate** il percorso di apprendimento.

