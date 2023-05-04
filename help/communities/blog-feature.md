---
title: Funzione blog
seo-title: Blog Feature
description: Informazioni della community in un formato di registrazione
seo-description: Community information in a journaling format
uuid: 01f1a547-d22b-4da6-a69c-ab420e5a9e19
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d5519211-8a04-4699-97bc-e162ec0f3781
exl-id: 12ae8b4c-73c5-4ec9-beea-b682b55ebdfd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1632'
ht-degree: 6%

---

# Funzione blog {#blog-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La funzione blog per AEM Communities si è trasformata da attività di authoring a una vera attività community che si svolge nell’ambiente di pubblicazione.

La funzione blog supporta la fornitura di informazioni sulla community in un formato di inserimento nel journal. Le voci di blog vengono effettuate nell&#39;ambiente di pubblicazione da membri autorizzati (utenti registrati e registrati).

La funzione blog fornisce:

* Creazione lato pubblicazione di articoli e commenti di blog
* Modifica RTF
* Immagini in linea (con supporto per trascinamento)
* Contenuto di social networking integrato ([Supporto oEmbed](blog-developer-basics.md#allowing-rich-media))
* Modalità Bozza
* Pubblicazione pianificata
* Composizione per conto terzi (a [membro privilegiato](users.md#privileged-members-group) può creare contenuti per conto di un membro della comunità diverso)
* [Moderazione contestuale e collettiva](moderate-ugc.md) articoli e commenti di blog

Questa sezione della documentazione descrive

* Aggiunta della funzione blog a un sito AEM
* Impostazioni di configurazione per i componenti del blog

>[!NOTE]
>
>I componenti `Journal`e `Journal Sidebar` hanno titolo `Blog` e `Blog Sidebar`.
>
>La funzione blog disponibile nelle versioni AEM 6.0 e precedenti è stata rimossa. Era basato su un modello e consentiva solo agli autori di creare contenuti nell’ambiente di authoring.

## Aggiunta di componenti blog a una pagina {#adding-blog-components-to-a-page}

Se desideri aggiungere un blog a una pagina in modalità di authoring, utilizza il browser Componenti per individuare

* `Communities / Blog`
* `Communities / Blog Sidebar`

Trascinali nella posizione desiderata su una pagina in cui dovrebbe essere visualizzato il blog.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](blog-developer-basics.md#essentials-for-client-side) sono inclusi, è così che `Blog`apparirà il componente:

![chlimage_1-147](assets/chlimage_1-147.png)

E come `Blog Sidebar` apparirà:

![chlimage_1-148](assets/chlimage_1-148.png)

### Configurazione del blog {#configuring-blog}

Seleziona il `Blog` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![icona configura](assets/chlimage_1-149.png) ![Impostazioni del blog](assets/Blog-configure.png)

#### Scheda Impostazioni {#settings-tab}

Sotto la **[!UICONTROL Impostazioni]** , specifica le funzioni di base del blog:

* **[!UICONTROL Consenti miniatura allegato]**
Se questa opzione è selezionata, viene creata una miniatura dell&#39;immagine allegata.

* **[!UICONTROL Dimensione massima delle miniature di attacco]**
Dimensione massima (in pixel) dell&#39;immagine miniatura dell&#39;allegato. Il valore predefinito è 800 x 800.

* **[!UICONTROL Dimensione minima dell&#39;immagine per la miniatura]**
Dimensione minima (in byte) dell&#39;immagine per la generazione di miniature per le immagini in linea. Il valore predefinito è 100000 byte (100 kb).

* **[!UICONTROL Dimensione massima miniatura]**
Dimensione massima (in pixel) dell&#39;immagine in miniatura per l&#39;immagine in linea. Il valore predefinito è 800 x 800.

* **[!UICONTROL Consenti membri con privilegi]**
Se questa opzione è selezionata, solo i membri con privilegi possono creare contenuto.

* **[!UICONTROL Membri con privilegi consentiti]**
Aggiungi i membri con privilegi consentiti per creare contenuto.

* **[!UICONTROL Bloccare contenuti generati dagli utenti in modalità Modifica autore]**
Se attivato, blocca il contenuto generato dall’utente durante la modifica in modalità Autore.

* **[!UICONTROL Titolo del diario]**
Titolo del blog da visualizzare sulla pagina.
   >Nota:
   >Il Titolo del diario viene utilizzato per creare automaticamente l&#39;URL del blog. Dal titolo del giornale qui specificato viene utilizzato un massimo di 50 caratteri (con 5 caratteri aggiuntivi per l&#39;univocità) per creare l&#39;URL del blog.

* **[!UICONTROL Descrizione del diario]**
Descrizione del blog.

* **[!UICONTROL Topic per pagina]**

   Definisce il numero di post/commenti di blog visualizzati per pagina. Il valore predefinito è 10.

* **[!UICONTROL Moderato]**

   Se questa opzione è selezionata, è necessario approvare i post e i commenti dei blog prima che vengano visualizzati su un sito di pubblicazione. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiuso]**

   Se selezionato, il blog viene chiuso a nuovi post e commenti del blog. Il valore predefinito è deselezionato.

* **[!UICONTROL Editor Rich Text]**

   Se questa opzione è selezionata, è possibile inserire commenti e post di blog con tag. Il valore predefinito è selezionato.

* **[!UICONTROL Consenti assegnazione tag]**

   Se questa opzione è selezionata, consenti ai membri di aggiungere etichette di tag al proprio post (consulta **[!UICONTROL Campo tag]** ). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti caricamenti file]**

   Se questa opzione è selezionata, consenti l&#39;aggiunta di allegati di file a un post di blog o a un commento. Il valore predefinito è deselezionato.

* **[!UICONTROL Dimensione file massima]**

   Pertinente solo se `Allow File Uploads` è controllata. Questo campo limita le dimensioni (in byte) di un file caricato. Il valore predefinito è 104857600 (10 Mb).

* **[!UICONTROL Tipi di file consentiti]**

   Pertinente solo se `Allow File Uploads` è controllata. Elenco di estensioni di file separate da virgola con il separatore &quot;punto&quot;. Ad esempio: .jpg, .jpeg, .png, .doc, .docx, .pdf. Se sono specificati dei tipi di file, non sarà possibile caricare quelli non specificati. Il valore predefinito non è specificato in modo che tutti i tipi di file siano consentiti.

* **[!UICONTROL Dimensione massima per file immagine allegato]**

   Pertinente solo se l’opzione Consenti caricamenti file è selezionata. Numero massimo di byte di un file immagine caricato. Il valore predefinito è 2097152 (2 Mb).

* **[!UICONTROL Consenti risposte]**

   Se questa opzione è selezionata, consenti risposte ai commenti pubblicati sul post di blog. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti agli utenti di eliminare commenti e argomenti]**

   Se questa opzione è selezionata, consenti ai membri di eliminare i commenti e i post di blog che hanno pubblicato. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti Segui]**

   Se questa opzione è selezionata, includi la seguente funzione per gli articoli di blog, che consente ai membri di essere [notificato](notifications.md) di nuovi posti. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti iscrizioni e-mail]**

   Se questa opzione è selezionata, consente ai membri di ricevere notifiche sui nuovi post via e-mail ([abbonamento](subscriptions.md)). Richiede `Allow Following` da controllare e [e-mail configurata](email.md). Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti votazione]**

   Se questa opzione è selezionata, includi la funzionalità Voto con un post sul blog. Il valore predefinito è deselezionato.

