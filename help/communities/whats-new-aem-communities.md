---
title: Novità in AEM 6.4 Communities
seo-title: Novità in AEM 6.4 Communities
description: 'null'
seo-description: 'null'
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 0%

---


# What&#39;s New in AEM 6.4 Communities {#what-s-new-in-aem-communities}

 AEM Communities offre alle aziende un framework per la collaborazione tra partner, clienti e dipendenti. Offre funzionalità social per la struttura dei siti web e aiuta le aziende a coinvolgere e a fornire conoscenze ai propri azionisti, per migliorare il valore del marchio nel loro modo di fare.

AEM 6.4 Community offre funzionalità per migliorare l&#39;esperienza degli utenti della community e semplificare le attività quotidiane di amministratori, moderatori e manager della community.

Ulteriori informazioni per introduzione rapida a nuove funzioni e miglioramenti. Inoltre, consultate AEM 6.4 Communities [release notes](../release-notes/communities-release-notes.md). Per AEM documentazione di Communities 6.4, visitate [AEM Guida](home.md)utente di Communities 6.4.

## Gestione di sottocommunity o gruppi di community {#managing-sub-communities-or-community-groups}

 AEM Communities consente agli amministratori della community di creare gruppi e sottogruppi all’interno del sito community, utilizzando modelli predefiniti, nell’ambiente di authoring. Questi gruppi fungono da sottocomunità, che possono ereditare molte configurazioni, come i temi e lo stile dal sito padre. Tuttavia, questi gruppi possono essere diversi dal sito padre, ad esempio con un set diverso di moderatori di gruppo o possono variare a livello di protezione. Questi gruppi funzionano come mini-community indipendenti completamente sviluppate e ulteriormente potenziate dai seguenti miglioramenti.

### Creare gruppi con più impostazioni internazionali in un singolo passaggio {#create-multi-locale-groups-in-single-step}

Come parte di un sito della community, è possibile creare gruppi multilingue in un&#39;unica operazione. **[!UICONTROL Ulteriori campi Lingua(i)]** gruppo community disponibili nella pagina Modello **[!UICONTROL gruppo]** community, disponibile durante la creazione di un [nuovo gruppo](groups.md) community all&#39;interno di un sito community, rendono possibile tale operazione.

![multilingue-group-1](assets/multilingualgroup-1.png)

Per creare tali gruppi, gli utenti possono semplicemente accedere a Raccolta gruppi del sito community desiderato dalla console Siti. Create un gruppo e specificate le lingue desiderate nel campo **[!UICONTROL Ulteriori lingue del gruppo community disponibili]** della pagina Modello **[!UICONTROL gruppo]** community.

### Eliminare gruppi community dalla console Gruppi {#delete-community-groups-from-groups-console}

AEM 6.4 Communities fornisce l&#39;icona Elimina gruppo sui gruppi community esistenti, nella raccolta Gruppi community all&#39;interno della console Siti community. Questo consente l’eliminazione [del](groups.md#deleting-the-group) gruppo con un solo clic, insieme all’eliminazione di tutti gli elementi associati al gruppo (ad esempio contenuto e appartenenze utente).

![delete](assets/deletegrp.png)

### Creazione e assegnazione di risorse di abilitazione all’interno dei gruppi {#create-and-assign-enablement-resources-within-groups}

