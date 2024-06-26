---
title: Sviluppo con SAP Commerce Cloud
seo-title: Developing with SAP Commerce Cloud
description: Il framework di integrazione SAP Commerce Cloud include un livello di integrazione con un’API
seo-description: The SAP Commerce Cloud integration framework includes an integration layer with an API
uuid: a780dd17-027a-4a61-af8f-3e2f600524c7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 96dc0c1a-b21d-480a-addf-c3d0348bd3ad
exl-id: fa5b9b61-7dba-42e0-8fbd-4a96617569d8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2346'
ht-degree: 1%

---

# Sviluppo con SAP Commerce Cloud{#developing-with-sap-commerce-cloud}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Il framework eCommerce può essere utilizzato con qualsiasi soluzione eCommerce. Talune specifiche e alcuni esempi trattati in questa sede si riferiscono alla [ibrido](https://www.hybris.com/) soluzione.

Il framework di integrazione include un livello di integrazione con un’API. Questo consente di:

* plug-in di un sistema eCommerce ed estrarre i dati dei prodotti in AEM
* creazione di componenti AEM per funzionalità commerce indipendenti dallo specifico motore di eCommerce

![chlimage_1-11](assets/chlimage_1-11.png)

>[!NOTE]
>
>[Documentazione API](/help/sites-developing/ecommerce.md#api-documentation) è disponibile anche.

Per utilizzare il livello di integrazione, sono disponibili diversi componenti AEM pronti all’uso. Attualmente questi sono:

* un componente di visualizzazione del prodotto
* un carrello
* check-out

Per la ricerca viene fornito un hook di integrazione che consente di utilizzare la ricerca AEM, la ricerca del sistema eCommerce, una ricerca di terze parti o una combinazione di esso.

## Selezione del motore di eCommerce {#ecommerce-engine-selection}

Il framework eCommerce può essere utilizzato con qualsiasi soluzione eCommerce; il motore utilizzato deve essere identificabile da AEM:

* I motori eCommerce sono servizi OSGi che supportano i `CommerceService` interfaccia

   * I motori possono essere distinti da un `commerceProvider` proprietà del servizio

* Supporti AEM `Resource.adaptTo()` per `CommerceService` e `Product`

   * La `adaptTo` l’implementazione cerca un `cq:commerceProvider` nella gerarchia della risorsa:

      * Se trovato, il valore viene utilizzato per filtrare la ricerca del servizio commerce.
      * Se non viene trovato, viene utilizzato il servizio di e-commerce più alto.
   * A `cq:Commerce` mixin viene utilizzato in modo che il `cq:commerceProvider` può essere aggiunto alle risorse fortemente tipizzate.


* La `cq:commerceProvider` viene utilizzata anche per fare riferimento alla definizione appropriata di commerce factory.

   * Ad esempio, un `cq:commerceProvider` con il valore `hybris` sarà correlata alla configurazione OSGi per **Day CQ Commerce Factory per Hybris** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory) - dove il parametro `commerceProvider` ha anche il valore `hybris`.

   * Ulteriori proprietà, ad esempio **Versione catalogo** può essere configurato (se appropriato e disponibile).

Vedi i seguenti esempi:

| `cq:commerceProvider = geometrixx` | in un impianto AEM standard è necessaria un’implementazione specifica; ad esempio, l&#39;esempio geometrixx, che include estensioni minime per l&#39;API generica |
|---|---|
| `cq:commerceProvider = hybris` | implementazione di hybris |

### Esempio {#example}

```shell
/content/store 
+ cq:commerceProvider = hybris 
  + mens 
    + polo-shirt-1 
    + polo-shirt-2 
    + employee 
+ cq:commerceProvider = jcr 
  + adobe-logo-shirt 
    + cq:commerceType = product 
    + price = 12.50 
  + adobe-logo-shirt_S 
    + cq:commerceType = variant 
    + size = S 
  + adobe-logo-shirt_XL 
    + cq:commerceType = variant 
    + size = XL 
    + price = 14.50
```

>[!NOTE]
>
>Utilizzando CRXDE Lite puoi vedere come viene gestito il componente prodotto per l’implementazione di hybris:
>
>`/apps/geometrixx-outdoors/components/hybris/product/product.jsp`

### Sviluppo per hybris 4 {#developing-for-hybris}

L&#39;estensione hybris di eCommerce Integration Framework è stata aggiornata per supportare Hybris 5, mantenendo al tempo stesso la compatibilità con le versioni precedenti di Hybris 4.

