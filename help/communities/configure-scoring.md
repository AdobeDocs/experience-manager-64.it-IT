---
title: Punteggio e Badge Essentials
seo-title: Punteggio e Badge Essentials
description: Panoramica delle funzioni Punteggio e Badge
seo-description: Panoramica delle funzioni Punteggio e Badge
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 1%

---


# Punteggio e Badge Essentials {#scoring-and-badges-essentials}

La funzione  punteggio e distintivi AEM Communities consente di identificare e premiare i membri della community.

I dettagli relativi alla configurazione della funzione sono descritti in

* [Punteggio e distintivi delle community](implementing-scoring.md)

Questa pagina contiene ulteriori dettagli tecnici:

* Come [visualizzare un contrassegno](#displaying-badges) come immagine o testo
* Come attivare la registrazione [debug estesa](#debug-log-for-scoring-and-badging)
* Come [accedere a UGC](#ugc-for-scoring-and-badging) in relazione al punteggio e al contrassegno

>[!CAUTION]
>
>La struttura di implementazione visibile in CRXDE Lite è soggetta a modifiche.

## Visualizzazione dei Badge {#displaying-badges}

Se un contrassegno viene visualizzato come testo o immagine viene controllato sul lato client nel modello HBS.

Ad esempio, cercare `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Se true, isAssigned indica che il contrassegno è stato assegnato a un ruolo e che il contrassegno deve essere visualizzato come testo.

Se false, viene assegnato indica che il contrassegno è stato assegnato per un punteggio ottenuto e che il contrassegno deve essere visualizzato come immagine.

Eventuali modifiche a questo comportamento devono essere apportate in uno script personalizzato (override o sovrapposizione). Vedere [Personalizzazione lato client](client-customize.md).

## Registro di debug per il punteggio e il contrassegno {#debug-log-for-scoring-and-badging}

Per facilitare il debug del punteggio e del contrassegno, è possibile configurare un file di registro personalizzato. Il contenuto di questo file di registro può quindi essere fornito all&#39;assistenza clienti in caso di problemi con la funzionalità.

Per istruzioni dettagliate, visitare [Crea un file di registro personalizzato](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

Per impostare rapidamente un file slinglog:

1. Accedere al **[!UICONTROL supporto dei registri della console Web Adobe Experience Manager]**, ad esempio

   * http://localhost:4502/system/console/slinglog

1. Selezionare **[!UICONTROL Aggiungi nuovo logger]**

   1. Selezionare `DEBUG` per **[!UICONTROL Livello di registro]**
   1. Immettere un nome per **[!UICONTROL File di registro]**, ad esempio

      * logs/scoring-debug.log
   1. Immettere due voci **[!UICONTROL Logger]** (classe) (utilizzando l&#39;icona `+`)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Seleziona **[!UICONTROL Salva]**



![chlimage_1-248](assets/chlimage_1-248.png)

Per visualizzare le voci di registro:

* Dalla console Web

   * Nel menu **[!UICONTROL Stato]**
   * Selezionare **[!UICONTROL File di registro]**
   * Cerca il nome del file di registro, ad esempio `scoring-debug`

* Sul disco locale del server

   * Il file di registro si trova in &lt;*server-install-dir*/crx-quickstart/logs/&lt;*log-file-name*.log
   * Esempio, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC per il punteggio e il contrassegno {#ugc-for-scoring-and-badging}

È possibile visualizzare l&#39;UGC relativo al punteggio e al contrassegno quando l&#39;SRP scelto è JSRP o MSRP, ma non ASRP. (Se non avete familiarità con questi termini, consultate [Community Content Storage](working-with-srp.md) e [Panoramica del provider di risorse di storage](srp.md).)

Le descrizioni per accedere ai dati di punteggio e contrassegno utilizzano JSRP, in quanto l&#39;UGC è facilmente accessibile tramite [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**JSRP sull’autore**: la sperimentazione nell’ambiente di authoring produce UGC visibile solo dall’ambiente di authoring.

**JSRP al momento della pubblicazione**: analogamente, se si eseguono test nell’ambiente di pubblicazione, sarà necessario accedere ai CRXDE Lite con privilegi amministrativi in un’istanza di pubblicazione. Se l&#39;istanza di pubblicazione è in esecuzione in [modalità di produzione](../../help/sites-administering/production-ready.md) (modalità di esecuzione nosamplecontent), sarà necessario [abilitare CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md).

La posizione di base dell&#39;UGC su JSRP è `/content/usergenerated/asi/jcr/`.

### API Punteggio e Badging {#scoring-and-badging-apis}

Le seguenti API sono disponibili per l&#39;uso:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Gli ultimi Javadocs per le [versioni](deploy-communities.md#LatestReleases) installate sono disponibili per gli sviluppatori dall&#39;archivio del Adobe . Vedere [Utilizzo di Maven per Communities: Javadocs](maven.md#javadocs).

**La posizione e il formato dell’UGC nel repository sono soggetti a modifiche senza preavviso**.

### Impostazione esempio {#example-setup}

Le schermate dei dati del repository derivano dalla configurazione del punteggio e del contrassegno per un forum su due siti AEM diversi:

1. Un sito AEM con un ID univoco (sito community creato tramite la procedura guidata):

   * Utilizzo del sito relativo all&#39;esercitazione introduttiva (interazione) creato durante l&#39;esercitazione [guida introduttiva](getting-started.md)
   * Individuare il nodo della pagina del forum

      * `/content/sites/engage/en/forum/jcr:content`
   * Aggiunta di proprietà di punteggio e contrassegno

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * Individuare il nodo del componente forum

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Aggiungi proprietà a simboli di visualizzazione

      * `allowBadges = true`
   * Un utente accede, crea un argomento del forum e riceve un contrassegno di bronzo





1. Un sito AEM *senza* un ID univoco:

   * Utilizzo della guida [Community Components](components-guide.md)
   * Individuare il nodo della pagina del forum

      * `/content/community-components/en/forum/jcr:content`
   * Aggiunta di proprietà di punteggio e contrassegno

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * Individuare il nodo del componente forum

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Aggiungi proprietà a simboli di visualizzazione

      * `allowBadges = true`
   * Un utente accede, crea un argomento del forum e riceve un contrassegno di bronzo




1. A un utente viene assegnato un contrassegno moderatore utilizzando cURL:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Come un utente ha guadagnato due simboli in bronzo e ha ricevuto un badge moderatore, questo è come appare l&#39;utente con la voce forum:

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Questo esempio non segue le best practice seguenti:
>
>* i nomi delle regole di punteggio devono essere univoci a livello globale; non devono terminare con lo stesso nome.\
   >  Esempio di operazione *not*:\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* creazione di immagini di contrassegno univoche per siti AEM diversi

>



### UGC punteggio di accesso {#access-scoring-ugc}

È preferibile utilizzare le [API](#scoring-and-badging-apis).

A scopo investigativo, utilizzando JSRP per esempio, la cartella base contenente i punteggi è

* `/content/usergenerated/asi/jcr/scoring`

Il nodo secondario di `scoring`è il nome della regola di punteggio. Di conseguenza, si consiglia di assegnare a un server nomi univoci per le regole di punteggio.

Per il sito di Geometrixx Engage, l&#39;utente e il relativo punteggio si trovano in un percorso conteggiato con il nome della regola di punteggio, l&#39;ID del sito della community ( `engage-ba81p`), un ID univoco e l&#39;ID dell&#39;utente:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Per il sito della guida per i componenti della community, l&#39;utente e il relativo punteggio si trovano in un percorso costruito con il nome della regola di punteggio, un ID predefinito ( `default-site`), un ID univoco e l&#39;ID dell&#39;utente:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Il punteggio è memorizzato nella proprietà `scoreValue_tl` che può contenere direttamente solo un valore o fare riferimento indirettamente a un atomicCounter.

![chlimage_1-251](assets/chlimage_1-251.png)

### Accesso UGC Badge {#access-badging-ugc}

È preferibile utilizzare le [API](#scoring-and-badging-apis).

A scopo investigativo, utilizzando JSRP per esempio, la cartella di base contenente informazioni sui simboli assegnati o assegnati è

* /content/usergenerated/asi/jcr

Seguito dal percorso del profilo dell&#39;utente, che termina in una cartella dei simboli, ad esempio

* /home/users/community/w271Oup2Z4DjnOQrviv/profile/badges

#### Contrassegno assegnato {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### contrassegno assegnato {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Informazioni aggiuntive {#additional-information}

Per visualizzare un elenco ordinato di membri in base ai punti:

* [Funzione ](functions.md#leaderboard-function) della classifica per l&#39;inclusione in un sito o modello di gruppo community.
* [Componente](enabling-leaderboard.md) Leaderboard, componente della funzione Leaderboard per l’authoring delle pagine.

