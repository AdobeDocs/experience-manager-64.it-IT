---
title: Funzionalità Contenuto
seo-title: Funzionalità Contenuto
description: 'La funzione Contenuto in evidenza consente ai visitatori del sito che hanno effettuato l’accesso di evidenziare i contenuti '
seo-description: 'La funzione Contenuto in evidenza consente ai visitatori del sito che hanno effettuato l’accesso di evidenziare i contenuti '
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
translation-type: tm+mt
source-git-commit: 1bbd917ef20c4a618e93af66ffe8a6cfc8448e78
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 5%

---


# Funzionalità contenuto in evidenza {#featured-content-feature}

## Introduzione {#introduction}

La funzione di contenuto disponibile fornisce un&#39;area per i visitatori del sito che hanno effettuato l&#39;accesso (membri della community) nell&#39;ambiente di pubblicazione per evidenziare i contenuti per

* [Blog](blog-feature.md)
* [Calendari](calendar.md)
* [Forum](forum.md)
* [Idee](ideation-feature.md)
* [D/R](working-with-qna.md)

Una volta che il contenuto è contrassegnato come disponibile, verrà elencato all&#39;interno di questo componente, che può essere posizionato in pagine di destinazione o aree specifiche che catturano facilmente l&#39;attenzione dei membri della community.

La possibilità di visualizzare il contenuto può essere consentita o disabilitata per ciascun componente.

Questa sezione della documentazione descrive

* Aggiunta di contenuti contenuti a un sito community
* Impostazioni di configurazione per il componente `Featured Content`

## Aggiunta di contenuti contenuti contenuti a una pagina {#adding-featured-content-to-a-page}

Per aggiungere un componente `Featured Content` a una pagina in modalità di creazione, usate il browser componenti per individuare

* `Communities / Featured Content`

trascinatelo nella posizione desiderata su una pagina in cui deve comparire il contenuto in primo piano.

Per le informazioni necessarie, visitare [Community Components Basics](basics.md).

Quando sono incluse le [librerie lato client ](essentials-featured.md#essentials-for-client-side), viene visualizzato il componente `Featured Content`seguente:

![chlimage_1-13](assets/chlimage_1-13.png)

## Configurazione del contenuto disponibile {#configuring-featured-content}

Selezionare il componente `Featured Content` inserito a cui accedere e selezionare l&#39;icona `Configure` che apre la finestra di dialogo di modifica.

![chlimage_1-14](assets/chlimage_1-14.png) ![chlimage_1-15](assets/chlimage_1-15.png)

### Scheda Impostazioni {#settings-tab}

Nella scheda **[!UICONTROL Impostazioni]**, identificate il contenuto da includere:

* **[!UICONTROL Nome visualizzatoTitolo dell’elenco del contenuto disponibile.]**
Esempio 
`Featured Questions` o `Featured Ideas`. Il valore predefinito è `Featured Content` se lasciato vuoto.

* **[!UICONTROL Posizione del contenuto in primo piano]**

   *(Obbligatorio)* Individuate la pagina contenente il contenuto che potrebbe essere una funzione (i componenti di tale pagina devono essere configurati per Consenti contenuto disponibile). Esempio, `/content/sites/engage/en/forum`

* **[!UICONTROL Visualizzazione]**
limite: il numero massimo di contenuti contenuti da visualizzare. Il valore predefinito è 5.

## Esperienza visitatori del sito {#site-visitor-experience}

La capacità di contrassegnare il contenuto come contenuto in primo piano richiede privilegi di moderatore.

Quando un moderatore visualizza il contenuto pubblicato, ha accesso ai flag di moderazione contestuale, che includono il nuovo flag `Feature`.

![chlimage_1-16](assets/chlimage_1-16.png)

Una volta contrassegnata come feature, il flag di modem diventa `Unfeature`.

La pagina contenente il componente `Featured Content` ora includerà questo post.

![chlimage_1-17](assets/chlimage_1-17.png)

`Read More` è un collegamento al post effettivo.

## Informazioni aggiuntive {#additional-information}

Ulteriori informazioni sono disponibili nella pagina [Contenuto in evidenza](essentials-featured.md) per gli sviluppatori.

Per contrassegnare i contenuti come disponibili, consultate [Moderating User Generated Content](moderate-ugc.md) (Contenuto generato dall&#39;utente).
