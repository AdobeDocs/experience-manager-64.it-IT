---
title: Aggiungi commento a pagina di esempio
seo-title: Aggiungi commento a pagina di esempio
description: Aggiunta di commenti personalizzati a una pagina
seo-description: Aggiunta di commenti personalizzati a una pagina
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
translation-type: tm+mt
source-git-commit: 44c56ec5de6e9a832aaa52ab4a6c4978af7a9865
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Aggiungi commento a pagina di esempio {#add-comment-to-sample-page}

Ora che i componenti per il sistema di commenti personalizzato sono presenti nella directory dell&#39;applicazione (/apps), è possibile utilizzare il componente esteso. L’istanza del sistema di commenti in un sito Web da modificare deve impostare resourceType come sistema di commenti personalizzato e includere tutte le librerie client necessarie.

## Identificare Clientlibs richiesti {#identify-required-clientlibs}

Le librerie client necessarie per lo stile e il funzionamento dei commenti predefiniti sono necessarie anche per i commenti estesi.

La [Guida ai componenti della community](components-guide.md) identifica le librerie client richieste. Passare alla Guida ai componenti e visualizzare il componente Commenti, ad esempio:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Tenere presenti le tre librerie client necessarie affinché Commenti possa eseguire correttamente il rendering e il funzionamento. Questi dovranno essere inclusi nel punto in cui viene fatto riferimento ai commenti estesi, così come nella libreria client dei commenti [estesi](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Aggiungi commenti personalizzati a una pagina {#add-custom-comments-to-a-page}

Poiché per ogni pagina può essere presente un solo sistema di commenti, è più semplice creare una pagina di esempio come descritto nella breve [Creazione di una pagina di esempio](create-sample-page.md) esercitazione.

Una volta creato, entrate in modalità Progettazione e rendete disponibile il gruppo di componenti Personalizzato per consentire l&#39;aggiunta del componente `Alt Comments` alla pagina.

Affinché il commento venga visualizzato e funzioni correttamente, è necessario aggiungere le librerie client per i commenti all&#39;elenco clientlibslist della pagina (vedere [Clientlibs for Communities Components](clientlibs.md)).

### Commenti Clientlibs sulla pagina di esempio {#comments-clientlibs-on-sample-page}

![Commenti Clientlibs sulla pagina di esempio](assets/chlimage_1-48.png)

### Autore: Commento Alt sulla pagina di esempio {#author-alt-comment-on-sample-page}

![Commento Alt sulla pagina di esempio](assets/chlimage_1-49.png)

### Autore: Nodo commenti pagina di esempio {#author-sample-page-comments-node}

È possibile verificare resourceType in CRXDE visualizzando le proprietà del nodo dei commenti per la pagina di esempio in `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Pubblica pagina di esempio {#publish-sample-page}

Dopo che il componente personalizzato è stato aggiunto alla pagina, è inoltre necessario (ri) [pubblicare la pagina](sites-console.md#publishing-the-site).

### Pubblica: Commento Alt sulla pagina di esempio {#publish-alt-comment-on-sample-page}

Dopo aver pubblicato l&#39;applicazione personalizzata e la pagina di esempio, dovrebbe essere possibile inserire un commento. Quando si effettua l&#39;accesso, con un utente [demo](tutorials.md#demo-users) o un amministratore, dovrebbe essere possibile pubblicare un commento.

Di seguito è riportato aaron.mcdonald@mailinator.com di un commento:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Ora che il componente esteso funziona correttamente con l’aspetto predefinito, è ora di modificare l’aspetto.

