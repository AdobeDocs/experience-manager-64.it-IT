---
title: SSL per impostazione predefinita
seo-title: SSL By Default
description: Scopri come utilizzare SSL per impostazione predefinita in AEM.
seo-description: Learn how to use SSL by Default in AEM.
uuid: 262474b0-f5fa-4cff-8727-9f39c5b5f760
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
discoiquuid: 3a1817cd-357b-473d-9a09-e18bbfc60dfd
exl-id: 07f89673-125b-4205-bc54-c90287a1e9a5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 1%

---

# SSL per impostazione predefinita{#ssl-by-default}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Nel tentativo di migliorare continuamente la sicurezza di AEM, Adobe ha introdotto una funzione chiamata SSL By Default. Lo scopo è incoraggiare l’uso di HTTPS per connettersi alle istanze AEM.

## Abilitazione di SSL per impostazione predefinita {#enabling-ssl-by-default}

Per iniziare a configurare SSL per impostazione predefinita, fai clic sul messaggio casella in entrata corrispondente nella schermata iniziale AEM. Per raggiungere la casella in entrata, premere l&#39;icona della campana nell&#39;angolo superiore destro dello schermo. Quindi, fai clic su **Visualizza tutto**. Verrà visualizzato un elenco di tutti gli avvisi ordinati in una vista a elenco.

Nell’elenco, seleziona e apri le **Configura HTTPS** avviso:

![chlimage_1-341](assets/chlimage_1-341.png)

>[NOTA!]
>
>Se la **Configura HTTPS** L&#39;avviso non è presente nella casella in entrata, è possibile passare direttamente alla procedura guidata HTTPS andando a *<http://serveraddress:serverport/libs/granite/security/content/sslConfig.html?item=configuration%2fconfiguressl&_charset_=utf-8>*

Utente di un servizio denominato **servizio ssl** è stato creato per questa funzione. Una volta aperto l’avviso, verrà visualizzata la seguente procedura guidata di configurazione:

1. Impostare innanzitutto le credenziali dell&#39;archivio. Queste sono le credenziali per **servizio ssl** archivio chiavi dell&#39;utente del sistema che conterrà la chiave privata e l&#39;archivio di attendibilità per il listener HTTPS.

   ![chlimage_1-342](assets/chlimage_1-342.png)

