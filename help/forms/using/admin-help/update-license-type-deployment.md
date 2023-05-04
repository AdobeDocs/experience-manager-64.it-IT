---
title: Aggiornare il tipo di licenza per la distribuzione
seo-title: Update the license type for the deployment
description: Aggiorna il tipo di licenza per la distribuzione utilizzando la pagina Cambia licenza nella console di amministrazione.
seo-description: Update the license type for the deployment by using the Change License page in administration console.
uuid: 0152635e-2c00-4944-b9b6-64b368589a91
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e4f31377-ccc9-4986-a3bf-ef2e83d12448
exl-id: 07671470-59dd-4290-be9a-465fcd89ac2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 2%

---

# Aggiornare il tipo di licenza per la distribuzione {#update-the-license-type-for-the-deployment}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Come parte del processo di installazione dei moduli di AEM, è stato utilizzato Configuration Manager per configurare e distribuire i moduli di moduli di AEM richiesti. Per impostazione predefinita, tali moduli sono configurati con una licenza di valutazione di 60 giorni. Utilizzare la pagina Modifica licenza nella console di amministrazione per modificare il tipo di licenza per la distribuzione. I moduli attualmente distribuiti vengono visualizzati nella pagina Modifica licenza .

Nella pagina Modifica licenza sono visualizzate le informazioni sulla licenza:

* Tipo di licenza corrente
* Data e ora dell’ultimo aggiornamento della licenza
* Chi ha eseguito l’ultimo aggiornamento
* Stato attuale della licenza
* Data di installazione AEM moduli
* Data di scadenza della licenza corrente

>[!NOTE]
>
>La modifica della licenza si applica a tutti i moduli distribuiti. Prima di modificare il tipo di licenza, annullare la distribuzione dei moduli privi di licenza. Non selezionare il tipo di licenza Produzione se l’elenco dei moduli distribuiti contiene moduli diversi da quelli acquistati da Adobe.

## Aggiornare il tipo di licenza {#update-the-license-type}

1. Nella console di amministrazione, fare clic su Licenze.
1. Leggere il contratto di licenza per gli utenti finali dei moduli di AEM, selezionare Accetto se si accettano i termini del contratto, quindi fare clic su Avanti.
1. Nella pagina Modifica licenza selezionare un tipo di licenza:

   * **EVAL:** Licenza di valutazione di 60 giorni
   * **DEV:** Licenza di sviluppo permanente
   * **NFR:** Licenza di valutazione biennale
   * **IDEV:** abbonamento di 1 anno al programma Adobe Developer
   * **Produzione:** Licenza perpetua

1. Selezionare Sì, la modifica della licenza è valida per tutti i moduli distribuiti.
1. Fare clic su Conferma modifica licenza. Viene visualizzato un messaggio che indica che la licenza è stata aggiornata correttamente.
