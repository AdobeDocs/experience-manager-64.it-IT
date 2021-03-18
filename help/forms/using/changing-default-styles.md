---
title: Modifica degli stili predefiniti dei moduli HTML5
seo-title: Modifica degli stili predefiniti dei moduli HTML5
description: Lo stile dei moduli HTML5 è basato su CSS. È possibile modificare gli stili predefiniti del modulo.
seo-description: Lo stile dei moduli HTML5 è basato su CSS. È possibile modificare gli stili predefiniti del modulo.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Forms Mobile
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---


# Modifica degli stili predefiniti dei moduli HTML5 {#changing-default-styles-of-html-forms}

I moduli HTML5 vengono sottoposti a rendering utilizzando le funzionalità HTML5 e lo stile del modulo di cui è stato eseguito il rendering viene eseguito utilizzando i CSS. L’aspetto predefinito di un modulo HTML5 è simile al rendering PDF corrispondente. Gli sviluppatori possono utilizzare CSS personalizzati per modificare l’aspetto predefinito dei moduli HTML5.

Questo articolo fornisce informazioni dettagliate sulla modifica dello stile di un modulo HTML5 e l&#39;articolo [Introduzione agli stili](/help/forms/using/css-styles.md) contiene informazioni dettagliate sui vari aspetti dello stile dei moduli HTML5. Assicurati di aver letto Introduzione agli stili prima di eseguire i passaggi menzionati in questo articolo.

Le due immagini seguenti mostrano la differenza tra gli stili predefiniti e personalizzati.

![picture-002-small](assets/pictures-002-small.png)

## Personalizzare lo stile dei moduli {#style-your-forms}

1. **Scegliere un profilo per aggiungere stili personalizzati**

   Accedi all&#39;interfaccia CRX DE all&#39;URL: **https://&lt;server>:&lt;port>/crx/de** e crea un profilo o scegli un profilo esistente. Per informazioni su come creare un profilo, consulta [Creazione di un nuovo profilo](/help/forms/using/custom-profile.md)

1. **Creare un foglio di stile CSS per lo stile dei moduli HTML5**

   Passa alla cartella in cui hai creato il renderer del profilo e crea un file foglio di stile CSS. I passaggi da seguire sono

   1. Fai clic con il pulsante destro del mouse sulla cartella e seleziona **crea** -> **crea file** dal menu
   Per sapere quali classi CSS creare per un particolare componente nei moduli HTML5, consulta [Introduzione agli stili](/help/forms/using/css-styles.md).

1. **Includere il foglio di stile nel modulo di rendering del profilo**

   Apri la pagina Renderer di profilo (file jsp) in CRX DE e includi il file CSS nella pagina immediatamente sotto la libreria client XFA. Esegui questi passaggi per includere il file CSS nel profilo.

   1. Cerca nella pagina del renderer la seguente riga:

      &lt;cq:includeclientlib categories=&quot;xfaforms.profile&quot; />

   1. Inserire quanto segue sotto la riga precedente per includere il foglio di stile:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot; />

   1. Salva il file.

