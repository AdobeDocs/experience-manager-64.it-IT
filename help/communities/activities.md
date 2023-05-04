---
title: Funzionalità dei flussi di attività
seo-title: Activity Streams Feature
description: Attività di un membro della comunità firmato
seo-description: Activities of a signed-in community member
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
exl-id: e62b7c0d-5004-4672-9fdc-566ece2785c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---

# Funzionalità dei flussi di attività {#activity-streams-feature}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

Le attività di un membro della comunità firmato, come il post su un forum o blog, vengono raccolte in un flusso che può essere filtrato e visualizzato in vari modi attraverso la configurazione del `Activity Streams` componente.

La possibilità di seguire aggiunge un altro punto di vista sulle attività quando i membri della comunità seguono posizioni di interesse o seguono le attività di altri membri della comunità.

Questa sezione della documentazione descrive

* Aggiunta del componente Flussi attività a un sito AEM
* Impostazioni di configurazione per il componente Flussi attività

## Aggiunta di flussi di attività a una pagina {#adding-activity-streams-to-a-page}

Se desideri aggiungere un `Activity Streams` componente per una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Activity Streams`

e trascinalo nella posizione di una pagina in cui dovrebbero essere visualizzati i flussi di attività.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-activities.md#essentials-for-client-side) sono inclusi, è così che `Activity Streams` apparirà il componente:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configurazione dei flussi di attività {#configuring-activity-streams}

Seleziona il `Activity Streams` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-196](assets/chlimage_1-196.png)

Sotto la **[!UICONTROL Attività utente]** scheda , specifica le attività da visualizzare:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Numero massimo di attività]**
Il numero di attività da visualizzare
* **[!UICONTROL Percorso risorsa flusso]**
Lascia vuoto per impostazione predefinita sul sito community o sul gruppo community. Il percorso della risorsa del flusso identifica l&#39;origine delle attività. Il valore predefinito è vuoto.
* **[!UICONTROL Visualizzazione delle attività utente]**
se questa opzione è selezionata, la pagina attività includerà una scheda che filtra le attività in base a quelle generate all’interno della community dal membro corrente. Il valore predefinito è selezionato.
* **[!UICONTROL Visualizza visualizzazione tutte le attività]**
Se questa opzione è selezionata, la pagina attività includerà una scheda che include tutte le attività generate all’interno della community a cui il membro corrente ha accesso. Il valore predefinito è selezionato.
* **[!UICONTROL Visualizzazione seguente]**
Se questa opzione è selezionata, la pagina attività includerà una scheda che filtra le attività in base a quelle che il membro corrente sta seguendo. Il valore predefinito è selezionato.

## Visualizzazione seguente {#following-view}

I componenti devono essere configurati per abilitare quanto segue. Funzioni che consentono quanto segue: [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filelibrio](file-library.md)e [commenti](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

La **Segui** pulsante fornisce un mezzo per seguire le voci come attività, [Notifiche](notifications.md)e/o [abbonamenti](subscriptions.md). Ogni volta che **Segui** è selezionato, è possibile attivare o disattivare una selezione. La `Email Subscriptions` la selezione è presente solo se configurata.

Se è selezionato un metodo di seguito, il testo del pulsante diventa **Seguente**. Per comodità, è possibile selezionare `Unfollow All` per disattivare tutti i metodi.

La **Segui** apparirà il pulsante:

* Visualizzazione del profilo di un altro membro
* In una pagina principale con funzioni quali forum, QnA e blog
   * Segue tutta l&#39;attività per quella funzione generale

* Per un post specifico, ad esempio un argomento del forum, una domanda QnA o un articolo di blog
   * Segue tutte le attività per quella voce specifica

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sui flussi di attività](essentials-activities.md) per sviluppatori.