Le impostazioni predefinite nel codice vengono regolate per Hybris 5.

Per sviluppare per Hybris 4 è necessario quanto segue:

* Quando si richiama maven, aggiungere al comando il seguente argomento della riga di comando

   `-P hybris4`

   Scarica la distribuzione preconfigurata di Hybris 4 e la incorpora nel bundle:

   ```
   cq-commerce-hybris-server
   ```

* Nel gestore di configurazione OSGi:

   * Disattiva il supporto di Hybris 5 per il servizio Parser di risposta predefinito.
   * Assicurati che il servizio Hybris Basic Authentication Handler abbia una classificazione di servizio inferiore rispetto al servizio Hybris OAuth Handler.

### Gestione delle sessioni {#session-handling}

hybris utilizza una sessione utente per memorizzare informazioni come il carrello del cliente. L&#39;id della sessione viene restituito da hybris in un `JSESSIONID` cookie da inviare in caso di richieste successive ad hybris. Per evitare di memorizzare l’ID sessione nell’archivio, viene codificato in un altro cookie memorizzato nel browser dell’acquirente. Vengono eseguiti i seguenti passaggi:

* Sulla prima richiesta non è impostato alcun cookie sulla richiesta dell&#39;acquirente; viene quindi inviata una richiesta all&#39;istanza hybris per creare una sessione.
* I cookie di sessione vengono estratti dalla risposta, codificati in un nuovo cookie (ad esempio, `hybris-session-rest`) e imposta la risposta all&#39;acquirente. La codifica in un nuovo cookie è necessaria, perché il cookie originale è valido solo per un determinato percorso e in caso contrario non verrebbe inviato nuovamente dal browser nelle richieste successive. Le informazioni sul percorso devono essere aggiunte anche al valore del cookie.
* Nelle richieste successive, i cookie vengono decodificati dal `hybris-session-<*xxx*>` cookie e impostati sul client HTTP utilizzato per richiedere dati da hybris.

>[!NOTE]
>
>Viene creata una nuova sessione anonima quando la sessione originale non è più valida.

#### CommerceSession {#commercesession}

* Questa sessione &quot;possiede&quot; il **carrello**

   * esegue add/remove/etc
   * esegue i vari calcoli sul carrello;

      `commerceSession.getProductPrice(Product product)`

* Possiede *posizione di archiviazione* per **ordine** dati

   `CommerceSession.getUserContext()`

* Possiede anche **pagamento** connessione di elaborazione
* Possiede anche **realizzazione** connection

### Sincronizzazione e pubblicazione dei prodotti {#product-synchronization-and-publishing}

I dati di prodotto mantenuti in hybris devono essere disponibili in AEM. È stato attuato il seguente meccanismo:

* Un caricamento iniziale degli ID viene fornito da hybris come feed. Ci possono essere aggiornamenti a questo feed.
* hybris fornirà informazioni aggiornate tramite un feed (che AEM sondaggi).
* Quando AEM utilizza i dati di prodotto, invia le richieste ad hybris per i dati correnti (richiesta di acquisizione condizionale utilizzando l’ultima data di modifica).
* Su hybris è possibile specificare il contenuto di feed in modo dichiarativo.
* La mappatura della struttura del feed sul modello di contenuto AEM avviene nella scheda di feed sul lato AEM.

![chlimage_1-12](assets/chlimage_1-12.png)

* L’importazione (b) viene utilizzata per la configurazione iniziale della struttura ad albero della pagina in AEM per i cataloghi.
* Le modifiche al catalogo in hybris sono indicate per AEM tramite un feed, che poi si propagano a AEM b)

   * Prodotto aggiunto/eliminato/modificato rispetto alla versione del catalogo.
   * Prodotto approvato.

* L&#39;estensione hybris fornisce un importatore di polling (&quot;schema hybris&quot;), che può essere configurato per importare le modifiche in AEM a un intervallo specificato (ad esempio, ogni 24 ore in cui l&#39;intervallo è specificato in secondi):

   ```
     http://localhost:4502/content/geometrixx-outdoors/en_US/jcr:content.json
      {
      * "jcr:mixinTypes": ["cq:PollConfig"],
      * "enabled": true,
      * "source": "hybris:outdoors",
      * "jcr:primaryType": "cq:PageContent",
      * "interval": 86400
      }
   ```

* La configurazione del catalogo in AEM riconosce **Staging** e **Online** versioni catalogo.

