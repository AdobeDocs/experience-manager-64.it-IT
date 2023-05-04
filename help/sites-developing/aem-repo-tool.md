---
title: AEM Repo Tool
seo-title: AEM Repo Tool
description: AEM Repo Tool è una soluzione semplice per trasferire il contenuto JCR tra il filesystem locale e il server AEM tramite la riga di comando paragonabile a FTP. Lo AEM Repo Tool è simile allo strumento Jackrabbit FileVault, ma è più veloce, ha dipendenze minime ed è un semplice script bash.
seo-description: The AEM Repo Tool is a simple solution to transfer JCR content between your local filesystem and the AEM server via the command line comparable to FTP. The AEM Repo Tool is similar to the Jackrabbit FileVault tool, but is faster, has minimal dependencies, and is a simple bash script.
uuid: 6c4a3504-e8e8-46c0-83cb-c18d9791f93e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 7de7b2f9-770e-4af3-8a31-c7b4de64fd43
exl-id: 8da27ef5-bb61-4246-8a13-96a60188ebbb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 4%

---

# AEM Repo Tool{#aem-repo-tool}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

AEM Repo Tool è una soluzione semplice per trasferire il contenuto JCR tra il filesystem locale e il server AEM tramite la riga di comando paragonabile a FTP. Lo strumento Repo AEM è simile al [Strumento Jackrabbit FileVault](/help/sites-developing/ht-vlttool.md), ma è più veloce, ha dipendenze minime ed è un semplice script bash.

Questo strumento semplifica il trasferimento di file per lo sviluppatore e può anche essere integrato in IntelliJ ed Eclipse per rendere lo sviluppo ancora più efficiente.

## Panoramica {#overview}

Per un determinato percorso all&#39;interno di un `jcr_root` struttura filevault sul filesystem, AEM Repo Tool crea un pacchetto con un singolo filtro per l&#39;intero sottoalbero e lo invia al server (simile a FTP `put`), lo recupera dal server ( `get`) o confronta le differenze ( `status` e `diff`).

Lo strumento non supporta più percorsi di filtro o FileVault `filter.xml`.

>[!CAUTION]
>
>Tieni presente che lo AEM Repo Tool sovrascrive sempre l’intero file o directory specificato.

## Download e documentazione {#download-and-documentation}

La [AEM Repo Tool è disponibile su GitHub tramite questo collegamento](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) oltre a istruzioni dettagliate sull&#39;installazione e sull&#39;utilizzo.

Per scaricare l’origine dello strumento Repo AEM, fai riferimento al progetto GitHub collegato di seguito.

CODICE SU GITHUB

Puoi trovare il codice di questa pagina su GitHub

* [Progetto Open tools su GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Scarica il progetto come [un file ZIP](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
