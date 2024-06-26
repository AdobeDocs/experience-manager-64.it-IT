---
title: Sincronizzazione utente
seo-title: User Synchronization
description: Scopri la sincronizzazione utente in AEM.
seo-description: Learn about user synchronization in AEM.
uuid: 0c7c35a3-9fed-4d48-8bd5-7f4382bf5fa3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 707b150b-7759-437f-9150-9f4784856754
exl-id: 537b86f5-ad38-4419-8dde-40ec08091b7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2529'
ht-degree: 4%

---

# Sincronizzazione utente{#user-synchronization}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

Quando la distribuzione è [pubblica azienda](/help/sites-deploying/recommended-deploys.md#tarmk-farm), i membri devono essere in grado di accedere e visualizzare i propri dati su qualsiasi nodo di pubblicazione.

Gli utenti e i gruppi di utenti (dati utente) creati nell’ambiente di pubblicazione non sono necessari nell’ambiente di authoring.

La maggior parte dei dati utente creati nell’ambiente di authoring ha lo scopo di rimanere nell’ambiente di authoring e non essere copiati nelle istanze di pubblicazione.

La registrazione e le modifiche apportate a un’istanza di pubblicazione devono essere sincronizzate con altre istanze di pubblicazione per consentire loro di accedere agli stessi dati utente.

A partire da AEM 6.1, quando la sincronizzazione utente è abilitata, i dati utente vengono sincronizzati automaticamente tra le istanze di pubblicazione nella farm e non vengono creati sull’autore.

## Distribuzione Sling {#sling-distribution}

I dati utente, insieme ai [ACL](/help/sites-administering/security.md), sono memorizzati nel [Oak Core](/help/sites-deploying/platform.md), il livello sotto Oak JCR e sono accessibili utilizzando [API Oak](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). Con aggiornamenti non frequenti, è ragionevole che i dati utente siano sincronizzati con altre istanze di pubblicazione utilizzando [Distribuzione dei contenuti Sling](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md) (distribuzione Sling).

Rispetto alla replica tradizionale, i vantaggi della sincronizzazione utente tramite la distribuzione Sling sono i seguenti:

* *utenti*, *profili utente* e *gruppi di utenti* creati al momento della pubblicazione non vengono creati sull&#39;autore

* La distribuzione Sling imposta le proprietà negli eventi jcr, consentendo di agire all&#39;interno dei listener di eventi lato pubblicazione senza preoccuparsi di cicli di replica infiniti
* La distribuzione Sling invia solo i dati utente alle istanze di pubblicazione non originarie, eliminando il traffico non necessario
* [ACL](/help/sites-administering/security.md) impostati nel nodo utente sono inclusi nella sincronizzazione

>[!NOTE]
>
>Se sono necessarie sessioni, si consiglia di utilizzare una soluzione SSO o una sessione appiccicosa e di chiedere ai clienti di effettuare l&#39;accesso se passano a un altro editore.

>[!CAUTION]
>
>Sincronizzazione del ***amministratori** *gruppo non supportato, anche quando la sincronizzazione utente è abilitata. Al contrario, un errore di &quot;importazione del diff&quot; verrà registrato nel registro degli errori.
>
>Pertanto, quando la distribuzione è una farm di pubblicazione, se un utente viene aggiunto o rimosso dal ***amministratori** *gruppo, la modifica deve essere eseguita manualmente su ogni istanza di pubblicazione.

## Abilita sincronizzazione utente {#enable-user-sync}

>[!NOTE]
>
>Per impostazione predefinita, la sincronizzazione utente è `disabled`.
>
>L&#39;abilitazione della sincronizzazione utente comporta la modifica *esistente* Configurazioni OSGi.
>
>Non è necessario aggiungere nuove configurazioni per abilitare la sincronizzazione utente.

La sincronizzazione utente si basa sull’ambiente di authoring per gestire le distribuzioni dei dati utente, anche se i dati utente non vengono creati sull’autore. Molte, ma non tutte, della configurazione avviene nell’ambiente di authoring e ogni passaggio indica chiaramente se deve essere eseguito sull’autore o sulla pubblicazione.

Di seguito sono riportati i passaggi necessari per abilitare la sincronizzazione utente, seguiti da un [Risoluzione dei problemi](#troubleshooting) sezione:

### Prerequisiti {#prerequisites}

1. Se utenti e gruppi di utenti sono già stati creati su un solo editore, si consiglia di [sincronizzazione manuale](#manually-syncing-users-and-user-groups) i dati utente a tutti gli editori prima di configurare e abilitare la sincronizzazione utente.

   Una volta abilitata la sincronizzazione utente, vengono sincronizzati solo gli utenti e i gruppi appena creati.

1. Verifica che sia stato installato il codice più recente:

* [Aggiornamenti AEM piattaforma](https://helpx.adobe.com/it/experience-manager/kb/aem62-available-hotfixes.html)
* [Aggiornamenti AEM Communities](/help/communities/deploy-communities.md#latest-releases)

### 1. Agente di distribuzione Apache Sling - Agente di sincronizzazione Factory {#apache-sling-distribution-agent-sync-agents-factory}

**Abilita sincronizzazione utente**

* **sull&#39;autore**

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizzare `Apache Sling Distribution Agent - Sync Agents Factory`

      * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

         Verifica `name`: **`socialpubsync`**

      * seleziona la `Enabled` spunta
      * select `Save`



![chlimage_1-387](assets/chlimage_1-387.png)

### 2. Creare un utente autorizzato {#createauthuser}

**Configurare le autorizzazioni**
Questo utente autorizzato verrà utilizzato nel passaggio 3 per configurare la distribuzione Sling sull&#39;autore.

* **su ogni istanza di pubblicazione**

   * accesso con privilegi di amministratore
   * accedere al [Console di sicurezza](/help/sites-administering/security.md)

      * ad esempio, [http://localhost:4503/useradmin](http://localhost:4503/useradmin)
   * creare un nuovo utente

      * ad esempio, `usersync-admin`
   * aggiungi questo utente al **`administrators`** gruppo utenti
   * [aggiungi ACL per questo utente a /home](#addacls)

      * `Allow jcr:all` con restrizione `rep:glob=*/activities/*`



>[!CAUTION]
>
>È necessario creare un nuovo utente.
>
>* L&#39;utente predefinito assegnato è **`admin`**.
>* Non utilizzare `*communities-user-admin *user*.*`
>


#### Come aggiungere ACL {#addacls}

* CRXDE Lite di accesso

   * ad esempio, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* select `/home` nodo
* nel riquadro a destra, seleziona la `Access Control` scheda
* seleziona la `+` pulsante per aggiungere una voce ACL

   * **Principale**: *cerca utente creato per la sincronizzazione utente*
   * **Tipo**: `Allow`
   * **Privilegi**: `jcr:all`
   * **Restrizioni** rep:glob: `*/activities/*`
   * select **OK**

* select **Salva tutto**

![chlimage_1-388](assets/chlimage_1-388.png)

Consulta anche

* [Accesso alla gestione dei diritti](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Sezione Risoluzione dei problemi [Modifica eccezione di operazione durante l&#39;elaborazione della risposta](#modify-operation-exception-during-response-processing).

### 3. Distribuzione Granite Adobe - Provider Segreto Di Trasporto Password Crittografata {#adobegraniteencpasswrd}

**Configurare le autorizzazioni**

Una volta autorizzato l&#39;utente, un membro del **`administrators`**gruppo di utenti, creato su tutte le istanze di pubblicazione, l&#39;utente autorizzato deve essere identificato nell&#39;autore come avente l&#39;autorizzazione per sincronizzare i dati utente dall&#39;autore alla pubblicazione.

* **sull&#39;autore**

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizzare `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`
   * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

      Verifica `property name` : **`socialpubsync-publishUser`**

   * imposta il nome utente e la password del [utente autorizzato](#createauthuser) creato al momento della pubblicazione nel passaggio 2

      * ad esempio, `usersync-admin`


![chlimage_1-389](assets/chlimage_1-389.png)

### 4. Agente di distribuzione Apache Sling - Coda Agenti Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Abilita sincronizzazione utente**

* **al momento della pubblicazione** :

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizzare `Apache Sling Distribution Agent - Queue Agents Factory`

      * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

         Verifica `Name` : `socialpubsync-reverse`

      * seleziona la `Enabled` spunta
      * select `Save`
   * **repeat** per ogni istanza di pubblicazione



![chlimage_1-390](assets/chlimage_1-390.png)

### 5. Distribuzione granite Adobe - Diff Observer Factory {#diffobserver}

**Abilita sincronizzazione gruppo**

* **su ogni istanza di pubblicazione** :

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizzare `Adobe Granite Distribution - Diff Observer Factory`

      * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

         Verifica `agent name` : `socialpubsync-reverse`

      * seleziona la `Enabled` spunta
      * select `Save`


![chlimage_1-391](assets/chlimage_1-391.png)

### 6. Trigger di distribuzione Apache Sling - Trigger di fabbrica programmati {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Facoltativo) modificare l&#39;intervallo di polling**

Per impostazione predefinita, l’autore esegue il polling delle modifiche ogni 30 secondi. Per modificare questo intervallo:

* **sull&#39;autore**

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizzare `Apache Sling Distribution Trigger - Scheduled Triggers Factory`

      * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

         * Verifica `Name` : `socialpubsync-scheduled-trigger`
      * imposta `Interval in Seconds` all&#39;intervallo desiderato
      * select `Save`



![chlimage_1-392](assets/chlimage_1-392.png)

## Configurazione per più istanze di pubblicazione {#configure-for-multiple-publish-instances}

La configurazione predefinita è per una singola istanza di pubblicazione. Poiché l’abilitazione della sincronizzazione utente è dovuta alla sincronizzazione di più istanze di pubblicazione, ad esempio per una farm di pubblicazione, le istanze di pubblicazione aggiuntive dovranno essere aggiunte a Sync Agent Factory .

### 7. Agente di distribuzione Apache Sling - Agente di sincronizzazione Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Aggiungi istanze di pubblicazione :**

* **sull&#39;autore**

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizzare `Apache Sling Distribution Agent - Sync Agents Factory`

      * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

         Verifica `Name` : `socialpubsync`


![chlimage_1-393](assets/chlimage_1-393.png)

* **Endpoint per l’esportazione**
Deve essere presente un endpoint di esportazione per ogni editore. Ad esempio, se ci sono 2 editori, localhost:4503 e 4504, ci dovrebbero essere 2 voci:

   * http://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse
   * http://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse

* **Endpoint importazione**
Per ogni editore deve essere presente un endpoint di importazione. Ad esempio, se ci sono 2 editori, localhost:4503 e 4504, ci dovrebbero essere 2 voci:

   * http://localhost:4503/libs/sling/distribution/services/importers/socialpubsync
   * http://localhost:4504/libs/sling/distribution/services/importers/socialpubsync

* select `Save`

### 8. Listener di sincronizzazione degli utenti di AEM Communities {#aem-communities-user-sync-listener}

**(Facoltativo) Sincronizza nodi JCR aggiuntivi**

Se desideri sincronizzare dati personalizzati tra più istanze di pubblicazione, effettua le seguenti operazioni:

* **su ogni istanza di pubblicazione**:

   * accesso con privilegi di amministratore
   * accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

      * ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizzare `AEM Communities User Sync Listener`
   * seleziona la configurazione esistente da aprire per la modifica (icona a forma di matita)

      Verifica `Name`: `socialpubsync-scheduled-trigger`


![chlimage_1-394](assets/chlimage_1-394.png)

* **Tipi di nodo**

   Elenco dei tipi di nodo che verranno sincronizzati. È necessario elencare qui qualsiasi tipo di nodo diverso da sling:Folder (sling:folder viene gestito separatamente).

   Elenco predefinito dei tipi di nodo da sincronizzare:

   * rep:User
   * nt:unstructured
   * nt:resource

* **Proprietà ignorabili**

   Elenco delle proprietà che verranno ignorate in caso di rilevamento di modifiche. Le modifiche a queste proprietà potrebbero essere sincronizzate come effetto collaterale di altre modifiche (poiché la sincronizzazione è sempre a livello di nodo), ma le modifiche a queste proprietà non attiveranno di per sé la sincronizzazione.

   Proprietà predefinita da ignorare:

   * cq:lastModified

* **Nodi ignorabili**

   Percorsi secondari che verranno completamente ignorati durante la sincronizzazione. Niente sotto questi percorsi secondari verrà sincronizzato in qualsiasi momento.

   Nodi predefiniti da ignorare:

   * .token
   * system

* **Cartelle distribuite**

   La maggior parte delle cartelle sling:Folders vengono ignorate perché la sincronizzazione non è necessaria. Le poche eccezioni sono elencate qui.

   Cartelle predefinite da sincronizzare

   * segmenti/punteggio
   * social/relazioni
   * attività

### 9. ID Sling univoco {#unique-sling-id}

>[!CAUTION]
>
>Se l’ID Sling corrisponde tra due o più istanze di pubblicazione, la sincronizzazione dei gruppi di utenti non riuscirà.

Se l’ID Sling è lo stesso per più istanze di pubblicazione in una farm di pubblicazione, i gruppi di utenti non verranno sincronizzati.

Per verificare che tutti i valori Sling ID siano diversi, per ogni istanza di pubblicazione :

1. naviga a `http://<host>:<port>/system/console/status-slingsettings`
1. controlla il valore di **Sling ID**

![chlimage_1-395](assets/chlimage_1-395.png)

Se l’ID Sling di un’istanza di pubblicazione corrisponde all’ID Sling di qualsiasi altra istanza di pubblicazione, allora:

1. interrompi una delle istanze di pubblicazione con un ID Sling corrispondente
1. nella directory crx-quickstart/launchpad/felix

   * cercare ed eliminare il file denominato *sling.id.file*

      * per esempio, su un sistema Linux:

         `rm -i $(find . -type f -name sling.id.file)`

      * ad esempio, in un sistema Windows:

         `use windows explorer and search for *sling.id.file*`

1. avvia l&#39;istanza di pubblicazione

   * all&#39;avvio gli verrà assegnato un nuovo Sling ID

1. convalida che **Sling ID** è ora univoco

Ripeti questi passaggi fino a quando tutte le istanze di pubblicazione hanno un ID Sling univoco.

## Vault Package Builder Factory {#vault-package-builder-factory}

Per garantire la corretta sincronizzazione degli aggiornamenti, è necessario modificare il generatore di pacchetti vault per la sincronizzazione utente :

* su ogni istanza di pubblicazione AEM
* accedere al [Console web](/help/sites-deploying/configuring-osgi.md)

   * ad esempio, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* individua `Apache Sling Distribution Packaging - Vault Package Builder Factor`

   * `Builder name: socialpubsync-vlt`

* seleziona l’icona modifica
* aggiungi due `Package Filters` :

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* gestione dei criteri :

   * per sovrascrivere i nodi rep:policy esistenti con quelli nuovi, aggiungi un terzo filtro pacchetto :

      * `/home/users|+.*/rep:policy`
   * per evitare la distribuzione dei criteri, impostare

      * `Acl Handling :` `IGNORE`


![chlimage_1-396](assets/chlimage_1-396.png)

## Cosa Succede Quando ... {#what-happens-when}

### Registri o modifica del profilo utente in Pubblica {#user-self-registers-or-edits-profile-on-publish}

Per progettazione, gli utenti e i profili creati nell’ambiente di pubblicazione (registrazione automatica) non vengono visualizzati nell’ambiente di authoring.

Quando la topologia è un [pubblica azienda](/help/sites-deploying/recommended-deploys.md#tarmk-farm) e la sincronizzazione utente è stata configurata correttamente, il *user *e *profilo utente* viene sincronizzato nella farm di pubblicazione utilizzando la distribuzione Sling.

### Utenti o gruppi di utenti creati tramite la console di sicurezza {#users-or-user-groups-are-created-using-security-console}

Per progettazione, i dati utente creati nell’ambiente di pubblicazione non vengono visualizzati nell’ambiente di authoring e viceversa.

Quando il [Amministrazione degli utenti e sicurezza](/help/sites-administering/security.md) viene utilizzata per aggiungere nuovi utenti nell’ambiente di pubblicazione, la sincronizzazione utente sincronizza i nuovi utenti e la loro appartenenza al gruppo con altre istanze di pubblicazione, se necessario. La sincronizzazione utente sincronizza anche i gruppi di utenti creati tramite la console di sicurezza.

## Risoluzione dei problemi {#troubleshooting}

### Come attivare la sincronizzazione utente offline {#how-to-take-user-sync-offline}

Per impostare la sincronizzazione utente su fine, al fine di [rimuovere un editore](#how-to-remove-a-publisher) o [sincronizzazione manuale dei dati](#manually-syncing-users-and-user-groups), la coda di distribuzione deve essere vuota e silenziosa.

Per controllare lo stato della coda di distribuzione:

* autore:

   * utilizzo [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * cerca le voci in `/var/sling/distribution/packages`

         * nodi di cartella denominati con il pattern `distrpackage_*`
   * utilizzo [Gestione pacchetti](/help/sites-administering/package-manager.md)

      * cerca pacchetti in sospeso (non ancora installati)

         * denominato con il pattern `socialpubsync-vlt*`
         * creato da `communities-user-admin`


Quando la coda di distribuzione è vuota, disattiva la sincronizzazione utente :

* sull&#39;autore

   * *deselezionare *il `Enabled` casella di controllo [Agente di distribuzione Apache Sling - Sync Agent Factory](#apache-sling-distribution-agent-sync-agents-factory)

Una volta completate le attività, per riabilitare la sincronizzazione utente :

* sull&#39;autore

   * controlla `Enabled` casella di controllo [Agente di distribuzione Apache Sling - Sync Agent Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnostica sincronizzazione utenti {#user-sync-diagnostics}

Diagnostica sincronizzazione utenti è uno strumento che controlla la configurazione e tenta di identificare eventuali problemi.

Sull’autore, è sufficiente navigare dalla console principale attraverso **Strumenti, Operazioni, Diagnosi, Diagnostica sincronizzazione utente.**

È sufficiente accedere alla console Diagnostica sincronizzazione utente per visualizzare i risultati.

Questo è ciò che viene visualizzato quando la sincronizzazione utente non è stata abilitata :

![chlimage_1-397](assets/chlimage_1-397.png)

#### Come eseguire la diagnostica per gli editori {#how-to-run-diagnostics-for-publishers}

Quando la diagnosi viene eseguita dall’ambiente di authoring, i risultati di pass/fail includono un [INFORMAZIONI] visualizzazione dell’elenco delle istanze di pubblicazione configurate per la conferma.

Nell’elenco è incluso un URL per ogni istanza di pubblicazione che eseguirà la diagnostica per quell’istanza. Il parametro url `syncUser` viene aggiunto all’URL di diagnostica con il relativo valore impostato su *utente di sincronizzazione autorizzato* creato in [Passaggio 2](/help/sites-administering/sync.md#createauthuser).

**Nota** : prima di avviare l’URL, la *utente di sincronizzazione autorizzato* deve essere già firmato in quell&#39;istanza di pubblicazione.

![chlimage_1-398](assets/chlimage_1-398.png)

### Configurazione aggiunta errata {#improperconfig}

Quando la sincronizzazione utente non funziona, il problema più comune è che le configurazioni aggiuntive erano *aggiunto*. Invece, la *configurazione predefinita esistente dovrebbe essere stata *modificato*.

Di seguito sono riportate le visualizzazioni di visualizzazione delle configurazioni predefinite modificate nella console Web. Se vengono visualizzate più istanze, la configurazione aggiunta deve essere rimossa.

#### (autore) Un agente di distribuzione Sling Apache - Agente di sincronizzazione Factory {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![chlimage_1-399](assets/chlimage_1-399.png)

#### (autore) Un Adobe Distribuzione Granite - Provider segreto di trasporto password crittografata {#author-one-adobe-granite-distribution-encrypted-password-transport-secret-provider}

![chlimage_1-400](assets/chlimage_1-400.png)

#### (pubblicare) Un agente di distribuzione Apache Sling - Coda Agenti Factory {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![chlimage_1-401](assets/chlimage_1-401.png)

#### (pubblicare) Un Adobe Distribuzione Granite - Diff Observer Factory {#publish-one-adobe-granite-distribution-diff-observer-factory}

![chlimage_1-402](assets/chlimage_1-402.png)

#### (autore) Un trigger di distribuzione Apache Sling - Scheduled Triggers Factory {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![chlimage_1-403](assets/chlimage_1-403.png)

### Modifica eccezione di operazione durante l&#39;elaborazione della risposta {#modify-operation-exception-during-response-processing}

Se nel registro è visibile quanto segue:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

Quindi verifica che la sezione [2. Crea utente autorizzato](#createauthuser) è stato seguito correttamente.

Questa sezione descrive la creazione di un utente autorizzato, che esiste su tutte le istanze di pubblicazione, e l&#39;identificazione di tali istanze nella configurazione OSGi &#39;Provider segreto&#39; dell&#39;autore. Per impostazione predefinita, l’utente è `admin`.

L&#39;utente autorizzato deve essere membro del **`administrators`** il gruppo di utenti e le autorizzazioni per quel gruppo non devono essere modificate.

L’utente autorizzato deve avere esplicitamente i seguenti privilegi e restrizioni su tutte le istanze di pubblicazione :

| **percorso** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | &amp;ast;/activities/&amp;ast; |
| /home/users | X | &amp;ast;/activities/&amp;ast; |
| /home/groups | X | &amp;ast;/activities/&amp;ast; |

Come membro del `administrators` gruppo , l&#39;utente autorizzato deve avere i seguenti privilegi su tutte le istanze di pubblicazione :

| **percorso** | **jcr:all** | **jcr:read** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Sincronizzazione gruppo utenti non riuscita {#user-group-sync-failed}

Se l’ID Sling corrisponde tra due o più istanze di pubblicazione, la sincronizzazione dei gruppi di utenti non riuscirà.

Vedere la sezione [9. ID Sling univoco](#unique-sling-id)

### Sincronizzazione manuale di utenti e gruppi di utenti {#manually-syncing-users-and-user-groups}

* sull’editore in cui esistono utenti e gruppi di utenti :

   * [se attivato, disattiva la sincronizzazione utente](#how-to-take-user-sync-offline)
   * [creare un pacchetto](/help/sites-administering/package-manager.md#creating-a-new-package) di `/home`

      * durante la modifica del pacchetto

         * Scheda Filtri : Aggiungi filtro : Percorso principale: `/home`
         * Scheda Avanzate : Gestione AC : `Overwrite`
   * [esporta il pacchetto](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* su altre istanze di pubblicazione :

   * [importare il pacchetto](/help/sites-administering/package-manager.md#installing-packages)

Per configurare o abilitare la sincronizzazione utente, passa al passaggio 1: [Agente di distribuzione Apache Sling - Sync Agent Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Quando un editore diventa non disponibile {#when-a-publisher-becomes-unavailable}

Quando un’istanza di pubblicazione diventa non disponibile, non deve essere rimossa se torna online in futuro. Le modifiche verranno messe in coda per l&#39;editore e, una volta tornate online, le modifiche saranno elaborate.

Se l’istanza di pubblicazione non torna mai online, se è offline in modo permanente, deve essere rimossa perché la compilazione della coda comporterà un notevole utilizzo dello spazio su disco nell’ambiente di authoring.

Quando un editore non è attivo, il registro dell&#39;autore avrà eccezioni simili a :

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Come rimuovere un editore {#how-to-remove-a-publisher}

Per rimuovere un editore dal [Agente di distribuzione Apache Sling - Sync Agent Factory](#apache-sling-distribution-agent-sync-agents-factory), la coda di distribuzione deve essere vuota e silenziosa.

* sull’autore :

   * [Disconnetti utente offline](#how-to-take-user-sync-offline)
   * seguire [passaggio 7](#apache-sling-distribution-agent-sync-agents-factory) per rimuovere l’editore da entrambi gli elenchi server :

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * riattiva sincronizzazione utente

      * controlla `Enabled` casella di controllo [Agente di distribuzione Apache Sling - Sync Agent Factory](#apache-sling-distribution-agent-sync-agents-factory)