* La sincronizzazione dei prodotti tra le versioni del catalogo richiederà una (de-)attivazione della pagina di AEM corrispondente (a, c)

   * Aggiunta di un prodotto a un **Online** la versione di catalogo richiede l’attivazione della pagina del prodotto.
   * La rimozione di un prodotto richiede la disattivazione.

* L’attivazione di una pagina in AEM (c) richiede un controllo (b) ed è possibile solo se

   * Il prodotto si trova in un **Online** versione catalogo per le pagine di prodotto.
   * I prodotti di riferimento sono disponibili in un **Online** versione di catalogo per altre pagine (ad esempio pagine di campagna).

* Le pagine di prodotto attivate devono accedere ai dati del prodotto **Online** versione d).

* L&#39;istanza di pubblicazione AEM richiede l&#39;accesso ad hybris per il recupero di dati personalizzati e di prodotti (d).

### Architettura {#architecture}

#### Architettura di prodotti e varianti {#architecture-of-product-and-variants}

Un singolo prodotto può presentare più varianti; ad esempio, potrebbe variare a seconda del colore e/o della dimensione. Un prodotto deve definire quali proprietà determinano la variazione; li chiamiamo *assi variabili*.

Tuttavia, non tutte le proprietà sono assi variabili. Le varianti possono influenzare anche altre proprietà; ad esempio, il prezzo potrebbe dipendere dalle dimensioni. Queste proprietà non possono essere selezionate dall&#39;acquirente e quindi non sono considerate assi di variante.

Ogni prodotto e/o variante è rappresentato da una risorsa e pertanto viene mappato 1:1 su un nodo di archivio. È un corollario che un prodotto e/o variante specifico possa essere identificato in modo univoco dal suo percorso.

La risorsa prodotto/variante non contiene sempre i dati effettivi del prodotto. Potrebbe trattarsi di una rappresentazione dei dati effettivamente conservati su un altro sistema (ad esempio gli ibridi). Ad esempio, le descrizioni dei prodotti, i prezzi e così via non vengono memorizzati in AEM, ma recuperati in tempo reale dal motore eCommerce.

Qualsiasi risorsa di prodotto può essere rappresentata da un `Product API`. La maggior parte delle chiamate nell&#39;API del prodotto sono specifiche per le varianti (anche se le varianti potrebbero ereditare valori condivisi da un predecessore), ma ci sono anche chiamate che elencano il set di varianti ( `getVariantAxes()`, `getVariants()`, ecc.).

>[!NOTE]
>
>In effetti, un asse di variante è determinato da qualsiasi `Product.getVariantAxes()` restituisce:
>
>* hybris lo definisce per l&#39;implementazione dell&#39;hybris
>
>Mentre i prodotti (in generale) possono avere molti assi di variante, il componente di prodotto preconfigurato gestisce solo due elementi:
>
>1. `size`
>
>1. più uno

>
>   Questa variante aggiuntiva viene selezionata tramite la variabile `variationAxis` proprietà del riferimento del prodotto (di solito `color` per Geometrixx Outdoors).

#### Riferimenti prodotto e dati prodotto {#product-references-and-product-data}

In generale:

* i dati del prodotto si trovano in `/etc`

* e i riferimenti dei prodotti di cui `/content`.

Deve essere presente una mappa 1:1 tra le varianti di prodotto e i nodi di dati di prodotto.

I riferimenti al prodotto devono avere anche un nodo per ogni variante presentata - ma non è necessario presentare tutte le varianti. Ad esempio, se un prodotto presenta varianti S, M, L, i dati del prodotto potrebbero essere:

```shell
etc
  commerce
    products
      shirt
        shirt-s
        shirt-m
        shirt-l
```

Mentre un catalogo &quot;Grande e alto&quot; potrebbe avere solo:

```shell
content
  big-and-tall
    shirt
      shirt-l
```

Infine, non vi è alcun obbligo di utilizzare i dati dei prodotti. È possibile inserire tutti i dati di prodotto sotto i riferimenti nel catalogo; ma non puoi avere più cataloghi senza duplicare tutti i dati dei prodotti.

**API**

#### com.adobe.cq.com Interfaccia di Commerce.api.Product {#com-adobe-cq-commerce-api-product-interface}

