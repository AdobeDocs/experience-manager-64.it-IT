---
title: Scopri il sito pubblicato
seo-title: Scopri il sito pubblicato
description: Passare a un sito pubblicato
seo-description: Passare a un sito pubblicato
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 2%

---


# Esperienza con il sito pubblicato {#experience-the-published-site}

## Passa a nuovo sito in Pubblica {#browse-to-new-site-on-publish}

Ora che il sito community appena creato è stato pubblicato, individuate l’URL visualizzato al momento della creazione del sito, ma sul server di pubblicazione, ad esempio

* URL autore = http://localhost:4502/content/sites/engage/en.html
* URL pubblicazione = http://localhost:4503/content/sites/engage/en.html

Per ridurre la confusione relativa al membro che ha effettuato l’accesso in fase di creazione e pubblicazione, si consiglia di utilizzare browser diversi per ogni istanza.

Al primo arrivo sul sito pubblicato, il visitatore del sito in genere non avrebbe già effettuato l’accesso e sarebbe anonimo.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## Visitatore anonimo del sito {#anonymous-site-visitor}

Un visitatore anonimo del sito vede quanto segue nell’interfaccia utente:

* Titolo del sito. Esercitazione introduttiva
* Nessun collegamento profilo
* Nessun collegamento messaggi
* Nessun collegamento di notifica
* Campo di ricerca
* Collegamento di accesso
* Il banner del marchio
* Collegamenti al menu per i componenti inclusi nel Modello del sito di riferimento

Se selezionate vari collegamenti, questi saranno in modalità di sola lettura.

## Impedisci l&#39;accesso anonimo su JCR {#prevent-anonymous-access-on-jcr}

Una limitazione nota espone il contenuto del sito community ai visitatori anonimi attraverso contenuti jcr e json, anche se **consenti l&#39;accesso anonimo** è disabilitato per il contenuto del sito. Tuttavia, questo comportamento può essere controllato utilizzando Limitazioni Sling come soluzione alternativa.

Per proteggere i contenuti del sito della community dall&#39;accesso di utenti anonimi tramite contenuti jcr e json, procedi come segue:

1. Nell&#39;istanza di AEM Author, andate a https://&lt;host>:&lt;porta>/editor.html/content/site/&lt;nome sito>.html.

   >[!NOTE]
   >
   >Non andate al sito localizzato.

1. Vai a **[!UICONTROL Proprietà pagina]**.

   ![autenticazione del sito](assets/site-authentication.png)

1. Vai alla scheda **[!UICONTROL Avanzate]**.

   ![page-properties](assets/page-properties.png)

1. Abilita **[!UICONTROL Autenticazione richiesta]**.
1. Aggiungete il percorso della pagina di login. Esempio, `/content/......./GetStarted`.
1. Pubblicate la pagina.

## Membro della community trusted {#trusted-community-member}

