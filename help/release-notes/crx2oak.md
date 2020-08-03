---
title: Strumento di migrazione CRX2OAK
seo-title: Strumento di migrazione CRX2OAK
description: Note sulla versione specifiche per lo strumento di migrazione  Adobe Experience Manager 6.4 CRX2OAK.
seo-description: Note sulla versione specifiche per lo strumento di migrazione  Adobe Experience Manager 6.4 CRX2OAK.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Strumento di migrazione CRX2OAK {#crx-oak-migration-tool}

## Elenco delle modifiche e delle correzioni {#list-of-changes-and-fixes}

### 1.8.6 (giugno 2018) {#june}

* OAK-7339 È stata corretta l&#39;interruzione di tutti i lati con UnsupportedOperationException su MissingBlobStore introducendo LoopbackBlobStore
* Usa Oak 1.8.4

### 1.8.4 (aprile 2018) {#april}

* Usa versione 1.8.2
* GRANITE-18104 L&#39;errore di migrazione Repo dal 6.3 al 6.4 dovrebbe essere più significativo
* GRANITE-16571 Sostituisce l&#39;utilizzo di SHA-1

   * Il checksum dell&#39;utensile è ora SHA-512 quando si utilizza l&#39;opzione —version

* GRANITE-17601 Incorpora l&#39;aggiornamento della quercia in CRX2Oak con rovere-blob-cloud
* GRANITE-18553 crx2oak lascia sul nodo le proprietà della versione anche quando le versioni non sono migrate

### Versione 1.6.8 (marzo 2017) {#version-march}

* Aggiornamento della versione Oak alla 1.6.1
* CQ-61847 Unisci crx2oak-quickstart-extension con crx2oak (aggiunti profili di migrazione)
* CQ-97488 Promozione e rilascio delle modalità di AEM esecuzione (riscrivendo sling.options.file)
* GRANITE-12798/OAK-4260 Possibilità di effettuare la valutazione laterale dal segmento Oak alla ar segmento Oak

### Versione 1.4.2 (marzo 2016) {#version-march-1}

* Aggiornamento della versione Oak alla 1.4.1
* OAK-3846/GRANITE-10748 Rinominare i nodi SNS se violano i vincoli del tipo di nodo
* OAK-3910 / GRANITE-10730 Migrazione del nodo da cui ereditare `mix:versionable` senza cronologia delle versioni
* OAK-4128/GRANITE-11757 `RepositorySidegrade` non copia le proprietà del nodo radice

### Versione 1.3.4 (gennaio 2016) {#version-january}

* Aggiornamento della versione Oak alla 1.3.16
* OAK-3844 / GRANITE-10730 Supporto migliore per i nodi versionabili senza precedenti
* OAK-3846 Rinominare i nodi SNS se violano i vincoli del tipo di nodo

### Versione 1.3.2 (dicembre 2015) {#version-december}

* Aggiorna la versione Oak alla 1.3.12
* La directory del datastore non deve essere spostata dopo la migrazione (GRANITE-10447)
* Unisci crx2oak-quickstart-extension con crx2oak (CQ-61847)
* crx2oak non riesce su valori duplicati nell&#39;archivio (CQ-61906)
* Lunga AEM avviata dopo la migrazione da CQ 5.x (GRANITE-10309)
* Supporto per più server LDAP in crx2oak (GRANITE-9917)
* Applica il controllo per la lunghezza massima del nome del nodo (OAK-3111)
* Supporto di S3DataSource come origine di migrazione (OAK-3685)
