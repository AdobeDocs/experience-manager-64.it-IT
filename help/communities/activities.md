---
title: Funzionalità Flussi di attività
seo-title: Funzionalità Flussi di attività
description: Attività di un membro della community che ha effettuato l'accesso
seo-description: Attività di un membro della community che ha effettuato l'accesso
uuid: 8a05a5ed-0edf-4528-a145-f9dc37d10247
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ccaebb4c-cc1c-4ee7-b080-99667f348427
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 1%

---


# Funzionalità dei flussi di attività {#activity-streams-feature}

## Introduzione {#introduction}

Le attività di un membro della comunità firmato, come l&#39;invio a un forum o blog, vengono raccolte in un flusso che può essere filtrato e visualizzato in vari modi attraverso la configurazione del componente `Activity Streams`.

La possibilità di seguire aggiunge un&#39;altra visione delle attività quando i membri della comunità seguono i post di interesse o seguono le attività di altri membri della comunità.

Questa sezione della documentazione descrive

* Aggiunta del componente Activity Streams a un sito AEM
* Impostazioni di configurazione per il componente Activity Streams

## Aggiunta di flussi di attività a una pagina {#adding-activity-streams-to-a-page}

Se si desidera aggiungere un componente `Activity Streams` a una pagina in modalità di creazione, utilizzare il browser componenti per individuare

* `Communities / Activity Streams`

e trascinatelo nella stessa posizione in una pagina in cui dovrebbero essere visualizzati i flussi di attività.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando vengono incluse le [librerie lato client ](essentials-activities.md#essentials-for-client-side), viene visualizzato il componente `Activity Streams`:

![chlimage_1-195](assets/chlimage_1-195.png)

## Configurazione dei flussi di attività {#configuring-activity-streams}

Selezionare il componente `Activity Streams` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-196](assets/chlimage_1-196.png)

Nella scheda **[!UICONTROL Attività utente]**, specificare quali attività visualizzare:

![chlimage_1-197](assets/chlimage_1-197.png)

* **[!UICONTROL Numero massimo di]**
attivitàNumero di attività da visualizzare
* **[!UICONTROL Percorso risorsa flusso:]**
lasciate vuoto per impostazione predefinita il sito della community o il gruppo della community. Il percorso della risorsa del flusso identifica l&#39;origine delle attività. Il valore predefinito è vuoto.
* **[!UICONTROL Visualizza visualizzazione attività utente]**
selezionata, la pagina delle attività includerà una scheda che filtra le attività in base a quelle generate all&#39;interno della community dal membro corrente. Il valore predefinito è selezionato.
* **[!UICONTROL Visualizza]**
visualizzazione Tutte le attivitàSe questa opzione è selezionata, la pagina delle attività includerà una scheda che include tutte le attività generate all&#39;interno della comunità a cui il membro corrente ha accesso. Il valore predefinito è selezionato.
* **[!UICONTROL Visualizza]**
visualizzazione seguente: se questa opzione è selezionata, la pagina delle attività includerà una scheda che filtra le attività in base a quelle che il membro corrente sta seguendo. Il valore predefinito è selezionato.

## Visualizzazione seguente {#following-view}

I componenti devono essere configurati per abilitare quanto segue. Le funzioni che consentono di seguire sono [blog](blog-feature.md), [forum](forum.md), [QnA](working-with-qna.md), [calendario](calendar.md), [filelibrary](file-library.md) e [commenti](comments.md).

![chlimage_1-198](assets/chlimage_1-198.png)

Il pulsante **Segui** consente di seguire le voci come attività, [notifiche](notifications.md) e/o [iscrizioni](subscriptions.md). Ogni volta che il tasto **Segui** è selezionato, è possibile attivare o disattivare una selezione. La selezione `Email Subscriptions` è presente solo se configurata.

Se è selezionato un metodo di seguito, il testo del pulsante diventa **Successivo**. Per comodità, è possibile selezionare `Unfollow All` per disattivare tutti i metodi.

Verrà visualizzato il pulsante **Segui**:

* Quando si visualizza il profilo di un altro membro
* In una pagina delle funzioni principali, ad esempio forum, QnA e blog
   * Segue tutta l&#39;attività per la funzione generale

* Per un post specifico, ad esempio un argomento forum, una domanda QnA o un articolo blog
   * Segue tutta l&#39;attività per la voce specifica

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Activity Streams Essentials](essentials-activities.md) per gli sviluppatori.
