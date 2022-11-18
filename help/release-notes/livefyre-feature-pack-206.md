---
title: Note sulla versione di Livefyre Feature Pack 2.0.6
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Note sulla versione di Livefyre Feature Pack 2.0.6
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Note sulla versione di Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informazioni sulla versione {#release-information}

| Prodotti | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Versione | 2.0.6 |
| Tipo | Versione in funzione |
| Data | 31 agosto 2018 |
| URL di download | Contattare l&#39;amministratore |
| Compatibilità (*) | AEM 6.4 SP1, 6.4, 6.3 GA e 6.2 SP1 |
| Descrizione | Questo pacchetto ti consente di integrare le funzionalità di cura leader del settore di Livefyre con la tua istanza AEM, consentendoti di pubblicare in pochi minuti contenuti generati dagli utenti (UGC) dai social network al tuo sito. |

## Contenuto in Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Questo pacchetto integra le funzionalità di cura leader del settore di Livefyre con la tua istanza AEM, consentendoti di pubblicare in pochi minuti contenuti generati dagli utenti (UGC) dai social network al tuo sito. Il pacchetto include tre componenti diversi:

**Importare contenuti UGC in AEM Assets**

* Importa contenuti generati dagli utenti di Twitter e Instagram (UGC) da Livefyre Studio ad AEM Assets utilizzando l’importazione UGC.
* Accedi alla tua libreria Livefyre.
* Cerca in tempo reale su Twitter e Instagram utilizzando la funzione di ricerca social di Livefyre.
* Gestire i diritti sull&#39;UGC.

**Aggiungere componenti Livefyre ad AEM Sites o Communities**

* Crea e personalizza istantaneamente esperienze dinamiche e coinvolgenti utilizzando una suite di componenti social quali mappe, Gallerie e muri multimediali.
* Pubblica UGC in AEM Sites o Communities.

**Importare cataloghi di prodotti in Livefyre con AEM Commerce**

* Integra facilmente il catalogo di prodotti esistente in Livefyre per stimolare il coinvolgimento e la conversione degli utenti nei tuoi siti, nonché fornire esperienze UGC acquistabili.
* Modifica o elimina elementi nel tuo catalogo di prodotti Commerce AEM e aggiorna automaticamente le modifiche in Livefyre.

Per informazioni sull&#39;installazione, consulta [Integrazione con Livefyre](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html).

### Informazioni aggiuntive sulla versione {#additional-release-information}

A causa di aggiornamenti che influiscono sull’aggregazione di contenuti dagli account utente non aziendali di Instagram, non è più possibile pubblicare commenti per tuo conto o controllare automaticamente le risposte dell’autore. [Fai clic qui per ulteriori informazioni](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 non supporta AEM’interfaccia classica.

#### Nuova funzionalità o miglioramento {#new-feature-or-improvement}

* È stata aggiunta la possibilità di cercare UGC prima di configurare gli account social della richiesta di diritti in Livefyre. È necessario impostare account social per richiedere diritti o ignorare la richiesta di diritti se si possiede il contenuto.
* Instagram e Twitter [Flusso di lavoro della richiesta di diritti UGC](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html) è stato aggiornato per conformarsi alle API più recenti.
* Lo stato dei diritti e le azioni appropriate vengono ora visualizzati nella schermata di richiesta dei diritti.

#### Correzioni di bug {#bug-fixes}

* È stato risolto un problema che causava un errore durante il caricamento della libreria UGC in AEM l’eliminazione di un account social in Livefyre Studio utilizzato per la richiesta di diritti.
* È stato risolto un problema a causa del quale il conteggio delle risorse nello studio Livefyre non corrispondeva al conteggio delle risorse nella libreria UGC AEM.
* È stato risolto un problema nella libreria UGC a causa del quale i risultati filtrati venivano visualizzati dopo la reimpostazione delle opzioni del filtro.
* È stato risolto un problema relativo a Commerce a causa del quale i pulsanti di chiamata all’azione reindirizzavano gli utenti all’URL errato.
* È stato risolto un problema in AEM Sites a causa del quale il trascinamento e il rilascio di più componenti nel segnaposto parsys causava la sua scomparsa.
* È stato risolto un problema a causa del quale gli account social disabilitati erano disponibili per la selezione durante l’invio di una richiesta di diritti.
* È stato risolto un problema che causava un errore durante il trascinamento e il rilascio di UGC da Assets in Sites.
* È stato risolto un problema a causa del quale il trascinamento e il rilascio dei componenti Chat e Liveblog in Sites non creava l’app.
* È stato risolto un problema che causava un errore durante il tentativo di commento da parte degli utenti.
* È stato risolto un problema che causava la creazione di un nodo aggiuntivo nell’archivio dei contenuti Java quando si aggiungeva l’app Livefyre Media Wall a un sito.
* È stato risolto un problema che causava interruzioni di pagina ed errori di console nella ricerca UGC di Instagram.
* È stato risolto un problema a causa del quale le icone utente di Instagram generavano errori API in Assets.
* È stato risolto un problema che causava l’aggiunta dell’app Revisioni a un sito senza formato predefinito.
* È stato risolto un problema relativo alla funzionalità Touch UI e alla modifica in linea.
* È stato risolto un problema che causava un errore durante l’importazione di alcune risorse di immagini Instagram.
* È stato risolto un problema a causa del quale il client HTTP Livefyre in AEM non supportava la configurazione proxy.
