---
title: Scelta di un tipo di persistenza per un’installazione di AEM Forms
seo-title: Choosing a persistence type for an AEM Forms installation
description: Scegli un tipo di persistenza con saggezza. Consente di creare un ambiente AEM Forms efficiente e scalabile.
seo-description: Choose a persistence type wisely. It helps you build an efficient and scale able AEM Forms environment.
uuid: 1c692502-5039-4757-9358-1772772b3904
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: a972fb35-38a7-4b83-99bd-6a6dddf8043b
role: Admin
exl-id: ef486673-30fe-410a-83cf-c55be6064ce4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---

# Scelta di un tipo di persistenza per un’installazione di AEM Forms {#choosing-a-persistence-type-for-an-aem-forms-installation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Scegli un tipo di persistenza con saggezza. Consente di creare un ambiente AEM Forms efficiente e scalabile.

La persistenza è il metodo per memorizzare i contenuti negli archivi fisici. Definisce la struttura dei dati e il meccanismo di archiviazione effettivi per i dati. I MicroKernel fungono da gestori di persistenza in AEM Forms. AEM Forms supporta la persistenza (MicroKernals) di tipo TarMK, MongoMK e RDBMK. Puoi scegliere un tipo di persistenza per AEM Forms a seconda dello scopo e del tipo di distribuzione (Server singolo, farm o Cluster) di un’istanza AEM Forms.

>[!NOTE]
>
>Il LiveCycle ES4 SP1 utilizza la persistenza TarPM per archiviare il contenuto.

Nella tabella seguente sono elencati tutti i tipi di persistenza supportati insieme a vari parametri per aiutarti a scegliere un tipo di persistenza per l’ambiente:

<table> 
 <tbody>
  <tr>
   <th><strong>Tipo di installazione / costo</strong></th> 
   <th><strong>TarMK</strong></th> 
   <th><strong>MongoMk</strong></th> 
   <th><strong>RDBMK</strong></th> 
  </tr>
  <tr>
   <th><strong>Configurazione autonoma</strong></th> 
   <td>Funzione supportata<br /> </td> 
   <td>Supportato</td> 
   <td>Supportato</td> 
  </tr>
  <tr>
   <th><strong>Configurazione cluster</strong></th> 
   <td>Non supportato</td> 
   <td>Supportato</td> 
   <td>Supportato</td> 
  </tr>
  <tr>
   <th><strong>Costo licenza</strong></th> 
   <td>Incluso con AEM </td> 
   <td>Licenza separata richiesta</td> 
   <td>Licenza separata richiesta</td> 
  </tr>
 </tbody>
</table>

TarMK è progettato per le prestazioni, mentre MongoMK e RDBMK sono progettati per la scalabilità. L’Adobe consiglia vivamente TarMK come tecnologia di persistenza predefinita per tutti gli scenari di distribuzione AEM Forms, sia per le istanze Author che Publish, eccetto nei casi d’uso descritti nella sezione [Scelta di Mongo o di un Microkernel di database relazionale su TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p).

Per l’elenco dei microkernel supportati, consulta [AEM Forms sui requisiti tecnici OSGi](/help/sites-deploying/technical-requirements.md) o [Combinazioni di piattaforme supportate da AEM Forms su JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) articoli.

## Scelta di Mongo o di un Microkernel di database relazionale su TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Un ambiente AEM Forms scalabile (cluster) è un set di due o più istanze di authoring attive configurate orizzontalmente. È possibile scegliere di eseguire più istanze di authoring se un singolo server, che supporta tutte le attività di authoring simultanee, non è più sostenibile.

Solo il tipo di persistenza MongoMK e RDBMK è supportato per un AEM Forms scalabile (cluster) in ambiente JEE. Il numero di server o le dimensioni dell&#39;ambiente scalabile variano per ogni installazione. Per un elenco di considerazioni ed esempi, consulta [Implementazioni consigliate](/help/sites-deploying/recommended-deploys.md) e [Architettura e topologie di implementazione per AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) articolo. È inoltre possibile contattare il supporto AEM Forms per informazioni dettagliate sulla pianificazione della capacità per AEM Forms con RDBMK e TarMK.
