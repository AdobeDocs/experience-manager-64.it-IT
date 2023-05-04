---
title: Modulo di installazione delle patch di AEM Forms JEE
description: Modulo di installazione delle patch di AEM Forms JEE
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 23%

---

# Modulo di installazione delle patch di AEM Forms JEE {#aem-forms-jee-patch-installer}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>[Contatta il supporto](https://www.adobe.com/account/sign-in.supportportal.html) per ulteriori informazioni o per ottenere la patch.

## Informazioni sul programma di installazione della patch {#about-the-patch-installer}

Il programma di installazione delle patch JEE per Forms 6.4 AEM include tutti i problemi risolti per tutti i componenti di JEE Forms 6.4 disponibili fino al rilascio di questa patch. Scopri le ultime  [Note sulla versione di Cumulative Fix Pack](cfp-release-notes.md) per un elenco completo dei problemi risolti.

## Prerequisiti per l’installazione della patch {#prerequisites-to-installing-the-patch}

* Forms 6.4

## Installazione e configurazione della patch {#installing-and-configuring-the-patch}

1. Esegui un backup del &lt;*AEM_forms_root*>/distribuisci cartella. Sarà necessaria se decidi di disinstallare la correzione rapida.
1. Arresta il server applicazioni.
1. Estrai sul disco rigido il file archivio del programma di installazione della patch.
1. Nella directory denominata in base al sistema operativo in uso:

   * **Windows**
Accedere alla directory appropriata del supporto di installazione o della cartella sul disco rigido in cui è stato copiato il programma di installazione e fare doppio clic sul pulsante 
`aemforms64_cfp_install.exe` file.

      * (Windows a 32 bit) `Windows\Disk1\InstData\VM`
      * (Windows a 64 bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**
Passa alla directory appropriata e, dal prompt dei comandi, digita 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Viene avviata una procedura di installazione guidata.

1. Nel pannello introduttivo, fai clic su **[!UICONTROL Avanti]**.
1. Nella schermata Scegli cartella di installazione , verifica che il percorso predefinito visualizzato sia corretto per l’installazione esistente oppure fai clic su **[!UICONTROL Sfoglia]** per selezionare la cartella alternativa in cui è installato AEM moduli e fare clic su **[!UICONTROL Successivo]**.

1. Leggi le informazioni di riepilogo della patch di correzione rapida e fai clic su **[!UICONTROL Avanti]**.
1. Leggi le informazioni di riepilogo di pre-installazione e fai clic su **[!UICONTROL Installa]**.
1. Al termine dell&#39;installazione, fai clic su **[!UICONTROL Successivo]**per applicare gli aggiornamenti rapidi ai file installati.
1. [Solo Windows] Esegui uno dei seguenti passaggi:

   * Deselezionare l&#39;opzione Avvia Configuration Manager prima di fare clic su Fine. Esegui Configuration Manager in un secondo momento utilizzando la `ConfigurationManager.bat` file che si trova in `[aem-forms root]\configurationManager\bin`. Utilizzo `ConfigurationManager.bat` aiuta a evitare di aggiornare manualmente il nome di axis.jar nei file .lax
   * Deselezionare l&#39;opzione Avvia Configuration Manager prima di fare clic su Fine. Prima di eseguire la gestione della configurazione utilizzando **ConfigurationManager.exe** o **ConfigurationManager_IPv6.exe**, passa a *&lt;aemforms_install_dir>\configurationManager\bin* directory e aggiornamento **axis.jar** a **axis-1.4.1.1.jar** nei file seguenti:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Solo basato su Unix) La casella di controllo Avvia Configuration Manager è selezionata per impostazione predefinita. Fai clic su **[!UICONTROL Fine]** per eseguire Configuration Manager.

   Per eseguire Configuration Manager in un secondo momento, deseleziona l’opzione Avvia Configuration Manager prima di fare clic su Fine. Puoi avviare Configuration Manager in un secondo momento utilizzando lo script appropriato nel `[AEM_forms_root]/configurationManager/bin` directory.

1. A seconda del server delle applicazioni, scegli uno dei seguenti documenti e segui le istruzioni in *Configurazione e distribuzione dei moduli AEM* sezione .

   * [Installazione e distribuzione di moduli AEM per JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Installazione e distribuzione di moduli AEM per WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Installazione e distribuzione di moduli AEM per WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Solo JBoss) Dopo aver installato la patch e configurato il server, elimina tmp e le directory di lavoro del server applicazioni JBoss.

## Configurazioni post-distribuzione {#post-deployment-configurations}

### Configurazioni SAML {#saml-configurations}

Se hai configurato l’autenticazione SAML e hai problemi con metadati IDP di grandi dimensioni, procedi come segue dopo l’installazione della patch:

1. Imposta la seguente proprietà di sistema nel server dell&#39;applicazione:\
   `um.saml.enable.large.xml=true`

1. Riavvia il server.
1. Elimina i provider di autenticazione SAML esistenti e aggiungili di nuovo per i domini esistenti come descritto nelle impostazioni SAML.

## Moduli interessati {#impacted-modules}

* Document Services
* Document Security
* JEE per Foundation
* Servizio PDFG

[Contatta il supporto](https://www.adobe.com/account/sign-in.supportportal.html)