* **[!UICONTROL Visualizza badge]**

   Se selezionato, visualizza guadagnato e assegnato [badge](implementing-scoring.md) con il post di blog di un membro. Il valore predefinito è deselezionato.

* **[!UICONTROL Consenti contenuto in primo piano]**

   se questa opzione è selezionata, l’idea può essere identificata come [contenuto in primo piano](featured.md). Il valore predefinito è deselezionato.

#### Scheda Moderazione utente {#user-moderation-tab}

Sotto la **[!UICONTROL Moderazione utente]** specificare le impostazioni di moderazione:

* **[!UICONTROL Rifiuta post]**

   Se questa opzione è selezionata, ai moderatori di membri affidabili sarà consentito di negare i post e impedire che il post appaia sul forum pubblico. Il valore predefinito è deselezionato.

* **[!UICONTROL Chiudi/Riapri argomenti]**

   Se questa opzione è selezionata, i moderatori di membri attendibili possono chiudere un argomento per ulteriori modifiche e commenti e riaprire un argomento. Il valore predefinito è deselezionato.

* **[!UICONTROL Segnala post]**

   Se questa opzione è selezionata, consentire ai membri di contrassegnare gli argomenti o i commenti di altri come inappropriati. Il valore predefinito è deselezionato.

* **[!UICONTROL Elenco di motivi per segnalazione]**

   Se questa opzione è selezionata, consenti ai membri di scegliere, da un elenco a discesa, il motivo per cui contrassegnano un argomento o un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Motivo per segnalazione personalizzato]**

   Se questa opzione è selezionata, consenti ai membri di inserire il proprio motivo per contrassegnare un argomento o un commento come inappropriato. Il valore predefinito è deselezionato.

