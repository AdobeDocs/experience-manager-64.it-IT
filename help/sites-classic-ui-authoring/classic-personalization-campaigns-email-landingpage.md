---
title: Creazione di una pagina di destinazione efficace per una newsletter
seo-title: Creating an Effective Newsletter Landing Page
description: Una pagina di destinazione efficace per una newsletter consente di ottenere il maggior numero possibile di persone che si iscrivono alla newsletter (o ad altre campagne di marketing e-mail). Per ottenere i lead, è possibile utilizzare le informazioni raccolte dalle registrazioni alla newsletter.
seo-description: An effective newsletter landing page helps you get as many people as possible to sign up for your newsletter (or other email marketing campaign). You can use the information you gather from your newsletter sign ups to get leads.
uuid: 810f3d1c-6648-4342-9fbc-0701765311a1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: dfe0ad66-9df5-4ea3-9e66-543b5ccd594a
exl-id: 1ab81235-2627-4304-bbf2-71598de948db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 1%

---

# Creazione di una pagina di destinazione efficace per una newsletter{#creating-an-effective-newsletter-landing-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Una pagina di destinazione efficace per una newsletter consente di ottenere il maggior numero possibile di persone che si iscrivono alla newsletter (o ad altre campagne di marketing e-mail). Per ottenere i lead, è possibile utilizzare le informazioni raccolte dalle registrazioni alla newsletter.

Per creare una pagina di destinazione efficace per una newsletter, è necessario effettuare le seguenti operazioni:

1. Crea un elenco per la newsletter in modo che gli utenti possano registrarsi.
1. Creare il modulo di registrazione. In questo modo, aggiungi un passaggio del flusso di lavoro che aggiunga automaticamente la persona che si iscrive alla newsletter all’elenco dei lead.
1. Crea una pagina di conferma per ringraziare gli utenti che si sono registrati ed eventualmente fornire loro una promozione.
1. Aggiungi dei teaser.

>[!NOTE]
>
>Adobe non prevede di migliorare ulteriormente questa funzionalità (Gestione di lead ed elenchi).\
>La raccomandazione è di sfruttare [Adobe Campaign e la sua integrazione AEM](/help/sites-administering/campaign.md).

## Creazione di un elenco per la newsletter {#creating-a-list-for-the-newsletter}

Crea un elenco, ad esempio: **Newsletter Geometrixx**, in MCM per la newsletter a cui gli utenti devono effettuare l’abbonamento. La creazione di elenchi è descritta in [Creazione di elenchi](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingnewlists).

Di seguito è riportato un esempio di elenco:

![mcm_listcreate](assets/mcm_listcreate.png)

## Creare un modulo di registrazione {#create-a-sign-up-form}

Crea un modulo di registrazione per la newsletter che consenta agli utenti di iscriversi ai tag. Il sito Web di Geometrixx di esempio fornisce una pagina newsletter nella barra degli strumenti di Geometrixx in cui è possibile creare il modulo.

Per creare un modulo per newsletter, consulta le informazioni sulla creazione di moduli nella sezione [Documentazione di Forms](/help/sites-authoring/default-components.md#form). La newsletter utilizza i tag della libreria Tag. Per aggiungere altri tag, consulta [Amministrazione dei tag](/help/sites-authoring/tags.md#tagadministration).

I campi nascosti nell’esempio seguente forniscono la quantità minima di informazioni (e-mail) scarse; inoltre, puoi aggiungere altri campi in un secondo momento, ma questo avrà un impatto sul tasso di conversione.

L’esempio seguente è un modulo creato all’indirizzo http://localhost:4502/cf#/content/geometrixx/en/toolbar/newsletter.html.

1. Creare il modulo.

   ![mcm_newsletterpage](assets/mcm_newsletterpage.png)

1. Fai clic su **Modifica** nel componente Modulo per configurare il modulo per passare a una pagina di ringraziamento (consulta [Creazione di pagine di ringraziamento](#creating-a-thank-you-page)).

   ![dc_formstart_thankyou](assets/dc_formstart_thankyou.png)

1. Imposta l’azione Modulo (ossia cosa deve accadere quando il modulo viene inviato) e configura il gruppo per assegnare gli utenti registrati all’elenco creato in precedenza (ad esempio, geometrixx-newsletter).

   ![dc_formstart_thankyouadvanced](assets/dc_formstart_thankyouadvanced.png)

## Creazione di una pagina di ringraziamento {#creating-a-thank-you-page}

Quando gli utenti fanno clic su **Iscriviti ora**, si desidera aprire automaticamente una pagina di ringraziamento . Crea la pagina di ringraziamento nella pagina Newsletter di Geometrixx. Dopo aver creato il modulo per la newsletter, modifica il componente Modulo e aggiungi il percorso alla pagina di ringraziamento.

L’invio della richiesta porta l’utente a un **Grazie** pagina dopo la quale riceveranno un’e-mail. Questa pagina di ringraziamento è stata creata in /content/geometrixx/en/toolbar/newsletter/thank_you.

![mcm_newsletter_thankyoupage](assets/mcm_newsletter_thankyoupage.png)

## Aggiunta di teaser {#adding-teasers}

Aggiungi [teaser](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) per eseguire il targeting di tipi di pubblico specifici. Ad esempio, puoi aggiungere dei teaser nella pagina di ringraziamento e di registrazione della newsletter.

Per aggiungere dei teaser per rendere efficace la pagina di destinazione della newsletter:

1. Crea un paragrafo teaser per un regalo di iscrizione. Seleziona **Primo** come strategia e includi testo che informi loro quale regalo riceveranno.

   ![dc_teaser_thankyou](assets/dc_teaser_thankyou.png)

1. Crea un paragrafo teaser per la pagina di ringraziamento. Seleziona **Primo** come strategia e includi il testo che indica che il regalo è in arrivo.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Crea una campagna con i due teaser: uno con tag business e uno senza tag.

## Invio di contenuti agli abbonati {#pushing-content-to-subscribers}

Invia eventuali modifiche alle pagine tramite la funzionalità Newsletter in MCM. Successivamente, invia i contenuti aggiornati agli abbonati.

Vedi [Invio di newsletter](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters).
