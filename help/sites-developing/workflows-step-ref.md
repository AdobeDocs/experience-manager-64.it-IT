---
title: Guida di riferimento per i passaggi dei flussi di lavoro
seo-title: Guida di riferimento per i passaggi dei flussi di lavoro
description: Guida di riferimento per i passaggi dei flussi di lavoro
seo-description: 'null'
uuid: 72a64495-d1b1-49e7-8257-d6b2ed36961c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 25f0e0f7-9570-4748-81cb-ccec6492c0b4
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2833'
ht-degree: 3%

---


# Guida di riferimento per i passaggi dei flussi di lavoro{#workflow-step-reference}

I modelli di flusso di lavoro sono composti da una serie di passaggi di vari tipi. A seconda del tipo, questi passaggi possono essere configurati ed estesi con parametri e script per fornire la funzionalità e il controllo necessari.

>[!NOTE]
>
>Questa sezione descrive i passaggi standard del flusso di lavoro.
>
>Per i passaggi specifici del modulo consulta anche:
>
>* [Riferimento dettagliato sui flussi di lavoro per AEM Forms](/help/forms/using/aem-forms-workflow-step-reference.md)
>* [Elaborazione delle risorse tramite gestori di contenuti multimediali e flussi di lavoro](/help/assets/media-handlers.md)

>



## Proprietà passaggio {#step-properties}

Ogni componente del passaggio dispone di una finestra di dialogo **[!UICONTROL Proprietà passaggio]** che consente di definire e modificare le proprietà richieste.

### Proprietà del passaggio - Scheda comune {#step-properties-common-tab}

Per la maggior parte dei componenti dei passaggi del flusso di lavoro è disponibile una combinazione delle seguenti proprietà, nella scheda **[!UICONTROL Comune]** della finestra di dialogo delle proprietà:

* **[!UICONTROL Titolo]**

   Titolo del passaggio.

* **[!UICONTROL Descrizione]**

   Una descrizione del passaggio.

