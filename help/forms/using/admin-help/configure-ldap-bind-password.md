---
title: Configurare la password di binding LDAP
seo-title: Configure the LDAP bind password
description: Scopri come configurare il campo password di binding prima di importare il file di configurazione in un altro sistema.
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 3%

---

# Configurare la password di binding LDAP{#configure-the-ldap-bind-password}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per evitare rischi di protezione, il campo di binding della password nel file di configurazione esportato (config.xml) non è configurato. Prima di importare il file di configurazione in un altro sistema, assicurati di configurare questa password. Questa password sostituisce una password esistente memorizzata nel database. Una password null non sostituisce un valore di password esistente non nullo.

1. Nella console di amministrazione, fai clic su Impostazioni > Gestione utente > Configurazione > Importa ed esporta file di configurazione.
1. Per esportare l&#39;impostazione di configurazione corrente in un file, fare clic su Esporta e salvare il file di configurazione in un&#39;altra posizione.
1. Nel file , individua il `Domains` > *[Nome di dominio]* > `DirectoryConfigs` > `LDAPGroupConfig` nodo. Ecco un esempio:

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   Digita un valore per `bindpassword` e salva le modifiche.

1. Nel file , individua il `Domains` > *[Nome di dominio]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` nodo. Ecco un esempio:

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   Digita un valore per `bindpassword` e salva le modifiche.

1. Per importare il file aggiornato, in Gestione utente fare clic su Configurazione > Importa ed esporta file di configurazione.
1. Fare clic su Sfoglia per trovare il file, fare clic su Importa e quindi su OK.
