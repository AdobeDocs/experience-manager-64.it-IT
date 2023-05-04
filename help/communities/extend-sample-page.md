---
title: Aggiungi commento alla pagina di esempio
seo-title: Add Comment to Sample Page
description: Aggiungere commenti personalizzati a una pagina
seo-description: Add Custom Comments to a page
uuid: 7dbaff4f-9986-435d-9379-7add676ea254
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7185fb13-46a2-4fa3-aa21-a51e63cdb9be
exl-id: 96ef7e58-66c9-4985-973b-0c6fc7c39fd5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 2%

---

# Aggiungi commento alla pagina di esempio {#add-comment-to-sample-page}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Ora che i componenti del sistema di commento personalizzato sono presenti nella directory dell&#39;applicazione (/apps), è possibile utilizzare il componente esteso. L&#39;istanza del sistema di commenti in un sito Web da modificare deve impostare resourceType come sistema di commenti personalizzato e includere tutte le librerie client necessarie.

## Identificare le clientlib richieste {#identify-required-clientlibs}

Le librerie client necessarie per lo stile e il funzionamento dei commenti predefiniti sono necessarie anche per i commenti estesi.

La [Guida ai componenti della community](components-guide.md) identifica le librerie client richieste. Accedi alla Guida dei componenti e visualizza il componente Commenti , ad esempio:

[http://localhost:4502/content/community-components/en/comments.html](http://localhost:4502/content/community-components/en/comments.html)

Tieni presente le tre librerie client necessarie affinché Commenti possa eseguire correttamente il rendering e il funzionamento di . Questi dovranno essere inclusi nei casi in cui si fa riferimento ai commenti estesi, nonché nella [libreria client di commenti esteso](extend-create-components.md#create-a-client-library-folder) ( `apps.custom.comments`).

![chlimage_1-47](assets/chlimage_1-47.png)

## Aggiungere commenti personalizzati a una pagina {#add-custom-comments-to-a-page}

Poiché può esistere un solo sistema di commento per pagina, è più semplice creare una pagina di esempio come descritto nel breve [Creare una pagina di esempio](create-sample-page.md) esercitazione.

Una volta creato, entra in modalità Progettazione e rende disponibile il gruppo di componenti Personalizzato per consentire al `Alt Comments` da aggiungere alla pagina.

Affinché il Commento appaia e funzioni correttamente, è necessario aggiungere le librerie client per Commenti all’elenco delle clientlibslist per la pagina (consulta [Componenti Clientlibs for Communities](clientlibs.md)).

### Commenti Clientlibs sulla pagina di esempio {#comments-clientlibs-on-sample-page}

![Commenti Clientlibs sulla pagina di esempio](assets/chlimage_1-48.png)

### Autore: Commento Alt sulla pagina di esempio {#author-alt-comment-on-sample-page}

![Commento Alt sulla pagina di esempio](assets/chlimage_1-49.png)

### Autore: Nodo dei commenti della pagina di esempio {#author-sample-page-comments-node}

Puoi verificare resourceType in CRXDE visualizzando le proprietà del nodo dei commenti per la pagina di esempio in `/content/sites/sample/en/jcr:content/content/primary/comments`.

![chlimage_1-50](assets/chlimage_1-50.png)

### Pubblica pagina di esempio {#publish-sample-page}

Dopo aver aggiunto il componente personalizzato alla pagina, è necessario anche (ri) [pubblicare la pagina](sites-console.md#publishing-the-site).

### Pubblica: Commento Alt sulla pagina di esempio {#publish-alt-comment-on-sample-page}

Dopo aver pubblicato sia l’applicazione personalizzata che la pagina di esempio, dovrebbe essere possibile inserire un commento. Al momento dell’accesso, con un [utente dimostrativo](tutorials.md#demo-users) o amministratore, dovrebbe essere possibile pubblicare un commento.

Ecco aaron.mcdonald@mailinator.com un commento:

![chlimage_1-51](assets/chlimage_1-51.png) ![chlimage_1-52](assets/chlimage_1-52.png)

Ora che sembra che il componente esteso funzioni correttamente con l’aspetto predefinito, è il momento di modificare l’aspetto.
