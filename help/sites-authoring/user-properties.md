---
title: Configurazione dell’ambiente dell’account
seo-title: Configuring your account environment
description: Con AEM è possibile configurare il proprio account e alcuni aspetti dell’ambiente di authoring
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 53%

---

# Configurazione dell’ambiente dell’account{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Con AEM è possibile configurare il proprio account e alcuni aspetti dell’ambiente di authoring.

Utilizzo della [Utente](/help/sites-authoring/user-properties.md#user-settings) in [header](/help/sites-authoring/basic-handling.md#the-header) e i [Preferenze](#my-preferences) è possibile modificare le opzioni utente.

## Impostazioni utente {#user-settings}

La **Utente** la finestra di dialogo delle impostazioni consente di accedere a:

* Impersona

   * Con la [Impersona come](/help/sites-administering/security.md#impersonating-another-user) un utente può lavorare a nome di un altro utente.

* Profilo

   * Offre un collegamento semplice [impostazioni utente](/help/sites-administering/security.md))

* [Preferenze](/help/sites-authoring/user-properties.md#my-preferences)

   * Consente di specificare varie preferenze di impostazione specifiche dell’utente.

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## Preferenze {#my-preferences}

Puoi accedere alla finestra di dialogo **Preferenze** tramite l’opzione [Utente](/help/sites-authoring/user-properties.md#user-settings) nell’intestazione.

Ogni utente può impostare autonomamente determinate proprietà.

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **Lingua**

   Consente di definire la lingua da usare nell’interfaccia dell’ambiente di authoring. Seleziona la lingua desiderata dall’elenco delle opzioni disponibili.

   Questa configurazione viene utilizzata anche per l’interfaccia classica.

* **Gestione finestre**

   Definisce il comportamento o l&#39;apertura delle finestre. Puoi selezionare:

   * **Finestre multiple** (Predefinito)

      * Le pagine verranno aperte in una nuova finestra.
   * **Finestra singola**

      * Le pagine verranno aperte nella finestra corrente.


* **Mostra azioni desktop per Assets**

   Questa opzione richiede AEM’app desktop da utilizzare.

* **Colore annotazione**

   Definisce il colore predefinito utilizzato per le annotazioni.

   * Fai clic sul blocco dei colori per aprire il selettore dei campioni e selezionare un colore.
   * In alternativa, immetti nel campo il codice esadecimale del colore desiderato.

* **Presentazione data relativa**

   Per migliorare la leggibilità, AEM le date degli ultimi sette giorni come date relative (ad esempio, tre giorni fa) e date più vecchie come date esatte (ad esempio, il 20 marzo 2017).

   Questa opzione definisce il modo in cui il sistema visualizza le date. Sono disponibili le seguenti opzioni:

   * **Mostra sempre data esatta**: viene sempre visualizzata la data esatta e non una data relativa.
   * **1 giorno**: viene visualizzata la data relativa per le date entro un giorno; in caso contrario viene visualizzata una data esatta.
   * **7 giorni (impostazione predefinita)**: viene visualizzata la data relativa per date entro sette giorni; in caso contrario viene visualizzata una data esatta.
   * **1 mese**: viene visualizzata la data relativa per le date entro un mese; in caso contrario viene visualizzata una data esatta.
   * **1 anno**: viene visualizzata la data relativa per le date entro un anno; in caso contrario viene visualizzata una data esatta.
   * **Mostra sempre data relativa**: non vengono mai visualizzate date esatte, ma solo date relative.

* **Abilita scelte rapide**

   AEM supporta una serie di scelte rapide da tastiera per ottimizzare l’authoring.

   * [Scelte rapide da tastiera per la modifica delle pagine](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Scelte rapide da tastiera per le console](/help/sites-authoring/keyboard-shortcuts.md)

   Questa opzione abilita le scelte rapide da tastiera. Per impostazione predefinita sono abilitate, ma possono essere disabilitate, ad esempio se un utente ha determinati requisiti di accessibilità.

* **Usa esperienza di authoring classica**

   Questa opzione abilita [interfaccia classica](/help/sites-classic-ui-authoring/home.md)Authoring basato su pagine. Per impostazione predefinita viene utilizzata l’interfaccia utente standard.

* **Abilita pagina iniziale di Assets**

   Questa opzione è disponibile solo se l’amministratore di sistema ha abilitato l’esperienza Home page di Assets per l’intera organizzazione.
