---
title: Incorpora modulo adattivo in una pagina Web esterna
seo-title: Incorpora modulo adattivo in una pagina Web esterna
description: Informazioni su come incorporare un modulo adattivo in una pagina Web esterna
seo-description: Informazioni su come incorporare un modulo adattivo in una pagina Web HTML esterna
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: a3e7cd30ba6933e6f36734d3b431db41365b6e20
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---


# Incorpora modulo adattivo in una pagina Web esterna{#embed-adaptive-form-in-external-web-page}

Informazioni su come incorporare un modulo adattivo in una pagina Web esterna

Potete [incorporare un modulo adattivo nella pagina AEM Sites](/help/forms/using/embed-adaptive-form-aem-sites.md) o in una pagina Web ospitata all’esterno di AEM. Il modulo adattivo incorporato è completamente funzionante e gli utenti possono compilare e inviare il modulo senza uscire dalla pagina. Consente all&#39;utente di restare nel contesto di altri elementi della pagina Web e di interagire contemporaneamente con il modulo.

## Prerequisiti {#prerequisites}

Effettuare le seguenti operazioni prima di incorporare un modulo adattivo in un sito Web esterno:

* Pubblicate il modulo adattivo sull’istanza AEM Publish.
* Create o identificate una pagina Web nel sito Web in cui è ospitato il modulo adattivo. Verificate che la pagina Web sia in grado di [leggere i file jQuery da un CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) o che disponga di una copia locale del file jQuery incorporato. jQuery è richiesto per eseguire il rendering di un modulo adattivo.
* Quando il server AEM e la pagina Web si trovano su domini diversi, eseguite i passaggi elencati nella sezione, [abilitate i AEM Forms a distribuire moduli adattivi a un sito](#cross-domain-sites)interdominio.
* [Imposta proxy](#reveseproxy) inverso per abilitare la comunicazione tra la pagina esterna e il server AEM Forms.

## Incorpora modulo adattivo {#embed-adaptive-form}

È possibile incorporare un modulo adattivo inserendo alcune righe di JavaScript nella pagina Web. L’API nel codice invia una richiesta HTTP al server AEM per risorse di moduli adattivi e inserisce il modulo adattivo nel contenitore di moduli specificato. Di seguito è riportato un esempio di codice per incorporare un modulo adattivo in una pagina esterna. Non utilizzare il codice così come è in un ambiente di produzione. Personalizzate il codice in base alle vostre esigenze, ad esempio utilizzando un iFrame per i siti Web che utilizzano una propria versione di jQuery. L’utilizzo di iFrame consente di evitare conflitti nelle versioni jQuery:


1. Incorpora il seguente codice in una pagina Web del tuo sito Web:

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>Questo è il titolo della pagina web!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>Questa sezione viene sostituita con il modulo adattivo.</p>


    &lt;script>opzioni
    var = {percorso:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;, percorso:&quot;, CSS_Selector:&quot;.customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path) {
    // options.path fa riferimento all&#39;URL di pubblicazione dell&#39;adattivo form
    // Ad Esempio: http:myserver:4503/content/forms/af/ABC, dove ABC è il modulo
    adattivo// Nota: Se il server AEM è in esecuzione su un percorso contestuale, l’URL del modulo adattivo deve contenere il percorso
    percorso del percorso del contesto = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url : path,
    type : &quot;GET&quot;,
    dati: {
    // Impostare wcmmode su
    disablewcmmode: &quot;disabled&quot;
    // Imposta il riferimento ai dati, se presente
    // &quot;dataRef&quot;: options.dataRef
    // Specificare un tema diverso per l&#39;oggetto
    modulo// &quot;subjectOverride&quot;: options.themepath
    },
    asincrono: false,
    success: function (data) {
    // Se si carica jquery, impostare l&#39;HTML interno del contenitore
    // Se jquery non è caricata, utilizzare le API fornite dal documento per impostare l&#39;HTML interno, ma queste API non valuterebbero il tag script in HTML come da HTML5 spec
    // Ad esempio: document.getElementById().
    innerHTMLif(window).$ &amp;&amp; options.CSS_Selector){
    // HTML API di jquery estrae i tag, aggiorna il DOM e valuta il codice incorporato nel tag script.
    $(options.CSS_Selector).html(data);
    }
    },
    errore: function (data) {
    // qualsiasi gestore
    di errori}
    };
    } else {
    if (typeof(console) !== &quot;undefined&quot;) {
    console.log(&quot;Percorso del modulo adattivo non specificato per loadAdaptiveForm&quot;);
    }
    }
    }(opzioni);
    
    &lt;/script>
