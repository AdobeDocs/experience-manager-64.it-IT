---
title: Nozioni di base sui messaggi
seo-title: Nozioni di base sui messaggi
description: Panoramica del componente Messaggistica
seo-description: Panoramica del componente Messaggistica
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
translation-type: tm+mt
source-git-commit: 98fae2d51d73bda946f3c398e9276fe4d5a8a0fe
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---


# Nozioni di base sui messaggi {#messaging-essentials}

Questa pagina illustra i dettagli dell’utilizzo del componente Messaggi per includere una funzione di messaggistica in un sito Web.

## Essentials for Client-Side {#essentials-for-client-side}

**Componi messaggio**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/composemessaggio</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
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
   <td><a href="messaging.md">Configurazione dei messaggi</a></td> 
  </tr> 
 </tbody> 
</table>

**Elenco** messaggi (per Inbox, Inviato e Cestino)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>social/messaging/components/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>css</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>proprietà</strong></td> 
   <td>Vedere <a href="configure-messaging.md">Configurazione dei messaggi</a></td> 
  </tr> 
  <tr> 
   <td><strong>configurazione amministratore</strong></td> 
   <td><a href="messaging.md">Configurazione dei messaggi</a></td> 
  </tr> 
 </tbody> 
</table>

Vedere anche Personalizzazioni lato [client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [Configurazione dei messaggi](configure-messaging.md)

* [API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) client di messaggistica per componenti SCF

* [API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) di messaggistica per il servizio

* [Endpoint di messaggistica](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [Personalizzazioni lato server](server-customize.md)

>[!CAUTION]
>
>Il parametro String *non deve contenere una barra finale &quot;/&quot; per i seguenti metodi di MessageBuilder:
>
>* `setInboxPath`()
>* `setSentItemsPath`()

>
>
Ad esempio:
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Sito community {#community-site}

Una struttura del sito community, creata utilizzando la procedura guidata, includerà la funzione di messaggistica selezionata. Consulta `User Management` Impostazioni della console [Siti](sites-console.md#user-management)community.

### Codice di esempio: Notifica ricevuta messaggio {#sample-code-message-received-notification}

La funzione Messaggi social genera eventi per le operazioni, ad esempio `send`, `marking read`, `marking delete`. Questi eventi possono essere rilevati e le azioni eseguite sui dati contenuti nell’evento.

L&#39;esempio seguente fa riferimento a un gestore di eventi che ascolta l&#39; `message sent` evento e invia un messaggio e-mail a tutti i destinatari del messaggio che utilizzano l&#39; `Day CQ Mail Service`.

Per provare lo script di esempio lato server, sarà necessario un ambiente di sviluppo e la capacità di creare un bundle OSGi.

1. Login as an administrator to ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. Crea un `bundle node`in `/apps/engage/install` con nomi arbitrari, come

   * **[!UICONTROL Nome]** simbolico: com.interazione.media.social.messaging.MessagingNotification
   * **[!UICONTROL Nome]**: Notifiche per messaggi introduttivi sull’esercitazione
   * **[!UICONTROL Descrizione]**: un servizio di esempio per inviare una notifica e-mail agli utenti che ricevono un messaggio
   * **[!UICONTROL Pacchetto]**: `com.engage.media.social.messaging.notification`

1. Accedi a `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. Eliminare la `Activator.java` classe creata automaticamente
   1. Crea classe `MessageEventHandler.java`
   1. Copia/incolla il codice riportato di seguito in `MessageEventHandler.java`

1. Fate clic su **[!UICONTROL Salva tutto]**
1. Individuare `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` e aggiungere tutte le istruzioni di importazione come scritte nel `MessageEventHandler.java` codice.
1. Creare il bundle
1. Verificare che il servizio `Day CQ Mail Service`OSGi sia configurato
1. Effettua il login come utente dimostrativo e invia un&#39;e-mail a un altro utente
1. Il destinatario deve ricevere un&#39;e-mail relativa a un nuovo messaggio

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

