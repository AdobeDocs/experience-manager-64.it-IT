---
title: Creare una sandbox SCF
seo-title: Create An SCF Sandbox
description: Questa esercitazione è rivolta principalmente agli sviluppatori, non esperti di AEM, interessati all’utilizzo dei componenti SCF.  Viene descritto come creare un sito Sandbox SCF
seo-description: This tutorial is primarily for developers, new to AEM, who are interested in using SCF components.  It walks through the creation of An SCF Sandbox site
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
exl-id: f8cd2866-6e4d-47e6-b9aa-c2190b0b1b7b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 2%

---

# Creare una sandbox SCF {#create-an-scf-sandbox}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).


A partire da AEM 6.1 Communities, il modo più semplice per creare rapidamente una sandbox è quello di creare un sito community. Vedi [Guida introduttiva ad AEM Communities](getting-started.md).

Un altro strumento utile per gli sviluppatori è la [Guida ai componenti della community](components-guide.md), che consente l’esplorazione e la rapida prototipazione dei componenti e delle caratteristiche di Communities.

L’esercizio di creazione di un sito web può essere utile per comprendere la struttura di un sito web AEM che può includere funzionalità di Communities, fornendo al contempo pagine semplici su cui esplorare la possibilità di lavorare con [quadro della componente sociale (SCF)](scf.md).

Questa esercitazione è rivolta principalmente agli sviluppatori, non esperti di AEM, interessati all’utilizzo dei componenti SCF. Viene descritto come creare un sito Sandbox SCF, simile all’esercitazione per [Come creare un sito web Internet completo](../../help/sites-developing/website.md) che si concentra sulle strutture del sito, ad esempio la navigazione, il logo, la ricerca, la barra degli strumenti e l’elenco delle pagine figlie.

Lo sviluppo avviene su un’istanza di authoring, mentre la sperimentazione con il sito è ottimale su un’istanza di pubblicazione.

I passaggi di questa esercitazione sono i seguenti:

* [Imposta struttura sito Web](setup-website.md)
* [Applicazione Sandbox iniziale](initial-app.md)
* [Contenuto della sandbox iniziale](initial-content.md)
* [Sviluppa applicazione sandbox](develop-app.md)
* [Aggiungi clientlibs](add-clientlibs.md)
* [Sviluppa contenuto sandbox](develop-content.md)

>[!CAUTION]
>
>Questa esercitazione non crea un sito community con le funzionalità create utilizzando [Console Sites di Communities](sites-console.md). Ad esempio, questa esercitazione non descrive come impostare accesso, registrazione automatica, [accesso social](social-login.md), messaggi, profili e così via.
>
>Se si preferisce un semplice sito di community, segui la [Creare una pagina di esempio](create-sample-page.md) esercitazione.

## Prerequisiti {#prerequisites}

Questa esercitazione presuppone che sia installato un autore AEM e un&#39;istanza di pubblicazione AEM che ha [ultima versione](deploy-communities.md#latest-releases) delle Comunità.

Di seguito sono riportati alcuni collegamenti utili per gli sviluppatori che non hanno mai utilizzato la piattaforma AEM:

* [Introduzione](../../help/sites-deploying/deploy.md#getting-started) - Per la distribuzione di istanze AEM

   * [Nozioni di base](../../help/sites-developing/the-basics.md) - Per gli sviluppatori di siti web e funzionalità
   * [Primi passi per gli autori](../../help/sites-authoring/first-steps.md) - Per la creazione di contenuti di pagina

## Utilizzo dell’ambiente di sviluppo di CRXDE Lite {#using-crxde-lite-development-environment}

AEM gli sviluppatori trascorrono gran parte del loro tempo nel [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) ambiente di sviluppo in un’istanza di authoring. CRXDE Lite fornisce un accesso meno limitato all’archivio CRX. Gli strumenti dell’interfaccia classica e le console di interfaccia touch consentono un accesso più strutturato a porzioni specifiche dell’archivio CRX.

Dopo aver effettuato l’accesso con privilegi amministrativi, sono disponibili diversi modi per accedere a CRXDE Lite:

1. Dalla navigazione globale, seleziona navigazione **[!UICONTROL Strumenti > CRXDE Lite]**.

   ![chlimage_1-350](assets/chlimage_1-350.png)

2. Da [pagina di benvenuto dell’interfaccia classica](http://localhost:4502/welcome.html), scorri verso il basso e fai clic su **[!UICONTROL CRXDE Lite]** nel pannello di destra.

   ![chlimage_1-351](assets/chlimage_1-351.png)

3. Sfoglia direttamente in `CRXDE Lite`: `<server>:<port>/crx/de`

   Ad esempio, in un’istanza di authoring locale: ` [http://localhost:4502/crx/de](http://localhost:4502/crx/de)`

Per utilizzare CRXDE Lite, è necessario accedere con i privilegi di sviluppatore o amministratore. Per l&#39;istanza localhost predefinita, puoi accedere con

* `username: admin`
* `password: admin`


**Attenzione** che questo accesso si interrompa e dovrai effettuare di nuovo l’accesso periodicamente utilizzando il pull down all’estremità destra della barra degli strumenti CRXDe Lite.

Se non hai effettuato l’accesso, non potrai navigare nell’archivio JCR o eseguire operazioni di modifica/salvataggio.

***In caso di dubbio, riaccedi!***

![chlimage_1-352](assets/chlimage_1-352.png)
