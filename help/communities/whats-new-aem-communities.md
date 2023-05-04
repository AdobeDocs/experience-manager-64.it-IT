---
title: Novità di AEM 6.4 Communities
description: AEM Communities offre un framework alle aziende per collaborare tra partner, clienti e dipendenti.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 0%

---

# Novità di AEM 6.4 Communities {#what-s-new-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Communities offre un framework alle aziende per collaborare tra partner, clienti e dipendenti. Offre funzionalità social alla struttura dei siti web e aiuta le aziende a coinvolgere e a fornire conoscenze ai propri stakeholder, per migliorare il valore del marchio nel loro modo.

AEM 6.4 Communities introduce funzionalità per migliorare le esperienze degli utenti della community e semplificare le attività quotidiane di amministratori, moderatori e manager della community.

Ulteriori informazioni per introduzione rapida a nuove funzioni e miglioramenti. Vedi anche AEM 6.4 Communities [note sulla versione](../release-notes/communities-release-notes.md). Per la documentazione di AEM 6.4 Communities, visita [Guida utente di AEM 6.4 Communities](home.md).

## Gestione di sottocommunity o gruppi di community {#managing-sub-communities-or-community-groups}

AEM Communities consente agli amministratori della community di creare gruppi e sottogruppi all’interno del sito community, utilizzando modelli predefiniti nell’ambiente di authoring. Questi gruppi fungono da sottocomunità, che possono ereditare molte configurazioni, come i temi e lo stile dal sito padre. Tuttavia, questi gruppi possono differire dal sito padre, ad esempio con un set diverso di moderatori di gruppo o possono variare a livello di sicurezza. Questi gruppi funzionano come mini-community indipendenti e completamente sviluppate, ulteriormente potenziate dai seguenti miglioramenti.

### Creare gruppi con più impostazioni internazionali in un singolo passaggio {#create-multi-locale-groups-in-single-step}

Come parte di un sito della community, è possibile creare gruppi multilingue in un’unica operazione. **[!UICONTROL Lingue disponibili aggiuntive per i gruppi della community]** campo **[!UICONTROL Modello Gruppo community]** , disponibile durante la creazione di un [nuovo gruppo community](groups.md) all&#39;interno di un sito della community, rende possibile tale operazione.

![multilingue-group-1](assets/multilingualgroup-1.png)

Per creare tali gruppi, gli utenti possono semplicemente accedere a Raccolta di gruppi del sito community desiderato dalla console Sites . Crea un gruppo e specifica le lingue desiderate in **[!UICONTROL Lingue disponibili aggiuntive per i gruppi della community]** campo **[!UICONTROL Modello Gruppo community]** pagina.

### Elimina gruppi community dalla console gruppi {#delete-community-groups-from-groups-console}

AEM 6.4 Communities fornisce l&#39;icona Elimina gruppo sui gruppi community esistenti, nella raccolta Gruppi community nella console Sites della community. Ciò consente [eliminazione di gruppi](groups.md#deleting-the-group) con un solo clic, insieme all’eliminazione di tutti gli elementi associati al gruppo (come contenuti e appartenenze utente).

![cancella](assets/deletegrp.png)

### Creare e assegnare risorse di abilitazione all’interno dei gruppi {#create-and-assign-enablement-resources-within-groups}

