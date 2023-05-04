---
title: Nozioni di base sul punteggio e sui badge
seo-title: Scoring and Badges Essentials
description: Panoramica della funzione Punteggio e badge
seo-description: Scoring and Badges feature overview
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
exl-id: 84aa46d5-4ca4-4f6e-b0b9-fc9907be00a5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 2%

---

# Nozioni di base sul punteggio e sui badge {#scoring-and-badges-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La funzione di valutazione e badge di AEM Communities consente di identificare e premiare i membri della community.

I dettagli della configurazione della funzione sono descritti in

* [Punteggio e badge delle community](implementing-scoring.md)

Questa pagina contiene ulteriori dettagli tecnici:

* Come fare per [visualizzare un badge](#displaying-badges) come immagine o testo
* Come attivare esteso [registrazione debug](#debug-log-for-scoring-and-badging)
* Come fare per [accesso UGC](#ugc-for-scoring-and-badging) relativo al punteggio e al contrassegno

>[!CAUTION]
>
>La struttura di implementazione visibile in CRXDE Lite è soggetta a modifiche.

## Visualizzazione dei badge {#displaying-badges}

Se un badge viene visualizzato come testo o immagine è controllato sul lato client nel modello HBS.

Ad esempio, cerca `this.isAssigned` in `/libs/social/forum/components/hbs/topic/list-item.hbs`,

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

Se true, isAssigned indica che il badge è stato assegnato a un ruolo e che il badge deve essere visualizzato come testo.

Se false, viene assegnato indica che il badge è stato assegnato per un punteggio ottenuto e che il badge deve essere visualizzato come immagine.

Qualsiasi modifica a questo comportamento deve essere apportata in uno script personalizzato (override o sovrapposizione). Vedi [Personalizzazione lato client](client-customize.md).

## Registro di debug per il punteggio e il contrassegno {#debug-log-for-scoring-and-badging}

Per facilitare il debug del punteggio e del badging, è possibile impostare un file di registro personalizzato. Il contenuto di questo file di registro può quindi essere fornito all’assistenza clienti in caso di problemi con la funzione .

Per istruzioni dettagliate, visita [Creare un file di registro personalizzato](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

Per impostare rapidamente un file slinglog:

1. Accedere al **[!UICONTROL Supporto per il registro della console Web di Adobe Experience Manager]**, ad esempio

   * http://localhost:4502/system/console/slinglog

1. Seleziona **[!UICONTROL Aggiungi nuovo logger]**

   1. Seleziona `DEBUG` per **[!UICONTROL Livello di log]**
   1. Immettere un nome per **[!UICONTROL File di log]**, ad esempio

      * logs/scoring-debug.log
   1. Inserisci due **[!UICONTROL Registratore]** (classe) voci (utilizzando `+` icona)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Seleziona **[!UICONTROL Salva]**



![chlimage_1-248](assets/chlimage_1-248.png)

Per visualizzare le voci di registro:

* Dalla console Web

   * Sotto la **[!UICONTROL Stato]** menu
   * Seleziona **[!UICONTROL File di registro]**
   * Cerca il nome del file di registro, ad esempio `scoring-debug`

* Sul disco locale del server

   * Il file di registro si trova in &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*nome-file-registro*>.log
   * Ad esempio `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC per il punteggio e il badge {#ugc-for-scoring-and-badging}

È possibile visualizzare l’UGC relativo al punteggio e al contrassegno quando l’SRP scelto è JSRP o MSRP, ma non ASRP. (Se non conosci questi termini, consulta [Archiviazione dei contenuti della community](working-with-srp.md) e [Panoramica del provider di risorse di storage](srp.md).)

Le descrizioni per l’accesso ai dati di punteggio e badging utilizzano JSRP, in quanto l’UGC è facilmente accessibile tramite [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**JSRP sull&#39;autore**: la sperimentazione nell’ambiente di authoring genera contenuti generati dagli utenti che sono visibili solo nell’ambiente di authoring.

**JSRP in pubblicazione**: analogamente, se esegui test sull’ambiente di pubblicazione, sarà necessario accedere ad CRXDE Lite con privilegi amministrativi su un’istanza di pubblicazione. Se l&#39;istanza di pubblicazione è in esecuzione in [modalità di produzione](../../help/sites-administering/production-ready.md) (modalità runmode nosamplecontent), è necessario [abilita CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md).

La posizione di base di UGC su JSRP è `/content/usergenerated/asi/jcr/`.

### API di valutazione e contrassegno {#scoring-and-badging-apis}

Le seguenti API sono disponibili per l’utilizzo:

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Gli ultimi Javadocs per l&#39;installazione [release](deploy-communities.md#LatestReleases) sono disponibili per gli sviluppatori dall’archivio Adobe. Vedi [Utilizzo di Maven per Communities: Javadocs](maven.md#javadocs).

**La posizione e il formato dell’UGC nell’archivio sono soggetti a modifiche senza preavviso**.

### Configurazione di esempio {#example-setup}

Le schermate dei dati dell’archivio provengono dalla configurazione del punteggio e del badging per un forum su due siti di AEM diversi:

1. Un sito AEM con un ID univoco (sito community creato tramite la procedura guidata):

   * Utilizzo del sito tutorial (coinvolgi) introduttivo creato durante [esercitazione introduttiva](getting-started.md)
   * Individua il nodo della pagina del forum

      * `/content/sites/engage/en/forum/jcr:content`
   * Aggiungere proprietà di valutazione e contrassegno

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * Individua il nodo componente forum

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Aggiungi proprietà per visualizzare i badge

      * `allowBadges = true`
   * L&#39;utente effettua l&#39;accesso, crea un argomento del forum e viene assegnato un badge in bronzo





1. Un sito AEM *senza* un id univoco:

   * Utilizzo della [Guida ai componenti della community](components-guide.md)
   * Individua il nodo della pagina del forum

      * `/content/community-components/en/forum/jcr:content`
   * Aggiungere proprietà di valutazione e contrassegno

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * Individua il nodo componente forum

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Aggiungi proprietà per visualizzare i badge

      * `allowBadges = true`
   * L&#39;utente effettua l&#39;accesso, crea un argomento del forum e viene assegnato un badge in bronzo




1. A un utente viene assegnato un badge moderatore utilizzando cURL:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Come un utente ha guadagnato due distintivi di bronzo ed è stato assegnato un badge moderatore, questo è il modo in cui appare l&#39;utente con la loro voce del forum:

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Questo esempio non segue le seguenti best practice:
>
>* i nomi delle regole di punteggio devono essere univoci a livello globale; non devono terminare con lo stesso nome.\
   >  Un esempio di cosa *not* per eseguire:\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
>
>* creazione di immagini di badge univoche per siti AEM diversi
>


### UGC per il punteggio di accesso {#access-scoring-ugc}

Uso del [API](#scoring-and-badging-apis) è da preferirsi.

A scopo investigativo, utilizzando JSRP per l’esempio, la cartella base contenente i punteggi è

* `/content/usergenerated/asi/jcr/scoring`

Il nodo figlio di `scoring`è il nome della regola di punteggio. Di conseguenza, è consigliabile che i nomi delle regole di punteggio su un server siano univoci a livello globale.

Per il sito Geometrixx Engage, l&#39;utente e il relativo punteggio si trovano in un percorso conteggiato con il nome della regola di punteggio, l&#39;ID del sito della community ( `engage-ba81p`), un id univoco e l&#39;ID dell&#39;utente:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Per il sito della guida ai componenti della community, l’utente e il relativo punteggio si trovano in un percorso costruito con il nome della regola di punteggio, un id predefinito ( `default-site`), un id univoco e l&#39;ID dell&#39;utente:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Il punteggio viene memorizzato nella proprietà `scoreValue_tl` che può contenere solo un valore o fare riferimento indirettamente a un atomicCounter.

![chlimage_1-251](assets/chlimage_1-251.png)

### UGC di accesso {#access-badging-ugc}

Uso del [API](#scoring-and-badging-apis) è da preferirsi.

A scopo investigativo, utilizzando JSRP per esempio, la cartella base contenente informazioni sui badge assegnati o assegnati è

* /content/usergenerate/asi/jcr

Seguito dal percorso del profilo dell’utente, che termina in una cartella dei badge, ad esempio

* /home/users/community/w271Oup2Z4DjnOQrviv/profile/badges

#### Badge aggiudicato {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### badge assegnato {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Informazioni aggiuntive {#additional-information}

Per visualizzare un elenco ordinato di membri in base ai punti:

* [Funzione di classifica](functions.md#leaderboard-function) per l&#39;inclusione in un sito o modello di gruppo community.
* [Componente della classifica](enabling-leaderboard.md), il componente in primo piano della funzione Leaderboard per la creazione delle pagine.
