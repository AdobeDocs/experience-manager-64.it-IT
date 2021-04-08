---
title: Annullare la validità di contenuti CDN memorizzati nella cache
seo-title: Annullare la validità di contenuti CDN memorizzati nella cache
description: L’annullamento della validità della rete CDN (Content Delivery Network) memorizzata nella cache consente di aggiornare rapidamente le risorse consegnate da Dynamic Media, anziché attendere la scadenza della cache.
seo-description: L’annullamento della validità della rete CDN (Content Delivery Network) memorizzata nella cache consente di aggiornare rapidamente le risorse consegnate da Dynamic Media, anziché attendere la scadenza della cache.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Gestione risorse, cache CDN
role: Administrator,Business Practitioner,Developer
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 28%

---

# Annullare la validità di contenuti CDN memorizzati nella cache {#invalidating-your-cdn-cached-content}

Le risorse Dynamic Media sono memorizzate nella cache della rete CDN per una distribuzione rapida. Tuttavia, quando apporti aggiornamenti a una risorsa, potresti voler che tali modifiche abbiano effetto immediato. L’annullamento della validità della rete CDN (Content Delivery Network) memorizzata nella cache consente di aggiornare rapidamente le risorse consegnate da Dynamic Media, anziché attendere la scadenza della cache.

Vedi anche [Panoramica sulla cache in Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Per annullare la validità del contenuto CDN memorizzato nella cache:**

1. Accedi all’applicazione desktop Dynamic Media Classic.

   [applicazione desktop Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app)

   Le credenziali e l&#39;accesso sono stati forniti da Adobe al momento del provisioning. Se non si dispone di tali informazioni, contattare il supporto tecnico.

1. Fai clic su **[!UICONTROL Configurazione > Impostazione applicazione > Impostazioni generali]**.
1. Nella pagina Impostazioni generali applicazione, sotto l&#39;intestazione del gruppo Server, individuare la casella di testo **[!UICONTROL Modello di invalidazione CDN]**.

1. Specifica il modello utilizzato per annullare la validità della cache CDN (Content Delivery Network).

   Ad esempio, supponiamo di inserire un URL immagine (inclusi predefiniti immagine o modificatori) che fa riferimento a `<ID>`, invece di un ID immagine specifico come nell&#39;esempio seguente:

   `https://server.com/is/image/Company/<ID>?$product$`

   Se il modello contiene solo `<ID>`, Dynamic Media compila `https://<server>/is/image` dove `<server>` è il nome del server di pubblicazione definito in Impostazioni generali e &lt;ID> è la risorsa o le risorse selezionate da annullare.

1. Nell&#39;angolo in basso a destra della pagina, fai clic su **[!UICONTROL Chiudi]**.
1. Nell’interfaccia utente dell’applicazione desktop Dynamic Media Classic, seleziona una o più risorse, quindi fai clic su **[!UICONTROL File > Annulla validità CDN]**. Verrà visualizzato un elenco di uno o più URL generati dal modello creato e dalle risorse selezionate. Utilizza l&#39;URL del server elencato in &quot;Nome server pubblicato&quot; nelle Impostazioni generali dell&#39;applicazione.

   Ad esempio, con il modello di annullamento validità CDN impostato nel passaggio precedente, supponi di aver selezionato una singola immagine di risorsa immagine denominata `Backpack_B`. Quando fai clic su **[!UICONTROL File > Annulla validità CDN]**, ottieni il seguente URL generato nell&#39;interfaccia utente di annullamento validità CDN:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Nella casella di riepilogo URL, fai clic su **[!UICONTROL Continua]** per cancellare la cache per ogni URL specifico. È possibile modificare un URL o aggiungere un URL digitandolo o incollandolo nella casella di riepilogo URL; non è necessario impostare prima il modello di annullamento validità CDN.

   Dopo aver fatto clic su **[!UICONTROL Continua]**, viene visualizzato un indicatore che fornisce una stima del tempo necessario per cancellare la cache.

   Se hai selezionato più risorse e poi hai selezionato **[!UICONTROL File > Annulla validità CDN]**, nell’**[!UICONTROL URL del modello]** salvato viene fatto riferimento a ciascuna risorsa. Di conseguenza, puoi definire un **[!UICONTROL Modello di annullamento validità CDN]** facendo riferimento a ciascun predefinito dell’URL immagine a cui viene fatto riferimento nel tuo sito web (ad esempio dettagli del prodotto, risultati di ricerca e così via). Quindi, quando selezioni una o più immagini della cache di cui annullare la validità, gli URL compilano automaticamente l’interfaccia.

   >[!NOTE]
   >
   >Quando selezioni le risorse e fai clic su **[!UICONTROL File > Annulla validità CDN]**, Dynamic Media utilizza un modello CDN non valido per creare automaticamente gli URL che consentano di annullare la validità dalla rete CDN (Content Delivery Network). Se nella casella di testo **[!UICONTROL Modello di annullamento validità CDN]** non è presente alcun elemento, viene visualizzato un elenco URL vuoto. La memorizzazione nella cache della rete CDN non è basata su risorse, bensì su URL. Pertanto, è necessario conoscere gli URL completi presenti sul tuo sito web. Dopo aver determinato questi URL, puoi aggiungerli alla casella di testo **[!UICONTROL Invalidate CDN Template (Annulla validità modello CDN)]** descritta nei passaggi precedenti. A questo punto puoi selezionare queste risorse e annullare la validità degli URL, tutto in un unico passaggio.
   >
   >Un&#39;altra opzione è quella di aggiungere URL completi all&#39;elenco **[!UICONTROL Annulla validità CDN]**. Se segui questo approccio, non è necessario selezionare le risorse in Dynamic Media Classic prima di passare all’opzione **[!UICONTROL File > Annulla validità CDN]** .