</body>
</html>
   ```

1. Nel codice incorporato:

   * Modificate il valore della `options.path` variabile con il percorso dell’URL di pubblicazione del modulo adattivo. Se il server AEM è in esecuzione su un percorso contestuale, accertati che l’URL includa il percorso contestuale. Ad esempio, il codice riportato sopra e l&#39;adattatore risiedono sullo stesso server di moduli AEM, pertanto nell&#39;esempio viene utilizzato il percorso contestuale del modulo adattivo /content/forms/af/locbasic.html.
   * Sostituire `options.dataRef` con gli attributi da trasmettere con l’URL. È possibile utilizzare la variabile dataref per [precompilare un modulo](/help/forms/using/prepopulate-adaptive-form-fields.md)adattivo.
   * Sostituire `options.themePath` con il percorso a un tema diverso dal tema configurato nel modulo adattivo. In alternativa, potete specificare il percorso del tema utilizzando l&#39;attributo request.
   * `CSS_Selector` è il selettore CSS del contenitore di moduli in cui è incorporato il modulo adattivo. Ad esempio, la classe css .customafsection è il selettore CSS nell&#39;esempio precedente.

Il modulo adattivo è incorporato nella pagina Web. Osservate quanto segue nel modulo adattivo incorporato:

* L&#39;intestazione e il piè di pagina del modulo adattivo originale non sono inclusi nel modulo incorporato.
* Le bozze e i moduli inviati sono disponibili nella scheda Bozze e invii del portale Forms.
* L&#39;azione di invio configurata sul modulo adattivo originale viene mantenuta nel modulo incorporato.
* Le regole dei moduli adattivi vengono mantenute e completamente funzionanti nel modulo incorporato.
* Il targeting delle esperienze e i test A/B configurati nel modulo adattivo originale non funzionano nel modulo incorporato.
* Se Adobe  Analytics è configurato sul modulo originale, i dati di analisi vengono acquisiti nel server Adobe  Analytics. Tuttavia, non è disponibile nel rapporto di analisi Moduli.

## Imposta proxy inverso  {#reveseproxy}

La pagina Web esterna che incorpora il modulo adattivo invia le richieste al server AEM, che in genere si trova dietro il firewall in una rete privata. Per garantire che le richieste siano indirizzate in modo sicuro al server AEM, si consiglia di configurare un server proxy inverso.

Vediamo un esempio di come impostare un server proxy inverso Apache 2.4 senza dispatcher. In questo esempio, ospiterai il server AEM con il percorso `/forms` contestuale e mapperai `/forms` il proxy inverso. In questo modo tutte le richieste `/forms` sul server Apache vengono indirizzate all’istanza AEM. Questa topologia consente di ridurre il numero di regole nel livello del dispatcher, poiché tutte le richieste hanno il prefisso `/forms` route al server AEM.

1. Aprite il file di `httpd.conf` configurazione e rimuovete il commento dalle seguenti righe di codice. In alternativa, è possibile aggiungere queste righe di codice nel file.

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Configurate le regole del proxy aggiungendo le seguenti righe di codice nel file di `httpd-proxy.conf` configurazione.

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Sostituisci `[AEM_Instance`] con l’URL di pubblicazione del server AEM presente nelle regole.

Se non installi il server AEM su un percorso contestuale, le regole del proxy sul livello Apache saranno le seguenti:

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Se configurate un’altra topologia, accertatevi di aggiungere gli URL di invio, precompilazione e altri URL all’elenco consentito nel livello dispatcher.

## Best practices {#best-practices}

Durante l&#39;incorporazione di un modulo adattivo in una pagina Web, tenere in considerazione le procedure ottimali seguenti:

* Assicurarsi che le regole di stile definite nella pagina Web CSS non siano in conflitto con l&#39;oggetto modulo CSS. Per evitare i conflitti, potete riutilizzare il CSS della pagina Web nel tema del modulo adattivo utilizzando la libreria client AEM. Per informazioni sull&#39;utilizzo della libreria client nei temi dei moduli adattivi, vedere [Temi in AEM Forms](/help/forms/using/themes.md).
* Per fare in modo che il contenitore del modulo nella pagina Web utilizzi l’intera larghezza della finestra. Garantisce il funzionamento delle regole CSS configurate per i dispositivi mobili senza alcuna modifica. Se il contenitore del modulo non occupa l&#39;intera larghezza della finestra, è necessario scrivere CSS personalizzato per adattare il modulo ai diversi dispositivi mobili.
* Utilizzare [getData](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API per ottenere la rappresentazione XML o JSON dei dati del modulo nel client.
* Utilizzare [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-4/forms/javascript-api/GuideBridge.html) API per scaricare il modulo adattivo dal DOM HTML.
* Configurate l’intestazione access-control-origin quando inviate la risposta dal server AEM.

## Abilitare i AEM Forms per distribuire moduli adattivi a un sito interdominio  {#cross-domain-sites}

1. Nell’istanza di creazione di AEM, andate a Gestione configurazione console Web AEM all’indirizzo `http://[server]:[port]/system/console/configMgr`.
1. Individuate e aprite la configurazione del filtro **Apache Sling Referrer** Filter.
1. Nel campo Host **** consentiti, specificate il dominio in cui risiede la pagina Web. Consente all’host di effettuare richieste POST al server AEM. È inoltre possibile utilizzare l&#39;espressione regolare per specificare una serie di domini applicazione esterni.