* **[!UICONTROL Soglia moderazione]**

   Immettere il numero di volte in cui un argomento o un commento deve essere segnalato dai membri prima che i moderatori ne vengano informati. Il valore predefinito è 1 (una volta).

* **[!UICONTROL Limite segnalazione]**

   Immetti il numero di volte in cui un argomento o un commento deve essere contrassegnato prima che sia nascosto dalla visualizzazione pubblica. Se è impostato su -1, l&#39;argomento o il commento contrassegnato non viene mai nascosto dalla visualizzazione pubblica. In caso contrario, questo numero deve essere maggiore o uguale alla soglia di moderazione. Il valore predefinito è 5.

#### Scheda Campo tag {#tag-field-tab}

Sotto la **[!UICONTROL Campo tag]** , specifica i tag che possono essere applicati se **[!UICONTROL Consenti assegnazione tag]** controlla il **[!UICONTROL Impostazioni]** scheda:

* **[!UICONTROL Namespace consentiti]**

   Pertinente se `Allow Tagging` è controllato sotto **[!UICONTROL Impostazioni]** scheda . I tag che possono essere applicati sono limitati a quelli nelle categorie dello spazio dei nomi selezionate. L’elenco dei namespace include sia &quot;Tag standard&quot; (lo spazio dei nomi predefinito) che &quot;Includi tutti i tag&quot;. Il valore predefinito non è selezionato, il che significa che tutti i namespace sono consentiti.

* **[!UICONTROL Limite di suggerimenti]**

   Immettere il numero di tag da visualizzare come suggerimento al membro che pubblica sul forum. Un valore pari a -1 non indica limiti. Il valore predefinito è 0.

### Configurazione della barra laterale del blog {#configuring-blog-sidebar}

Quando fai doppio clic sul pulsante `Blog Sidebar` viene visualizzata una finestra di dialogo di modifica.

Sotto la **[!UICONTROL Impostazioni della barra laterale del diario]** specificare il formato della data per gli archivi e il tipo di voci da visualizzare nella barra laterale:

![chlimage_1-151](assets/chlimage_1-151.png)

* **[!UICONTROL Formato data]**

   Formato utilizzato per visualizzare gli archivi dei post di blog. Il formato utilizza segnaposto seguendo la convenzione Java.

   * aaaa: anno intero, come &#39;2015&#39;
   * Sì: anno breve, come &#39;15&#39;
   * MMMM: mese intero, come giugno
   * MMM: mese breve, come Jun
   * MM: numero del mese, ad esempio 06

   Il valore predefinito è &quot;aaaa MMMMM&quot; che mostrerebbe, ad esempio, &quot;2015 June&quot;

