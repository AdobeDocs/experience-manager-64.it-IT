---
title: Procedura dettagliata sul sito di riferimento per il rinnovo dell'assicurazione automatica We.Finance
seo-title: We.Finance Auto Insurance Renewal reference site walkthrough
description: Leggi la descrizione dettagliata del sito di riferimento del caso d’uso della funzione Assicurazione automatica We.Finance che illustra come AEM moduli e la sua integrazione con Microsoft Dynamics contribuiscano a personalizzare l’esperienza del cliente in una società di servizi finanziari.
seo-description: Read on detailed reference site walkthrough of We.Finance Auto Insurance use case which showcases how AEM forms and its integration with Microsoft Dynamics helps personalize customer experience in a financial service company.
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
exl-id: db416cbc-27a7-4a2c-b4b3-43e8963faf22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 1%

---

# Procedura dettagliata sul sito di riferimento per il rinnovo dell&#39;assicurazione automatica We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Prerequisiti {#pre-requisites}

Imposta il sito di riferimento come descritto in [Configurazione e configurazione del sito di riferimento Forms 6.4 AEM](/help/forms/using/setup-reference-sites.md).

## Scenario del sito di riferimento We.Finance  {#we-finance-reference-site-scenario}

Il sito We.Finance è un sito di servizi finanziari progettato per aiutarti a imparare le funzionalità di comunicazione interattiva di AEM Forms.

Leggi la descrizione dettagliata del caso d’uso della funzione Assicurazione automatica We.Finance che illustra come AEM moduli e la sua integrazione con Microsoft Dynamics contribuiscano a personalizzare l’esperienza del cliente in una società di servizi finanziari. La procedura dettagliata interattiva è progettata per facilitare l&#39;implementazione di transazioni digitali complesse e la comunicazione con i clienti in una società finanziaria.

**Il percorso inizia con il caso d’uso:**

Sarah Rose è un cliente esistente di We.Finance e ha acquistato una polizza di assicurazione auto. Ora è il momento dell’anno in cui rinnova la sua polizza assicurativa. Gloria Rios, Agente Assicurativo, We.Finance invia un promemoria a Sarah circa il rinnovo della sua polizza. Sarah segue le istruzioni fornite nell&#39;e-mail e completa con successo il processo.

## Procedura dettagliata sull&#39;applicazione di assicurazione automatica {#auto-insurance-application-walkthrough}

Lo scenario dell&#39;applicazione di assicurazione automatica We.Finance è una narrazione visiva per l&#39;utente e si basa su due persone:

* Sarah Rose, cliente di We.Finance
* Gloria Rios, Agente Assicurativo, We.Finance

### Gloria invia una comunicazione di rinnovo della polizza assicurativa da We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria accede AEM&#39;istanza, clicca **Rinnovo automatico delle assicurazioni,** e poi clicca **Apri l&#39;interfaccia utente dell&#39;agente.** Il clic precompila il documento di assicurazione con i dettagli della polizza di Sarah Rose. Clic di Gloria **Invia** e un messaggio viene visualizzato sullo schermo &quot;Invio avviato&quot; e quindi in pochi secondi &quot;Inviato correttamente&quot;.

Sarah riceve un&#39;e-mail con l&#39;oggetto &quot;Il tuo rinnovo dell&#39;assicurazione automatica&quot;.

![agent_ui_email](assets/agent_ui_email.png)

#### Vedi di persona {#see-it-yourself}

Vai a **Adobe Experience Manager** > **Forms** > **Forms e documenti** > **We.Finance** > **Assicurazione automatica**. Seleziona la **Rinnovo dell&#39;assicurazione automatica** comunicazione interattiva e clicca **Interfaccia utente di Open Agent**. La comunicazione interattiva si apre nell’interfaccia utente dell’agente. Immettere un indirizzo e-mail valido per ricevere l&#39;e-mail con il documento di criteri allegato e fare clic su Invia.

Puoi accedere e rivedere la comunicazione interattiva Rinnovo automatico dell&#39;assicurazione direttamente da `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`

### Sarah riceve una comunicazione di rinnovo della polizza assicurativa da We.Finance e decide di rinnovare {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah riceve un&#39;e-mail con un allegato da We.Finance che le ricorda che la sua assicurazione auto sta per scadere. L&#39;allegato è la versione stampata della sua lettera di assicurazione automatica.

Sarah clicca **Rinnova ora** ed è diretto alla versione web della sua lettera di assicurazione automatica. In cima a questa lettera, Sarah trova il numero di giorni rimasti per la scadenza della sua politica. La pagina fornisce a Sarah una panoramica di base dei suoi dettagli sulla polizza di assicurazione, come numero della polizza, importo dovuto e altre informazioni come le offerte di sconto e i premi fedeltà. Sarah di nuovo clicca **Rinnova ora** in fondo alla politica.

![ref1](assets/ref1.png)

#### Come funziona {#how-it-works}

L&#39;output web e di stampa della tua lettera di assicurazione automatica viene creato utilizzando le funzionalità multicanale delle comunicazioni interattive.

Il pulsante Rinnova ora nell’e-mail è collegato all’applicazione Rinnova assicurazione automatica, che è una comunicazione interattiva su un’istanza di pubblicazione.

#### Vedi di persona {#see-it-yourself-1}

Devi aver ricevuto un&#39;e-mail con un PDF allegato. PDF è una versione stampata della tua lettera di assicurazione automatica. Fai clic su **Rinnova ora** per accedere alla versione web del criterio. Controlla i tuoi dati personali e i dettagli della politica e fai clic su **Rinnova ora** che ti porta a un&#39;altra comunicazione interattiva.

La **Rinnova ora** pulsante nell&#39;e-mail indirizza Sarah alla versione web del criterio. Puoi visitare il seguente URL:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Puoi controllare il riepilogo dettagliato del rinnovo dell&#39;assicurazione automatica e fare clic su **Rinnova ora** nella parte inferiore della pagina.

### Sarah raggiunge la pagina di pagamento {#sarah-reaches-the-payment-page}

We.Finance porta Sarah alla pagina Pagamento. Sarah ricontrolla il suo numero di criteri e la data di scadenza con i suoi record. Sul lato destro della pagina, controlla il Riepilogo pagamenti del rinnovo con uno sconto del 10% sull&#39;importo totale.

#### Come funziona {#how-it-works-1}

Il pulsante Rinnova ora indirizza Sarah alla pagina di pagamento. La pagina di pagamento è un modulo adattivo.

#### Vedi di persona {#see-it-yourself-2}

Fai clic su **Rinnova ora** per accedere alla pagina Pagamento. Inserisci le informazioni sulla carta di credito e fai clic su **Effettua Pagamenti.**

Puoi raggiungere la pagina del pagamento nell’istanza di authoring in

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah effettua il pagamento e completa il processo {#sarah-makes-the-payment-and-completes-the-process}

Sarah compila i suoi dettagli e clicca sulla carta di credito **Effettua il pagamento**.

#### Come funziona {#how-it-works-2}

Quando Sarah compila i dettagli della carta di credito e fa clic su Invia, il pagamento della sua carta di credito viene elaborato e sullo schermo viene visualizzato un messaggio di ringraziamento configurato nel modulo adattivo.

#### Vedi di persona {#see-it-yourself-3}

Puoi visualizzare il messaggio di conferma dopo aver fatto clic su Effettua pagamento in

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
