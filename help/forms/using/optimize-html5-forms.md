---
title: Ottimizzazione dei moduli HTML5
seo-title: Optimizing HTML5 forms
description: È possibile ottimizzare le dimensioni di output dei moduli HTML5.
seo-description: You can optimize the output size of the HTML5 forms.
uuid: 959f0b6a-9e4d-478a-afa8-4c39011fdf7a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: bdb9edc2-6a37-4d3f-97d5-0fc5664316be
feature: Mobile Forms
exl-id: 8d2b5294-9763-4348-b927-706ebac90b95
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 2%

---

# Ottimizzazione dei moduli HTML5 {#optimizing-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

HTML5 forms esegue il rendering dei moduli nel formato HTML5. L’output risultante potrebbe essere grande a seconda di fattori quali le dimensioni del modulo e le immagini nel modulo. Per ottimizzare il trasferimento dei dati, l’approccio consigliato consiste nel comprimere la risposta di HTML utilizzando il server Web da cui viene distribuita la richiesta. Questo approccio riduce le dimensioni di risposta, il traffico di rete e il tempo necessario per lo streaming dei dati tra server e computer client.

Questo articolo descrive i passaggi necessari per abilitare la compressione per Apache Web Server 2.0 a 32 bit, con JBoss.

*Nota: Le istruzioni seguenti non si applicano a server diversi da Apache Web Server 2.0 a 32 bit.*

Ottieni il software del server web Apache applicabile al tuo sistema operativo:

* Per Windows, scarica il server web Apache dal sito Apache HTTP Server Project.
* Per Solaris a 64 bit, scaricare il server Web Apache dal sito Web Sunfreeware per Solaris.
* Per Linux, il server web Apache è preinstallato su un sistema Linux.

Apache può comunicare con JBoss utilizzando HTTP o il protocollo AJP.

1. Rimuovi il commento alle seguenti configurazioni del modulo nel *APACHE_HOME/conf/httpd.conf* file.

   ```java
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Per Linux, la directory APACHE_HOME predefinita è /etc/httpd/.

1. Configura il proxy sulla porta 8080 di JBoss.

   Aggiungi la seguente configurazione al *APACHE_HOME/conf/httpd.conf* file di configurazione.

   ```java
   ProxyPass / https://<server_Name>:8080/
   ProxyPassReverse / https://<server_Name>:8080/
   ```

   >[!NOTE]
   >
   >Quando utilizzi un proxy, sono necessarie le seguenti modifiche di configurazione:
   > 
   >* Accesso: *https://&lt;server>:&lt;port>/system/console/configMgr*
   * Modifica la configurazione per il filtro di riferimento Apache Sling
   * In Consenti host, aggiungi la voce per il server proxy


1. Abilita compressione.

   Aggiungi la seguente configurazione al *APACHE_HOME/conf/httpd.conf* file di configurazione.

   ```java
   <Location /content/xfaforms>
     <IfModule mod_deflate.c>
        SetOutputFilter DEFLATE
        # Don’t compress
        SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
        SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
       #Dealing with proxy servers
   
        <IfModule mod_headers.c>
           Header append Vary User-Agent
        </IfModule>
     </IfModule>
   </Location>
   ```

1. Per accedere al server AEM, utilizza https://[Apache_server]80.
