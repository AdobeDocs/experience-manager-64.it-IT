---
title: Abilitare la registrazione per i moduli HTML5
seo-title: Enable logging for HTML5 forms
description: L'utilità logger abilita la registrazione di un modulo e consente di eseguire il debug dei problemi relativi al modulo.
seo-description: The logger utility enables logging for a form and helps you debug form-related issues.
uuid: d6279092-57f3-4fc6-b41b-9caf65459d4d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 23bc7cd2-7d06-4ef8-977a-778e290daef9
feature: Mobile Forms
exl-id: c7953d1b-a332-4138-b744-516f3881cd4d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 7%

---

# Abilitare la registrazione per i moduli HTML5 {#enable-logging-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile configurare l’utility logger per avviare la creazione di registri per i moduli HTML5. L&#39;utilità logger ha vari livelli, è possibile impostare un livello in base alle proprie esigenze. HTML5 forms dispone di componenti server e client. Puoi configurare i registri per entrambi i componenti.

## Configurazione della registrazione lato server {#configuring-server-side-logging}

Esegui i seguenti passaggi per configurare i registri lato server:

1. Passa a `https://[server]:[port]/system/console/configMgr`. Individua e apri la *Configurazione del logger di registrazione di Apache Sling* opzione . Viene visualizzata una finestra di dialogo:

   ![ Finestra di dialogo delle opzioni di configurazione del logger di registrazione di Apache Sling](assets/logconfig.png)

   Opzione di configurazione del logger di registrazione di Apache Sling

1. Modificare la **Livello di log** a **Debug**.

1. Specifica nome e percorso del **File di log**.

   >[!NOTE]
   >
   >Per generare i registri nella directory di registro dei moduli di HTML5, aggiungi ../logs/ prima del nome del file.

1. Modifica **Registratore** a **HTMLFormsPerfLogger.** Fai clic su **Salva**.

## Configurazione della registrazione client {#configuring-client-logging}

Per abilitare la registrazione lato client nei moduli HTML5 è possibile utilizzare i metodi seguenti:

* Utilizzo del parametro di richiesta denominato `log`
* Utilizzo di CQ Configuration Manager

### Abilitazione della registrazione utilizzando il parametro di richiesta {#enabling-logging-using-request-parameter}

Utilizzando questo metodo, puoi generare registri per una particolare richiesta. Il nome del parametro della richiesta è **log**. L’URL del registro è il seguente:

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

La configurazione del registro è composta dal livello di registro e dalla categoria logger.

#### Destinazione log {#log-destination}

<table> 
 <tbody> 
  <tr> 
   <th><strong>Destinazione log</strong></th> 
   <th><strong>Descrizione</strong></th> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>I registri vengono indirizzati al browser <strong>Console</strong></td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>I registri vengono raccolti in un oggetto JavaScript sul lato client e possono essere pubblicati in <strong>Server</strong> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>Entrambe le opzioni di cui sopra<br /> </td> 
  </tr> 
 </tbody> 
</table>

#### Livelli di log {#log-levels}

<table> 
 <tbody> 
  <tr> 
   <th>Livello registro</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td>0</td> 
   <td>DISATTIVATO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>1</td> 
   <td>GRASSETTO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>2</td> 
   <td>ERRORE<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>3</td> 
   <td>AVVISO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>4</td> 
   <td>INFO<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>5</td> 
   <td>DEBUG<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>6</td> 
   <td>TRACE<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>7</td> 
   <td>TUTTO<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Categorie di logger {#logger-categories}

<table> 
 <tbody> 
  <tr> 
   <th>Categoria registro</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td>a</td> 
   <td>xfa (registri relativi al motore di script)</td> 
  </tr> 
  <tr> 
   <td>b</td> 
   <td>xfaView (registri relativi al motore di layout)<br type="_moz" /> </td> 
  </tr> 
  <tr> 
   <td>c</td> 
   <td>xfaPerf (registri relativi alle prestazioni)<br type="_moz" /> </td> 
  </tr> 
 </tbody> 
</table>

#### Configurazione del registro {#log-configuration}

Nell’URL del registro, il parametro della stringa di query per la configurazione del registro è definito come segue:

`{destination}-{a level}-{b level}-{c level}`

Ad esempio:

<table> 
 <tbody> 
  <tr> 
   <th>Configurazione del registro</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td>2-a4-b5-c6<br type="_moz" /> </td> 
   <td>Destinazione: Server<br /> livello xfa: INFORMAZIONI<br /> livello xfaView: DEBUG<br /> livello xfaPerf: TRACE</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Il livello di log predefinito per ogni categoria di log a (xfa), b (xfaView) e c (xfaPerf) è 2 (ERROR). Di conseguenza, per la configurazione del registro: 2-b6, i livelli di log per le diverse categorie sono:\
>a (xfa): 2 (livello predefinito ERROR)\
>b (xfaView): 6 (TRACE specificato dall&#39;utente)\
>a (xfaPerf): 2 (livello predefinito ERROR)

### Abilitazione della registrazione tramite Configuration Manager {#enabling-logging-using-configuration-manager}

Se si utilizza Configuration Manager per abilitare la registrazione, vengono generati i registri per ogni richiesta di rendering fino a quando la registrazione non viene nuovamente disabilitata.

1. Accedi a CQ Configuration Manager all&#39;indirizzo `https://[server]:[port]/system/console/configMgr` e accedi con le credenziali di amministratore.
1. Cerca e fai clic su **Configurazioni Forms per dispositivi mobili**.
1. Nella casella di testo Opzioni di debug, immetti le configurazioni del registro come descritto, ad esempio, nella sezione precedente, **2-a4-b5-c6**

   ![Configurazione dei moduli](assets/forms_configuration.png)

   Configurazione dei moduli

## Caricamento dei registri {#uploading-logs}

Se la destinazione è impostata su 1, tutti i messaggi di log degli script client vengono indirizzati alla console. Se un amministratore richiede questi registri insieme ai registri del server, imposta il livello di destinazione su 2. A questo livello, tutti i registri vengono raccolti in un oggetto JS sul lato client e, se viene eseguito il rendering del modulo con il profilo predefinito, un **Registri di invio** a sinistra di **Evidenzia campi esistenti** nella barra degli strumenti. Quando l&#39;utente fa clic sul collegamento, tutti i registri raccolti vengono inviati al server e vengono registrati nel file di registro degli errori configurato sul server.

Per impostazione predefinita, tutte le informazioni vengono aggiunte al file error.log nella directory /crx-repository/logs/ .

Per modificare la posizione e il nome del file di log:

1. Accedi a Configuration Manager come amministratore. L’URL predefinito di Configuration Manager è `https://[*Server*]:[*Port*]/system/console/configMgr`.
1. Fai clic su **Configurazione del logger di registrazione Sling di Apache**. Viene visualizzata una finestra di dialogo.

   ![logconfig-1](assets/logconfig-1.png)

1. Modificare la **Livello di log** da eseguire il debug.

1. Specificare il percorso e il nome dell&#39;operatore **File di log**.

   >[!NOTE]
   >
   >Per creare i registri nella stessa directory in cui vengono conservati gli altri file di registro, specifica ../logs/&lt;filename> nella proprietà File di registro.

1. Modificare la **Registratore** a **HTMLFormsPerfLogger** e fai clic su **Salva**.
