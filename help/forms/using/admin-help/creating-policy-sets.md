---
title: Creazione e gestione dei set di criteri
seo-title: Creating and managing policy sets
description: I set di criteri vengono utilizzati per raggruppare i criteri con uno scopo aziendale comune. È possibile creare, modificare ed eliminare i criteri in un set di criteri.
seo-description: Policy sets are used to group policies that have a common business purpose. You can create, edit and delete policies in a policy set.
uuid: 11faf67c-b9b7-4394-8672-d43cace131ad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a4fb1a11-8fe3-4092-a036-1c079aea1250
feature: Document Security
exl-id: e17ab7de-9f4a-4456-be80-43ab9663940e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 0%

---

# Creazione e gestione dei set di criteri {#creating-and-managing-policy-sets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I set di criteri vengono utilizzati per raggruppare i criteri con uno scopo aziendale comune. I set di criteri possono essere resi disponibili a un sottoinsieme di utenti nel sistema.

A ciascun set di criteri è associato almeno un coordinatore set di criteri. La *coordinatore del set di regole* è un amministratore o un utente con autorizzazioni aggiuntive. Il coordinatore del set di criteri è in genere uno specialista dell&#39;organizzazione che può creare al meglio i criteri in un determinato set di criteri.

I coordinatori dei set di criteri possono eseguire le seguenti attività:

* Creare nuovi criteri
* Modificare ed eliminare i criteri nel set di criteri
* Modifica impostazioni set di criteri
* Aggiungi e rimuovi coordinatori per il set di criteri
* Visualizza eventi di criteri e documenti per qualsiasi criterio o documento all&#39;interno del set di criteri
* Revoca dell’accesso ai documenti
* Cambia criteri per il documento

I set di criteri vengono creati ed eliminati nell’interfaccia di amministrazione della protezione dei documenti da super utenti e dai coordinatori dei set di criteri che dispongono delle autorizzazioni necessarie.

Quando si elimina un set di criteri, i criteri che facevano parte del set non possono essere applicati ai nuovi documenti. Tuttavia, è possibile visualizzare le informazioni sui criteri sia nella console di amministrazione che nelle pagine web dell’utente finale per i criteri ancora in uso. È possibile visualizzare le informazioni sui criteri dalla pagina dei dettagli del documento per qualsiasi documento protetto dal criterio. È possibile modificare i criteri ancora in uso.

Il super utente o il coordinatore del set di criteri aggiunge i domini creati in Gestione utente all&#39;utente e al gruppo visibili per ciascun set di criteri. Questo elenco è visibile al coordinatore del set di criteri e viene utilizzato per limitare i domini che il coordinatore del set di criteri può cercare quando sceglie gli utenti da aggiungere ai criteri.

Quando si creano set di criteri, si assegna agli utenti il ruolo di editore del documento. La *editore di documenti* è l&#39;utente che protegge il documento con un criterio. Per impostazione predefinita, questo utente è sempre incluso in un criterio con diritti di accesso completi, incluse le funzionalità di revoca e di cambio di policy. Tuttavia, gli amministratori possono modificare i diritti di accesso dell’editore del documento per i criteri condivisi. Ad esempio, l’amministratore può disabilitare il diritto dell’autore del documento di revocare l’accesso al documento o di cambiare il criterio. Se un amministratore cambia il criterio associato al documento, il nome dell&#39;autore verrà aggiornato al nome del proprietario del criterio applicato per ultimo al documento.

Al momento dell&#39;installazione della protezione dei documenti, viene creato un set di criteri predefinito denominato *Set di criteri globale*. Questo set di criteri viene gestito dall&#39;amministratore che ha installato il software o dal coordinatore del set di criteri designato per questo set di criteri.

## Creare un set di criteri {#create-a-policy-set}

Il set di criteri globale è l’unico set di criteri predefinito creato al momento dell’installazione. È possibile creare set di criteri aggiuntivi e aggiungere criteri, utenti, coordinatori di set di criteri ed editori di documenti. Dopo aver creato un set di criteri, è possibile creare i criteri all’interno del set.

Durante la creazione del set di criteri, è possibile utilizzare il pulsante Indietro per tornare alla schermata precedente e il pulsante Salva per salvare il set di criteri in qualsiasi momento.

1. Nella pagina Protezione documento fare clic su Criteri, fare clic sulla scheda Set di criteri e quindi su Nuovo.
1. Nella casella Nome digitare un nome per il set di criteri, digitare facoltativamente una Descrizione e quindi fare clic su Avanti. Il nome non può contenere due punti **:**.

   >[!NOTE]
   >
   >È possibile creare un nome di set di criteri contenente caratteri estesi; tuttavia, quando si effettua un confronto tra due stringhe, i caratteri accentati e non accenti come &quot;e&quot; e &quot;é&quot; sono considerati uguali. Quando un utente crea un set di criteri, viene effettuato un confronto per verificare se esiste già un set di criteri con lo stesso nome. Il confronto non è in grado di distinguere tra nomi uguali, ad eccezione dei caratteri accentati. Si presume che il set di criteri sia già stato aggiunto al database e che il nuovo non sia stato aggiunto.

