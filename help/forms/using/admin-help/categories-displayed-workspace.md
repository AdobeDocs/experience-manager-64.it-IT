---
title: Gestione delle categorie visualizzate in Workspace
seo-title: Managing the categories displayed in Workspace
description: In Workspace, i processi che un utente può avviare vengono visualizzati in categorie nel riquadro di navigazione a sinistra. Scopri come gestire queste categorie visualizzate in Workspace.
seo-description: In Workspace, the processes that a user can start are displayed in categories in the left navigation pane. Learn how you can manage these categories displayed in Workspace.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 5a2bd0ea-2c5e-4e0c-aff1-dba06be6a5b7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 1%

---

# Gestione delle categorie visualizzate in Workspace {#managing-the-categories-displayed-in-workspace}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

In Workspace, i processi che un utente può avviare vengono visualizzati in categorie nel riquadro di navigazione a sinistra. È possibile impostare le categorie nella console di amministrazione oppure i progettisti di processi possono impostarle in Workbench. Quando i progettisti di processi creano processi, li assegnano a categorie.

Quando specifichi i nomi delle categorie, creali in modo che vengano visualizzati correttamente nel riquadro di navigazione Area di lavoro. Per impostazione predefinita, il riquadro di navigazione a sinistra ha una larghezza fissa di 210 pixel, che è di circa 24 caratteri. Se il nome della categoria specificato è troppo lungo per adattarsi alla larghezza fissa del riquadro di navigazione a sinistra, viene troncato. Il nome completo viene visualizzato solo quando il puntatore del mouse viene messo in pausa. Cerca di evitare i nomi di categoria che verranno troncati. Gli esempi seguenti illustrano i nomi delle categorie corrispondenti e troncati:

**Nome della categoria adatto:** Partecipazione e congedo

**Nome della categoria troncata:** Partecipazione e congedo (Stati Uniti)

In Workspace, i processi all’interno di una categoria vengono generalmente visualizzati come schede nella pagina Avvia processo . In generale, sei schede possono essere visualizzate sullo schermo per una categoria prima che l&#39;utente sia tenuto a scorrere per visualizzare le schede rimanenti. Poiché lo scorrimento rende più difficile trovare un processo, è consigliabile limitare ciascuna categoria a sei processi o, a seconda della risoluzione, limitare il numero di processi che possono essere visualizzati sullo schermo senza richiedere alcuno scorrimento.

Se si utilizza MySQL come database di moduli AEM, la console di amministrazione non può distinguere tra due nomi di categoria che differiscono solo nell’uso di caratteri estesi. Ad esempio, se si crea una categoria denominata abcde e una categoria denominata âbcdè, vengono considerate uguali.

## Aggiungi una categoria {#add-a-category}

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione categorie.
1. Fai clic su Aggiungi. Se si desidera aggiungere una sottocategoria, selezionare una categoria e quindi fare clic su Aggiungi.
1. Nella casella Nome digitare un nome per la categoria e nella casella Descrizione digitare una descrizione per la categoria.
1. Fai clic su Aggiungi. La categoria viene visualizzata nella pagina Gestione categorie .

   ***nota **: Durante la creazione di categorie è possibile aggiungere solo fino a cinque livelli di gerarchia.*

## Modificare una categoria {#edit-a-category}

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione categorie.
1. Selezionare la categoria da modificare e fare clic su Modifica. In alternativa, puoi fare doppio clic su una categoria da modificare.
1. Modificare il nome della categoria nella casella Nome.

## Rimuovere una categoria {#remove-a-category}

È possibile rimuovere solo le categorie non in uso.

1. Nella console di amministrazione, fare clic su Servizi > Applicazioni e servizi > Gestione categorie.
1. Nella pagina Gestione categorie selezionare la casella di controllo relativa alla categoria da rimuovere e fare clic su Rimuovi. La categoria non viene più visualizzata.
