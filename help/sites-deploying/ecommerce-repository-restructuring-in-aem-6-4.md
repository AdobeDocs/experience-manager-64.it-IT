---
title: Ristrutturazione dell’archivio di e-commerce in AEM 6.4
seo-title: E-Commerce Repository Restructuring in AEM 6.4
description: Scopri come apportare le modifiche necessarie per migrare alla nuova struttura dell’archivio in AEM 6.4 per E-Commerce.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 6adcc1a4-eb0f-4410-8219-dbd7e6bbe469
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 5%

---

# Ristrutturazione dell’archivio di e-commerce in AEM 6.4{#e-commerce-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Come descritto nell&#39;elemento padre [Ristrutturazione dell’archivio in AEM 6.4](/help/sites-deploying/repository-restructuring.md) I clienti che eseguono l’aggiornamento a AEM 6.4 devono utilizzare questa pagina per valutare lo sforzo di lavoro associato alle modifiche dell’archivio che influiscono sulla soluzione AEM E-Commerce. Alcune modifiche richiedono un lavoro durante il processo di aggiornamento di AEM 6.4, mentre altre possono essere differite fino a un aggiornamento 6.5.

## Con aggiornamento alla versione 6.4 {#with-upgrade}

### Dati relativi a prodotti, ordini, raccolte, classificazioni, metodi di spedizione e metodi di pagamento {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Puoi utilizzare un <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Migrazione Lazy</a> eseguire la migrazione dei dati di E-Commerce.</p> <p>Esegue i seguenti passaggi:</p> 
    <ul> 
     <li>regola i riferimenti alla vecchia posizione in modo che punti alla nuova posizione</li> 
     <li>sposta il contenuto dalla vecchia posizione alla nuova posizione</li> 
     <li>rimuove la vecchia posizione per attivare infine l'utilizzo della nuova posizione nell'intero sistema</li> 
    </ul> <p>Le sedi interessate dall'attività sono:</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>Per i cataloghi più grandi, si consiglia di eseguire l’attività di migrazione Commerce singolarmente passando la seguente proprietà di sistema Java a AEM:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Dopo la migrazione AEM necessario riavviare.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>
