---
title: Strumento di migrazione CRX2OAK
seo-title: CRX2OAK Migration Tool
description: Note sulla versione specifiche dello strumento di migrazione CRX2OAK di Adobe Experience Manager 6.4.
seo-description: Release notes specific to the Adobe Experience Manager 6.4 CRX2OAK Migration tool.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Strumento di migrazione CRX2OAK {#crx-oak-migration-tool}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Elenco delle modifiche e delle correzioni {#list-of-changes-and-fixes}

### 1.8.6 (giugno 2018) {#june}

* OAK-7339 Correggi tutti i sidegrade che si interrompono con UnsupportedOperationException su MissingBlobStore introducendo LoopbackBlobStore
* Utilizzare Oak 1.8.4

### 1.8.4 (aprile 2018) {#april}

* Utilizzare Oak versione 1.8.2
* GRANITE-18104 L&#39;errore di migrazione da 6.3 a 6.4 Repo dovrebbe essere più significativo
* GRANITE-16571 Sostituisci l&#39;utilizzo di SHA-1

   * Il checksum dell&#39;utensile è ora SHA-512 quando si utilizza l&#39;opzione —version

* GRANITE-17601 Incorpora oak-upgrade in CRX2Oak con oak-blob-cloud
* GRANITE-18553 crx2oak lascia le proprietà della versione sul nodo anche quando le versioni non sono migrate

### Versione 1.6.8 (marzo 2017) {#version-march}

* Aggiornamento della versione Oak alla 1.6.1
* CQ-61847 Unisci crx2oak-quickstart-extension con crx2oak (aggiunti profili di migrazione)
* CQ-97488 Promozione e rilascio delle modalità di esecuzione AEM (riscrivendo sling.options.file)
* GRANITE-12798/OAK-4260 Possibilità di valutare in parallelo il segmento Oak al trar del segmento Oak

### Versione 1.4.2 (marzo 2016) {#version-march-1}

* Aggiorna la versione Oak alla 1.4.1
* OAK-3846 / GRANITE-10748 Rinomina i nodi SNS se violano i vincoli del tipo di nodo
* OAK-3910 / GRANITE-10730 Migrazione del nodo che eredita da `mix:versionable` senza cronologia delle versioni
* OAK-4128/GRANITE-11757 `RepositorySidegrade` non copia le proprietà del nodo principale

### Versione 1.3.4 (gennaio 2016) {#version-january}

* Aggiorna la versione Oak alla 1.3.16
* OAK-3844 / GRANITE-10730 Migliore supporto per nodi versionabili senza cronologia delle versioni
* OAK-3846 Rinomina i nodi SNS se violano i vincoli del tipo di nodo

### Versione 1.3.2 (dicembre 2015) {#version-december}

* Aggiorna la versione Oak alla 1.3.12
* La directory del datastore non deve essere spostata dopo la migrazione (GRANITE-10447)
* Unisci crx2oak-quickstart-extension con crx2oak (CQ-61847)
* crx2oak non riesce sui valori duplicati nell&#39;archivio (CQ-61906)
* Long AEM start dopo la migrazione da CQ 5.x (GRANITE-10309)
* Supporto per più server LDAP in crx2oak (GRANITE-9917)
* Applica il controllo per la lunghezza massima del nome del nodo (OAK-3111)
* Supporto di S3DataSource come origine di migrazione (OAK-3685)
