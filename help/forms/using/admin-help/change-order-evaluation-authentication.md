---
title: Modificare l'ordine di valutazione per l'autenticazione
seo-title: Modificare l'ordine di valutazione per l'autenticazione
description: 'È possibile modificare l''ordine in cui AEM moduli valuta più provider di autenticazione. '
seo-description: 'È possibile modificare l''ordine in cui AEM moduli valuta più provider di autenticazione. '
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Modificare l&#39;ordine di valutazione per l&#39;autenticazione {#change-the-order-of-evaluation-for-authentication}

Se sono stati configurati più provider di autenticazione, è possibile modificare l&#39;ordine in cui AEM moduli li valuta per l&#39;autenticazione. L&#39;ordine dei provider di autenticazione elencati nel file config.xml determina l&#39;ordine di valutazione per l&#39;autenticazione.

1. Nella console di amministrazione, fate clic su Impostazioni > Gestione utente > Configurazione > Importa ed esporta file di configurazione.
1. Per esportare l’impostazione di configurazione corrente in un file, fate clic su Esporta e salvate il file di configurazione in un’altra posizione.
1. Trovare il seguente nodo nel file:

   ```as3
    <node name="AuthSchemes"> 
        <map />  
            <node name="CertificateAuth"> 
                <map> 
                    <entry key="order" value="3" />  
                    <entry key="name" value="edc.server.auth.scheme.certificate" />  
                </map> 
        </node> 
        <node name="Kerberos"> 
            <map> 
                <entry key="kerberosSPN" value="defaultSPN" />  
                <entry key="order" value="1" />  
                <entry key="name" value="edc.server.auth.scheme.kerberos" />  
            </map> 
    </node>
   ```

   In `<entry key="order" value="3" />`, modificare il valore di ciascun nodo per impostare l&#39;ordine della valutazione dell&#39;autenticazione.

1. Per importare il file aggiornato, in Gestione utente fate clic su Configurazione > Importa ed esporta file di configurazione.
1. Fate clic su Sfoglia per trovare il file, fate clic su Importa, quindi fate clic su OK.