```java
public interface Product extends Adaptable {

    public String getPath();            // path to specific variation
    public String getPagePath();        // path to presentation page for all variations
    public String getSKU();             // unique ID of specific variation

    public String getTitle();           // shortcut to getProperty(TITLE)
    public String getDescription();     // shortcut to getProperty(DESCRIPTION)
    public String getImageUrl();        // shortcut to getProperty(IMAGE_URL)
    public String getThumbnailUrl();    // shortcut to getProperty(THUMBNAIL_URL)

    public <T> T getProperty(String name, Class<T> type);

    public Iterator<String> getVariantAxes();
    public boolean axisIsVariant(String axis);
    public Iterator<Product> getVariants(VariantFilter filter) throws CommerceException;
}
```

#### com.adobe.cq.commerce.api.VariantFilter  {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * e.g. when using {@link Product#getVariants(VariantFilter filter)}.
 */
public interface VariantFilter {
    public boolean includes(Product product);
}

/**
 * A {@link VariantFilter} for filtering variants by the given
 * axis and value. The following example returns a list of
 * variant products that have a value of <i>blue</i> on the
 * <i>color</i> axis.
 * 
 * <p>
 * <code>product.getVariants(new AxisFilter("color", "blue"));</code>
 */
public class AxisFilter implements VariantFilter {

    private String axis;
    private String value;

    public AxisFilter(String axis, String value) {
        this.axis = axis;
        this.value = value;
    }

    /**
     * {@inheritDoc}
     */
    public boolean includes(Product product) {
        ValueMap values = product.adaptTo(ValueMap.class);

        if(values != null) {
            String v = values.get(axis, String.class);

            return v != null && v == value;
        }

        return false;
    }
}
```

* **Meccanismo generale di stoccaggio**

   * I nodi di prodotto non sono:non strutturati.
   * Un nodo di prodotto può essere:

      * Un riferimento con i dati dei prodotti memorizzati altrove:

         * I riferimenti di prodotto contengono un `productData` , che fa riferimento ai dati del prodotto (in genere in `/etc/commerce/products`).
         * I dati del prodotto sono gerarchici; gli attributi di prodotto vengono ereditati dagli predecessori di un nodo di dati di prodotto.
         * I riferimenti ai prodotti possono anche contenere proprietà locali, che sovrascrivono quelle specificate nei relativi dati di prodotto.
      * Un prodotto:

         * Senza un `productData` proprietà.
         * Un nodo di prodotto che contiene tutte le proprietà localmente (e non contiene una proprietà productData) eredita gli attributi di prodotto direttamente dai propri predecessori.


* **Struttura del prodotto AEM-generico**

   * Ogni variante deve avere un proprio nodo foglia.
   * L’interfaccia del prodotto rappresenta sia i prodotti che le varianti, ma il nodo di archivio correlato è specifico a riguardo.
   * Il nodo prodotto descrive gli attributi del prodotto e gli assi delle varianti.

#### Esempio {#example-1}

```shell
+ banyan_shirt
    - cq:commerceType = product
    - cq:productAttributes = [jcr:title, jcr:description, size, price, color]
    - cq:productVariantAxes = [color, size]
    - jcr:title = Banyan Shirt
    - jcr:description = Flowery, all-cotton shirt.
    - price = 14.00
    + banyan_shirt_s
        - cq:commerceType = variant
        - size = S
        + banyan_shirt_s_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_s_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_m
        - cq:commerceType = variant
        - size = M
        + banyan_shirt_m_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_m_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_l
        - cq:commerceType = variant
        - size = L
        + banyan_shirt_l_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_l_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_xl
        - cq:commerceType = variant
        - size = XL
        - price = 18.00
```

#### Architettura del carrello {#architecture-of-the-shopping-cart}

**Componenti**

* Il carrello è di proprietà della `CommerceSession:`

   * La `CommerceSession` esegue add/remove/etc.
   * La `CommerceSession` esegue anche i vari calcoli sul carrello. &quot;

* Anche se non direttamente correlati al carrello, il `CommerceSession` deve anche fornire informazioni sui prezzi di catalogo (dal momento che possiede i prezzi)

   * I prezzi possono avere diversi modificatori:

      * Sconti sulla quantità.
      * Valute diverse.
      * IVA soggetta e IVA esente.
   * I modificatori sono completamente aperti con la seguente interfaccia:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`


**Archiviazione**

* Archiviazione

   * Nel caso dell&#39;hybris, il server hybris è proprietario del carrello.
   * Nel caso AEM-generico i carrelli di sono memorizzati nel [ClientContext](/help/sites-administering/client-context.md).

**Personalizzazione**

* La personalizzazione deve sempre essere guidata attraverso [ClientContext](/help/sites-administering/client-context.md).
* Un ClientContext `/version/` del carrello viene creato in tutti i casi:

   * I prodotti devono essere aggiunti utilizzando la variabile `CommerceSession.addCartEntry()` metodo .

