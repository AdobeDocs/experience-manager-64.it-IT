---
title: Eliminazione di moduli e risorse correlate
seo-title: Deleting forms and related resources
description: Come eliminare un modulo o una risorsa in AEM Forms e l’impatto sulle risorse di riferimento e di provenienza e sui moduli XFA.
seo-description: How to delete a form or an asset in AEM Forms and the impact on referenced and referring assets and XFA forms.
uuid: df522b87-59d8-4678-922d-c9aab82b1381
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: c8519eec-f841-4867-baa9-a9e03042755e
role: Admin
exl-id: 94a66d83-b359-4be6-b668-4b4ba024b1e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# Eliminazione di moduli e risorse correlate {#deleting-forms-and-related-resources}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Puoi eliminare i moduli e le risorse per rimuovere queste risorse dalla directory archivio. L’operazione Elimina funziona su tutti i tipi di risorse e le cartelle.

Se elimini una risorsa dall’istanza Author, anche la risorsa viene eliminata dall’istanza Publish. Il server AEM Forms è costituito da istanze Author e Publish. L’istanza Autore consente di creare e gestire le risorse e le risorse dei moduli. L’istanza Pubblica contiene le risorse dei moduli pubblicati e le relative risorse disponibili per gli utenti finali.

## Eliminazione di un modulo {#how-to-delete-a-form}

1. Accedi all’interfaccia utente di AEM Forms accedendo a `https://[hostname]:[portport]/aem/forms.html.`
1. Individuare e selezionare il modulo da eliminare. Fai clic su Elimina ![aem6forms_delete2](assets/aem6forms_delete2.png) dalla barra degli strumenti e conferma l’operazione di eliminazione.

   >[!NOTE]
   >
   >È possibile eliminare un solo modulo alla volta. Eliminare più moduli singolarmente o eliminare la cartella principale.

1. Prima di eliminare una risorsa, AEM Forms verifica la presenza di riferimenti e richiede una conferma esplicita. Fai clic su Forza eliminazione per eliminare la risorsa indipendentemente dallo stato della relazione.

   >[!NOTE]
   >
   >L’eliminazione di una risorsa cui fanno riferimento altre risorse può causare problemi funzionali.

   >[!NOTE]
   >
   >Se la risorsa selezionata è una cartella e contiene tale risorsa nella sua gerarchia, elimina le altre risorse singolarmente o elimina l’intera cartella.

## Impatto dell&#39;eliminazione di un modulo XFA di riferimento {#impact-of-deleting-a-referenced-xfa-form}

In AEM Forms, un modello di modulo XFA può essere indirizzato da un modulo adattivo o da un altro modello di modulo XFA. Inoltre, un modello può fare riferimento a una risorsa o a un altro modello XFA.

Non è consigliabile eliminare un modulo XFA a cui si fa riferimento in un modulo adattivo, in quanto può danneggiare il modulo adattivo. Quando un modulo adattivo fa riferimento a un modulo XFA, i relativi campi sono associati. Dopo l’eliminazione di XFA, il modulo adattivo non può sincronizzare i campi con i campi XFA e visualizza un messaggio di errore per tali campi. Per ulteriori informazioni sull&#39;impatto della cancellazione XFA di riferimento e sugli AF sporchi, vedi [Aggiornamento dei moduli XFA di riferimento](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Per eliminare un modulo XFA di questo tipo, aggiorna il modulo adattivo e rimuovi i binding con i campi XFA.