* **[!UICONTROL Stadio flusso di lavoro]**

   Un selettore a discesa per applicare un elemento [Stage](/help/sites-developing/workflows.md#workflow-stages) al passaggio.

* **[!UICONTROL Timeout]**

   Il periodo dopo il quale il passaggio verrà &quot;interrotto&quot;.

   Puoi scegliere tra: **[!UICONTROL Off]**, **[!UICONTROL Immediato]**, **[!UICONTROL 1h]**, **[!UICONTROL 6h]**, **[!UICONTROL 12h]**, **[!UICONTROL 24h]**.

* **[!UICONTROL Gestore timeout]**

   Il gestore che controllerà il flusso di lavoro quando il passaggio scade; ad esempio:

   `Auto Advancer`

* **[!UICONTROL Avanzamento gestore]**

   Seleziona questa opzione per avanzare automaticamente il flusso di lavoro al passaggio successivo dopo l’esecuzione. Se non è selezionato, lo script di implementazione deve gestire l’avanzamento del flusso di lavoro.

#### Proprietà passaggio: scheda Utente/gruppo {#step-properties-user-group-tab}

Le seguenti proprietà sono disponibili per molti componenti dei passaggi del flusso di lavoro, nella scheda **[!UICONTROL Utente/Gruppo]** della finestra di dialogo delle proprietà:

* **[!UICONTROL Notifica all&#39;utente via e-mail]**

   * Puoi inviare una notifica ai partecipanti inviando loro un messaggio e-mail quando il flusso di lavoro raggiunge il passaggio .
   * Se attivato, un messaggio e-mail verrà inviato all&#39;utente definito dalla proprietà **[!UICONTROL Utente/Gruppo]** o a ciascun membro del gruppo, se è definito un gruppo.

* **[!UICONTROL Utente/Gruppo]**

   * Una casella di selezione a discesa consente di navigare e selezionare un utente o un gruppo.
   * Se assegni il passaggio a un utente specifico, solo questo utente può intervenire sul passaggio.
   * Se assegni il passaggio a un intero gruppo, quando il flusso di lavoro raggiunge questo passaggio tutti gli utenti del gruppo avranno l&#39;azione nella **[!UICONTROL Casella in entrata flusso di lavoro]**.
   * Per ulteriori informazioni, consulta [Partecipazione ai flussi di lavoro](/help/sites-authoring/workflows-participating.md) .

## Suddivisione E {#and-split}

Il **[!UICONTROL AND Split]** crea una suddivisione nel flusso di lavoro, dopodiché entrambi i rami saranno attivi. Puoi aggiungere i passaggi del flusso di lavoro a ogni ramo in base alle tue esigenze. Questo passaggio ti consente di introdurre più percorsi di elaborazione nel flusso di lavoro. Ad esempio, puoi consentire che determinati passaggi di revisione si verifichino in parallelo, risparmiando tempo.

![wf-26](assets/wf-26.png)

### AND Split - Configurazione {#and-split-configuration}

* Modifica le proprietà **[!UICONTROL AND Split]** :

   * **[!UICONTROL Nome]** diviso: assegnare un nome a scopo esplicativo.
   * Selezionare il numero di rami richiesti; 2, 3, 4 o 5.

* Aggiungi i passaggi del flusso di lavoro ai rami come necessario.

   ![wf-27](assets/wf-27.png)

## Passaggio contenitore {#container-step}

Un passaggio **[!UICONTROL Container]** avvia un altro modello di flusso di lavoro che viene eseguito come flusso di lavoro secondario.

Questo **[!UICONTROL Contenitore]** consente di riutilizzare i modelli di flusso di lavoro per implementare sequenze di passaggi comuni. Ad esempio, un modello di flusso di lavoro di traduzione può essere utilizzato in più flussi di lavoro di modifica.

![wf-28](assets/wf-28.png)

### Passaggio contenitore - Configurazione {#container-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* **[!UICONTROL Contenitore]**

   * **[!UICONTROL Flusso di lavoro secondario]**: Seleziona il flusso di lavoro da avviare.

## Passaggio GoTo {#goto-step}

Il **[!UICONTROL Passaggio]** consente di specificare il passaggio successivo nel modello di flusso di lavoro da eseguire, in base al risultato di uno script ECMAScript:

* `true`: Il passaggio specificato viene completato  **[!UICONTROL da Passaggio]** completato e il motore del flusso di lavoro esegue il passaggio specificato.

* `false`: Il passaggio successivo da eseguire è determinato dalla logica di indirizzamento  **[!UICONTROL Passaggio]** completato e dalla logica di indirizzamento normale.

Il **[!UICONTROL Passaggio]** consente di implementare strutture di indirizzamento avanzate nei modelli di flusso di lavoro. Ad esempio, per implementare un ciclo, è possibile definire il **[!UICONTROL Passaggio di destinazione]** per eseguire un passaggio precedente nel flusso di lavoro, con lo script che valuta una condizione di ciclo.

### Passaggio a : configurazione {#goto-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* **[!UICONTROL Processo]**

   * **[!UICONTROL Il passaggio da]**: Seleziona il passaggio da eseguire.
   * **[!UICONTROL Percorso]** script: Percorso di ECMAScript che determina l&#39;esecuzione del  **[!UICONTROL Passaggio]**.
   * **[!UICONTROL Script]**: ECMAScript che determina se eseguire il  **[!UICONTROL Passaggio]** di destinazione.

>[!CAUTION]
>
>Specificare il percorso **[!UICONTROL Script]** o **[!UICONTROL Script]**. Non è possibile utilizzare entrambe le opzioni contemporaneamente. Se si specificano i valori per entrambe le proprietà, il passaggio utilizza il percorso **[!UICONTROL Script]**.

#### Simulazione di un loop per {#simulating-a-for-loop}

Per simulare un ciclo for è necessario mantenere un conteggio del numero di iterazioni del ciclo che si sono verificate:

* In genere, il conteggio rappresenta un indice degli elementi su cui viene eseguito il processo nel flusso di lavoro.
* Il conteggio viene valutato come criterio di uscita del ciclo.

Ad esempio, per implementare un flusso di lavoro che esegue un&#39;azione su più nodi JCR, puoi utilizzare un contatore di loop come indice per i nodi. Per mantenere il conteggio, memorizza un valore `integer` nella mappa dati dell’istanza del flusso di lavoro. Utilizza lo script del **[!UICONTROL Passaggio]** per incrementare il conteggio e confrontare il conteggio con i criteri di uscita.

```
function check(){
   var count=0;
   var keyname="loopcount"
   try{
      if (workflowData.getMetaDataMap().containsKey(keyname)){ 
        log.info("goto script: found loopcount key");
        count= parseInt(workflowData.getMetaDataMap().get(keyname))+1;
      } 
 
     workflowData.getMetaDataMap().put(keyname,count);
 
     }catch(err) {
         log.info(err.message);
         return false;
    }
   if (parseInt(count) <7){
       return true;
   } else {
      return false;
   }
}
```

## Suddivisione O {#or-split}

Il **[!UICONTROL Split]** crea una suddivisione nel flusso di lavoro, dopodiché sarà attivo un solo ramo. Questo passaggio ti consente di introdurre i percorsi di elaborazione condizionale nel flusso di lavoro. Puoi aggiungere i passaggi del flusso di lavoro a ogni ramo in base alle tue esigenze.

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione di una divisione OR, consulta: [https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html](https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html)

![wf-29](assets/wf-29.png)

### Divisione OR - Configurazione {#or-split-configuration}

* Modifica le proprietà **[!UICONTROL OR Split]** :

   * **[!UICONTROL Comune]**

      * Selezionare il numero di rami richiesti; 2, 3, 4 o 5.
   * **[!UICONTROL Ramo :  *x*>]**

      * **[!UICONTROL Percorso]** script: Percorso di un file contenente lo script.
      * **[!UICONTROL Script]**: Aggiungi lo script nella casella.
      * **[!UICONTROL Percorso]** predefinito: Il ramo predefinito viene seguito quando più rami restituiscono true. Per impostazione predefinita, è possibile specificare un solo ramo.

   >[!NOTE]
   >
   >È disponibile una scheda separata per ogni ramo:
   >
   >* Lo script di ciascun ramo viene valutato uno alla volta.
   >* I rami vengono valutati da sinistra a destra.
   >* Viene eseguito il primo script che restituisce true.
   >* Se nessun ramo restituisce true, il flusso di lavoro non procede.


   >[!CAUTION]
   >
   >Specificare il percorso **[!UICONTROL Script]** o **[!UICONTROL Script]**. Non è possibile utilizzare entrambe le opzioni contemporaneamente. Se si specificano i valori per entrambe le proprietà, il passaggio utilizza il percorso **[!UICONTROL Script]**.

   >[!NOTE]
   >
   >Consulta [Definizione di una regola per una divisione OR](/help/sites-developing/workflows-models.md#example-defining-a-rule-for-an-or-split).

* Aggiungi i passaggi del flusso di lavoro ai rami come necessario.

## Passaggi e scelte dei partecipanti {#participant-steps-and-choosers}

### Passaggio partecipante {#participant-step}

Un **[!UICONTROL Passaggio partecipante]** consente di assegnare la proprietà per una particolare azione. Il flusso di lavoro procederà solo quando l’utente ha riconosciuto manualmente il passaggio. Viene utilizzato quando desideri che un utente esegua un’azione sul flusso di lavoro; ad esempio, un passaggio di revisione.

Sebbene non sia direttamente correlata, l’autorizzazione utente deve essere presa in considerazione al momento dell’assegnazione di un’azione; l’utente deve avere accesso alla pagina che è il payload del flusso di lavoro.

#### Passaggio partecipante: configurazione {#participant-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* [**[!UICONTROL Utente/Gruppo]**](#step-properties-user-group-tab)

>[!NOTE]
>
>L’iniziatore del flusso di lavoro viene sempre informato quando:
>
>* Il flusso di lavoro viene completato (completato).
>* Il flusso di lavoro viene interrotto (terminato).

>



>[!NOTE]
>
>Per abilitare le notifiche e-mail, è necessario configurare alcune proprietà. Puoi anche personalizzare il modello e-mail o aggiungere un modello e-mail per una nuova lingua. Consulta [Configurazione notifica e-mail](/help/sites-administering/notification.md) per configurare le notifiche e-mail in AEM.

### Passaggio partecipante finestra di dialogo {#dialog-participant-step}

Utilizza un **[!UICONTROL Passaggio partecipante finestra di dialogo]** per raccogliere informazioni dall&#39;utente a cui è assegnato l&#39;elemento di lavoro. Questo passaggio è utile per raccogliere piccole quantità di dati utilizzate più avanti nel flusso di lavoro.

Al termine del passaggio, la finestra di dialogo **[!UICONTROL Completa elemento di lavoro]** contiene i campi definiti nella finestra di dialogo. I dati raccolti nei campi vengono memorizzati nei nodi del payload del flusso di lavoro. I passaggi successivi del flusso di lavoro possono quindi leggere il valore dal repository.

Per configurare il passaggio, specificare il gruppo o l’utente a cui assegnare l’elemento di lavoro e il percorso della finestra di dialogo.

#### Passaggio partecipante finestra di dialogo - Configurazione {#dialog-participant-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* [**[!UICONTROL Utente/Gruppo]**](#step-properties-user-group-tab)
* **[!UICONTROL Finestra di dialogo]**

   * **[!UICONTROL Percorso finestra di dialogo**]: Percorso del nodo di dialogo della finestra di dialogo [creata](#dialog-participant-step-creating-a-dialog).

#### Passaggio partecipante finestra di dialogo - Creazione di una finestra di dialogo{#dialog-participant-step-creating-a-dialog}

Per creare una finestra di dialogo:

* Decidi dove saranno memorizzati i dati risultanti [nel payload](#dialog-participant-step-storing-data-in-the-payload).
* [Definire la finestra di dialogo; ciò include la definizione dei campi utilizzati per raccogliere (e salvare) i dati](#dialog-participant-step-dialog-definition).

#### Passaggio partecipante finestra di dialogo - Memorizzazione dei dati nel payload {#dialog-participant-step-storing-data-in-the-payload}

Puoi memorizzare i dati dei widget nel payload del flusso di lavoro o nei metadati dell’elemento di lavoro. Il formato della proprietà `name` del nodo del widget determina la posizione di memorizzazione dei dati.

* **[!UICONTROL Archiviare i dati con il payload]**

   * Per memorizzare i dati dei widget come proprietà del payload del flusso di lavoro, utilizza il formato seguente per il valore della proprietà name del nodo del widget:

      `./jcr:content/nodename`

   * I dati vengono memorizzati nella proprietà `nodename` del nodo di payload. Se il nodo non contiene tale proprietà, viene creata la proprietà .
   * Quando viene memorizzato con il payload, gli usi successivi della finestra di dialogo con lo stesso payload sovrascrivono il valore della proprietà.

* **[!UICONTROL Archiviare i dati con l’elemento di lavoro]**

   * Per memorizzare i dati dei widget come proprietà dei metadati dell&#39;elemento di lavoro, utilizza il formato seguente per il valore della proprietà name:

      `nodename`

   * I dati vengono memorizzati nella proprietà `nodename` dell&#39;elemento di lavoro `metadata`. I dati vengono conservati se la finestra di dialogo viene successivamente utilizzata con lo stesso payload.

#### Passaggio partecipante finestra di dialogo - Definizione finestra di dialogo {#dialog-participant-step-dialog-definition}

1. **[!UICONTROL Struttura finestra di dialogo]**

   Le finestre di dialogo per i passaggi partecipanti alla finestra di dialogo sono simili alle finestre di dialogo create per creare i componenti. Sono memorizzati in:

   `/apps/myapp/workflow/dialogs`

   Le finestre di dialogo per l’interfaccia touch standard hanno la seguente struttura di nodi:

   ```xml
   newComponent (cq:Component)
     |- cq:dialog (nt:unstructured)
       |- content 
         |- layout 
           |- items 
             |- column 
               |- items 
                 |- component0
                 |- component1
                 |- ...
   ```

   >[!NOTE]
   >
   >Per ulteriori informazioni, consulta [Creazione e configurazione di una finestra di dialogo](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog).

1. **[!UICONTROL Proprietà Percorso finestra di dialogo]**

   La proprietà **[!UICONTROL Dialog Participant Step]** include la proprietà **[!UICONTROL Dialog Path]** (insieme alle proprietà di un [Participant Step](#participant-step)). Il valore della proprietà **[!UICONTROL Percorso finestra di dialogo]** rappresenta il percorso del nodo `dialog` della finestra di dialogo.

   Ad esempio, la finestra di dialogo è contenuta in un componente denominato `EmailWatch` memorizzato nel nodo :

   `/apps/myapp/workflows/dialogs`

   Per l’interfaccia touch viene utilizzato il seguente valore per la proprietà **[!UICONTROL Percorso finestra di dialogo]** :

   `/apps/myapp/workflow/dialogs/EmailWatch/cq:dialog`

   ![wf-30](assets/wf-30.png)

1. **Definizione finestra di dialogo di esempio**

   Il seguente frammento di codice XML rappresenta una finestra di dialogo che memorizza un valore `String` nel nodo `watchEmail` del contenuto del payload. Il nodo titolo rappresenta il componente [TextField](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/textfield/index.html) :

   ```xml
   jcr:primaryType="nt:unstructured" 
       jcr:title="Watcher Email Address Dialog" 
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout jcr:primaryType="nt:unstructured" 
               margin="false" 
               sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
           />
           <items jcr:primaryType="nt:unstructured">
               <column jcr:primaryType="nt:unstructured"
                   sling:resourceType="granite/ui/components/foundation/container">
                   <items jcr:primaryType="nt:unstructured">
                       <title jcr:primaryType="nt:unstructured" 
                           fieldLabel="Notification Email Address" 
                           name="./jcr:content/watchEmails"
                           sling:resourceType="granite/ui/components/foundation/form/textfield"
                       />
                   </items>
               </column>
           </items>
       </content>
   </cq:dialog>
   ```

   Questo esempio, nel caso dell’interfaccia touch, darà luogo a una finestra di dialogo come:

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Passaggio partecipante dinamico {#dynamic-participant-step}

Il componente **[!UICONTROL Passaggio partecipante dinamico]** è simile a **[!UICONTROL Passaggio partecipante]** con la differenza che il partecipante viene selezionato automaticamente in fase di esecuzione.

Per configurare il passaggio, è necessario selezionare un **[!UICONTROL Selettore partecipante]** che identifichi il partecipante a cui assegnare l&#39;elemento di lavoro, insieme a una finestra di dialogo.

#### Passaggio partecipante dinamico - Configurazione {#dynamic-participant-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* **[!UICONTROL Selettore partecipanti]**

   * **[!UICONTROL Selettore]** partecipante: Nome del selettore  [partecipante creato](#dynamic-participant-step-developing-the-participant-chooser).
   * **[!UICONTROL Argomenti]**: Eventuali argomenti richiesti.
   * **[!UICONTROL E-mail]**: Se inviare una notifica e-mail all’utente.

* **[!UICONTROL Finestra di dialogo]**

   * **[!UICONTROL Percorso]** finestra di dialogo: Percorso del nodo di dialogo della  [finestra di dialogo creata (come con il  **Passaggio partecipante finestra di dialogo**)](#dialog-participant-step-creating-a-dialog).

#### Passaggio partecipante dinamico - Sviluppo del selettore partecipante {#dynamic-participant-step-developing-the-participant-chooser}

Si crea il selettore dei partecipanti. Pertanto, puoi utilizzare qualsiasi logica o criterio di selezione. Ad esempio, il selettore dei partecipanti può selezionare l&#39;utente (all&#39;interno di un gruppo) con il minor numero di elementi di lavoro. È possibile creare un numero qualsiasi di partecipanti che scelgono di utilizzare con istanze diverse del componente **Passaggio partecipante dinamico** nei modelli di flusso di lavoro.

Creare un servizio OSGi o un codice ECMAScript che seleziona un utente a cui assegnare l&#39;elemento di lavoro.

* **[!UICONTROL ECMAscript]**

   Gli script devono includere una funzione denominata getParticipant che restituisce un ID utente come valore `String`. Archivia gli script personalizzati, ad esempio nella cartella `/apps/myapp/workflow/scripts` o in una sottocartella.

   Uno script di esempio è incluso in un&#39;istanza AEM standard:

   `/libs/workflow/scripts/initiator-participant-chooser.ecma`

   >[!CAUTION]
   >
   >*Non è necessario* modificare nulla nel percorso `/libs`.
   >
   >
   >Questo perché il contenuto di `/libs` viene sovrascritto la prossima volta che aggiorni l&#39;istanza (e può essere sovrascritto quando applichi un hotfix o un feature pack).

   Questo script seleziona l’iniziatore del flusso di lavoro come partecipante:

   ```
   function getParticipant() {
       return workItem.getWorkflow().getInitiator();
   }
   ```

   >[!NOTE]
   >
   >Il componente **[!UICONTROL Selettore partecipante iniziatore flusso di lavoro]** estende il **[!UICONTROL Passaggio partecipante dinamico]** e utilizza questo script come implementazione del passaggio.

* **[!UICONTROL Servizio OSGi]**

   I servizi devono implementare l&#39;interfaccia [com.day.cq.workflow.exec.ParticipantStepChooser](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/ParticipantStepChooser.html) . L’interfaccia definisce i seguenti membri:

   * `SERVICE_PROPERTY_LABEL` campo: Utilizzare questo campo per specificare il nome del selettore dei partecipanti. Il nome viene visualizzato in un elenco dei selettori dei partecipanti disponibili nelle proprietà **[!UICONTROL Passaggio partecipante dinamico]** .
   * `getParticipant` metodo: Restituisce l&#39;ID principale risolto dinamicamente come  `String` valore.

   >[!CAUTION]
   >
   >Il metodo `getParticipant` restituisce l&#39;ID principale risolto dinamicamente. Può trattarsi di un ID gruppo o di un ID utente.
   >
   >
   >Tuttavia, un id gruppo può essere utilizzato solo per un **[!UICONTROL Passaggio partecipante]**, quando viene restituito un elenco di partecipanti. Per un **[!UICONTROL Passaggio partecipante dinamico]** viene restituito un elenco vuoto che non può essere utilizzato per la delega.

   Per rendere la tua implementazione disponibile ai componenti **[!UICONTROL Passaggio partecipante dinamico]** , aggiungi la tua classe Java a un bundle OSGi che esporta il servizio e distribuisci il bundle sul server AEM.

   >[!NOTE]
   >
   >**[!UICONTROL Random Participant]** Choosers è un servizio di esempio che seleziona un utente casuale (  `com.day.cq.workflow.impl.process.RandomParticipantChooser`). L&#39;esempio di componente **[!UICONTROL Selettore casuale partecipanti]** estende il **[!UICONTROL Passaggio partecipante dinamico]** e utilizza questo servizio come implementazione passo.

#### Passaggio partecipante dinamico - Esempio di servizio di selezione partecipanti {#dynamic-participant-step-example-participant-chooser-service}

La seguente classe Java implementa l&#39;interfaccia `ParticipantStepChooser` . La classe restituisce il nome del partecipante che ha avviato il flusso di lavoro. Il codice utilizza la stessa logica utilizzata dallo script di esempio ( `initator-participant-chooser.ecma`).

L’annotazione `@Property` imposta il valore del campo `SERVICE_PROPERTY_LABEL` su `Workflow Initiator Participant Chooser`.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.osgi.framework.Constants;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.ParticipantStepChooser;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.metadata.MetaDataMap;

@Component
@Service
@Properties({
        @Property(name = Constants.SERVICE_DESCRIPTION, value = "An example implementation of a dynamic participant chooser."),
        @Property(name = ParticipantStepChooser.SERVICE_PROPERTY_LABEL, value = "Workflow Initiator Participant Chooser (service)") })
public class InitiatorParticipantChooser implements ParticipantStepChooser {

 private Logger logger = LoggerFactory.getLogger(this.getClass());

 public String getParticipant(WorkItem arg0, WorkflowSession arg1,
   MetaDataMap arg2) throws WorkflowException {

  String initiator = arg0.getWorkflow().getInitiator();
  logger.info("Assigning Dynamic Participant Step work item to {}",initiator);

  return initiator;
 }
}
```

Nella finestra di dialogo delle proprietà **[!UICONTROL Passaggio partecipante dinamico]** , l&#39;elenco **[!UICONTROL Selettore partecipante]** include l&#39;elemento `Workflow Initiator Participant Chooser (script)` che rappresenta questo servizio.

&quot;All’avvio del modello di flusso di lavoro, il registro indica l’ID dell’utente che ha avviato il flusso di lavoro e a cui è stato assegnato l’elemento di lavoro. In questo esempio, l’utente `admin` ha avviato il flusso di lavoro.

`13.09.2015 15:48:53.037 *INFO* [10.176.129.223 [1347565733037] POST /etc/workflow/instances HTTP/1.1] com.adobe.example.InitiatorParticipantChooser Assigning Dynamic Participant Step work item to admin`

### Passaggio partecipante modulo {#form-participant-step}

Il **[!UICONTROL Passaggio partecipante al modulo]** presenta un modulo quando l’elemento di lavoro viene aperto. Quando l’utente compila e invia il modulo, i dati del campo vengono memorizzati nei nodi del payload del flusso di lavoro.

Per configurare il passaggio, specificare il gruppo o l’utente a cui assegnare l’elemento di lavoro e il percorso del modulo.

>[!CAUTION]
>
>Questa sezione tratta la sezione [Forms dei componenti di base per l&#39;authoring delle pagine](/help/sites-authoring/default-components-foundation.md#form).

#### Passaggio partecipante modulo - Configurazione {#form-participant-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* [**[!UICONTROL Utente/Gruppo]**](#step-properties-user-group-tab)
* **[!UICONTROL Modulo]**

   * **[!UICONTROL Percorso]** modulo: Percorso del  [modulo creato](#form-participant-step-creating-the-form).

#### Passaggio partecipante modulo - Creazione del modulo {#form-participant-step-creating-the-form}

Creare un modulo da utilizzare normalmente con un **[!UICONTROL Passaggio partecipante al modulo]**. Tuttavia, i moduli per un Passaggio partecipante a un modulo devono avere le seguenti configurazioni:

* Per il componente **[!UICONTROL Inizio modulo]** deve essere impostata la proprietà **[!UICONTROL Tipo azione]** su `Edit Workflow Controlled Resource(s)`.

* Il componente **[!UICONTROL Inizio modulo]** deve avere un valore per la proprietà `Form Identifier` .

* Ai componenti modulo deve essere impostata la proprietà **Nome elemento** sul percorso del nodo in cui sono memorizzati i dati del campo. Il percorso deve individuare un nodo nel contenuto del payload del flusso di lavoro. Il valore utilizza il formato seguente:

   `./jcr:content/path_to_node`

* Il modulo deve includere un componente **[!UICONTROL Pulsante di invio flusso di lavoro]**. Non configuri proprietà del componente.

I requisiti del flusso di lavoro determinano dove memorizzare i dati dei campi. Ad esempio, i dati dei campi possono essere utilizzati per configurare le proprietà del contenuto della pagina. Il seguente valore di una proprietà **[!UICONTROL Nome elemento]** memorizza i dati del campo come valore della proprietà `redirectTarget` del nodo `jcr:content`:

`./jcr:content/redirectTarget`

Nell’esempio seguente, i dati dei campi vengono utilizzati come contenuto di un componente **[!UICONTROL Testo]** nella pagina del payload:

`./jcr:content/par/text_3/text`

&quot;Il primo esempio può essere utilizzato per qualsiasi pagina sottoposta a rendering dal componente `cq:Page`. Il secondo esempio può essere utilizzato solo quando la pagina di payload include un componente **Testo** con un ID di `text_3`.

Il modulo può trovarsi in qualsiasi punto dell’archivio, tuttavia gli utenti del flusso di lavoro devono essere autorizzati a leggere il modulo.

### Selettore casuale partecipanti {#random-participant-chooser}

Il passaggio **[!UICONTROL Selettore casuale partecipante]** è un selettore partecipante che assegna l’elemento di lavoro generato a un utente selezionato in modo casuale da un elenco.

![wf-31](assets/wf-31.png)

#### Selettore casuale partecipanti - Configurazione {#random-participant-chooser-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* **[!UICONTROL Argomenti]**

   * **[!UICONTROL Partecipanti]**: Specifica l&#39;elenco di utenti disponibili per la selezione. Per aggiungere un utente all&#39;elenco, fare clic su **[!UICONTROL Aggiungi elemento]** e digitare il percorso principale del nodo utente o l&#39;ID utente. L&#39;ordine degli utenti non influisce sulla probabilità di assegnazione di un elemento di lavoro.

### Selettore partecipante iniziatore flusso di lavoro {#workflow-initiator-participant-chooser}

Il passaggio **[!UICONTROL Selettore partecipante iniziatore flusso di lavoro]** è un selettore dei partecipanti che assegna l’elemento di lavoro generato all’utente che ha avviato il flusso di lavoro. Non sono disponibili proprietà da configurare diverse dalle proprietà **[!UICONTROL Common]** .

#### Selettore partecipante iniziatore flusso di lavoro - Configurazione {#workflow-initiator-participant-chooser-configuration}

Per configurare il passaggio , modifica utilizzando le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)

## Passaggio processo {#process-step}

Un **[!UICONTROL Passaggio processo]** esegue un ECMAScript o chiama un servizio OSGi per eseguire l&#39;elaborazione automatica.

![wf-32](assets/wf-32.png)

### Passaggio del processo: configurazione {#process-step-configuration}

Per configurare il passaggio , modifica e utilizza le seguenti schede:

* [**[!UICONTROL Comune]**](#step-properties-common-tab)
* **[!UICONTROL Processo]**

   * **[!UICONTROL Processo]**: Implementazione del processo da eseguire. Utilizzare il menu a discesa per selezionare il servizio ECMAScript o OSGi. Per informazioni su:

      * I servizi standard ECMAScripts e OSGi, vedi [Processi incorporati per i passaggi del processo](/help/sites-developing/workflows-process-ref.md).
      * Creazione di script ECMAS per un passaggio **[!UICONTROL Process]**, vedere [Implementazione di un passaggio del processo con ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).
      * Creazione di servizi OSGi per un passaggio **[!UICONTROL Processo]**, vedere [Implementazione di un passaggio del processo con una classe Java](/help/sites-developing/workflows-customizing-extending.md#implementing-a-process-step-with-a-java-class).
   * **[!UICONTROL Avanzamento]** gestore: Seleziona questa opzione per avanzare automaticamente il flusso di lavoro al passaggio successivo dopo l’esecuzione. Se non è selezionato, lo script di implementazione deve gestire l’avanzamento del flusso di lavoro.
   * **[!UICONTROL Argomenti]**: Argomenti da passare al processo.


