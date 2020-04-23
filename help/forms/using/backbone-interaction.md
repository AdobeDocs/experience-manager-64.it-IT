---
title: Interazione con il dorso
seo-title: Interazione con il dorso
description: Informazioni concettuali sull'utilizzo di modelli JavaScript di base nell'area di lavoro di AEM Forms.
seo-description: Informazioni concettuali sull'utilizzo di modelli JavaScript di base nell'area di lavoro di AEM Forms.
uuid: c70da848-e514-42bc-a59b-44a7c00aa529
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: d363eec3-172b-413e-9743-ed51804ea1e9
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f

---


# Interazione con il dorso {#backbone-interaction}

Backbone è una libreria che consente di creare e seguire l&#39;architettura MVC nelle applicazioni Web. L&#39;idea di base di Backbone consiste nell&#39;organizzare l&#39;interfaccia in viste logiche, affiancate da modelli, ciascuno dei quali può essere aggiornato indipendentemente quando il modello cambia, senza dover ridisegnare la pagina. Per ulteriori informazioni sulla barra laterale, vedere [https://backbonejs.org](https://backbonejs.org/).

Alcuni concetti chiave sono i seguenti:

**Modello** backbone Contiene i dati e la maggior parte della logica correlata a tali dati.

**Vista** dorsale Utilizzata per rappresentare lo stato del modello corrispondente. Una vista dorsale si comporta come un controller, ascoltando eventi dell&#39;interfaccia utente come clic dell&#39;utente o eventi del modello (come i dati modificati) e modificando l&#39;interfaccia utente a seconda delle necessità.

**Modello** HTML Un modello di wrapper con segnaposto popolati dal modello.

**Area di lavoro** Moduli AEM Contiene diversi componenti singoli. Ciascun componente:

* Rappresenta un singolo elemento di interfaccia utente logico.
* Può essere un insieme di componenti simili.
* È costituito da un modello Backbone, una vista Backbone e un modello HTML.
* Contiene un riferimento a un servizio.
* Contiene un riferimento alle utility richieste.

Quando un componente viene inizializzato, vengono creati i seguenti oggetti:

* Viene creata una nuova istanza del modello Backbone per il componente. Il servizio è inserito nel modello.
* Viene creata una nuova istanza della vista Backbone.
* Nella vista vengono inserite le istanze del modello, del modello HTML e delle utility corrispondenti.

Nella visualizzazione Backbone è presente una mappa evento che mappa i vari eventi che possono verificarsi a causa delle interazioni dell&#39;interfaccia utente con un gestore corrispondente. Questa mappatura viene avviata una volta inizializzato un componente.

Quando una vista viene inizializzata, la vista richiama il modello corrispondente per recuperare i dati dal server. Quando tutti i dati richiesti da una visualizzazione sono disponibili, la visualizzazione esegue il rendering dei dati nel formato specificato dal modello HTML. Viste multiple possono condividere lo stesso modello per la comunicazione.

![](do-not-localize/aem_forms_workflow.png)

Esempio:

1. L&#39;utente fa clic su un modello di attività nell&#39;elenco delle attività.
1. La visualizzazione Attività ascolta il clic e richiama la funzione di rendering sul modello attività.
1. Il modello di attività richiama in seguito il servizio, che rappresenta un punto comune per tutte le comunicazioni con il server AEM Forms.
1. La classe di servizio chiama l’endpoint REST di AEM Forms per il metodo di rendering tramite ajax.
1. Il callback di riuscita per questa chiamata Ajax è definito nel modello attività.
1. Il modello di task genera un evento dorsale come notifica del completamento della chiamata di rendering.
1. Un&#39;altra visualizzazione, la visualizzazione dei dettagli dell&#39;attività, ascolta l&#39;evento dal modello dell&#39;attività.
1. La visualizzazione Dettagli attività modifica quindi il modello dei dettagli dell&#39;attività per visualizzare all&#39;utente l&#39;attività di cui è stato effettuato il rendering (modulo, dettagli, allegati, note e così via).

