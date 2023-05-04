---
title: API per richiamare il servizio del modello dati modulo dai moduli adattivi
seo-title: API to invoke form data model service from adaptive forms
description: Spiega l’API invokeWebServices che è possibile utilizzare per richiamare servizi Web scritti in WSDL da un campo modulo adattivo.
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 3%

---

# API per richiamare il servizio del modello dati modulo dai moduli adattivi {#api-to-invoke-form-data-model-service-from-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

AEM Forms consente agli autori dei moduli di semplificare e migliorare ulteriormente l’esperienza di compilazione dei moduli richiamando i servizi configurati in un modello di dati del modulo dall’interno di un campo modulo adattivo. Per richiamare un servizio del modello dati, puoi creare una regola nell’editor visivo o specificare un JavaScript utilizzando `guidelib.dataIntegrationUtils.executeOperation` API nell’editor di codice del [editor di regole](/help/forms/using/rule-editor.md).

Questo documento si concentra sulla scrittura di un JavaScript utilizzando `guidelib.dataIntegrationUtils.executeOperation` API per richiamare un servizio.

## Utilizzo dell’API {#using-the-api}

La `guidelib.dataIntegrationUtils.executeOperation` L’API richiama un servizio dall’interno di un campo modulo adattivo. La sintassi API è la seguente:

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

L&#39;API richiede i seguenti parametri.

| Parametro | Descrizione |
|---|---|
| `operationInfo` | Struttura per specificare l’identificatore del modello di dati del modulo, il titolo dell’operazione e il nome dell’operazione |
| `inputs` | Struttura per specificare gli oggetti modulo i cui valori vengono immessi nell’operazione del servizio |
| `outputs` | Struttura per specificare gli oggetti modulo che verranno compilati con i valori restituiti dall’operazione di servizio |

La struttura del `guidelib.dataIntegrationUtils.executeOperation` API specifica i dettagli sull&#39;operazione del servizio. La sintassi della struttura è la seguente.

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

La struttura API specifica i seguenti dettagli sull’operazione del servizio.

<table> 
 <tbody> 
  <tr> 
   <th>Parametro</th> 
   <th>Descrizione</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>Specificare il percorso del repository del modello dati del modulo, incluso il suo nome</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>Specificare il nome dell'operazione del servizio da eseguire</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>Mappare uno o più oggetti modulo agli argomenti di input per l’operazione del servizio</td> 
  </tr> 
  <tr> 
   <td>Output</td> 
   <td>Mappare uno o più oggetti modulo ai valori di output dall’operazione del servizio per compilare i campi del modulo<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Script di esempio per richiamare un servizio {#sample-script-to-invoke-a-service}

Lo script di esempio seguente utilizza `guidelib.dataIntegrationUtils.executeOperation` API per richiamare `getAccountById` operazione di servizio configurata in `employeeAccount` modello dati modulo.

La `getAccountById` prende il valore nel `employeeID` campo modulo come input per `empId` argomento e restituisce il nome del dipendente, il numero di conto e il saldo del conto per il dipendente corrispondente. I valori di output vengono compilati nei campi modulo specificati. Ad esempio, il valore in `name` viene popolato in `fullName` elemento e valore modulo per `accountNumber` argomento in `account` elemento modulo.

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```