1. Una volta immesse le credenziali, fai clic su **Successivo** nell’angolo superiore destro della pagina. Quindi, carica la chiave privata e il certificato associati per la connessione SSL.

   ![chlimage_1-343](assets/chlimage_1-343.png)

   >[!NOTE]
   >
   >Per informazioni su come generare una chiave privata e un certificato da utilizzare con la procedura guidata, consulta [presente procedura](/help/sites-administering/ssl-by-default.md#generating-a-private-key-certificate-pair-to-use-with-the-wizard) sotto.

1. Infine, specifica il nome host HTTPS e la porta TCP per il listener HTTPS.

   ![screen_shot_2018-07-25at31658pm](assets/screen_shot_2018-07-25at31658pm.png)

## Automazione SSL per impostazione predefinita {#automating-ssl-by-default}

Esistono tre modi per automatizzare SSL per impostazione predefinita.

### Tramite HTTP POST {#via-http-post}

Il primo metodo prevede la pubblicazione sul server SSLSetup utilizzato dalla configurazione guidata:

```shell
POST /libs/granite/security/post/sslSetup.html
```

Puoi utilizzare il seguente payload in POST per automatizzare la configurazione:

```xml
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePassword"
 
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePassword"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="privatekeyFile"; filename="server.der"
Content-Type: application/x-x509-ca-cert
 
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="certificateFile"; filename="server.crt"
Content-Type: application/x-x509-ca-cert
 
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="httpsPort"
8443
```

Il servlet, come qualsiasi servlet sling POST, risponderà con 200 OK o con un codice di stato HTTP di errore. Puoi trovare i dettagli sullo stato nel corpo HTML della risposta.

Di seguito sono riportati alcuni esempi di risposta corretta e di errore.

**ESEMPIO DI SUCCESSO** (stato = 200):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>OK</title>
</head>
<body>
<h1>OK</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>200</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>SSL successfully configured</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>OK</dd>
<dt class='foundation-form-response-description'>Description</dt>
<dd>HTTPS has been configured on port 8443. The private key and
certificate were stored in the key store of the user ssl-service.
Please take note of the key store password you provided. You will need
it for any subsequent updating of the private key or certificate.</dd>
</dl>
<h2>Links</h2>
<ul class='foundation-form-response-links'>
<li><a class='foundation-form-response-redirect' href='/'>Done</a></li>
</ul>
</body>
</html>
```

**ESEMPIO DI ERRORE** (stato = 500):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>Error</title>
</head>
<body>
<h1>Error</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>500</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>The provided file is not a valid key, DER format expected</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>Error</dd>
</dl>
</body>
</html>
```

### Tramite pacchetto {#via-package}

In alternativa, puoi automatizzare la configurazione SSL caricando un pacchetto che contiene già questi elementi richiesti:

* L&#39;archivio chiavi dell&#39;utente del servizio ssl. Si trova in */home/users/system/security/ssl-service/keystore* nel repository.
* La `GraniteSslConnectorFactory` configurazione

### Generazione di una coppia chiave/certificato privata da utilizzare con la procedura guidata {#generating-a-private-key-certificate-pair-to-use-with-the-wizard}

Di seguito è riportato un esempio per la creazione di un certificato autofirmato in formato DER utilizzabile dalla procedura guidata SSL.

>[!NOTE]
>
>L’uso di un certificato autofirmato è ad esempio limitato e non deve essere utilizzato in produzione.

1. Innanzitutto, crea la chiave privata:

   ```shell
   openssl genrsa -aes256 -out localhostprivate.key 4096
   openssl rsa -in localhostprivate.key -out localhostprivate.key
   ```

1. Quindi, genera una richiesta di firma del certificato (CSR, Certificate Signing Request) utilizzando una chiave privata:

   ```shell
   openssl req -sha256 -new -key localhostprivate.key -out localhost.csr -subj '/CN=localhost'
   ```

1. Genera il certificato SSL e firma con la chiave privata. In questo esempio, scadrà tra un anno:

   ```shell
   openssl x509 -req -days 365 -in localhost.csr -signkey localhostprivate.key -out localhost.crt
   ```

Converti la chiave privata in formato DER. Questo perché la procedura guidata SSL richiede che la chiave sia in formato DER:

```shell
openssl pkcs8 -topk8 -inform PEM -outform DER -in localhostprivate.key -out localhostprivate.der -nocrypt
```

Infine, carica il **localhostprivate.der** come chiave privata e **localhost.crt** come certificato SSL nel passaggio 2 della procedura guidata SSL grafica descritta all’inizio di questa pagina.

### Aggiornamento della configurazione SSL tramite cURL {#updating-the-ssl-configuration-via-curl}

>[!NOTE]
>
>Vedi [Utilizzo di cURL con AEM](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/curl.html) per un elenco centralizzato di comandi cURL utili in AEM.

Puoi anche automatizzare la configurazione SSL utilizzando lo strumento cURL. Per farlo, pubblica i parametri di configurazione in questo URL:

*https://&lt;serveraddress>:&lt;serverport>/libs/granite/security/post/sslSetup.html*

Di seguito sono riportati i parametri che è possibile utilizzare per modificare le varie impostazioni della procedura guidata di configurazione:

* `-F "keystorePassword=password"` - la password del keystore;

* `-F "keystorePasswordConfirm=password"` - confermare la password del keystore;

* `-F "truststorePassword=password"` - la password del truststore;

* `-F "truststorePasswordConfirm=password"` - confermare la password del truststore;

* `-F "privatekeyFile=@localhostprivate.der"` - specificare la chiave privata;

* `-F "certificateFile=@localhost.crt"` - specificare il certificato;

* `-F "httpsHostname=host.example.com"`- specificare il nome host;
* `-F "httpsPort=8443"` - la porta su cui funzionerà il listener HTTPS.

>[!NOTE]
>
>Il modo più veloce per eseguire cURL per automatizzare la configurazione SSL è dalla cartella in cui si trovano i file DER e CRT. In alternativa, è possibile specificare il percorso completo nel `privatekeyFile` e gli argomenti certificateFile.
>
>È inoltre necessario essere autenticati per eseguire l&#39;aggiornamento, quindi assicurati di aggiungere il comando cURL con il comando `-u user:passeword` parametro .
>
>Un comando post cURL corretto dovrebbe essere simile al seguente:

```shell
curl -u user:password -F "keystorePassword=password" -F "keystorePasswordConfirm=password" -F "truststorePassword=password" -F "truststorePasswordConfirm=password" -F "privatekeyFile=@localhostprivate.der" -F "certificateFile=@localhost.crt" -F "httpsHostname=host.example.com" -F "httpsPort=8443" https://host:port/libs/granite/security/post/sslSetup.html
```

#### Più certificati utilizzando cURL {#multiple-certificates-using-curl}

Puoi inviare al servlet una catena di certificati ripetendo il parametro certificateFile come riportato di seguito:

`-F "certificateFile=@root.crt" -F "certificateFile=@localhost.crt"..`

Dopo aver eseguito il comando, verifica che tutti i certificati siano stati inviati all&#39;archivio chiavi. Controlla il keystore da:\
[http://localhost:4502/libs/granite/security/content/userEditor.html/home/users/system/security/ssl-service](http://localhost:4502/libs/granite/security/content/userEditor.html/home/users/system/security/ssl-service)
