---
title: Utilizzo del voto
seo-title: Using Voting
description: Aggiunta del componente Voto a una pagina
seo-description: Adding the Voting component to a page
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
exl-id: 660a7106-0c21-4073-8319-4d6d20b9bc49
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 8%

---

# Utilizzo del voto {#using-voting}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La `Voting` Componente è uno strumento utile che consente ai membri della community di assegnare una valutazione a un particolare contenuto, ad esempio una risposta all’interno di un componente QnA. Con la `Voting` componenti, i membri selezionano frecce verso l’alto o verso il basso per indicare la propria opinione.

## Aggiunta di un voto a una pagina {#adding-voting-to-a-page}

Per aggiungere una `Voting` componente per una pagina in modalità di creazione, usate il browser componenti per individuare `Communities / Voting` e trascinarlo nella posizione desiderata su una pagina, ad esempio una posizione relativa alla funzione su cui gli utenti possono votare.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-voting.md#essentials-for-client-side) sono inclusi, è così che `Voting` apparirà .

![chlimage_1-307](assets/chlimage_1-307.png)

## Configurazione del voto {#configuring-voting}

Seleziona il `Voting` per accedere e selezionare il `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-308](assets/chlimage_1-308.png)

Sotto la **[!UICONTROL Testi ed etichette]** specificare le proprietà utilizzate per registrare i voti.

![chlimage_1-309](assets/chlimage_1-309.png)

* **[!UICONTROL Etichetta risposta positiva]**
(
*Obbligatorio*) Nome della proprietà interna per una risposta positiva.

* **[!UICONTROL Etichetta risposta negativa]**
(
*Obbligatorio*) Nome della proprietà interna per una risposta negativa.

* **[!UICONTROL Nome conteggio]**
(
*Obbligatorio*) Il nome della proprietà interna e identificabile per questa istanza di un componente di voto.

## Esperienza dei visitatori del sito {#site-visitor-experience}

### Membri {#members}

I deputati possono votare una sola volta, ma possono modificare il loro voto in qualsiasi momento.

### Anonimo {#anonymous}

Il voto anonimo non è supportato. I visitatori del sito devono registrarsi (diventare membro) e accedere per partecipare al voto una volta.

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Elementi essenziali del voto](essentials-voting.md) per sviluppatori.
