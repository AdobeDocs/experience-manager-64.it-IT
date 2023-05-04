---
title: "Gestione della corrispondenza: Risoluzione dei problemi"
seo-title: Correspondence Management Troubleshooting
description: Risoluzione dei problemi di gestione della corrispondenza
seo-description: Correspondence Management Troubleshooting
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
exl-id: 82a35d81-13d0-435f-875e-6fd0a6d574d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# Gestione della corrispondenza: Risoluzione dei problemi {#correspondence-management-troubleshooting}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Errori durante il salvataggio di una lettera {#errors-when-saving-a-letter}

### Problema   {#issue}

Durante il salvataggio di una lettera viene visualizzato uno dei seguenti errori:

* Binding dei dati non presente per il modulo di testo
* Fornisci informazioni sulla proprietà necessarie per

### Motivo {#reason}

Questi errori possono verificarsi a causa di uno dei seguenti elementi:

* Un dizionario dati è associato alla lettera ma non è presente sul server.
* Un dizionario dati è associato alla lettera ma il nome contiene un carattere di sottolineatura (_).

### Soluzione alternativa {#workaround}

Assicurati che il dizionario dati che stai utilizzando nella lettera sia presente sul server e non abbia un carattere di sottolineatura (_) nel suo nome.

## Errore durante l&#39;anteprima di una lettera {#error-when-previewing-a-letter}

### Problema   {#issue-1}

Durante l&#39;anteprima di una lettera, l&#39;errore &quot;Errore nel caricamento della lettera: Impossibile importare la risorsa da un input XML&quot; viene visualizzato anche quando viene pubblicata una risorsa di testo non pubblicata in precedenza nella lettera.

### Soluzione alternativa {#workaround-1}

Reimposta la cache delle lettere sull&#39;istanza di pubblicazione seguendo i passaggi seguenti, quindi riprova a visualizzare la lettera:

1. Vai a **`https://[server]:[port]/[contextPath]/system/console/configMgr`** e accedi come amministratore.
1. Seleziona **Configurazioni di gestione della corrispondenza**.
1. In **Configurazioni di gestione della corrispondenza** disable **Abilita cache lettera** quindi fai clic su **Salva.**
1. Abilita **Abilita cache lettera** quindi fai clic su **Salva**.
1. Riprova a visualizzare la lettera.
