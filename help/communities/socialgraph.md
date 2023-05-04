---
title: Utilizzo di Social Graph
seo-title: Using Social Graph
description: Aggiunta di un componente seguente a una pagina
seo-description: Adding a Following component to a page
uuid: 8be6334b-e6c9-40bc-90a8-750b98419470
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 0ce57ab1-e4c6-4c38-963d-556eef8757f2
exl-id: ab829d28-278d-4139-af16-edcc24b3d56b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 5%

---

# Utilizzo di Social Graph {#using-social-graph}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Introduzione {#introduction}

La capacità di un membro della comunità di seguire [attività](activities.md) oltre a essere seguito è costituito da due componenti: `Follow`e `Following`.

La `Follow`Il componente deve essere associato a un’altra risorsa e questa associazione è già stabilita per i membri e le funzionalità della community.

La `Following`Il componente elenca semplicemente i membri che seguono il membro corrente o che sono seguiti dal membro corrente. Questo grafico social delle relazioni tra i membri è incluso nel profilo utente stabilito per un [sito della community](overview.md#communitiessites).

## Aggiunta di seguito a una pagina {#adding-following-to-a-page}

Se desideri aggiungere una `Following`in una pagina in modalità di authoring, individua il componente `Communities / Following` e trascinalo nella posizione in una pagina in cui dovrebbe essere visualizzato il grafico social.

Per le informazioni necessarie, visita [Nozioni di base sui componenti di Communities](basics.md).

Quando il [librerie lato client richieste](essentials-socialgraph.md#essentials-for-client-side) sono inclusi, è così che `Following` apparirà il componente:

![chlimage_1-447](assets/chlimage_1-447.png)

## Configurazione seguente {#configuring-following}

Attualmente, è necessario impostare la proprietà per determinare se il componente visualizza il `follows`o `following`relazione.

## Informazioni aggiuntive {#additional-information}

Per ulteriori informazioni, consulta [Nozioni di base sul grafico social](essentials-socialgraph.md) per sviluppatori.