Ora è possibile creare, gestire e pubblicare contenuti di apprendimento per un set specifico di membri della community interessati. Grazie alla disponibilità di cataloghi e funzioni di assegnazione per gruppi della community (e non solo per l&#39;intero sito della community), i responsabili dell&#39;abilitazione possono [assegnare risorse di abilitazione](resource.md) e anche il percorso di apprendimento verso un piccolo gruppo di persone.

![assegna catalogo](assets/assignmentcatalog.png)

## Moderazione del contenuto generato dall’utente {#moderating-user-generated-content}

AEM 6.4 Communities offre pochi miglioramenti alla moderazione, che sono fondamentali per facilitare la vita quotidiana dei moderatori della comunità.

### Rilevamento automatico dello spam  {#automatic-spam-detection}

Il nuovo motore di rilevamento dello spam consente di filtrare i contenuti generati dagli utenti indesiderati e non richiesti sui siti o sui gruppi della community. Quando abilitata, questa funzionalità può contrassegnare un contenuto generato dall’utente come Spam o Not Spam in base a un set predefinito di parole spam. I moderatori possono agire ulteriormente sul contenuto per negarlo o consentirne la visualizzazione nell’istanza di pubblicazione. Queste azioni di moderazione possono essere eseguite in linea o tramite la console di moderazione di gruppo.

![spamdetection-1](assets/spamdetection-1.png)

[Rilevatore di spam](moderate-ugc.md#spam-detection) trova e contrassegna un dato contenuto generato dall’utente con precisione del 90%. Tuttavia, questa funzionalità non è abilitata per impostazione predefinita. Per abilitarlo, gli amministratori della community devono navigare su configMgr sul sistema/console e aggiungere il processo Spam.

![spamprocess-1](assets/spamprocess-1.png)

### Nuovi filtri (con risposta/senza risposta) per QnA {#new-answered-unanswered-filters-for-qna}

AEM 6.4 aggiunge due [nuovi filtri](moderation.md#filter-rail), con nome Risposte e non risposte per le domande di QnA, alla console di moderazione in blocco. Questi filtri sono disponibili in Stato nella barra dei filtri.

![stati](assets/statuses.png)

Quando si seleziona lo stato Risposta, tutte le domande risposte sono visibili al moderatore nell’area contenuto. Se invece è selezionato solo lo stato Non risposto, il moderatore visualizzerà tutti i contenuti (per tutti i tipi di contenuto) ad eccezione delle domande a cui è stato risposto, perché la proprietà responsabile della domanda a cui è stata data risposta non esiste nel caso di domande a cui non è stata data risposta e altri contenuti quali argomento del forum, articolo di blog o commenti.

### Filtri di moderazione dei segnalibri {#bookmark-moderation-filters}

AEM Communities offre la possibilità di [segnalibro dei filtri di moderazione predefiniti](moderation.md#filter-rail) sulla console di moderazione. Questi segnalibri salvati possono essere rivisitati in un secondo momento e condivisi con altri utenti.

Gli utenti devono semplicemente selezionare i filtri desiderati dalla barra Filtro nella console di moderazione, per visualizzare l’UGC filtrato e contrassegnare i filtri sui propri browser. Questi filtri vengono aggiunti alla fine della stringa URL e possono quindi essere condivisi, riutilizzati e rivisitati in un secondo momento.

## Gestione di siti della community {#managing-community-sites}

AEM 6.4 Communities offre miglioramenti alla gestione dei siti, che assicurano che numerosi siti community in lingue diverse vengano facilmente creati, gestiti ed eliminati dagli amministratori di sito.

### Creare siti di community locali multipli in un unico passaggio {#create-multi-locale-community-sites-in-one-step}

AEM Communities consente di creare un [siti di comunità multilingue](create-site.md) in un&#39;unica operazione. Questo è possibile a causa della disponibilità di più lingue tra cui scegliere in **[!UICONTROL Lingua di base del sito community]** campo **[!UICONTROL Modello del sito]** durante la creazione di un nuovo sito community dalla console Sites .

![multilocalesite](assets/multilocalesite.png)

Gli utenti possono selezionare le cartelle di configurazione, il branding e molte altre configurazioni contemporaneamente per tutti questi siti.

### Elimina siti della community dalla console Sites {#delete-community-sites-from-sites-console}

AEM 6.4 Communities fornisce l’icona Elimina sito sui siti della community esistenti, nella console Siti della community . Ciò abilita [eliminazione del sito](create-site.md) e gli elementi associati con un solo clic.

![siteazioni](assets/siteactions.png)

## Gestione di UGC e profili utente {#managing-ugc-and-user-profiles}

AEM Communities espone la protezione dei dati utente al centro dell’esperienza della community [API predefinite](user-ugc-management-service.md) e [servlet di esempio](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Queste API consentono di gestire in blocco i contenuti generati dagli utenti (eliminazione in blocco ed esportazione in blocco) ed eliminare i profili utente e sono fondamentali per gestire le richieste di conformità RGPD nell’UE.

## Modifiche {#what-s-changed}

* La verifica Captcha, durante la creazione di un nuovo sito della community, non è più disponibile come impostazione predefinita in AEM 6.4 Communities. Tuttavia, il sito di Communities può essere personalizzato per includere [Componente Google reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) per una maggiore sicurezza.
* L&#39;opzione per caricare un CSS personalizzato è stata rimossa dal tema dei siti e dei gruppi della community.
* Le icone Solo contenuto e Ricerca sono state aggiunte nella barra Filtro nell’interfaccia utente per la moderazione di gruppo.
* Il filtro Percorso contenuto è stato aggiunto nella barra Filtro nell’interfaccia utente per la moderazione di gruppo.
* L’opzione Passa alla modalità di massa e Esci dalla modalità di massa è stata rimossa dall’interfaccia utente di Moderazione di gruppo. Per accedere alla modalità di selezione multipla, fai clic sul pulsante Seleziona ( ![selticon](assets/selecticon.png)) su un post, che appare quando si passa il mouse sopra di esso (desktop) o si preme e si tiene premuto un dito sul post (mobile).
