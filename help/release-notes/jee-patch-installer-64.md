---
title: ' programma di installazione patch JEE AEM Forms'
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---


#  programma di installazione patch JEE AEM Forms {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Per ulteriori informazioni o per ottenere la patch, contattate il supporto](https://www.adobe.com/account/sign-in.supportportal.html) .

## Informazioni sul programma di installazione della patch {#about-the-patch-installer}

Il programma di installazione AEM patch Forms JEE 6.4 include tutti i problemi risolti per tutti i componenti di Forms JEE AEM 6.4 disponibili fino al rilascio di questa patch. Per un elenco completo dei problemi risolti, consultate le ultime note [sulla versione del](cfp-release-notes.md) Cumulative Fix Pack.

## Prerequisiti per l’installazione della patch {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Installazione e configurazione della patch {#installing-and-configuring-the-patch}

1. Eseguire un backup della cartella &lt;*AEM_forms_root*>/deploying. È richiesto se si decide di disinstallare la correzione rapida.
1. Arrestate il server applicazione.
1. Estrarre il file di archivio del programma di installazione della patch sul disco rigido.
1. Nella directory denominata in base al sistema operativo in uso:

   * **Windows** Individuate la directory appropriata nel supporto di installazione o nella cartella del disco rigido in cui avete copiato il programma di installazione e fate doppio clic sul pulsante 
`aemforms64_cfp_install.exe` file.

      * (Windows a 32 bit) `Windows\Disk1\InstData\VM`
      * (Windows a 64 bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX** Passare alla directory appropriata e da un prompt dei comandi digitare 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Viene avviata una procedura guidata di installazione che illustra le procedure di installazione.

1. Nel pannello Introduzione, fate clic su **[!UICONTROL Avanti]**.
1. Nella schermata Scegli cartella di installazione, verificare che il percorso predefinito visualizzato sia corretto per l&#39;installazione esistente oppure fare clic su **[!UICONTROL Sfoglia]** per selezionare la cartella alternativa in cui sono installati AEM moduli e fare clic su **[!UICONTROL Avanti]**.

1. Leggere le informazioni di riepilogo sulla correzione rapida e fare clic su **[!UICONTROL Avanti]**.
1. Leggere il Riepilogo pre-installazione e fare clic su **[!UICONTROL Installa]**.
1. Al termine dell&#39;installazione, fare clic su **[!UICONTROL Next]**per applicare gli aggiornamenti della correzione rapida ai file installati.
1. [Solo] Windows Effettuare una delle seguenti operazioni:

   * Deselezionate l&#39;opzione Avvia Configuration Manager prima di fare clic su Fine. Eseguire Configuration Manager in un secondo momento utilizzando il `ConfigurationManager.bat` file che si trova in `[aem-forms root]\configurationManager\bin`. L’utilizzo `ConfigurationManager.bat` consente di evitare l’aggiornamento manuale del nome axis.jar nei file .lax
   * Deselezionate l&#39;opzione Avvia Configuration Manager prima di fare clic su Fine. Prima di eseguire Configuration Manager con **ConfigurationManager.exe** o **ConfigurationManager_IPv6.exe**, andate alla *&lt;AEMForms_Install_Dir>\configurationManager\bin* directory e aggiornate **axis.jar** sull&#39; **asse 1.4.1.1.jar** nei file seguenti:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Solo basato su Unix) La casella di controllo Avvia Configuration Manager è selezionata per impostazione predefinita. Fate clic su **[!UICONTROL Fine]** per eseguire Gestione configurazione.

   Per eseguire Configuration Manager in un secondo momento, deselezionare l&#39;opzione Avvia Configuration Manager prima di fare clic su Fine. È possibile avviare Configuration Manager in un secondo momento utilizzando lo script appropriato nella `[AEM_forms_root]/configurationManager/bin` directory.

1. A seconda del server applicazione in uso, scegliere uno dei documenti seguenti e seguire le istruzioni fornite nella sezione *Configurazione e distribuzione AEM moduli* .

   * [Installazione e distribuzione di moduli AEM per JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Installazione e distribuzione di moduli AEM per WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Installazione e distribuzione di moduli AEM per WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Solo JBoss) Dopo aver installato la patch e configurato il server, eliminare tmp e le directory di lavoro del server applicazioni JBoss.

## Configurazioni post-distribuzione {#post-deployment-configurations}

### Configurazioni SAML {#saml-configurations}

Se l’autenticazione SAML è stata configurata e si verificano problemi con metadati IDP di grandi dimensioni, dopo l’installazione della patch effettuate le seguenti operazioni:

1. Impostate la seguente proprietà di sistema nel server applicazione:\
   `um.saml.enable.large.xml=true`

1. Riavviate il server.
1. Eliminate i provider di autenticazione SAML esistenti e aggiungeteli di nuovo per i domini esistenti come descritto nelle impostazioni SAML.

## Moduli interessati {#impacted-modules}

* Servizi basati su documenti
* Sicurezza dei documenti
* JEE per Foundation
* Servizio PDFG

[Contattare il supporto](https://www.adobe.com/account/sign-in.supportportal.html)