Questa esperienza presuppone che [Aaron McDonald](tutorials.md#demo-users) sia stato assegnato il ruolo di [community manager e moderatore](create-site.md#roles). In caso contrario, tornate all&#39;ambiente di authoring per [modificare le impostazioni del sito](sites-console.md#modifying-site-properties) e selezionate Aaron McDonald come manager e moderatore della community.

Nell&#39;angolo in alto a destra, selezionare `Log in` e firmare con nome utente &quot;aaron.mcdonald@mailinator.com&quot; e password &quot;password&quot;. Notate la possibilità di accedere con le credenziali di Twitter o Facebook.

![chlimage_1-312](assets/chlimage_1-312.png)

Una volta effettuato l&#39;accesso, viene visualizzata una nuova voce di menu, `Administration`, in quanto al membro è stato assegnato il ruolo di Moderatore. Ora la selezione di vari collegamenti è più interessante.

![chlimage_1-313](assets/chlimage_1-313.png)

Notate che la pagina Calendario è la home page perché il modello di sito di riferimento scelto includeva prima la funzione Calendario, seguita dalla funzione Flusso di attività, dalla funzione Forum e così via. Questa struttura è visibile dalla console [Site Template](sites.md#edit-site-template) o durante la modifica delle proprietà del sito nell&#39;ambiente di authoring:

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Per maggiori informazioni sui componenti e sulle funzioni di Community, visita
>
>* [Componenti](author-communities.md)  Community (per autori)
>* [Componenti, funzioni e funzionalità Essentials](essentials.md)  (per sviluppatori)

>



## Collegamento forum {#forum-link}

Per visualizzare la funzione forum di base, fate clic sul collegamento Forum.

I membri possono pubblicare un nuovo argomento o seguire un argomento.

I visitatori del sito possono visualizzare i post e ordinarli in vari modi.

![chlimage_1-315](assets/chlimage_1-315.png)

## Collegamento gruppi {#groups-link}

Poiché Aaron è un amministratore di gruppo, selezionando il collegamento Gruppi, Aaron potrà creare un nuovo gruppo di community selezionando un modello di gruppo, un’immagine, un gruppo aperto o segreto e i membri invitati.

Questo è un esempio in cui viene creato un gruppo nell’ambiente di pubblicazione.

I gruppi possono essere creati anche nell&#39;ambiente di authoring e gestiti all&#39;interno del sito community nell&#39;ambiente di authoring (la [console Gruppi community](groups.md)). L&#39;esperienza di [creazione di gruppi in author](nested-groups.md) è descritta di seguito in questa esercitazione.

![chlimage_1-316](assets/chlimage_1-316.png)

Crea un gruppo di riferimento:

1. Selezionare **[!UICONTROL Nuovo gruppo]**
1. **[!UICONTROL scheda Impostazioni]**
   * Nome gruppo: `Sports`
   * Descrizione: `A parent group for various sporting groups`
   * Nome URL del gruppo: `sports`
   * selezionare `Open Group` (consentire a qualsiasi membro della community di partecipare partecipando)
1. **[!UICONTROL Scheda Modello]**
   * Selezionare `Reference Group` (contiene una funzione di gruppi nella struttura per consentire i gruppi nidificati)
1. Selezionare **[!UICONTROL Crea gruppo]**

![chlimage_1-317](assets/chlimage_1-317.png)

Dopo la creazione del nuovo gruppo, **selezionate il nuovo gruppo Sport** per creare due gruppi (nidificati) al suo interno. Poiché una struttura del sito non può iniziare con la funzione dei gruppi, dopo aver aperto il gruppo Sport, è necessario selezionare il collegamento Gruppi:

![chlimage_1-318](assets/chlimage_1-318.png)

Il secondo gruppo di collegamenti, a partire da `Blog`, appartiene al gruppo attualmente selezionato, il `Sports`gruppo. Selezionando il collegamento Sport `Groups`, è possibile nidificare due gruppi all&#39;interno del gruppo Sport.

Ad esempio, aggiungere due n `ew groups.`

* Uno denominato `Baseball`
   * Lascialo impostato come `Open Group` (iscrizione obbligatoria)
   * Nella scheda Modelli, selezionare `Conversational Group`
* Uno denominato `Gymnastics`
   * Cambia l&#39;impostazione in `Member Only Group` (iscrizione limitata)
   * Nella scheda Modelli, selezionare `Conversational Group`

**Avviso**:

* Prima di visualizzare entrambi i gruppi potrebbe essere necessario aggiornare la pagina
* Questo modello *non *include la funzione dei gruppi, per cui non sarà possibile effettuare un&#39;ulteriore nidificazione dei gruppi
* All&#39;autore, la [console Gruppi](groups.md) offre una terza scelta, ovvero un `Public Group` (iscrizione facoltativa)

Una volta creati entrambi i gruppi, selezionate il gruppo Baseball, un gruppo aperto e notate i relativi collegamenti: `Discussions` `What's New` `Members`
I collegamenti del gruppo sono visualizzati sotto i collegamenti del sito principale e i risultati sono la seguente visualizzazione:

![chlimage_1-319](assets/chlimage_1-319.png)

Per l&#39;autore, con privilegi amministrativi, andate alla console [Gruppi community](members.md) e aggiungete Weston McCall al gruppo `Community Engage Gymnastics <uid> Members`.

Continuando a pubblicare, disconnettetevi come Aaron McDonald e visualizzate i gruppi nel Gruppo sportivo come visitatore anonimo del sito:

* Dalla home page
* Seleziona `Groups`collegamento
* Seleziona `Sports`collegamento
* Selezionare il collegamento Sport&#39; `Groups`

Solo il gruppo di baseball sarà visibile.

Effettuate l&#39;accesso come Weston McCall (weston.mccall@dodgit.com / password) e andate alla stessa posizione. Notate che Weston è in grado di `Join` il gruppo `Baseball` aperto e `enter or Leave` il gruppo privato `Gymnastics`.

![chlimage_1-320](assets/chlimage_1-320.png)

## Collegamento pagina Web {#web-page-link}

Visualizzare la pagina Web di base inclusa nel sito selezionando il collegamento Pagina Web. Per aggiungere contenuti a questa pagina nell’ambiente di authoring è possibile utilizzare gli strumenti AEM di authoring standard.

Ad esempio, andate all&#39;istanza **author**, aprite la cartella `engage` nella console [Siti community](sites-console.md), selezionate l&#39;icona **Apri sito** per passare alla modalità di modifica dell&#39;autore. Selezionate quindi la modalità di anteprima per selezionare il collegamento `Web Page`e quindi la modalità di modifica per aggiungere i componenti Titolo e Testo. Infine, ripubblicate solo la pagina o l’intero sito.

![chlimage_1-321](assets/chlimage_1-321.png)

## Collegamento di amministrazione {#administration-link}

Quando il membro della community dispone di privilegi di moderazione, il collegamento Amministrazione sarà visibile e la selezione di tale collegamento comporterà la visualizzazione del contenuto della community pubblicato e la possibilità di essere [moderato](moderate-ugc.md) in modo simile alla [console di moderazione](moderation.md) nell&#39;ambiente di authoring.

Utilizzate il pulsante Indietro del browser per tornare al sito pubblicato. La maggior parte delle console non è accessibile dalla navigazione globale nell’ambiente di pubblicazione.

![chlimage_1-322](assets/chlimage_1-322.png)

## Registrazione automatica {#self-registration}

Dopo la disconnessione, è possibile creare una nuova registrazione utente.

* Seleziona `Log In`
* Seleziona `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

Per impostazione predefinita, l’indirizzo e-mail è l’ID di login. Se questa opzione è deselezionata, il visitatore può immettere il proprio ID di accesso (nome utente). Il nome utente deve essere univoco nell’ambiente di pubblicazione.

Dopo aver specificato il nome utente, l&#39;e-mail e la password, selezionando `Sign Up`l&#39;utente verrà creato e gli verrà consentito di firmare.

Una volta effettuato l&#39;accesso, la prima pagina presentata è la relativa `Profile`pagina, che possono personalizzare.

![chlimage_1-325](assets/chlimage_1-325.png)

Se il membro dimentica il suo ID di accesso, è possibile recuperare utilizzando il suo indirizzo e-mail.

![chlimage_1-326](assets/chlimage_1-326.png)
