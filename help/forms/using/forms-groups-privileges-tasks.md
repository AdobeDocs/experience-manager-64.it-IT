---
title: AEM Forms su gruppi OSGi e privilegi
seo-title: AEM Forms su gruppi OSGi e privilegi
description: Assegnazione di utenti ai gruppi per gestire AEM Forms su OSGi
seo-description: Assegnazione di utenti ai gruppi per gestire AEM Forms su OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
translation-type: tm+mt
source-git-commit: f87d70515a385fb23b36797e468325fa1a5e9ff4
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---


# AEM Forms su gruppi OSGi e privilegi {#aem-forms-on-osgi-groups-and-privileges}

Assegnazione di utenti ai gruppi per gestire AEM Forms su OSGi

Potete [creare gruppi](/help/sites-administering/user-group-ac-admin.md#group-administration) e assegnare criteri e [utenti](/help/sites-administering/user-group-ac-admin.md#user-administration) ai gruppi in AEM. Tali criteri controllano i privilegi degli utenti che fanno parte del gruppo.

Dopo aver installato il pacchetto [aggiuntivo](/help/forms/using/installing-configuring-aem-forms-osgi.md)AEM Forms, i gruppi menzionati in questo articolo, quali form-user e form-power-user, sono automaticamente disponibili per l&#39;assegnazione. Nella tabella seguente sono elencate le attività che un utente può eseguire per AEM Forms su OSGi in base alle assegnazioni dei gruppi:

<table> 
 <tbody>
  <tr>
   <td>Gruppo</td> 
   <td>Attività</td> 
  </tr>
  <tr>
   <td>forms-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Creare, visualizzare in anteprima, pubblicare e inviare moduli adattivi</li> 
     <li>Creazione, anteprima e pubblicazione di comunicazioni interattive e frammenti di documento</li> 
     <li>Caricare le risorse in un’istanza di AEM</li> 
     <li>Creazione di temi</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>form-power-user</td> 
   <td>
    <ul> 
     <li>Creare, visualizzare in anteprima, pubblicare e inviare moduli adattivi</li> 
     <li>Creazione, anteprima e pubblicazione di comunicazioni interattive e frammenti di documento</li> 
     <li>Creazione di script per i moduli adattivi tramite l'editor di codice</li> 
     <li>Caricare le risorse inclusi gli script</li> 
     <li>Creazione di temi</li> 
     <li>Importa pacchetti contenenti XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>form-submit-reviewers</td> 
   <td>
    <ul> 
     <li>Esaminare i contributi</li> 
     <li>Approvare o rifiutare gli invii</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Creazione e anteprima di moduli adattivi o modelli di comunicazione interattiva</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Creazione e modifica di un modello dati modulo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>agente utente</td> 
   <td>
    <ul> 
     <li>Accedere a lettere di gestione della corrispondenza o a comunicazioni interattive mediante l'interfaccia utente dell'agente</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>editor di workflow</p> </td> 
   <td>
    <ul> 
     <li>Creare un’applicazione in entrata</li> 
     <li>Creare un modello di workflow</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Utilizzare le applicazioni inbox AEM</li> 
     <li>Gestione delle istanze del flusso di lavoro</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Configura PDF Generator</li> 
     <li>Configura cartella esaminata</li> 
     <li>Gestione delle applicazioni di workflow</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. L&#39;utente con privilegi di gruppo di moduli non è in grado di scrivere script per i moduli adattivi.
1. L&#39;utente con privilegi di gruppo di autori di modelli non può scrivere script per i modelli.

