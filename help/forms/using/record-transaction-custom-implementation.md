---
title: Registra una transazione per implementazioni personalizzate
seo-title: Record a transaction for custom implementations
description: Utilizzare l'API TransactionRecorder per registrare le azioni non contabilizzate automaticamente come transazioni
seo-description: Use the TransactionRecorder API to record actions which are not accounted as transactions automatically
uuid: a22b1a0b-7553-4a17-8fb4-a3bee97b4a98
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 0d961630-573b-4c8e-902f-996f1d1265b6
exl-id: e97ecb77-96a0-44cf-8da9-1e85cc122011
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 3%

---

# Registra una transazione per implementazioni personalizzate {#record-a-transaction-for-custom-implementations}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizzare l&#39;API TransactionRecorder per registrare le azioni non contabilizzate automaticamente come transazioni

È possibile utilizzare un codice personalizzato per inviare un modulo PDF, per inviare l’URL di anteprima dell’interfaccia utente dell’agente agli utenti finali per visualizzare l’anteprima di una comunicazione interattiva o per inviare un modulo utilizzando metodi personalizzati anziché utilizzare i metodi di invio forniti con AEM Forms. Tutte le azioni e le implementazioni personalizzate precedentemente menzionate delle API AEM Forms non vengono contabilizzate come transazioni. AEM Forms fornisce un’API, [TransactionRecorder](https://helpx.adobe.com/experience-manager/6-4/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html), per registrare azioni quali transazioni.

Per registrare una transazione, scrivi la [servlet sling standard](https://helpx.adobe.com/experience-manager/using/custom-sling-servlets.html) e chiama il servlet da un client per registrare una transazione. Puoi chiamare il servlet utilizzando AJAX o qualsiasi altro metodo standard.

## Esempio di codice lato server {#sample-server-sided-code}

Puoi utilizzare il codice di esempio seguente per eseguire l&#39;API TransactionRecorder da una classe JAVA utilizzando un bundle OSGi personalizzato.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;
 
doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## Esempio di codice lato client {#sample-client-side-code}

Puoi usare il codice di esempio seguente per chiamare il servlet che ha `TransactionRecorder`API.

```
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1, 
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## Articoli correlati {#related-articles}

* [Panoramica dei rapporti sulle transazioni](/help/forms/using/transaction-reports-overview.md)
* [Visualizzazione e comprensione di rapporti sulle transazioni](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [API fatturabili per report transazioni](/help/forms/using/transaction-reports-billable-apis.md)
