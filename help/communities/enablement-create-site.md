---
title: Creazione di un nuovo sito community per l'abilitazione
seo-title: Creazione di un nuovo sito community per l'abilitazione
description: Creazione di un sito community per l'abilitazione
seo-description: Creazione di un sito community per l'abilitazione
uuid: 6822cc99-e272-4661-bddf-aa0800b88c41
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: aff8b79f-dd4e-486e-9d59-5d09dfe34f27
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '1744'
ht-degree: 3%

---


# Creazione di un nuovo sito community per l&#39;abilitazione {#author-a-new-community-site-for-enablement}

## Crea sito community {#create-community-site}

[La creazione](sites-console.md) di siti community utilizza una procedura guidata che guida l&#39;utente attraverso i passaggi necessari per creare un sito community. È possibile passare al `Next`passo precedente o `Back`al passo precedente prima di eseguire il commit del sito nel passaggio finale.

Per iniziare a creare un nuovo sito community:

Utilizzo dell’istanza di [creazione](Http://localhost:4502/)

* Accesso con privilegi di amministratore
* Vai a **[!UICONTROL Community > Siti]**

* Seleziona **[!UICONTROL Crea]**

### Passaggio 1: Modello del sito {#step-site-template}

![enablementsitetemplate](assets/enablementsitetemplate.png)

Nel passaggio Modello **** sito, immettete un titolo, una descrizione, il nome dell&#39;URL e selezionate un modello di sito community, ad esempio:

* **Titolo del sito community**: `Enablement Tutorial`

* **Descrizione del sito community**: `A site for enabling the community to learn.`

* **Radice** sito community: (lasciare vuoto per la radice predefinita `/content/sites`)

* **Configurazioni** cloud: (lasciate vuoto se non sono specificate configurazioni cloud) fornite il percorso alle configurazioni cloud specificate.
* **Lingua** di base del sito community: (lasciare invariate le lingue per una sola: Inglese) utilizzate il menu a discesa per scegliere una *o più* lingue di base tra quelle disponibili: tedesco, italiano, francese, giapponese, spagnolo, portoghese (Brasile), cinese (tradizionale) e cinese (semplificato). Verrà creato un sito community per ogni lingua aggiunta, all&#39;interno della stessa cartella del sito seguendo la procedura descritta in [Traduzione di contenuti per siti](../../help/sites-administering/translation.md)multilingue. La pagina principale di ciascun sito conterrà una pagina figlia denominata dal codice della lingua di una delle lingue selezionate, ad esempio &#39;en&#39; per l&#39;inglese o &#39;fr&#39; per il francese.

* **[!UICONTROL Nome sito community]**: `enable`

   * l&#39;URL iniziale verrà visualizzato sotto il nome del sito community
   * per un URL valido, aggiungete un codice della lingua di base + &quot;.html&quot;

      *ad esempio*, http://localhost:4502/content/sites/ `enable/en.html`

* **[!UICONTROL Modello]** del sito di riferimento: premuto per scegliere `Reference Structured Learning Site Template`

Seleziona **[!UICONTROL Avanti]**

### Passaggio 2: Progettazione {#step-design}

Il passaggio Progettazione viene presentato in due sezioni per selezionare il tema e il banner di branding:

#### COMMUNITY SITE THEME {#community-site-theme}

Selezionate lo stile da applicare al modello. Quando è selezionato, il tema sarà sovrapposto con un segno di spunta.

![enablementsitetheme](assets/enablementsitetheme.png)

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Facoltativo) Caricate un&#39;immagine banner da visualizzare nelle pagine del sito. Il banner è fissato al bordo sinistro del browser, tra l&#39;intestazione del sito community e il menu (collegamenti di navigazione). L’altezza del banner viene ritagliata a 120 pixel. Il banner non può essere ridimensionato in modo da adattarlo alla larghezza del browser e all&#39;altezza di 120 pixel.

![chlimage_1-284](assets/chlimage_1-284.png) ![chlimage_1](assets/chlimage_1.jpeg)

Seleziona **[!UICONTROL Avanti]**.

### Passaggio 3: Impostazioni {#step-settings}

Nella fase Settings (Impostazioni), prima di selezionare `Next`, sono presenti sette sezioni che forniscono l&#39;accesso alle configurazioni che includono gestione utente, tag, ruoli, moderazione, analisi, traduzione e abilitazione.

#### USER MANAGEMENT {#user-management}