* Di seguito è riportato un esempio di informazioni sul carrello nel carrello del ClientContext:

![chlimage_1-13](assets/chlimage_1-13.png)

#### Architettura del checkout {#architecture-of-checkout}

**Dati carrello e ordine**

La `CommerceSession` possiede i tre elementi seguenti:

1. Contenuto del carrello
1. Prezzi
1. Dettagli dell&#39;ordine

1. **Contenuto del carrello**

   Lo schema del contenuto del carrello è fisso dall’API:

   ```java
       public void addCartEntry(Product product, int quantity);
       public void modifyCartEntry(int entryNumber, int quantity);
       public void deleteCartEntry(int entryNumber);
   ```

1. **Prezzi**

   Lo schema tariffario viene inoltre corretto dall’API:

   ```java
       public String getCartPreTaxPrice();
       public String getCartTax();
       public String getCartTotalPrice();
       public String getOrderShipping();
       public String getOrderTotalTax();
       public String getOrderTotalPrice();
   ```

1. **Dettagli ordine**

   Tuttavia, i dettagli dell’ordine sono *not* corretto dall’API:

   ```java
       public void updateOrderDetails(Map<String, String> orderDetails);
       public Map<String, String> getOrderDetails();
       public void submitOrder();
   ```

**Calcoli di spedizione**

* I moduli di ordine spesso devono presentare più opzioni di spedizione (e prezzi).
* I prezzi possono essere basati su articoli e dettagli dell&#39;ordine, quali peso e/o indirizzo di consegna.
* La `CommerceSession` ha accesso a tutte le dipendenze, in modo che possa essere trattato in modo simile al prezzo del prodotto:

   * La `CommerceSession` possiede i prezzi di spedizione.
   * Può recuperare/aggiornare i dettagli di consegna utilizzando `updateOrder(Map<String, Object> delta)`

>[!NOTE]
>
>Puoi implementare un selettore di spedizione; ad esempio:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* Essenzialmente questa potrebbe essere una copia di `foundation/components/form/radio`, ma con callback al `CommerceSession` per:
>
>* Verifica della disponibilità del metodo
>* Aggiunta di informazioni sui prezzi
>* Per consentire agli acquirenti di aggiornare la pagina dell&#39;ordine in AEM (compreso il superset di metodi di spedizione e il testo che li descrive), pur mantenendo il controllo per esporre il pertinente `CommerceSession` informazioni.


**Elaborazione dei pagamenti**

* La `CommerceSession` possiede anche la connessione di elaborazione del pagamento.
* Gli esecutori devono aggiungere chiamate specifiche (al servizio di elaborazione dei pagamenti scelto) al `CommerceSession` implementazione.

**evasione ordine**

* La `CommerceSession` possiede anche la connessione di evasione.
* Gli esecutori dovranno aggiungere chiamate specifiche (al servizio di elaborazione dei pagamenti scelto) al `CommerceSession` implementazione.

### Definizione ricerca {#search-definition}

Seguendo il modello API di servizio standard, il progetto eCommerce fornisce un set di API relative alla ricerca che possono essere implementate dai singoli motori di e-commerce.

>[!NOTE]
>
>Attualmente, solo il motore ibrido implementa l’API di ricerca preconfigurata.
>
>Tuttavia, l’API di ricerca è generica e può essere implementata singolarmente da ogni CommerceService.

Il progetto eCommerce contiene un componente di ricerca predefinito, che si trova in:

`/libs/commerce/components/search`

![chlimage_1-14](assets/chlimage_1-14.png)

