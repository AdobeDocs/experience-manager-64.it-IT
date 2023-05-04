---
title: Uso di un modulo
seo-title: Working with a Form
description: Visualizza e aggiorna il modulo associato a un’attività o a un punto iniziale nell’app AEM Forms
seo-description: View and update the form associated with a task or Startpoint in the AEM Forms app
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
exl-id: ae565dbd-2631-4364-89f7-675700b43320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 2%

---

# Uso di un modulo {#working-with-a-form}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Se un modulo è abilitato per la sincronizzazione nell’app dei moduli, il modulo viene scaricato e puoi utilizzarlo direttamente.

I moduli vengono scaricati nell’app e sono disponibili offline. Ad esempio, si esegue un&#39;azienda bancaria e un cliente compila un&#39;applicazione sul sito. L’applicazione è un modulo adattivo che accetta le informazioni dei clienti e le memorizza per la revisione. L’amministratore rivede il modulo e crea un modulo di verifica nell’istanza AEM autore. L’amministratore abilita la sincronizzazione del modulo con l’app AEM Forms. Se il modulo di verifica è disponibile nell’app AEM Forms, l’agente di campo può utilizzare un dispositivo mobile per verificare i dettagli del cliente. Il dispositivo mobile si sincronizza con il server e il modulo di verifica viene caricato nell’app. L’agente del campo può visitare il cliente, verificare i dettagli, salvare i dati come bozza o inviare il modulo di verifica. Il modulo viene sincronizzato con il server ogni volta che l’app è online.

Per sincronizzare il modulo nell’app AEM Forms:

1. Nell’istanza di authoring, seleziona un modulo e fai clic su **Visualizza proprietà**.

1. Nella pagina delle proprietà, fai clic su **Avanzate.**
1. In Avanzate, abilita l&#39;opzione: **Sincronizzazione con l’app AEM Forms**, e tocca **Salva**.

Per sincronizzare più moduli, nell’istanza di authoring, seleziona più moduli in Forms Manager e tocca **Sincronizzazione con l’app AEM Forms**. Quando il modulo viene pubblicato, l’app AEM Forms può connettersi al server di pubblicazione e recuperare i moduli.

>[!NOTE]
>
>Moduli supportati:
>
>* Moduli adattivi (senza caricamento lento)
>* Moduli mobili
>
>Gli allegati a livello di modulo non sono supportati nei moduli adattivi recuperati nell’app AEM Forms sincronizzati con il server OSGi di AEM Forms. Gli utenti possono allegare file in un campo se l’autore ha abilitato allegati a livello di campo al momento della creazione del modulo.

**Apertura e aggiornamento di un modulo**

1. Per aprire un modulo, toccare il modulo nella schermata iniziale.
1. È possibile aggiornare i campi del modulo, aggiungere allegati, salvare come bozza e inviarlo.
