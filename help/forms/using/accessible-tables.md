---
title: Creazione di tabelle complesse con accesso facilitato nei moduli di HTML5
seo-title: Create accessible complex tables in HTML5 forms
description: Scopri come creare tabelle accessibili in HTML5 forms.
seo-description: Learn how to create accessible tables in HTML5 forms.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: Mobile Forms
exl-id: a3337bb1-635c-4dc9-b438-3a829d4a9e03
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# Creazione di tabelle complesse con accesso facilitato nei moduli di HTML5 {#create-accessible-complex-tables-in-html-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

L’implementazione predefinita delle tabelle in HTML5 Forms utilizza elementi DIV di HTML per eseguire il rendering di una tabella. Il rendering comporta l’utilizzo di ruoli ARIA per soddisfare i requisiti di accessibilità.

Per evitare problemi di accessibilità con gli assistenti vocali che non supportano completamente i ruoli ARIA utilizzati con le tabelle di dati, HTML5 Forms fornisce un rendering alternativo per le tabelle. Queste tabelle si basano sul nuovo formato di tabella introdotto in Designer e supporta inoltre:

* Intestazioni riga
* Intervallo di righe

Per utilizzare il nuovo formato in HTML5 Forms, contrassegnare la tabella come complessa. Per contrassegnare la tabella come complessa, aggiungi `extras` nell’origine XML del sottomodulo tabella come segue:

```
</extras>
 <text name="complexTable">1</text>
 </extras>
```

Tabelle contrassegnate come *complexTable* segui il rendering nativo di HTML e fornisci un supporto di accessibilità migliore per alcuni assistenti vocali.  Per creare un intervallo di righe, selezionare le celle consecutive di una tabella nella stessa colonna, fare clic con il pulsante destro del mouse sulla selezione e quindi fare clic su **[!UICONTROL Unisci celle]**.

***Nota:**La creazione di un intervallo di righe funziona solo per le celle più a sinistra.*

Per contrassegnare una riga come intestazione di riga, selezionare tutte le celle della riga, fare clic con il pulsante destro del mouse sulla selezione e quindi fare clic su **[!UICONTROL Segna intestazione]**.

Per contrassegnare una cella come intestazione di colonna, selezionare una cella nella colonna, fare clic con il pulsante destro del mouse sulla selezione e quindi fare clic su **[!UICONTROL Segna intestazione]**.

Limitazioni nelle nuove *AccessibleTable* formato:

* Mancanza di supporto per i campi espandibili se nella tabella viene utilizzato l’intervallo di righe
* Nessun supporto per tabelle nidificate (tabelle all’interno di celle di tabella)
* Il supporto per l&#39;estensione di riga è limitato alle righe di intestazione e alle celle di intestazione
* Il supporto è limitato alle tabelle normali
* Nessun supporto per le precompilazioni dei dati nelle tabelle con estensione di riga > 1
