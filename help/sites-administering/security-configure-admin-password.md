---
title: Configurare la password amministratore durante l’installazione
seo-title: Configure the Admin Password on Installation
description: Scopri come modificare la password dell’amministratore nell’installazione AEM.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 2%

---

# Configurare la password amministratore durante l’installazione{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

A partire dalla versione 6.3, AEM consente di impostare la password dell’amministratore utilizzando la riga di comando durante l’installazione di una nuova istanza.

Con le versioni precedenti di AEM, dopo l’installazione era necessario modificare la password dell’account amministratore, insieme alla password per diverse altre console.

Questa funzione aggiunge la possibilità di impostare una nuova password amministratore per l&#39;archivio e il Servlet Engine durante l&#39;installazione di un&#39;istanza AEM, eliminando così la necessità di farlo manualmente in seguito.

>[!CAUTION]
>
>Tieni presente che la funzione non copre la console Felix, per la quale la password deve essere modificata manualmente. Per ulteriori informazioni, consulta la sezione [Sezione Lista di controllo protezione](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Come La Uso? {#how-do-i-use-it}

Questa funzione si attiva automaticamente se scegli di installare AEM tramite la riga di comando, invece di fare doppio clic sul JAR da un file system explorer.

La sintassi generale per l&#39;esecuzione di un&#39;istanza AEM dalla riga di comando è:

```shell
java -jar aem6.3.jar
```

Dopo aver eseguito l’istanza dalla riga di comando, ti verrà offerta l’opzione di cambiare la password dell’amministratore durante il processo di installazione:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>La richiesta di modifica della password dell&#39;amministratore verrà visualizzata solo durante l&#39;installazione di una nuova istanza AEM.

## Utilizzo del flag -nointerattivo {#using-the-nointeractive-flag}

Puoi anche scegliere di specificare la password da un file di proprietà. A tale scopo, utilizza le `-nointeractive` bandiera combinata con `-Dadmin.password.file` proprietà di sistema.

Di seguito è riportato un esempio:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

La password all&#39;interno della `passwordfile.properties` il file deve avere il formato seguente:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Se si utilizza semplicemente il `-nointeractive` senza `-Dadmin.password.file` proprietà di sistema, AEM utilizzerà la password amministratore predefinita senza chiedere di cambiarla, essenzialmente replicando il comportamento delle versioni precedenti. Questa modalità non interattiva può essere utilizzata per le installazioni automatizzate utilizzando la riga di comando in uno script di installazione.
