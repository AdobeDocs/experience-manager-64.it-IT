---
title: AEM Forms su gruppi e privilegi OSGi
seo-title: AEM Forms on OSGi Groups and Privileges
description: Assegnare gli utenti ai gruppi per gestire AEM Forms su OSGi
seo-description: Assign users to the groups to manage AEM Forms on OSGi
uuid: 9ebb3a4e-4c0e-4105-921f-58077fc45281
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 71412f5d-ff34-415f-baf8-d300756b93a9
role: Admin
exl-id: a79e863e-c316-422e-a565-b0ffdeffcc00
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 4%

---

# AEM Forms su gruppi e privilegi OSGi {#aem-forms-on-osgi-groups-and-privileges}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Assegnare gli utenti ai gruppi per gestire AEM Forms su OSGi

È possibile [creare gruppi](/help/sites-administering/user-group-ac-admin.md#group-administration) e assegna politiche e [utenti](/help/sites-administering/user-group-ac-admin.md#user-administration) ai gruppi in AEM. Questi criteri controllano i privilegi degli utenti che fanno parte del gruppo.

Una volta installata [Pacchetto aggiuntivo di AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md), i gruppi menzionati in questo articolo, come forms-user e forms-power-user, sono automaticamente disponibili per l&#39;assegnazione. Nella tabella seguente sono elencate le attività che un utente può eseguire per AEM Forms su OSGi in base alle assegnazioni dei gruppi:

<table> 
 <tbody>
  <tr>
   <td>Gruppo</td> 
   <td>Attività</td> 
  </tr>
  <tr>
   <td>form-user <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Creare, visualizzare in anteprima, pubblicare e inviare moduli adattivi</li> 
     <li>Creazione, visualizzazione in anteprima e pubblicazione di comunicazioni interattive e frammenti di documento</li> 
     <li>Caricare le risorse in un’istanza AEM</li> 
     <li>Creare temi</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>utenti di moduli</td> 
   <td>
    <ul> 
     <li>Creare, visualizzare in anteprima, pubblicare e inviare moduli adattivi</li> 
     <li>Creazione, visualizzazione in anteprima e pubblicazione di comunicazioni interattive e frammenti di documento</li> 
     <li>Creazione di script per i moduli adattivi tramite l’editor di codice</li> 
     <li>Caricare le risorse inclusi gli script</li> 
     <li>Creare temi</li> 
     <li>Importa pacchetti contenenti XDP</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>moduli-sottomissione-revisori</td> 
   <td>
    <ul> 
     <li>Recensione dei documenti</li> 
     <li>Approvare o rifiutare gli invii</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>autori di modelli <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Creare e visualizzare in anteprima moduli adattivi o modelli di comunicazione interattivi</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Creare e modificare un modello di dati modulo</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>agente utente</td> 
   <td>
    <ul> 
     <li>Accedere alle lettere di gestione della corrispondenza o alle comunicazioni interattive tramite l’interfaccia utente dell’agente</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>editor di workflow</p> </td> 
   <td>
    <ul> 
     <li>Creare un’applicazione inbox</li> 
     <li>Creare un modello di flusso di lavoro</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-user</td> 
   <td>
    <ul> 
     <li>Utilizzare le applicazioni di posta in AEM</li> 
     <li>Gestire le istanze del flusso di lavoro</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>amministratori di file</td> 
   <td>
    <ul> 
     <li>Configura PDF Generator</li> 
     <li>Configura cartella di controllo</li> 
     <li>Gestione delle applicazioni del flusso di lavoro</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. L&#39;utente con privilegi di gruppo per l&#39;utente dei moduli non può scrivere script per i moduli adattivi.
1. L&#39;utente con privilegi di gruppo di autori modelli non può scrivere script per i modelli.
