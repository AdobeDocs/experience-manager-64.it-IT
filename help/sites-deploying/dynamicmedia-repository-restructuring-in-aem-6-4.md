---
title: Ristrutturazione dell’archivio Dynamic Media in AEM 6.4
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: Scopri come apportare le modifiche necessarie per migrare alla nuova struttura dell’archivio in AEM 6.4 per Dynamic Media.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# Ristrutturazione dell’archivio Dynamic Media in AEM 6.4{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Come descritto nell&#39;elemento padre [Ristrutturazione dell’archivio in AEM 6.4](/help/sites-deploying/repository-restructuring.md) I clienti che eseguono l’aggiornamento a AEM 6.4 devono utilizzare questa pagina per valutare lo sforzo di lavoro associato alle modifiche dell’archivio che influiscono sulla soluzione Dynamic Media. Alcune modifiche richiedono un lavoro durante il processo di aggiornamento di AEM 6.4, mentre altre possono essere differite fino a un aggiornamento 6.5.

**Prima dell’aggiornamento alla versione 6.5**

* [Configurazioni di codifica video adattiva personalizzate](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Configurazione cloud Dynamic Media (DMS7)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Configurazione del Cloud Service Dynamic Media (DM Hybrid)](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - Configurazione Cloud Service YouTube](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [Varie](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## Prima dell’aggiornamento alla versione 6.5 {#prior-to-upgrade}

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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Puoi eseguire il seguente script di migrazione per eseguire la migrazione alla nuova posizione:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>In alternativa, puoi modificare la configurazione nell’interfaccia utente AEM e salvare le modifiche nella nuova posizione.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Configurazione cloud Dynamic Media (DMS7) {#dynamic-media-dms-cloud-configuration}

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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire uno script di migrazione nel seguente percorso:<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>Riavvia il bundle OSGi di Dynamic Media.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>

### Configurazione del Cloud Service Dynamic Media (DM Hybrid) {#cloudserviceconfiguration}

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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Puoi eseguire lo script di migrazione seguente per allinearlo al modello più recente:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media - Configurazione del Cloud Service YouTube  {#youtubecloudserviceconfiguration}

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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>1. Annulla la pubblicazione di tutti i video da YouTube<br /> 2. Crea la configurazione YouTube utilizzando la nuova interfaccia Touch (da <code>/conf</code>) inclusa la copia di tutti i canali dalla vecchia posizione<br /> 3. Pubblica tutti i video in YouTube.</p> <p>Questo flusso di lavoro genera nuovi URL YouTube. Se non annulli la pubblicazione prima di creare una nuova configurazione di YouTube TouchUI, avrai più URL YouTube elencati in Proprietà perché i canali ricreati verranno pubblicati di nuovo se è possibile. Questo significa che avrai URL inutili elencati in Proprietà.</p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D<br /> </td> 
  </tr>
 </tbody>
</table>

### Varie {#misc}

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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire lo script di migrazione seguente.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>In alternativa, puoi modificare la configurazione nell’interfaccia utente AEM e salvare le modifiche nella nuova posizione.</p> </td> 
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
   <td><strong>Orientamento alla ristrutturazione</strong></td> 
   <td><p>Il cliente può eseguire lo script di migrazione seguente.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>Note</strong></td> 
   <td>N/D</td> 
  </tr>
 </tbody>
</table>
