---
title: Nozioni di base sulla messaggistica
seo-title: Messaging Essentials
description: Panoramica del componente messaggistica
seo-description: Messaging component overview
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 3%

---

# Nozioni di base sulla messaggistica {#messaging-essentials}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Questa pagina illustra i dettagli dell’utilizzo del componente Messaggistica per includere una funzione di messaggistica su un sito web.

## Funzionalità di base per lato client {#essentials-for-client-side}

**Componi messaggio**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/compositemessage</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>modelli</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>proprietà</strong></td> 
   <td>vedere <a href="configure-messaging.md">Configurazione dei messaggi</a></td> 
  </tr> 
  <tr> 
   <td><strong>configurazione amministratore</strong></td> 
   <td><a href="messaging.md">Configurazione della messaggistica</a></td> 
  </tr> 
 </tbody> 
</table>

**Elenco messaggi** (per Posta in arrivo, Inviata e Cestino)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>modelli</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>proprietà</strong></td> 
   <td>Vedi <a href="configure-messaging.md">Configurazione dei messaggi</a></td> 
  </tr> 
  <tr> 
   <td><strong>configurazione amministratore</strong></td> 
   <td><a href="messaging.md">Configurazione della messaggistica</a></td> 
  </tr> 
 </tbody> 
</table>

Vedi anche [Personalizzazioni lato client](client-customize.md)

## Funzioni di base per lato server {#essentials-for-server-side}

* [Configurazione della messaggistica](configure-messaging.md)

* [API client di messaggistica](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) per componenti SCF

* [API di messaggistica](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) per il servizio

* [Endpoint di messaggistica](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

>[!CAUTION]
>
>Il parametro String deve *non *contenere una barra finale &quot;/&quot; per i seguenti metodi di MessageBuilder:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>Ad esempio:
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Sito community {#community-site}

Una struttura del sito community, creata utilizzando la procedura guidata, includerà la funzione di messaggistica selezionata. Vedi `User Management` impostazioni di [Console Sites della community](sites-console.md#user-management).

### Codice di esempio: Messaggio ricevuto notifica {#sample-code-message-received-notification}

La funzione Messaggi social genera eventi per operazioni, ad esempio `send`, `marking read`, `marking delete`. Questi eventi possono essere rilevati e le azioni intraprese sui dati contenuti nell’evento.

L&#39;esempio seguente è di un gestore eventi che ascolta il `message sent` e invia un’e-mail a tutti i destinatari del messaggio utilizzando `Day CQ Mail Service`.

Per provare lo script di esempio lato server, è necessario un ambiente di sviluppo e la capacità di creare un bundle OSGi.

1. Accedi come amministratore a ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. Crea un `bundle node`in `/apps/engage/install` con nomi arbitrari, quali

   * **[!UICONTROL Nome simbolico]**: com.eng.media.social.messaging.MessagingNotification
   * **[!UICONTROL Nome]**: Notifica dei messaggi tutorial introduttiva
   * **[!UICONTROL Descrizione]**: un servizio di esempio per l’invio di una notifica e-mail agli utenti che ricevono un messaggio
   * **[!UICONTROL Pacchetto]**: `com.engage.media.social.messaging.notification`

1. Accedi a `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. Elimina `Activator.java` classe creata automaticamente
   1. Crea classe `MessageEventHandler.java`
   1. Copia/incolla il codice sottostante in `MessageEventHandler.java`

1. Fai clic su **[!UICONTROL Salva tutto]**
1. Passa a `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` e aggiungi tutte le istruzioni di importazione scritte nella `MessageEventHandler.java` codice.
1. Creare il bundle
1. Assicurati `Day CQ Mail Service`Il servizio OSGi è configurato
1. Accedi come utente dimostrativo e invia un&#39;e-mail a un altro
1. Il destinatario deve ricevere un’e-mail relativa a un nuovo messaggio

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