1. (Facoltativo) Per impostare i domini visibili agli editori di documenti quando aggiungono utenti a un criterio, fare clic su Aggiungi domini, selezionare i domini da rendere ricercabili, fare clic su Aggiungi, quindi su OK.
1. Nella pagina Aggiungi utenti e gruppi visibili fare clic su Avanti.
1. (Facoltativo) Per aggiungere un coordinatore del set di criteri, fare clic su Aggiungi utenti e gruppi nella pagina Aggiungi coordinatori set di criteri (passaggio 3 di 4) ed eseguire le seguenti attività:

   * Nella casella Trova digitare il nome o l&#39;indirizzo e-mail.
   * Nell’elenco Utilizzo, selezionare l’opzione appropriata.
   * Nell’elenco Tipo, selezionare Utente e, nell’elenco In, selezionare un dominio da cercare.
   * Nell&#39;elenco Visualizzazione selezionare il numero di risultati da visualizzare per pagina, quindi fare clic su Trova.
   * Selezionare la casella di controllo relativa all&#39;utente o al gruppo da aggiungere e fare clic su Avanti.
   * Selezionare le autorizzazioni del coordinatore del set di criteri e fare clic su Aggiungi. È possibile impostare le seguenti autorizzazioni:

      * Visualizza eventi
      * Gestione dei documenti (revoca e ripristino dell&#39;accesso ai documenti e modifica dei criteri nei documenti)
      * Gestione dei criteri (creazione, modifica ed eliminazione dei criteri)
      * Gestione degli editori di documenti (aggiungere e rimuovere gli editori di documenti)
      * Delega (aggiungere e rimuovere i coordinatori dei set di criteri)

1. Ripetere il passaggio 5 per aggiungere altri coordinatori di set di criteri.
1. Esaminare le impostazioni del coordinatore del set di criteri e fare clic su Avanti.
1. Fare clic su Aggiungi utenti e gruppi per aggiungere gli editori di documenti che possono utilizzare i criteri all&#39;interno del set di criteri per proteggere i documenti.
1. Nella pagina Aggiungi publisher documento eseguire le operazioni seguenti:

   * Nella casella Trova digitare il nome o l&#39;indirizzo e-mail.
   * Nell’elenco Utilizzo, selezionare l’opzione appropriata.
   * Nell’elenco Tipo, selezionare Utente e, nell’elenco In, selezionare un dominio da cercare.
   * Nell&#39;elenco Visualizzazione selezionare il numero di risultati da visualizzare per pagina, quindi fare clic su Trova.
   * Selezionare le caselle di controllo relative agli utenti e ai gruppi da aggiungere, fare clic su Aggiungi e quindi su OK.

1. Fai clic su Salva.

È ora possibile aggiungere criteri al set di criteri. (Vedi [Creazione e modifica dei criteri](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Modificare un set di criteri {#edit-a-policy-set}

1. Nella pagina Protezione documento fare clic su Criteri, fare clic sulla scheda Set di criteri e quindi sul set di criteri da modificare.
1. Fai clic sulla scheda appropriata e modifica come necessario:

   * **Dettagli:** Modifica il nome e la descrizione del set di criteri.
   * **Criteri:** Creare, abilitare, modificare ed eliminare i criteri all&#39;interno del set di criteri.
   * **Utenti e gruppi visibili:** Aggiungi e rimuovi utenti e gruppi visibili che possono essere inclusi in un criterio.
   * **Coordinatori set di criteri:** Aggiungi, rimuovi e modifica le autorizzazioni per i coordinatori.
   * **Editori di documenti:** Aggiungi e rimuovi utenti che possono pubblicare documenti utilizzando i criteri del set.

1. Per eliminare un utente o un gruppo visibile, Coordinatore set di criteri o Editore documenti, fare clic sulla scheda appropriata, selezionare la casella di controllo relativa alla voce, fare clic su Elimina e quindi su OK.
1. Per aggiungere utenti o gruppi visibili, un coordinatore set di criteri o un editore di documenti, fare clic sulla scheda appropriata, fare clic su Aggiungi utenti o gruppi, cercare l&#39;utente o il gruppo da aggiungere, selezionare la voce, fare clic su Aggiungi, quindi fare clic su OK.
1. Nella scheda Criteri , cerca i criteri da aggiungere al set di criteri e crea nuovi criteri:

   * Per cercare un criterio, selezionare ID criterio o Nome criterio, digitare il valore corrispondente, selezionare il numero di elementi da visualizzare e fare clic su Trova.
   * Per informazioni dettagliate sulla creazione di un nuovo criterio, consulta [Creazione e modifica dei criteri](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Eliminare un set di criteri {#delete-a-policy-set}

Quando si elimina un set di criteri, i criteri che facevano parte del set non possono essere applicati ai nuovi documenti. Tuttavia, è possibile visualizzare le informazioni sui criteri sia nella console di amministrazione che nelle pagine web dell’utente finale per i criteri ancora in uso. È possibile visualizzare le informazioni sui criteri dalla pagina dei dettagli del documento per qualsiasi documento protetto dal criterio. È possibile modificare i criteri ancora in uso.

1. Fare clic su Criteri e quindi sulla scheda Set di criteri.
1. Selezionare la casella di controllo relativa al set di criteri da eliminare.
1. Fare clic su Elimina, quindi su OK.
