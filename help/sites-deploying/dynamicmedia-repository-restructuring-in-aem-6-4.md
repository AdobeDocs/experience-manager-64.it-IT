---
title: Ristrutturazione dell'archivio multimediale dinamico in AEM 6.4
seo-title: Ristrutturazione dell'archivio multimediale dinamico in AEM 6.4
description: Scoprite come apportare le modifiche necessarie per eseguire la migrazione alla nuova struttura del repository in AEM 6.4 per gli elementi multimediali dinamici.
seo-description: Scoprite come apportare le modifiche necessarie per eseguire la migrazione alla nuova struttura del repository in AEM 6.4 per gli elementi multimediali dinamici.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
translation-type: tm+mt
source-git-commit: 5dce4bcf4b10cce65798fd142a3eeb1956caf726
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 4%

---


# Ristrutturazione dell&#39;archivio multimediale dinamico in AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

Come descritto nella pagina Ristrutturazione [repository padre di AEM 6.4](/help/sites-deploying/repository-restructuring.md) , i clienti che effettuano l&#39;aggiornamento a AEM 6.4 devono utilizzare questa pagina per valutare lo sforzo di lavoro associato alle modifiche del repository che hanno un impatto sulla soluzione Dynamic Media. Alcune modifiche richiedono sforzi di lavoro durante il processo di aggiornamento di AEM 6.4, mentre altre possono essere posticipate fino a un aggiornamento di 6.5.

**Aggiornamento precedente a 6.5**

* [Configurazioni di codifica video adattiva personalizzate](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configurazione cloud Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configurazione Cloud Service Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Contenuti multimediali dinamici - Configurazione Cloud Service YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Misc](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Aggiornamento precedente a 6.5 {#prior-to-upgrade}

### Configurazioni di codifica video adattiva personalizzate  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>È possibile eseguire il seguente script di migrazione per eseguire la migrazione alla nuova posizione:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>In alternativa, puoi modificare la configurazione AEM'interfaccia utente e salvare le modifiche nella nuova posizione.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media (DMS7) Cloud configuration {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire uno script di migrazione nel seguente percorso:<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Riavviate il bundle Dynamic Media OSGi.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

### Configurazione Cloud Service Dynamic Media (DM Hybrid) {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>È possibile eseguire lo script di migrazione riportato di seguito per allineare il modello all'ultimo:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Contenuti multimediali dinamici - Configurazione Cloud Service YouTube  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>1. Annullate la pubblicazione di tutti i video da YouTube<br /> 2. Create la configurazione di YouTube utilizzando la nuova interfaccia touch (da <code>/conf</code>), compresa la copia di tutti i canali dalla vecchia posizione<br /> 3. Pubblicate tutti i video su YouTube.</p> <p>Questo flusso di lavoro genera nuovi URL per YouTube. Se non annullate la pubblicazione prima di creare una nuova configurazione di YouTube per l’interfaccia touch, avrete più URL YouTube elencati in Proprietà, perché i canali ricreati verranno pubblicati di nuovo se ne è data la possibilità. Questo significa che avrete degli URL inutili elencati in Proprietà.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Misc {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire lo script di migrazione riportato di seguito.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>In alternativa, puoi modificare la configurazione AEM'interfaccia utente e salvare le modifiche nella nuova posizione.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>Posizione precedente</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Nuove posizioni</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>Orientamenti per la ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire lo script di migrazione riportato di seguito.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

