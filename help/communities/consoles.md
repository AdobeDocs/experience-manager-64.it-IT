---
title: Console di Communities
seo-title: Communities Consoles
description: Informazioni sulle console della community
seo-description: Community Consoles explained
uuid: 1c5b2600-9059-4b44-9741-f1b627423d3c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5fa9ee8b-5893-4ae9-a986-bfdbb00f355f
role: Admin
exl-id: f31072dc-ad2d-4f2d-b222-05d7fb19e471
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 3%

---

# Console di Communities {#communities-consoles}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Le console AEM Communities, disponibili nell’ambiente di authoring dal pannello di navigazione globale, consentono di accedere a attività amministrative quali

* [Creazione di un sito community](sites-console.md)
* Aggiunta [gruppi](groups.md) nidificato all’interno del sito
* Gestione [modelli di sito community](sites.md)
* Gestione [membri della comunità](members.md)
* [Moderazione](moderate-ugc.md) contenuto generato dall’utente (UGC)
* Crea [badge personalizzati](badges.md)
* Configurazione della [archiviazione predefinita per UGC](srp-config.md)

Quando [Archiviazione UGC](working-with-srp.md) è configurato come archivio comune condiviso dagli ambienti di authoring e pubblicazione, [console di moderazione](moderation.md), disponibile sia negli ambienti di authoring che di pubblicazione, opera su un’istanza solitaria di UGC.

Nell’ambiente di authoring, dopo aver effettuato l’accesso con privilegi di amministratore, la variabile `Communities` le console sono disponibili nelle console di navigazione e strumenti.

>[!NOTE]
>
>Nell’ambiente di pubblicazione, un [sito della community](sites-console.md) visualizzerà un `Administration`voce di menu quando il membro connesso dispone dei privilegi appropriati.

## Pannello di navigazione globale {#global-navigation-panel}

![chlimage_1-91](assets/chlimage_1-91.png)

Seleziona la `Adobe Experience Manager` nell’angolo in alto a sinistra per aprire il pannello di navigazione globale e accedere a due icone:

* [Console di navigazione](#navigation-console)
* [Console Strumenti](tools.md)

## Console di navigazione {#navigation-console}

Per accedere alle varie console Community, dalla navigazione globale seleziona **navigazione, Community**.

![chlimage_1-92](assets/chlimage_1-92.png)

* [Sites](sites-console.md)

   La console Sites è accessibile nell’ambiente di authoring allo scopo di creare e gestire siti community e relativi [gruppi](groups.md).

* [Moderazione](moderation.md)

   La console Moderazione è per la moderazione in blocco di UGC e nell’ambiente di authoring. Una console di moderazione di gruppo simile è accessibile nell’ambiente di pubblicazione ai membri della community con il ruolo di [moderatore comunitario](users.md#publishenvironmentusersandgroups) per uno o più siti della community.

* [Membri, gruppi](members.md)

   Le console Membri e Gruppi consentono di gestire i membri della community e i gruppi di membri presenti nell’ambiente di pubblicazione dall’ambiente di authoring.

* [Rapporti](reports.md)

   Nella console Rapporti è possibile generare rapporti su assegnazioni, visualizzazioni di pagina e contenuti pubblicati (UGC) quando un sito della community dispone di [abilitato Adobe Analytics](sites-console.md#analytics). La console è disponibile solo nell’ambiente di authoring.

* [Riferimenti](resources.md)

   La console Risorse si trova nella posizione [responsabili dell&#39;abilitazione](enablement.md#communitymanagers) creare, gestire e assegnare risorse ai membri di un [sito della community di abilitazione](overview.md#enablement-community). La console è disponibile solo nell’ambiente di authoring.

## Console Strumenti {#tools-console}

Per accedere [Strumenti per le community](tools.md) (precedentemente console di amministrazione), dalla navigazione globale: **[!UICONTROL Strumenti > Community]**
