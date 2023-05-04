---
title: "Database DB2: Eseguire un processo settimanale"
seo-title: "DB2 database: Running a process weekly"
description: Scopri come migliorare le prestazioni del database DB2 AEM forms.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# Database DB2: Esecuzione settimanale di un processo{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Se il database DB2 di Forms AEM inizia a essere eseguito lentamente, l&#39;esecuzione del seguente processo su base settimanale può migliorare le prestazioni:

1. Avvia DB2 Control Center:

   (Windows) Selezionare Start > Programmi > IBM DB2 > Strumenti di amministrazione generale > Centro di controllo.

   (Linux e UNIX) Da un prompt dei comandi, digitare il comando `db2jcc` comando.

1. Nella struttura ad albero degli oggetti del Centro di controllo DB2 fare clic su Tutti i database.
1. Fare clic sul database creato per AEM moduli e quindi sulla cartella Tabelle.
1. Selezionare tutte le tabelle del database nel riquadro del contenuto, fare clic con il pulsante destro del mouse su di esse e selezionare Esegui statistiche.
1. Vai a Statistiche > Statistiche indice.
1. Selezionare Raccogli statistiche per tutti gli indici, selezionare Raccogli statistiche per gli indici con statistiche dettagliate estese, quindi fare clic su OK.

Al termine del processo viene visualizzato un messaggio. Chiudi il messaggio.
