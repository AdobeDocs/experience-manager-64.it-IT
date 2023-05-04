---
title: Tipi di endpoint
seo-title: Types of endpoints
description: Scopri i diversi tipi di endpoint.
seo-description: Learn about the different types of endpoints.
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
exl-id: 7c6b9b6c-d4b5-46a8-8a6a-3b8802ac392d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 1%

---

# Tipi di endpoint {#types-of-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Prima di poter utilizzare un servizio, devi configurare e abilitare un endpoint. Un endpoint specifica la modalità di chiamata di un servizio.

>[!NOTE]
>
>In Workbench, gli endpoint sono denominati punti iniziali.

È possibile aggiungere ai servizi i seguenti tipi di endpoint. Non tutti i servizi supportano tutti gli endpoint:

**E-mail:** Consente a un utente di richiamare un servizio inviando un messaggio e-mail con uno o più file allegati a un account e-mail specificato. Prima di configurare un endpoint e-mail, è necessario configurare gli account e-mail richiesti. (Consulta Configurazione degli endpoint e-mail .)

**Cartella osservata:** Consente a un utente di richiamare un servizio inserendo un file in una cartella, che viene analizzata a un intervallo definito. (Consulta Configurazione degli endpoint di cartelle controllati.)

**TaskManager:** Consente a un utente di Workspace di richiamare il servizio.

**Remoto:** Consente a un&#39;applicazione creata con Flex di richiamare il servizio utilizzando (Obsoleto per i moduli AEM) AEM Moduli Remoting. Viene creato automaticamente un endpoint remoto per ogni servizio attivato. Una destinazione Flex con lo stesso nome dell&#39;endpoint viene creata e i client Flex possono creare oggetti remoti che puntano a questa destinazione per richiamare le operazioni sul servizio pertinente.

**SOAP:** Consente a un’applicazione client sviluppata utilizzando le API di programmazione dei moduli AEM di richiamare il servizio utilizzando la modalità SOAP. Viene creato automaticamente un endpoint SOAP per ogni servizio attivato.

**nota**: *È possibile rimuovere la protezione dai documenti di sicurezza quando si utilizza l’endpoint SOAP durante la visualizzazione dei documenti in Adobe Acrobat o Adobe Reader. Per informazioni dettagliate su come disabilitare gli enpoint SOAP nei documenti LCRM, consulta [Disattivazione degli endpoint SOAP per i documenti di sicurezza](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**EJB:** Consente a un&#39;applicazione client sviluppata utilizzando le API di programmazione dei moduli AEM di richiamare il servizio utilizzando la modalità Enterprise JavaBeans (EJB). Viene creato automaticamente un endpoint EJB per ogni servizio attivato.

**WSDL:** Consente a un&#39;applicazione client sviluppata utilizzando le API di programmazione dei moduli AEM di richiamare il servizio utilizzando il linguaggio WSDL (Web Service Definition Language). La pagina Configurazioni principali contiene un’opzione per abilitare la generazione WSDL per tutti i servizi che fanno parte di moduli AEM. (Consultare Configurare le impostazioni generali dei moduli AEM.)

**REST:** I processi creati in Workbench possono essere configurati in modo da poterli richiamare tramite le richieste di trasferimento dello stato di rappresentanza (REST). Le richieste REST vengono inviate dalle pagine di HTML. In altre parole, è possibile richiamare un processo di moduli AEM direttamente da una pagina web utilizzando una richiesta REST.

Gli endpoint Email, TaskManager, Watched Folder e Remoting mostrano solo un&#39;operazione specifica del servizio. L&#39;aggiunta di questi endpoint richiede un secondo passaggio di configurazione per selezionare un metodo per richiamare il servizio, l&#39;impostazione dei parametri di configurazione e la specifica delle mappature dei parametri di input e output.
