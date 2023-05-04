---
title: Contenuto della sandbox iniziale
seo-title: Initial Sandbox Content
description: Crea contenuto
seo-description: Create content
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
exl-id: 171fd95d-51f6-468b-84ed-4a757dba868e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 6%

---

# Contenuto della sandbox iniziale {#initial-sandbox-content}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In questa sezione vengono create le pagine seguenti che utilizzano tutte le [modello di pagina](initial-app.md#createthepagetemplate):

* Sito Sandbox SCF, che reindirizzerà alla versione inglese della pagina principale

   * SCF Sandbox - La pagina principale per la versione inglese del sito

      * SCF Play - Figlio della pagina principale su cui riprodurre

Questa esercitazione non contiene informazioni approfondite su [copie per lingua](../../help/sites-administering/tc-prep.md), è progettato in modo che la pagina principale possa implementare il rilevamento della lingua preferita dall’utente tramite l’intestazione di HTML e reindirizzare alla pagina principale appropriata per la lingua. La convenzione è di utilizzare il codice del paese a due lettere per il nome del nodo della pagina, ad esempio &quot;en&quot; per inglese, &quot;fr&quot; per francese e così via.

## Crea prime pagine {#create-first-pages}

Ora che c&#39;è un [modello di pagina](initial-app.md#createthepagetemplate), possiamo stabilire la pagina principale del sito web nella directory /content.

1. L’interfaccia utente standard fornisce attualmente le blueprint per la creazione di siti. Questa esercitazione sta creando un sito semplice, e l’interfaccia classica è utile.

   Per passare all’interfaccia classica, seleziona navigazione globale e passa il cursore del mouse sul lato destro dell’icona Progetti . Seleziona la *Passa all’interfaccia classica* icona visualizzata:

   ![chlimage_1-36](assets/chlimage_1-36.png)

   La possibilità di passare all’interfaccia classica deve essere [abilitato da un amministratore](../../help/sites-administering/enable-classic-ui.md).

1. Da [pagina di benvenuto dell’interfaccia classica](http://localhost:4502/welcome.html), seleziona **[!UICONTROL Siti Web]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   In alternativa, accedi direttamente all’interfaccia classica per i siti web sfogliando [/siteadmin.](http://localhost:4502/siteadmin)

1. Nel riquadro Esplora risorse, seleziona **[!UICONTROL Siti Web]** quindi nella barra degli strumenti seleziona **[!UICONTROL Nuovo > Nuova pagina]**.

   In **[!UICONTROL Crea pagina]** , immetti quanto segue:

   * Titolo: `SCF Sandbox Site`
   * Nome: `an-scf-sandbox`
   * Seleziona **[!UICONTROL Un modello di riproduzione sandbox SCF]**
   * Fai clic su **[!UICONTROL Crea]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Nel riquadro Esplora risorse, seleziona la pagina appena creata, `/Websites/SCF Sandbox Site`e fai clic su **[!UICONTROL Nuovo > Nuova pagina]**:

   * Titolo: `SCF Sandbox`
   * Nome: `en`
   * Seleziona **Un modello di riproduzione sandbox SCF**
   * Fai clic su **Crea**

1. Nel riquadro Esplora risorse, seleziona la pagina appena creata, `/Websites/SCF Sandbox Site/SCF Sandbox`e fai clic su **[!UICONTROL Nuovo > Nuova pagina]**

   * Titolo: `SCF Play`
   * Nome: `play`
   * Seleziona **[!UICONTROL Un modello di riproduzione sandbox SCF]**
   * Fai clic su **[!UICONTROL Crea]**

1. Il sito web viene ora visualizzato nella console Siti web. Le pagine figlie dell&#39;elemento selezionato nel riquadro Esplora risorse vengono visualizzate nel riquadro di destra in cui possono essere gestite.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Questa è la vista archivio di ciò che è stato creato utilizzando lo strumento Sito web e il modello:

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Aggiungere il percorso di progettazione {#add-the-design-path}

Quando ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` è stato creato utilizzando la sezione delle progettazioni della console Strumenti, la proprietà &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

è stato definito, che offre la possibilità opzionale di fare riferimento a risorse di progettazione in uno script utilizzando `currentDesign.getPath()`. Per esempio

* &lt;% String preferitaIcon = currentDesign.getPath() + &quot;/favicon.ico&quot;; %>


   * Nome: `cq:designPath`
   * Tipo: `String`
   * Valore: `/etc/designs/an-scf-sandbox`

* Fai clic sul verde `[+] Add`

Il repository dovrebbe essere visualizzato come segue:

![chlimage_1-41](assets/chlimage_1-41.png)

* Fai clic su **[!UICONTROL Salva tutto]**

[ Problemi di salvataggio? Effettua nuovamente l&#39;accesso! ]

>[!NOTE]
>
>L&#39;utilizzo di cq:designPath è facoltativo e non è correlato al [uso di clientlibs](develop-app.md#includeclientlibsintemplate), che sono essenzialmente necessari in quanto i componenti SCF utilizzano [clientlibs](client-customize.md#clientlibs-for-scf) per gestire i rispettivi JS e CSS.
