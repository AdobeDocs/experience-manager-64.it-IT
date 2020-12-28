---
title: Note sulla versione di Livefyre Feature Pack 2.0.6
seo-title: Note sulla versione di Livefyre Feature Pack 2.0.6
description: Note sulla versione di Livefyre Feature Pack 2.0.6
seo-description: Note sulla versione di Livefyre Feature Pack 2.0.6
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Note sulla versione di Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informazioni sulla versione {#release-information}

| Prodotti | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Versione | 2.0.6 |
| Tipo | Release delle funzioni |
| Data | 31 agosto 2018 |
| URL di download | Contattare l&#39;amministratore |
| Compatibilità (*) | AEM 6.4 SP1, 6.4, 6.3 GA e 6.2 SP1 |
| Descrizione | Questo pacchetto consente di integrare le funzionalità di cura leader del settore di Livefyre con l&#39;istanza AEM, consentendo di pubblicare in pochi minuti contenuti generati dagli utenti (UGC) dai social network al sito. |

## Contenuto in Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Questo pacchetto integra le funzionalità di cura leader del settore di Livefyre con l&#39;istanza AEM, consentendo di pubblicare in pochi minuti contenuti generati dagli utenti (UGC) dai social network al sito. Il pacchetto include tre componenti diversi:

**Importare contenuti UGC in  AEM Assets**

* Importate contenuti generati dagli utenti di Twitter e Instagram (UGC) da Livefyre Studio a  AEM Assets tramite UGC Importer.
* Accedete alla libreria Livefyre.
* Effettuate ricerche in tempo reale su Twitter e Instagram tramite Livefyre Social Search.
* Gestire i diritti sull’UGC.

**Aggiungere componenti Livefyre a  AEM Sites o Communities**

* Crea e personalizza all&#39;istante esperienze dinamiche e coinvolgenti utilizzando una suite di componenti Social, tra cui mappe, Gallerie e muri multimediali.
* Pubblicare UGC in  AEM Sites o Communities.

**Importazione di cataloghi di prodotti in Livefyre con AEM Commerce**

* Integrate perfettamente il catalogo di prodotti esistente in Livefyre per stimolare il coinvolgimento e la conversione degli utenti nei vostri siti, oltre a fornire esperienze UGC acquistabili.
* Modificate o eliminate elementi nel catalogo prodotti di AEM Commerce e aggiornate automaticamente le modifiche in Livefyre.

Per informazioni sull&#39;installazione, consultate [Integrazione con Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Informazioni aggiuntive sulla versione {#additional-release-information}

A causa di aggiornamenti che influiscono sull&#39;aggregazione di contenuto dagli account utente non business di Instagram, non è più possibile pubblicare commenti per conto dell&#39;utente o verificare automaticamente la presenza di risposte dall&#39;autore. [Fai clic qui per saperne di più](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 non supporta AEM interfaccia classica.

#### Nuova funzionalità o miglioramento {#new-feature-or-improvement}

* Aggiunta la possibilità di effettuare ricerche UGC prima di configurare gli account social delle richieste di diritti in Livefyre. Per richiedere i diritti, dovete impostare gli account social o ignorare la richiesta di diritti se siete proprietari del contenuto.
* Instagram e Twitter [Flusso di lavoro della richiesta di diritti UGC](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) è stato aggiornato per conformarsi alle API più recenti.
* Lo stato dei diritti e le azioni appropriate vengono ora visualizzati nella schermata di richiesta dei diritti.

#### Correzioni di bug {#bug-fixes}

* È stato risolto un problema che causava un errore durante il caricamento della libreria UGC in AEM quando si eliminava un account social in Livefyre Studio utilizzato per la richiesta di diritti.
* È stato risolto un problema per cui il conteggio delle risorse nello studio Livefyre non corrispondeva al conteggio delle risorse nella libreria AEM UGC.
* È stato risolto un problema nella libreria UGC a causa del quale i risultati filtrati venivano visualizzati dopo la reimpostazione delle opzioni filtro.
* È stato risolto un problema con AEM Commerce a causa del quale i pulsanti call-to-action reindirizzavano gli utenti all&#39;URL errato.
* È stato risolto un problema in  AEM Sites a causa del quale il trascinamento di più componenti nel segnaposto parsys causava la scomparsa di tale componente.
* È stato corretto un problema a causa del quale gli account social disabilitati erano disponibili per la selezione al momento dell&#39;invio di una richiesta di diritti.
* È stato risolto un problema che causava un errore durante il trascinamento di UGC da Assets a Sites.
* È stato risolto un problema a causa del quale il trascinamento e il rilascio dei componenti Chat e Liveblog in Sites non creava l&#39;app.
* È stato risolto un problema che causava un errore nell&#39;app dei commenti quando gli utenti tentavano di aggiungere commenti.
* È stato risolto un problema a causa del quale l&#39;aggiunta dell&#39;app Livefyre Media Wall a un sito creava un nodo aggiuntivo nell&#39;archivio dei contenuti Java.
* È stato risolto un problema che causava interruzioni di pagina ed errori di console nella ricerca UGC di Instagram.
* È stato risolto un problema che causava errori API nelle risorse a causa del quale le icone utente di Instagram generavano errori nelle risorse.
* È stato risolto un problema che causava l&#39;aggiunta dell&#39;app Revisioni a un sito senza formato predefinito.
* È stato risolto un problema relativo alla funzionalità dell&#39;interfaccia utente touch e alla modifica in linea.
* È stato risolto un problema che causava un errore durante l&#39;importazione di determinate risorse di immagini Instagram.
* È stato risolto un problema per il quale il client Livefyre HTTP in AEM non supportava la configurazione proxy.
