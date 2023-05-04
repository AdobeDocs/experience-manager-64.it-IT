---
title: Risoluzione dei problemi relativi ad AEM
seo-title: Troubleshooting AEM
description: Scopri come risolvere i problemi relativi a AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: d68e9ead-8aa6-4108-9f1e-85d7cd7a370f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 1bc19f9a-fa3f-43e3-813e-23ab0b708d43
exl-id: 34b509d5-4e80-4229-b155-40004856e87e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 4%

---

# Risoluzione dei problemi relativi ad AEM{#troubleshooting-aem}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La sezione seguente illustra alcuni problemi che potresti riscontrare durante l’utilizzo di AEM, oltre a suggerimenti su come risolverli.

>[!NOTE]
>
>Se stai risolvendo i problemi di authoring in AEM, vedi [Risoluzione dei problemi relativi agli autori.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Quando si verificano problemi, è anche utile controllare l&#39;elenco di [Problemi noti](/help/release-notes/known-issues.md) per la tua istanza (release e service pack).

## Scenari di risoluzione dei problemi per gli amministratori {#troubleshooting-scenarios-for-administrators}

La tabella seguente fornisce una panoramica dei problemi che gli amministratori possono dover risolvere:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ruolo/i</strong></td> 
   <td><strong>Problema </strong></td> 
  </tr> 
  <tr> 
   <td>Amministratore di sistema</td> 
   <td><p>Fare doppio clic sul file jar Quickstart non ha alcun effetto o apre il file jar con un altro programma (ad esempio, gestione archivi)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Amministratore di sistema</p> </td> 
   <td><p>La mia applicazione in esecuzione su CRX genera errori di memoria esaurita</p> </td> 
  </tr> 
  <tr> 
   <td><p>Amministratore di sistema</p> </td> 
   <td><p>La schermata di benvenuto AEM non viene visualizzata nel browser dopo aver fatto doppio clic AEM CM Quickstart</p> </td> 
  </tr> 
  <tr> 
   <td><p>Amministratore di sistema</p> <p>utente amministratore</p> </td> 
   <td><p>Creazione di un dump di thread</p> </td> 
  </tr> 
  <tr> 
   <td><p>Amministratore di sistema</p> <p>utente amministratore</p> </td> 
   <td><p>Verifica di sessioni JCR non chiuse</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problemi di installazione {#installation-issues}

Vedi [Problemi comuni di installazione](/help/sites-deploying/troubleshooting.md#common-installation-issues) per informazioni sui seguenti scenari di risoluzione dei problemi:

* Fare doppio clic sul jar Quickstart non ha alcun effetto o sul file JAR con un altro programma (come archive manager).
* Le applicazioni in esecuzione su CRX generano errori di memoria esaurita.
* La schermata di benvenuto AEM non viene visualizzata nel browser dopo aver fatto doppio clic AEM Quickstart.

## Metodi per la risoluzione dei problemi di analisi {#methods-for-troubleshooting-analysis}

### Creazione di un dump di thread {#making-a-thread-dump}

Il dump di thread è un elenco di tutti i thread Java attualmente attivi. Se AEM non risponde correttamente, il dump di thread può aiutarti a identificare deadlock o altri problemi.

### Utilizzo del dump di thread Sling {#using-sling-thread-dumper}

1. Apri **Console Web AEM**; ad esempio in `http://localhost:4502/system/console/`.

1. Seleziona la **Thread** sotto **Stato** scheda .

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Utilizzo di jstack (riga di comando) {#using-jstack-command-line}

1. Trova il PID (process id) dell&#39;istanza Java AEM.

   Ad esempio, puoi utilizzare `ps -ef` o `jps`.

1. Esegui:

   `jstack <pid>`

1. Questo mostrerà il dump di thread.

>[!NOTE]
>
>Puoi aggiungere le immagini di thread a un file di registro utilizzando la `>>` reindirizzamento uscita:
>
>`jstack <pid> >> /path/to/logfile.log`

Consulta la sezione [Come prendere i dump di thread da una JVM](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) documentazione per ulteriori informazioni

### Verifica di sessioni JCR non chiuse {#checking-for-unclosed-jcr-sessions}

Quando si sviluppano funzionalità per AEM WCM, è possibile aprire sessioni JCR (paragonabili all&#39;apertura di una connessione al database). Se le sessioni aperte non vengono mai chiuse, il sistema potrebbe riscontrare i seguenti sintomi:

* Il sistema diventa più lento.
* Puoi vedere molti CacheManager: ridimensionaTutte le voci nel file di log; numero seguente (size=&lt;x>) mostra il numero di cache, ogni sessione apre diverse cache.
* Di tanto in tanto il sistema esaurisce la memoria (dopo alcune ore, giorni o settimane - a seconda della gravità).

Per analizzare le sessioni non chiuse e scoprire quale codice non sta chiudendo una sessione, consulta l’articolo della Knowledge Base [Analizzare le sessioni non chiuse](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### Utilizzo della console Web di Adobe Experience Manager {#using-the-adobe-experience-manager-web-console}

Lo stato dei bundle OSGi può anche fornire un&#39;indicazione tempestiva di possibili problemi.

1. Apri **Console Web AEM**; ad esempio in `http://localhost:4502/system/console/`.

1. Seleziona **Bundle** sotto **OSGI** scheda .

1. Seleziona:

   * lo stato dei bundle. Se qualcuno è Inattivo o Non soddisfatto, prova a interrompere e riavviare il bundle. Se il problema persiste, potrebbe essere necessario approfondire le indagini utilizzando altri metodi.
   * se uno dei bundle ha dipendenze mancanti. Tali dettagli possono essere visualizzati facendo clic sul nome del singolo bundle, che è un collegamento (il seguente esempio non ha problemi):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