È consigliabile che le comunità di [abilitazione](overview.md#enablement-community) siano private.

Un sito community è privato quando ai visitatori anonimi viene negato l&#39;accesso, non può registrarsi autonomamente e non può utilizzare il login mediante social network.

Verificare che la maggior parte delle caselle di controllo non sia selezionata per Gestione [](sites-console.md#user-management)utente:

* NON consentire ai visitatori del sito di registrarsi autonomamente
* NON consentire ai visitatori anonimi del sito di visualizzare il sito
* Facoltativo per consentire o meno la messaggistica tra i membri della community
* NON consentire l&#39;accesso con Facebook
* NON consentire l&#39;accesso con Twitter

![chlimage_1-285](assets/chlimage_1-285.png)

#### TAGGING {#tagging}

I tag che possono essere applicati al contenuto della community sono controllati selezionando gli spazi di nomi AEM definiti in precedenza tramite la console [](../../help/sites-administering/tags.md#tagging-console) Tagging (ad esempio lo spazio dei nomi [delle](enablement-setup.md#create-tutorial-tags)esercitazioni).

Inoltre, selezionando Tag namespace per il sito della community, la selezione presentata nella definizione di cataloghi e risorse di abilitazione viene limitata. Per informazioni importanti, consulta [Assegnazione di tag alle risorse](tag-resources.md) di abilitazione.

La ricerca di spazi dei nomi è semplice tramite la ricerca tipo-avanti. Ad esempio,

* Tipo &#39;tut&#39;
* Seleziona `Tutorial`

![chlimage_1-286](assets/chlimage_1-286.png)

### ROLES {#roles}

[I ruoli](users.md) dei membri della community vengono assegnati tramite le impostazioni nella sezione Ruoli.

Per consentire a un membro della comunità (o a un gruppo di membri) di utilizzare il sito come manager della comunità, utilizzate la ricerca tipo avanti e selezionate il nome del membro o del gruppo dalle opzioni disponibili nel menu a discesa.

Ad esempio,

* Tipo &quot;q&quot;
* Seleziona [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Il servizio](deploy-communities.md#tunnel-service-on-author) Tunnel consente la selezione di membri e gruppi esistenti solo nell’ambiente di pubblicazione.

![community_roles](assets/community_roles.png)

#### MODERATION {#moderation}

Accettate le impostazioni globali predefinite per [moderare](sites-console.md#moderation) il contenuto generato dall&#39;utente (UGC).

![chlimage_1-287](assets/chlimage_1-287.png)

#### ANALYTICS {#analytics}

Dal menu a discesa, seleziona il framework del servizio cloud di Analytics configurato per questo sito community.

La selezione vista nello screenshot `Communities`, è l&#39;esempio di framework tratto dalla documentazione di [configurazione.](analytics.md#aem-analytics-framework-configuration)

![chlimage_1-288](assets/chlimage_1-288.png)

#### TRANSLATION {#translation}

Le impostazioni [di](sites-console.md#translation) traduzione specificano se è possibile convertire o meno UGC e in quale lingua, se lo è.

* Controlla **[!UICONTROL Consenti traduzione automatica]**
* Utilizzare le impostazioni predefinite

![chlimage_1-289](assets/chlimage_1-289.png)

#### ENABLEMENT {#enablement}

Per una comunità di abilitazione, è necessario identificare uno o più manager di abilitazione della community.

* **[!UICONTROL Manager]** abilitazione (obbligatorio) Membri del gruppo 
`Community Enablement Managers` sono disponibili per essere selezionati per gestire questo sito community.

   * Tipo &quot;s&quot;
   * Seleziona `Sirius Nilson`

* **[!UICONTROL ID]** organizzazione Marketing Cloud (facoltativo) ID per un account Adobe Analytics , necessario per l’inclusione di [Video Heartbeat Analytics](analytics.md#video-heartbeat-analytics) nella generazione dei rapporti di abilitazione.

![chlimage_1-290](assets/chlimage_1-290.png)

Seleziona **[!UICONTROL Avanti]**.

### Passaggio 4: Crea sito community {#step-create-community-site}

Seleziona **[!UICONTROL Crea]**.

![chlimage_1-291](assets/chlimage_1-291.png)

Al termine del processo, la cartella del nuovo sito viene visualizzata nella console Community - Siti.

![enablementecreated](assets/enablementsitecreated.png)

### Pubblicare il nuovo sito della community {#publish-the-new-community-site}

Il sito creato deve essere gestito dalla console Community - Siti, la stessa console da cui è possibile creare nuovi siti.

Dopo aver selezionato la cartella del sito della community, passate il puntatore sull&#39;icona del sito in modo che vengano visualizzate quattro icone di azione:

![siteactionicons](assets/siteactionicons.png)

Selezionando l&#39;icona delle ellissi (icona Altre azioni), vengono visualizzate le opzioni Esporta sito ed Elimina sito.

![siteactionsnew](assets/siteactionsnew.png)

Da sinistra a destra sono:

* **Apri sito** Selezionate l’icona matita per aprire il sito della community in modalità di modifica dell’autore, per aggiungere e/o configurare componenti della pagina

* **Modifica sito** Selezionate l&#39;icona delle proprietà per aprire il sito della community e modificare le proprietà, ad esempio il titolo o il tema

* **Pubblica sito** Selezionate l&#39;icona del mondo per pubblicare il sito della community (per impostazione predefinita, localhost:4503)

* **Esporta sito** Selezionate l&#39;icona di esportazione per creare un pacchetto del sito della community che viene memorizzato e scaricato in [Gestione](../../help/sites-administering/package-manager.md) pacchetti.

   UGC non è incluso nel pacchetto del sito.

* **Elimina sito** Per eliminare il sito community, selezionate l&#39;icona Elimina sito visualizzata quando si passa il mouse sul sito nella console del sito di Communities. Questa azione rimuove tutti gli elementi associati al sito, come UGC, gruppi di utenti, risorse e record del database.

![enablesiteazioni](assets/enablesiteactions.png)

#### Selezionate Pubblica {#select-publish}

Selezionate l&#39;icona del mondo per pubblicare il sito della community.

![chlimage_1-292](assets/chlimage_1-292.png)

Ci sarà un&#39;indicazione che il sito è stato pubblicato.

![chlimage_1-293](assets/chlimage_1-293.png)

## Utenti e gruppi di utenti della community {#community-users-user-groups}

### Notifica nuovi gruppi di utenti community {#notice-new-community-user-groups}

Insieme al nuovo sito della community, vengono creati nuovi gruppi di utenti che dispongono delle autorizzazioni appropriate impostate per diverse funzioni amministrative. Per informazioni dettagliate, visitate Gruppi di [utenti per i siti](users.md#usergroupsforcommunitysites)della community.

Per questo nuovo sito community, dato il nome del sito &quot;enable&quot; nel passaggio 1, i nuovi gruppi di utenti presenti nell&#39;ambiente di pubblicazione possono essere visualizzati dalla console [Membri e gruppi di](members.md#groups-console)Communities:

![chlimage_1-294](assets/chlimage_1-294.png)

### Assegna membri a gruppo Abilita membri community {#assign-members-to-community-enable-members-group}

Per l&#39;autore, con il servizio tunnel attivato, è possibile assegnare gli [utenti creati durante l&#39;impostazione](enablement-setup.md#publishcreateenablementmembers) iniziale al gruppo Membri della community per il nuovo sito community creato.

Utilizzando la console Gruppi community, i membri possono essere aggiunti singolarmente o tramite appartenenza a un gruppo.

In questo esempio, il gruppo `Community Ski Class` viene aggiunto sia come membro del gruppo `Community Enable Members` che come membro `Quinn Harper`.

* Passa alla console **[!UICONTROL Community > Gruppi]**
* Seleziona gruppo **[!UICONTROL Abilita membri]** community
* Immettere `ski` nella casella di ricerca **[!UICONTROL Aggiungi membri a gruppo]**
* Selezione classe **[!UICONTROL di sci]** community (gruppo di studenti)
* Immettere `quinn` nella casella di ricerca
* Seleziona **[!UICONTROL Quinn Harper]** (contatto per l&#39;abilitazione delle risorse)

* Seleziona **[!UICONTROL Salva]**

![chlimage_1-295](assets/chlimage_1-295.png)

## Configurazioni su Pubblica {#configurations-on-publish}

### http://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}

![chlimage_1-296](assets/chlimage_1-296.png)

### Configura per errore di autenticazione {#configure-for-authentication-error}

Una volta configurato un sito e inviato per la pubblicazione, [configurate la mappatura](sites-console.md#configure-for-authentication-error) di accesso ( `Adobe Granite Login Selector Authentication Handler`) nell’istanza di pubblicazione. Il vantaggio è che quando le credenziali di accesso non vengono immesse correttamente, l&#39;errore di autenticazione riaprirà la pagina di accesso del sito community con un messaggio di errore.

Aggiungi un `Login Page Mapping` nome

* /content/sites/enable/it/signin:/content/sites/enable/it

### (Facoltativo) Cambia la home page predefinita {#optional-change-the-default-home-page}

Quando lavorate con il sito di pubblicazione a scopo dimostrativo, potrebbe essere utile modificare la pagina principale predefinita nel nuovo sito.

A tal fine, è necessario utilizzare [CRX|DE](http://localhost:4503/crx/de) Lite per modificare la tabella di mappatura [delle](../../help/sites-deploying/resource-mapping.md) risorse al momento della pubblicazione.

Per iniziare

1. Al momento della pubblicazione, accedete a CRXDE ed effettuate l&#39;accesso con privilegi di amministratore

   * Ad esempio, accedete a [http://localhost:4503/crx/de](http://localhost:4503/crx/de) e accedete con `admin/admin`

1. Nel browser del progetto, espandi `/etc/map`
1. Selezionare il `http` nodo

   * Seleziona **[!UICONTROL Crea nodo]**

      * **Nome** localhost.4503

         ( *Non* utilizzare `:`)

      * **Tipo** [sling:mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Con `localhost.4503` nodo appena creato selezionato

   * Aggiungi, proprietà

      * **Nome** sling:match
      * **Stringa tipo**
      * **Valore** localhost.4503/\$

         (Deve terminare con il carattere &#39;$&#39;)
   * Aggiungi, proprietà

      * **Nome** sling:internalRedirect
      * **Stringa tipo**
      * **Valore** /content/sites/enable/en.html


1. Seleziona **[!UICONTROL Salva tutto]**
1. (facoltativo) Elimina la cronologia di navigazione
1. Passa a http://localhost:4503/

   * Arrivate a http://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Per disattivare, anteponete semplicemente il valore della `sling:match` proprietà con &#39;x&#39; - `xlocalhost.4503/$` - e **[!UICONTROL Salva tutto]**.

![chlimage_1-297](assets/chlimage_1-297.png)

#### Risoluzione dei problemi: Errore durante il salvataggio della mappa {#troubleshooting-error-saving-map}

Se non è possibile salvare le modifiche, assicurarsi che il nome del nodo sia `localhost.4503`, con un separatore &#39;punto&#39; e non `localhost:4503` con un separatore &#39;due punti&#39;, in quanto non `localhost`è un prefisso valido per lo spazio nomi.

![chlimage_1-298](assets/chlimage_1-298.png)

#### Risoluzione dei problemi: Impossibile eseguire il reindirizzamento {#troubleshooting-fail-to-redirect}

Il valore &#39;**$**&#39; alla fine della `sling:match`stringa di espressione regolare è cruciale, in modo che solo `http://localhost:4503/` venga mappato esattamente, altrimenti il valore di reindirizzamento viene anteposto a qualsiasi percorso che potrebbe esistere dopo il server:port nell&#39;URL. Pertanto, quando AEM tenta di reindirizzare alla pagina di accesso, non riesce.

## Modifica del sito community {#modifying-the-community-site}

Dopo la creazione iniziale del sito, gli autori possono utilizzare l&#39;icona [](sites-console.md#authoring-site-content) Apri sito per eseguire le attività standard di authoring AEM.

Inoltre, gli amministratori possono utilizzare l’icona [](sites-console.md#modifying-site-properties) Modifica sito per modificare le proprietà del sito, ad esempio il titolo.

Dopo ogni modifica, ricordate di **salvare** e **pubblicare** nuovamente il sito.

>[!NOTE]
>
>Se non avete familiarità con AEM, consultate la documentazione sulla gestione [](../../help/sites-authoring/basic-handling.md) di base e una guida [rapida alle pagine](../../help/sites-authoring/qg-page-authoring.md)di authoring.

### Aggiungere un catalogo {#add-a-catalog}

Il modello di sito community scelto per questo sito community deve contenere la funzione di catalogo.

In caso contrario, è possibile aggiungere facilmente la funzione catalogo. Ciò consentirebbe ad altri membri della comunità, non assegnati a risorse di abilitazione o a un percorso di apprendimento, di selezionare le risorse di abilitazione da un catalogo.

Se la struttura del sito contiene già la funzione catalogo, è possibile modificarne il Titolo.

Per modificare la struttura del sito, accedete alla console **[!UICONTROL Community, Siti]** , aprite la `enable` cartella e selezionate l&#39;icona **Modifica sito** per accedere alle proprietà di `Enablement Tutorial`.

Selezionate il pannello STRUTTURA per aggiungere un catalogo o modificarne uno esistente:

* **Titolo**: `Ski Catalog`

* **URL**: `catalog`

* **Seleziona tutti gli spazi dei nomi**: lasciate come predefinito.
* Seleziona **[!UICONTROL Salva]**

![chlimage_1-299](assets/chlimage_1-299.png)

Utilizzate l&#39;icona Posizione per spostare la funzione Catalogo nella seconda posizione, dopo Assegnazioni.

![chlimage_1-300](assets/chlimage_1-300.png)

Selezionate **[!UICONTROL Salva]** nell&#39;angolo in alto a destra per salvare le modifiche apportate al sito della community.

Quindi **pubblicate nuovamente** il sito.