Ora è possibile creare, gestire e pubblicare contenuti didattici per un set specifico di membri della comunità. A causa della disponibilità di funzioni di catalogo e assegnazione per i gruppi della community (e non solo per l&#39;intero sito della community), i manager dell&#39;abilitazione possono [assegnare risorse](resource.md) di abilitazione e percorsi di apprendimento a un piccolo gruppo di persone.

![assignCatalog](assets/assignmentcatalog.png)

## Moderazione del contenuto generato dall&#39;utente {#moderating-user-generated-content}

AEM 6.4 Community offre pochi miglioramenti alla moderazione, che sono utili per facilitare la vita quotidiana dei moderatori della comunità.

### Rilevamento automatico dello spam  {#automatic-spam-detection}

Il nuovo motore di rilevamento dello spam consente di filtrare i contenuti generati dagli utenti indesiderati e non richiesti sui siti o sui gruppi della community. Quando abilitata, questa funzionalità può contrassegnare un contenuto generato dall’utente come Spam o Not Spam in base a un set predefinito di parole spam. I moderatori possono agire ulteriormente sul contenuto per negarlo o consentirne la visualizzazione nell’istanza di pubblicazione. Queste azioni di moderazione possono essere eseguite in linea o attraverso la console di moderazione in blocco.

![spamdetection-1](assets/spamdetection-1.png)

[Il rilevatore](moderate-ugc.md#spam-detection) di spam rileva e contrassegna un dato contenuto generato dall’utente con una precisione del 90%. Tuttavia, questa funzionalità non è abilitata per impostazione predefinita. Per attivarla, gli amministratori della community devono passare a configMgr sul sistema/console e aggiungere il processo Spam.

![spamprocess-1](assets/spamprocess-1.png)

### Nuovi filtri (con risposta/senza risposta) per QnA {#new-answered-unanswered-filters-for-qna}

AEM 6.4 aggiunge due [nuovi filtri](moderation.md#filter-rail), denominati Risposta e Non risposta per le domande QnA, alla console di moderazione di massa. Questi filtri sono disponibili in Stato nella barra Filtro.

![stati](assets/statuses.png)

Selezionando lo stato Risposta, tutte le domande cui è stato risposto sono visibili al moderatore nell&#39;area contenuto. Se è selezionato solo lo stato Non risposto, il moderatore visualizzerà tutto il contenuto (per tutti i tipi di contenuto) tranne le domande cui è stato risposto, perché la proprietà responsabile per la domanda con risposta non esiste nel caso di domande senza risposta e altri contenuti quali l&#39;argomento forum, l&#39;articolo di blog o i commenti.

### Filtri di moderazione segnalibro {#bookmark-moderation-filters}

 AEM Communities consente di [contrassegnare i filtri](moderation.md#filter-rail) di moderazione predefiniti nella console di moderazione. Questi segnalibri salvati possono essere rivisitati in seguito e condivisi con altri utenti.

Gli utenti devono semplicemente selezionare i filtri desiderati dalla Barra Filtro nella console di moderazione, per visualizzare l&#39;UGC filtrato e contrassegnare i filtri sui propri browser. Questi filtri vengono aggiunti alla fine della stringa URL e possono quindi essere condivisi, riutilizzati e rivisitati in un secondo momento.

## Gestione di siti community {#managing-community-sites}

AEM 6.4 Communities offre miglioramenti alla gestione del sito, che assicurano la creazione, la gestione e l&#39;eliminazione di numerosi siti community in diverse lingue da parte degli amministratori del sito.

### Creazione di siti community con più lingue in un unico passaggio {#create-multi-locale-community-sites-in-one-step}

 AEM Communities consente di creare siti [](create-site.md) di community multilingue in un&#39;unica operazione. Ciò è possibile a causa della disponibilità di più lingue da selezionare nel campo Lingua **[!UICONTROL base sito]** community nella pagina Modello **** sito, durante la creazione di un nuovo sito community dalla console Siti.

![multilocalesite](assets/multilocalesite.png)

Gli utenti possono selezionare le cartelle di configurazione, il branding e molte altre configurazioni contemporaneamente per tutti questi siti.

### Elimina siti community dalla console Siti {#delete-community-sites-from-sites-console}

AEM 6.4 Communities fornisce l&#39;icona Elimina sito sui siti community esistenti, nella console Siti community. Questo consente di [eliminare il sito](create-site.md) e gli elementi associati con un solo clic.

![siteazioni](assets/siteactions.png)

## Gestione di UGC e profili utente {#managing-ugc-and-user-profiles}

Mantenendo la protezione dei dati degli utenti al centro dell&#39;esperienza della community,  AEM Communities espone [API pronte all&#39;uso](user-ugc-management-service.md) e servlet [di](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet)esempio. Queste API consentono di gestire in massa (eliminazione ed esportazione in blocco) i contenuti generati dagli utenti e di eliminare i profili utente, e sono fondamentali per gestire le richieste di conformità ai requisiti GDPR dell&#39;UE.

## Che cosa è cambiato {#what-s-changed}

* La verifica Captcha, durante la creazione di un nuovo sito community, non è più disponibile out-of-the-box in AEM Community 6.4. Tuttavia, il sito Community può essere personalizzato per includere [Google component reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) per una migliore sicurezza.
* L&#39;opzione per caricare un CSS personalizzato è stata rimossa dal tema dei siti e dei gruppi della community.
* Le icone Solo contenuto e Ricerca sono state aggiunte nella Barra dei filtri nell’interfaccia utente Moderazione in blocco.
* Il filtro Percorso contenuto è stato aggiunto nella barra Filtro nell’interfaccia utente Moderazione in blocco.
* L’opzione Passa alla modalità in blocco e Esci dalla modalità in blocco è stata rimossa dall’interfaccia utente Moderazione in blocco. Per passare alla modalità multi-selezione, fai clic sull’icona Seleziona ( ![selezione](assets/selecticon.png)) su un post, che viene visualizzata quando si passa il mouse (desktop) o si preme e si tiene premuto un dito sul post (mobile).