* **[!UICONTROL Tipo di visualizzazione]**

   Titolo e tipo di post di blog da visualizzare nella barra laterale. La scelta è tra

   * Autori
   * Categorie
   * Archivi

* **[!UICONTROL Percorso componente diario]**

   *(Facoltativo)* Posizione della risorsa blog da cui devono essere elencati gli articoli di blog. Se lasciato vuoto, utilizza il componente di resourceType `social/journal/components/hbs/journal` che appare sulla stessa pagina.

   * Ad esempio `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **[!UICONTROL Limite di suggerimenti]**

   Numero di articoli di blog da visualizzare. Un valore pari a -1 non indica alcun limite. Il valore predefinito è -1.

## Esperienza dei visitatori del sito {#site-visitor-experience}

Nell&#39;ambiente di pubblicazione, la funzione blog mostrerà l&#39;articolo più recente seguito da articoli di blog precedenti in ordine decrescente di creazione. Le barre laterali dei blog consentono ai visitatori del sito di applicare filtri per limitare la selezione degli articoli del blog visualizzati.

L&#39;articolo del blog è seguito da un link per pubblicare o visualizzare i commenti.

Quando si seleziona un articolo di blog, vengono visualizzati l&#39;articolo e i commenti del blog (se abilitati).

Altre funzionalità dipendono dal fatto che il visitatore del sito sia un moderatore, un amministratore, un membro della community, un membro privilegiato o un anonimo.

### Utilizzo degli articoli {#working-with-articles}

Quando si crea un nuovo articolo di blog, è possibile scegliere

1. Pubblica immediatamente
1. Pubblicare una bozza
1. Pubblicare in una data e un’ora pianificate

Gli articoli del blog verranno visualizzati nella scheda appropriata (Pubblicato, Bozza o Pianificato) per i membri in grado di creare al momento della pubblicazione.

#### Moderatori e amministratori {#moderators-and-administrators}

Quando l&#39;utente connesso dispone di privilegi di moderatore o amministratore, può eseguire [attività di moderazione](moderate-ugc.md) (come consentito dalla configurazione del componente) su tutti gli articoli di blog e i commenti pubblicati su un blog.

![chlimage_1-152](assets/chlimage_1-152.png)

### Membri {#members}

Quando l&#39;utente connesso è un membro della community o [membro privilegiato](users.md#privileged-members-group) (a seconda della configurazione), possono selezionare `New Article` per creare e pubblicare un nuovo articolo di blog.

In particolare, possono:

* Crea un nuovo articolo di blog
* Pubblica un nuovo articolo di blog per conto di un altro membro
* Pubblica un commento a un articolo del blog
* Modifica il proprio articolo o commento di blog
* Elimina il proprio articolo o commento di blog
* Contrassegna altri articoli o commenti di blog

![chlimage_1-153](assets/chlimage_1-153.png) ![chlimage_1-154](assets/chlimage_1-154.png)

### Anonimo {#anonymous}

I visitatori del sito che non hanno effettuato l&#39;accesso possono solo leggere articoli e commenti di blog pubblicati, tradurli se supportati, ma non possono aggiungere un articolo o un commento di blog né contrassegnare gli articoli o i commenti di altri.

![chlimage_1-155](assets/chlimage_1-155.png)

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Blog Essentials](blog-developer-basics.md) per sviluppatori.

Per la moderazione di post e commenti di blog, vedi [Moderazione dei contenuti generati dagli utenti](moderate-ugc.md).

Per assegnare tag ai post e ai commenti dei blog, consulta [Assegnazione tag ai contenuti generati dagli utenti](tag-ugc.md).

Per la traduzione di post e commenti del blog, vedi [Traduzione di contenuti generati dagli utenti](translate-ugc.md).