In questo modo si utilizza l’API di ricerca per eseguire una query sul motore di e-commerce selezionato (vedi [Selezione del motore di eCommerce](#ecommerce-engine-selection)):

#### API di ricerca {#search-api}

Il progetto principale prevede diverse classi generiche / helper:

1. `CommerceQuery`

   Viene utilizzato per descrivere una query di ricerca (contiene informazioni sul testo della query, sulla pagina corrente, sulle dimensioni della pagina, sull’ordinamento e sui facet selezionati). Tutti i servizi eCommerce che implementano l’API di ricerca riceveranno istanze di questa classe per eseguire la ricerca. A `CommerceQuery` può essere creata un&#39;istanza da un oggetto di richiesta ( `HttpServletRequest`).

1. `FacetParamHelper`

   È una classe di utilità che fornisce un metodo statico: `toParams` - utilizzato per la generazione `GET` stringhe di parametri da un elenco di facet e un valore attivato. Questa funzione è utile sul lato dell’interfaccia utente, in cui è necessario visualizzare un collegamento ipertestuale per ogni valore di ciascun facet, in modo che quando l’utente fa clic sul collegamento ipertestuale il relativo valore venga attivato (ovvero, se è stato selezionato, viene rimosso dalla query, altrimenti aggiunto). Questo si occupa di tutte le logiche di gestione di facet con più/singoli valori, valori di override, ecc.

Il punto di ingresso per l’API di ricerca è il `CommerceService#search` metodo che restituisce un `CommerceResult` oggetto. Consulta la sezione [Documentazione API](/help/sites-developing/ecommerce.md#api-documentation) per ulteriori informazioni su questo argomento.

### Integrazione utente {#user-integration}

L’integrazione viene fornita tra AEM e diversi sistemi eCommerce. Ciò richiede una strategia per la sincronizzazione degli acquirenti tra i vari sistemi in modo che il codice specifico AEM debba conoscere solo AEM e viceversa:

* Autenticazione

   Si presume che AEM sia il *only* web front-end e quindi esegue *tutto* autenticazione.

* Conti in Hybris

   AEM un account corrispondente (subordinato) in hybris per ogni acquirente. Il nome utente di questo account è lo stesso del nome utente AEM. Una password crittografata casuale viene generata automaticamente e memorizzata (cifrata) in AEM.

#### Utenti preesistenti {#pre-existing-users}

Un front-end AEM può essere posizionato davanti a un&#39;implementazione ibrida esistente. È inoltre possibile aggiungere un motore ibrido a un&#39;installazione AEM esistente. A tal fine, i sistemi devono essere in grado di gestire correttamente gli utenti esistenti in entrambi i sistemi:

* AEM -> hybris

   * Quando accedi a hybris, se l&#39;utente AEM non esiste già:

      * creare un nuovo utente hybris con una password crittografata casuale
      * memorizza il nome utente hybris nella directory utente dell&#39;utente AEM
   * Consulta: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`


* hybris -> AEM

   * Quando accedi a AEM, se il sistema riconosce l&#39;utente:

      * tentativo di accesso a hybris con nome utente/pwd in dotazione
      * in caso di esito positivo, crea il nuovo utente in AEM con la stessa password (il valore di sale specifico per AEM risulterà in hash specifici per AEM)
   * L’algoritmo di cui sopra è implementato in uno Sling `AuthenticationInfoPostProcessor`

      * Consulta: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`


### Personalizzazione del processo di importazione {#customizing-the-import-process}

Per sfruttare le funzionalità esistenti del tuo gestore di importazione personalizzato:

* deve implementare `ImportHandler` interfaccia

* può estendere `DefaultImportHandler`

```java
/**
 * Services implementing the <code>ImportHandler</code> interface are
 * called by the {@link HybrisImporter} to create actual commerce entities
 * such as products.
 */
public interface ImportHandler {

    /**
     * Not used.
     */
    public void createTaxonomie(ImporterContext ctx);

    /**
     * Creates a catalog with the given name.
     * @param ctx   The importer context
     * @param name  The catalog's name
     * @return Path of created catalog
     */
    public String createCatalog(ImporterContext ctx, String name) throws Exception;

    /**
     * Creates a product from the given values.
     * @param ctx                The importer context
     * @param values             The product's properties
     * @param parentCategoryPath The containing category's path
     * @return Path of created product
     */
    public String createProduct(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;

    /**
     * Creates a variant product from the given values.
     * @param ctx             The importer context
     * @param values          The product's properties
     * @param baseProductPath The base product's path
     * @return Path of created product
     */
    public String createVariantProduct(ImporterContext ctx, ValueMap values, String baseProductPath) throws Exception;

    /**
     * Creates an asset for a product. This is usually a product
     * image.
     * @param ctx             The importer context
     * @param values          The product's properties
     * @param baseProductPath The product's path
     * @return Path of created asset
     */
    public String createAsset(ImporterContext ctx, ValueMap values, String productPath) throws Exception;

    /**
     * Creates a category from the given values.
     * @param ctx           The importer context
     * @param values        The category's properties
     * @param parentPath    Path of parent category or base path of import in case of root category
     * @return Path of created category
     */
    public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Affinché il tuo gestore personalizzato possa essere riconosciuto dall’importazione, devi specificare l’ `service.ranking`proprietà con un valore superiore a 0; ad esempio:

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler {
    ...
}
```
