---
title: Componenti OSGi Events for Community
seo-title: Componenti OSGi Events for Community
description: Gli eventi OSGi vengono inviati che possono attivare listener asincroni
seo-description: Gli eventi OSGi vengono inviati che possono attivare listener asincroni
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 4%

---


# Componenti OSGi Events for Communities {#osgi-events-for-communities-components}

## Panoramica {#overview}

Quando i membri interagiscono con le funzioni Community, vengono inviati eventi OSGi che possono attivare listener asincroni, come notifiche o gamificazioni (punteggio e contrassegno).

L&#39;istanza di un componente [SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) registra gli eventi come `actions`che si verificano per un `topic`. SocialEvent include un metodo per restituire un elemento `verb`associato all&#39;azione. Esiste una relazione *n-1* tra `actions`e `verbs`.

Per i componenti Community forniti nella release, le tabelle seguenti descrivono la `verbs`definita per ogni `topic`disponibile per l&#39;uso.

## Argomenti e verbi {#topics-and-verbs}

[Calendar ](calendar-basics-for-developers.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/Calendar

| **Verbo** | **Descrizione** |
|---|---|
| POST | membro crea un evento del calendario |
| AGGIUNGI | commenti dei membri su un evento del calendario |
| AGGIORNA | evento del calendario del membro o commento modificato |
| ELIMINA | l&#39;evento o il commento del calendario del membro viene eliminato |

[Commenti ](essentials-comments.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verbo** | **Descrizione** |
|---|---|
| POST | crea un commento |
| AGGIUNGI | risposta del membro al commento |
| AGGIORNA | commento del membro ?? stato modificato |
| ELIMINA | commento del membro ?? eliminato |

[Libreria file ](essentials-file-library.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verbo** | **Descrizione** |
|---|---|
| POST | create una cartella |
| ATTACCO | il membro carica un file |
| AGGIORNA | il membro aggiorna una cartella o un file |
| ELIMINA | il membro elimina una cartella o un file |

[Forum ](essentials-forum.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verbo** | **Descrizione** |
|---|---|
| POST | membro crea argomento del forum |
| AGGIUNGI | risposte dei membri all&#39;argomento del forum |
| AGGIORNA | argomento forum o risposta del membro ?? modificato |
| ELIMINA | l&#39;argomento o la risposta del forum del membro viene eliminata |

[Journal ](blog-developer-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/journal

| **Verbo** | **Descrizione** |
|---|---|
| POST | un membro crea un articolo di blog |
| AGGIUNGI | commenti dei membri su un articolo di blog |
| AGGIORNA | articolo o commento del blog del membro ?? stato modificato |
| ELIMINA | l&#39;articolo o il commento del blog del membro viene eliminato |

[QnA ](qna-essentials.md)
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verbo** | **Descrizione** |
|---|---|
| POST | un membro crea una domanda QnA |
| AGGIUNGI | un membro crea una risposta QnA |
| AGGIORNA | la domanda o la risposta QnA del membro viene modificata |
| SELECT | la risposta del membro ?? selezionata |
| ANNULLA | la risposta del membro ?? deselezionata |
| ELIMINA | la domanda o la risposta QnA del membro viene eliminata |

[Recensioni ](reviews-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verbo** | **Descrizione** |
|---|---|
| POST | il membro crea una revisione |
| AGGIORNA | revisione membro |
| ELIMINA | la revisione del membro viene eliminata |

[Valutazione ](rating-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally

| **Verbo** | **Descrizione** |
|---|---|
| AGGIUNGI VALUTAZIONE | il contenuto del membro ?? stato valutato |
| RIMUOVI VALUTAZIONE | il contenuto del membro non ?? stato valutato |

[Voto ](essentials-voting.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally

| **Verbo** | **Descrizione** |
|---|---|
| AGGIUNGI VOTO | il contenuto del membro ?? stato votato |
| RIMUOVI VOTO | il contenuto del membro ?? stato respinto |

**Moderation enabled**
ComponentsSocialEvent  `topic`= com/adobe/cq/social/moderation

| **Verbo** | **Descrizione** |
|---|---|
| NEGA | contenuto del membro negato |
| FLAG-AS-INAPPROPRIATE | il contenuto del membro ?? contrassegnato |
| INAPPROPRIATO | contenuto del membro non contrassegnato |
| ACCETTARE | il contenuto del membro ?? approvato dal moderatore |
| CHIUDI | il membro chiude il commento alle modifiche e alle risposte |
| APRI | riapre commento membro |

## Eventi per componenti personalizzati {#events-for-custom-components}

Per un componente personalizzato, ?? necessario estendere la [classe astratta SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) per registrare gli eventi del componente come `actions`che si verificano per un `topic`.

L&#39;evento personalizzato sostituisce il metodo `getVerb()` in modo che venga restituito un `verb`appropriato per ogni `action`. La `verb` restituita per un&#39;azione pu?? essere utilizzata comunemente (come `POST`) o una specifica per il componente (come `ADD RATING`). Esiste una relazione *n-1* tra `actions`e `verbs`.

>[!NOTE]
>
>Verifica che un&#39;estensione personalizzata sia registrata con una classificazione inferiore a qualsiasi implementazione esistente nel prodotto.

### Pseudo-Code per evento componente personalizzato {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.Event](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);\
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);\
[com.adobe.granite.activitystreams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);\
[com.adobe.granite.activitystreams.Verbs](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

```java
package com.mycompany.recipe;

import org.osgi.service.event.Event;
import com.adobe.cq.social.scf.core.SocialEvent;
import com.adobe.granite.activitystreams.ObjectTypes;
import com.adobe.granite.activitystreams.Verbs;

/* 
 * The Recipe type, passed to RecipeEvent(), would be a custom Recipe class 
 * that extends either 
 * com.adobe.cq.social.scf.SocialComponent 
 * or
 * com.adobe.cq.social.scf.SocialCollectionComponent
 * See https://docs.adobe.com/docs/en/aem/6-2/develop/communities/scf/server-customize.html
 */

/**
 * Defines events that are triggered on a custom component, "Recipe".
 */
public class RecipeEvent extends SocialEvent<RecipeEvent.RecipeActions> {

    private static final long serialVersionUID = 1L;
    protected static final String PARENT_PATH = "PARENT_PATH";

    /**
     * The event topic suffix for Recipe events
     */
    public static final String RECIPE_TOPIC = "recipe";

    /**
     * @param recipe - the recipe resource on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final Recipe recipe, final String userId, final RecipeEvent.RecipeActions action) {
        String recipePath = recipe.getResource().getPath();
        String parentPath = (recipe.getParentComponent() != null) ? 
                             recipe.getParentComponent().getResource().getPath() : 
                             recipe.getSourceComponentId();
        this(recipePath, userId, parentPath, action);
    }

    /**
     * @param recipePath - the path to the recipe resource (jcr node) on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param parentPath - the path to the parent node of the recipe resource
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final String recipePath, final String userId, final String parentPath) {
        super(RECIPE_TOPIC, recipePath, userId, action, 
              new BaseEventObject(recipePath, ObjectTypes.ARTICLE), 
              new BaseEventObject(parentPath, ObjectTypes.COLLECTION),
              new HashMap<String, Object>(1) {
            private static final long serialVersionUID = 1L;
            {
                if (parentPath != null) {
                    this.put(PARENT_PATH, parentPath);
                }

            }
        });
    }

    private RecipeEvent (final Event event) {
      super(event);
    }

    /**
     * List of available recipe actions that can trigger a recipe event.
     */
    public static enum RecipeActions implements SocialEvent.SocialActions {
        RecipeAdded, 
        RecipeModified, 
        RecipeDeleted;

        @Override
        public String getVerb() {
            switch (this) {
                case RecipeAdded:
                    return Verbs.POST;
                case RecipeModified:
                    return Verbs.UPDATE;
                case RecipeDeleted:
                    return Verbs.DELETE;
                default:
                    throw new IllegalArgumentException("Unsupported action");
            }
        }
    }

}
```

## Esempio di EventListener per filtrare i dati del flusso di attivit?? {#sample-eventlistener-to-filter-activity-stream-data}

?? possibile ascoltare gli eventi allo scopo di modificare ci?? che appare nel flusso di attivit??.

Il seguente esempio di pseudo-codice rimuove gli eventi DELETE per il componente Commenti dal flusso di attivit??.

### Pseudo-codice per EventListener {#pseudo-code-for-eventlistener}

Richiede [l&#39;ultimo pacchetto di funzioni](deploy-communities.md#latestfeaturepack).

```java
package my.company.comments;

import java.util.Collections;
import java.util.Map;

import org.apache.commons.lang.StringUtils;
import org.apache.felix.scr.annotations.Activate;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Modified;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.osgi.PropertiesUtil;
import org.osgi.service.component.ComponentContext;

import com.adobe.cq.social.activitystreams.listener.api.ActivityStreamProviderExtension;
import com.adobe.cq.social.commons.events.CommentEvent.CommentActions;
import com.adobe.cq.social.scf.core.SocialEvent;

@Service
@Component(metatype = true, label = "My Comment Delete Event Filter",
        description = "Prevents comment DELETE events from showing up in activity streams")
public class CommentDeleteEventActivityFilter implements ActivityStreamProviderExtension {

    @Property(name = "ranking", intValue = 10)
    protected int ranking;

    @Activate
    public void activate(final ComponentContext ctx) {
        ranking = PropertiesUtil.toInteger(ctx.getProperties().get("ranking"), 10);
    }

    @Modified
    public void update(final Map<String, Object> props) {
        ranking = PropertiesUtil.toInteger(props.get("ranking"), 10);
    }

    @Override
    public boolean evaluate(final SocialEvent<?> evt, final Resource resource) {
        if (evt.getAction() != null && evt.getAction() instanceof SocialEvent.SocialActions) {
            final SocialEvent.SocialActions action = evt.getAction();
            if (StringUtils.equals(action.getVerb(), CommentActions.DELETED.getVerb())) {
                return false;
            }
        }
        return true;
    }

    @Override
    public Map<String, ? extends Object> getActivityProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public Map<String, ? extends Object> getActorProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String getName() {
        return "My Comment Delete Event Filter";
    }

    @Override
    public Map<String, ? extends Object> getObjectProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    /* Ensure a custom extension is registered with a ranking lower than any existing implementation in the product. */
    @Override
    public int getRanking() {
        return this.ranking;
    }

    @Override
    public Map<String, ? extends Object> getTargetProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String[] getStreamProviderPid() {
        return new String[]{"*"};
    }

}
```

