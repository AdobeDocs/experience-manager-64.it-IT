---
title: Configurazione delle credenziali per l’utilizzo con le estensioni Acrobat Reader DC
seo-title: Configuring credentials for use with Acrobat Reader DC extensions
description: Scopri come configurare le credenziali per l’utilizzo con le estensioni Acrobat Reader DC.
seo-description: Learn how to configure credentials for use with Acrobat Reader DC extensions.
uuid: 9210e6c9-6f5c-402d-b355-b104cdffd5eb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5bb32fb1-4b6e-412f-aa16-f60db9dcaba1
exl-id: 40c2e205-0115-4ebe-ab24-66c8ee0663fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---

# Configurazione delle credenziali per l’utilizzo con le estensioni Acrobat Reader DC{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Per applicare i diritti di utilizzo ai documenti PDF, configura AEM moduli con una credenziale valida per le estensioni Acrobat Reader DC. È possibile che sia stata configurata una credenziale durante l’installazione dei moduli AEM. Se non hai configurato le credenziali delle estensioni Acrobat Reader DC durante l&#39;esecuzione di Configuration Manager o se hai bisogno di importare una credenziale nuova o sostitutiva, puoi farlo utilizzando le pagine Gestione archivi attendibili.

Se si utilizza una credenziale di valutazione, sostituirla con una credenziale di produzione quando si passa all&#39;ambiente di produzione. Per aggiornare una credenziale scaduta o di valutazione, elimina prima la credenziale delle estensioni Acrobat Reader DC precedenti.

Per informazioni su come ottenere una credenziale, consulta [Preparazione all’installazione di moduli AEM (server singolo)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63).

L&#39;archivio attendibilità può contenere più di una credenziale di estensione Acrobat Reader DC. È necessario specificare una di queste credenziali come credenziale predefinita delle estensioni di Reader. La credenziale predefinita viene utilizzata quando un utente di Workbench non è in grado di determinare quale credenziale utilizzare durante la creazione del processo. Queste regole si applicano alle credenziali predefinite:

* Se importi una credenziale di Acrobat Reader DC extensions e l&#39;archivio attendibilità non contiene altre credenziali di Acrobat Reader DC extensions, viene impostata come predefinita.
* Se importi una credenziale di Acrobat Reader DC extensions con l’opzione Predefinito selezionata, il tipo predefinito viene rimosso da una credenziale predefinita esistente. La credenziale importata diventa l’impostazione predefinita.
* Non è possibile eliminare una credenziale di estensione Acrobat Reader DC predefinita. Per eliminare la credenziale predefinita, impostare prima un&#39;altra credenziale come predefinita. Fa eccezione il fatto che, se esiste una sola credenziale, è possibile eliminarla anche se è l’impostazione predefinita.
* Non è possibile aggiornare una credenziale di estensione Acrobat Reader DC predefinita.

>[!NOTE]
>
>È inoltre possibile importare ed eliminare le credenziali a livello di programmazione. (Vedi [Programmazione con moduli AEM](https://www.adobe.com/go/learn_aemforms_programming_63).)

## Importare una credenziale di Acrobat Reader DC extensions {#import-a-acrobat-reader-dc-extensions-credential}

1. Nella console di amministrazione, fare clic su Impostazioni > Gestione archivio attendibilità > Credenziali locali.
1. Fare clic su Importa e, in Tipo archivio fonti attendibili, selezionare Credenziali estensioni Acrobat Reader DC.
1. (Facoltativo) Per indicare che questa credenziale è la credenziale predefinita da utilizzare con le estensioni Acrobat Reader DC, selezionare Predefinito.
1. Nella casella Alias digitare un identificatore per la credenziale. Questo identificatore viene utilizzato come nome visualizzato per la credenziale nelle estensioni Acrobat Reader DC. Questo alias viene utilizzato anche per accedere alle credenziali a livello di programmazione utilizzando l’SDK per moduli AEM.

   >[!NOTE]
   >
   >Il nome alias viene automaticamente convertito in maiuscolo a scopo di visualizzazione. Il nome dell&#39;alias non fa distinzione tra maiuscole e minuscole quando vi si fa riferimento in un processo.

1. Fare clic su Scegli file per individuare la credenziale, digitare la password della credenziale, quindi fare clic su OK.

   Se viene visualizzato il messaggio di errore &quot;Impossibile importare le credenziali a causa di un formato di file errato o di una password errata&quot;, verificare che la password sia valida.

## Rimuovere una credenziale di Acrobat Reader DC extensions {#remove-a-acrobat-reader-dc-extensions-credential}

1. Nella console di amministrazione, fare clic su Impostazioni > Gestione archivio attendibilità > Credenziali locali.
1. Selezionare la credenziale e fare clic su Elimina.

## Sostituire una credenziale di Acrobat Reader DC extensions {#replace-a-acrobat-reader-dc-extensions-credential}

1. Nella console di amministrazione, fare clic su Impostazioni > Gestione archivio attendibilità > Credenziali locali.
1. Prendi nota dell’alias della credenziale esistente, selezionalo e fai clic su Elimina.
1. Importa la nuova credenziale utilizzando esattamente lo stesso nome di alias.
