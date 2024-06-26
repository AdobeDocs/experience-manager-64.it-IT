---
title: Riutilizzare le risorse con MSM
description: Utilizzare risorse su più pagine/cartelle derivate e collegate a risorse principali. Le risorse rimangono sincronizzate con una copia primaria e, con alcuni clic, ricevono gli aggiornamenti dalle risorse principali.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Multi Site Manager
role: User,Admin,Architect
exl-id: a8e9f8de-ca84-4107-8f73-2fc75eeae1f1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3195'
ht-degree: 9%

---

# Riutilizzare le risorse con MSM per [!DNL Assets] {#reuse-assets-using-msm-for-assets}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Funzionalità Multi Site Manager (MSM) in [!DNL Adobe Experience Manager] consente agli utenti di riutilizzare contenuti creati una volta e riutilizzati in più posizioni web. Lo stesso è disponibile per le risorse digitali come MSM per [!DNL Assets] funzionalità. Utilizzo di MSM per [!DNL Assets], puoi:

* Crea le risorse una volta e quindi fai copie di queste risorse da riutilizzare in altre aree del sito.
* Mantieni più copie in sincronizzazione e aggiorna la copia principale originale una volta per inviare le modifiche alle copie figlio.
* Apporta modifiche locali sospendendo temporaneamente o permanentemente il collegamento tra le risorse principali e secondarie.

## Prerequisiti {#msm-prerequisites}

Per utilizzare MSM per [!DNL Assets], installa almeno [!DNL Experience Manager] 6.4 Service Pack 5. Per ulteriori informazioni, consulta [le note sulla versione dell&#39;ultimo service pack](/help/release-notes/sp-release-notes.md).

## Comprendere i vantaggi e i concetti {#understand-benefits-concepts}

### Come funziona e vantaggi {#how-it-works-the-benefits}

Per comprendere gli scenari di utilizzo per riutilizzare lo stesso contenuto (testo e risorse) in più posizioni web, vedi [possibili scenari MSM](/help/sites-administering/msm.md). [!DNL Experience Manager] mantiene un collegamento tra la risorsa originale e le relative copie collegate, denominate Live Copy (LC). Il collegamento mantenuto consente di inviare le modifiche centralizzate a molte Live Copy. Questo consente aggiornamenti più rapidi eliminando i limiti della gestione delle copie duplicate. La propagazione dei cambiamenti è priva di errori e centralizzata. Questa funzionalità consente di aggiornare le Live Copy in modo limitato. Gli utenti possono scollegare il collegamento, ovvero interrompere l’ereditarietà, e apportare modifiche locali che non verranno sovrascritte al successivo aggiornamento della copia principale e al rollout delle modifiche. Lo scollegamento può essere eseguito per alcuni campi di metadati selezionati o per un’intera risorsa. Consente la flessibilità di aggiornare localmente le risorse che sono originariamente ereditate da una copia primaria.

MSM mantiene una relazione live tra la risorsa di origine e le relative Live Copy in modo che:

* Le modifiche alle risorse di origine vengono applicate (rollout) anche alle Live Copy, ovvero le Live Copy sono sincronizzate con l’origine.

* Puoi aggiornare le Live Copy sospendendo la relazione live o rimuovendo l’ereditarietà per alcuni campi limitati. Le modifiche all’origine non vengono più applicate alla Live Copy.

### Glossario di MSM per i termini di Assets {#glossary-msm-for-assets}

* **Origine:** Le risorse o le cartelle originali. Copia principale da cui derivano le Live Copy.

* **Live Copy:** La copia delle risorse/cartelle sorgente in sincronizzazione con la relativa origine. Le Live Copy possono essere una fonte di ulteriori Live Copy. Vedi [come creare LC](#create-live-copy-asset).

* **Ereditarietà:** Un collegamento/riferimento tra una risorsa/cartella Live Copy e la relativa origine utilizzato dal sistema per ricordare dove inviare gli aggiornamenti. L’ereditarietà esiste a livello granulare per i campi di metadati. L’ereditarietà può essere rimossa per i campi di metadati selettivi, mantenendo al tempo stesso la relazione live tra la sorgente e la sua Live Copy.

* **Rollout**: Un&#39;azione che spinge le modifiche apportate alla sorgente a valle alle sue Live Copy. È possibile aggiornare una o più Live Copy contemporaneamente utilizzando l’azione di rollout. Vedi [rollout](#rollout-action).

* **Configurazione del rollout:** Regole che determinano le proprietà sincronizzate, come e quando. Queste configurazioni vengono applicate durante la creazione di Live Copy; possono essere modificati successivamente; e un figlio può ereditare la configurazione di rollout dalla risorsa principale. Per MSM per [!DNL Assets], utilizza solo la configurazione di rollout standard. Le altre configurazioni di rollout non sono disponibili per MSM per [!DNL Assets].

* **Sincronizza:** Un’altra azione, oltre al rollout, che porta la parità tra l’origine e la relativa Live Copy inviando gli aggiornamenti dall’origine alle Live Copy. Viene avviata una sincronizzazione per una particolare Live Copy e l’azione richiama le modifiche dall’origine. Utilizzando questa azione, è possibile aggiornare solo una delle Live Copy. Vedi [sincronizza azione](#about-synchronize-action).

* **Sospendi:** Rimuovi temporaneamente la relazione live tra una Live Copy e la relativa risorsa/cartella sorgente. È possibile riprendere la relazione. Vedi [sospendi azione](#suspend-and-resume-relationship).

* **Riprendi:** Riprende la relazione live in modo che una Live Copy riceva nuovamente gli aggiornamenti dall’origine. Vedi [riprendere azione](#suspend-and-resume-relationship).

* **Ripristina:** L’azione Reimposta rende la Live Copy nuovamente una replica dell’origine sovrascrivendo eventuali modifiche locali. Inoltre rimuove le cancellazioni di ereditarietà e ripristina l’ereditarietà su tutti i campi di metadati. Per apportare modifiche locali in futuro, è necessario annullare nuovamente l’ereditarietà di campi specifici. Vedi [modifiche locali a LC](#make-local-modifications-to-live-copy).

* **Stacca:** Rimuovi in modo irreversibile la relazione live di una risorsa/cartella Live Copy. Dopo aver scollegato l’azione, le Live Copy non possono mai ricevere aggiornamenti dall’origine e smette più di essere una Live Copy. Vedi [rimuovi relazione](#remove-live-relationship).

## Creare una Live Copy di una risorsa {#create-live-copy-asset}

Per creare una Live Copy da una o più risorse o cartelle sorgente, effettua una delle seguenti operazioni:

* **Metodo 1**: Seleziona le risorse sorgente e fai clic su **[!UICONTROL Crea]** > **[!UICONTROL Live Copy]** dalla barra degli strumenti nella parte superiore.
* **Metodo 2**: In [!DNL Experience Manager] interfaccia utente, fai clic su **[!UICONTROL Crea > Live Copy]** dall’angolo superiore destro dell’interfaccia.

Puoi creare Live Copy di una risorsa o di una cartella una alla volta. Puoi creare Live Copy derivate da una risorsa o da una cartella che è una Live Copy stessa.

I frammenti di contenuto (CF) non sono supportati per il caso d’uso. Quando tenti di creare le loro Live Copy, i CF vengono copiati così come sono senza alcuna relazione. I CF copiati sono un&#39;istantanea nel tempo e non si aggiornano quando i CF originali vengono aggiornati.

Per creare Live Copy utilizzando il primo metodo, effettua le seguenti operazioni:

1. Seleziona le risorse o le cartelle sorgente. Dalla barra degli strumenti, fai clic su **[!UICONTROL Crea > Live Copy]**.
   ![Crea Live Copy da [!DNL Experience Manager] interfaccia](assets/lc_create1.png)
1. Seleziona la risorsa o la cartella di origine. Fai clic su **[!UICONTROL Avanti]**.
1. Fornire titolo e nome. Le risorse non hanno figli. Quando crei una Live Copy di cartelle, puoi scegliere di includere o escludere elementi figlio.
1. Seleziona una configurazione di rollout. Fai clic su **[!UICONTROL Crea]**.

Per creare Live Copy utilizzando il secondo metodo, effettua le seguenti operazioni:

1. In [!DNL Experience Manager] interfaccia, dall&#39;angolo in alto a destra, fai clic su **[!UICONTROL Crea > Live Copy]**.
   ![Crea Live Copy da [!DNL Experience Manager] interfaccia](assets/lc_create2.png)
1. Seleziona la risorsa o la cartella di origine. Fai clic su **[!UICONTROL Avanti]**.
1. Selezionare la cartella di destinazione. Fai clic su **[!UICONTROL Avanti]**.
1. Fornire titolo e nome. Le risorse non hanno figli. Quando crei una Live Copy di cartelle, puoi scegliere di includere o escludere elementi figlio.
1. Seleziona una configurazione di rollout. Fai clic su **[!UICONTROL Crea]**.

>[!NOTE]
>
>Quando si sposta un&#39;origine o una Live Copy, le relazioni vengono mantenute. Quando una Live Copy viene eliminata, le relazioni vengono rimosse.

## Visualizza varie proprietà e stati della sorgente e della Live Copy {#view-properties-statuses-source-and-lc}

Puoi visualizzare le informazioni e gli stati relativi a MSM della Live Copy, ad esempio relazione, sincronizzazione, rollout e altro dalle varie aree del [!DNL Experience Manager] interfaccia utente. I due metodi seguenti funzionano per le risorse e le cartelle:

* Seleziona la risorsa Live Copy e trova le informazioni nella relativa **[!UICONTROL Proprietà]** pagina.
* Seleziona la cartella di origine e trova le informazioni dettagliate di ogni Live Copy dal **[!UICONTROL Console Live Copy]**.

>[!TIP]
>
>Per verificare lo stato di alcune Live Copy separate, utilizza il primo metodo per controllare il **[!UICONTROL Proprietà]** pagina. Per controllare lo stato di molte Live Copy, utilizza il secondo metodo per controllare **[!UICONTROL Stato della relazione]** pagina.

### Informazioni e stato di una Live Copy {#information-status-of-one-lc}

Per controllare le informazioni e gli stati di una risorsa Live Copy o di una cartella, segui questi passaggi.

1. Seleziona una risorsa Live Copy o una cartella. Fai clic su **[!UICONTROL Proprietà]** dalla barra degli strumenti. In alternativa, utilizza la scelta rapida da tastiera `p`.
1. Fai clic su **[!UICONTROL Live Copy]**. Puoi controllare il percorso dell’origine, lo stato di sospensione, lo stato di sincronizzazione, la data dell’ultimo rollout e l’utente che ha eseguito l’ultimo rollout.
   ![Le informazioni e gli stati della Live Copy vengono visualizzati in una console in Proprietà](assets/lc_folder_properties.png)
1. Puoi abilitare o disabilitare se le risorse secondarie prendono in prestito la configurazione Live Copy.
1. Puoi scegliere l’opzione per la Live Copy per ereditare la configurazione di rollout dall’elemento padre o modificare la configurazione.

### Informazioni e stati di tutte le Live Copy di una cartella {#information-status-of-all-lcs-of-folder}

[!DNL Experience Manager] fornisce una console per controllare le statue di tutte le Live Copy di una cartella sorgente. In questa console viene visualizzato lo stato di tutte le risorse secondarie.

1. Selezionare una cartella di origine. Fai clic su **[!UICONTROL Proprietà]** dalla barra degli strumenti. In alternativa, utilizza la scelta rapida da tastiera `p`.
1. Fai clic su **[!UICONTROL Origine Live Copy]**. Per aprire la console, fai clic su **[!UICONTROL Panoramica Live Copy]**. Questo dashboard offre uno stato di primo livello per tutte le risorse figlie.
   ![Visualizza lo stato delle Live Copy nella console Live Copy di origine](assets/lc_statuses.png)
1. Per visualizzare informazioni dettagliate su ciascuna risorsa della cartella Live Copy, seleziona la risorsa in questione, quindi dalla barra degli strumenti fai clic su **[!UICONTROL Stato di relazione]**.
   ![Informazioni dettagliate e stato di una risorsa figlia Live Copy in una cartella](assets/lc_relationship_status.png)

>[!TIP]
>
>È possibile visualizzare rapidamente gli stati delle Live Copy di altre cartelle senza dover navigare troppo. Modificare la cartella dalla parte superiore centrale del **[!UICONTROL Panoramica di Live Copy]** interfaccia.

### Azioni rapide dalla barra Riferimenti per la sorgente {#quick-actions-from-references-rail-for-source}

Per una risorsa o una cartella di origine, puoi visualizzare le seguenti informazioni ed effettuare le seguenti azioni direttamente dalla barra Riferimenti:

* Guarda i percorsi delle Live Copy.
* Apri o rivela una Live Copy specifica in [!DNL Experience Manager] interfaccia utente.
* Sincronizza gli aggiornamenti con una Live Copy specifica.
* Sospendi la relazione o modifica la configurazione di rollout per una Live Copy specifica.
* Accedi alla console della panoramica Live Copy.

Seleziona la risorsa o la cartella di origine, apri la barra a sinistra e fai clic su **[!UICONTROL Riferimenti]**. In alternativa, seleziona una risorsa o una cartella e utilizza la scelta rapida da tastiera `Alt + 4`.

![Azioni e informazioni disponibili nella barra Riferimenti per l’origine selezionata](assets/lc_referencerail_source.png)

Per una Live Copy specifica, fai clic su **[!UICONTROL Modifica Live Copy]** per sospendere la relazione o modificare la configurazione di rollout.

![Per una Live Copy specifica, l’opzione per sospendere la relazione o modificare la configurazione di rollout è accessibile dalla barra laterale Riferimenti quando la risorsa sorgente è selezionata](assets/lc_edit_referencerail.png)

### Azioni rapide dalla barra Riferimenti per Live Copy {#quick-actions-from-references-rail-for-live-copy}

Per una risorsa o una cartella Live Copy, puoi vedere le seguenti informazioni ed effettuare le seguenti azioni direttamente dalla barra Riferimenti:

* Visualizzare il percorso della relativa sorgente.
* Apri o rivela una Live Copy specifica in [!DNL Experience Manager] interfaccia utente.
* Implementa gli aggiornamenti.

Seleziona una risorsa o una cartella Live Copy, apri la barra a sinistra e fai clic su **[!UICONTROL Riferimenti]**. In alternativa, seleziona una risorsa o una cartella e utilizza la scelta rapida da tastiera `Alt + 4`.

![Azioni disponibili nella barra laterale Riferimenti per la Live Copy selezionata](assets/lc_referencerail.png)

## Propagare le modifiche dall&#39;origine alle Live Copy {#propagate-modifications-from-source-to-live-copies}

Dopo la modifica di un’origine, le modifiche possono essere propagate alle Live Copy utilizzando un’azione di sincronizzazione o un’azione di rollout. Per comprendere la differenza tra le due azioni, vedi [glossario](#glossary-msm-for-assets).

### Azione di rollout {#rollout-action}

Puoi avviare un’azione di rollout dalla risorsa sorgente e aggiornare tutte o alcune Live Copy selezionate.

1. Seleziona una risorsa Live Copy o una cartella. Fai clic su **[!UICONTROL Proprietà]** dalla barra degli strumenti. In alternativa, utilizza la scelta rapida da tastiera `p`.
1. Fai clic su **[!UICONTROL Origine Live Copy]**. Fai clic su **[!UICONTROL Rollout]** dalla barra degli strumenti.
1. Seleziona le Live Copy da aggiornare. Fai clic su **[!UICONTROL Rollout]**.
1. Per eseguire il rollout degli aggiornamenti apportati alle risorse figlio, seleziona **[!UICONTROL Origine rollout e tutti i figli]**.
   ![Implementa le modifiche dell’origine su alcune o tutte le Live Copy](assets/lc_rollout_page.png)

>[!NOTE]
>
>Le modifiche apportate a una risorsa di origine vengono implementate solo nelle Live Copy direttamente correlate. Se una Live Copy viene derivata da un’altra Live Copy, le modifiche non vengono implementate nella Live Copy derivata.

In alternativa, puoi avviare un’azione di rollout dal [!UICONTROL Riferimenti] dopo aver selezionato una Live Copy specifica. Per ulteriori informazioni, consulta [Azioni rapide dalla barra Riferimenti per Live Copy](#quick-actions-from-references-rail-for-live-copy). In questo metodo di rollout, vengono aggiornati solo la Live Copy selezionata ed eventualmente i relativi elementi secondari.

![Implementa le modifiche dell’origine nella Live Copy selezionata](assets/lc_rollout_dialog.png)

### Informazioni sull’azione di sincronizzazione {#about-synchronize-action}

Un’azione di sincronizzazione richiama le modifiche da un’origine solo alla Live Copy selezionata. L’azione di sincronizzazione rispetta e mantiene le modifiche locali eseguite dopo l’annullamento dell’ereditarietà. Le modifiche locali non vengono sovrascritte e l’ereditarietà annullata non viene ristabilita. Puoi avviare un’azione di sincronizzazione in tre modi.

| Dove [!DNL Experience Manager] interfaccia | Quando e perché utilizzare | Come utilizzare |
|---|---|---|
| [!UICONTROL Riferimenti] barra | Sincronizza rapidamente quando la sorgente è già selezionata. | Vedi [Azioni rapide dalla barra Riferimenti per la sorgente](#quick-actions-from-references-rail-for-source) |
| Barra degli strumenti [!UICONTROL Proprietà] page | Avvia una sincronizzazione quando le proprietà Live Copy sono già aperte. | Vedi [Sincronizzazione di una Live Copy](#synchronize-live-copy) |
| [!UICONTROL Panoramica di Live Copy] console | Sincronizza rapidamente più risorse (non necessariamente tutte) quando viene selezionata o [!UICONTROL Panoramica di Live Copy] console già aperta. L’azione di sincronizzazione viene avviata per una risorsa alla volta, ma è un modo più veloce per eseguire la sincronizzazione per più risorse contemporaneamente. | Vedi [Azioni su più risorse in una cartella Live Copy](#take-actions-on-many-assets-in-lcfolder) |

### Sincronizzazione di una Live Copy {#synchronize-live-copy}

Per avviare un’azione di sincronizzazione, apri la pagina **[!UICONTROL Proprietà]** di una Live Copy, fai clic su **[!UICONTROL Live Copy]** e nella barra degli strumenti seleziona l’azione desiderata.

Per visualizzare gli stati e le informazioni relativi a un’azione di sincronizzazione, consulta [Informazioni e stati di tutte le Live Copy di una cartella](#information-status-of-all-lcs-of-folder).

![L&#39;azione Sincronizza richiama le modifiche apportate all&#39;origine](assets/lc_sync.png)

>[!NOTE]
>
>Se la relazione è sospesa, l’azione di sincronizzazione non è disponibile nella barra degli strumenti. Mentre l’azione di sincronizzazione è disponibile nella [!UICONTROL Riferimenti] le modifiche non vengono propagate neanche in seguito a un rollout riuscito.

## Sospendi e riprendi relazione {#suspend-and-resume-relationship}

Puoi sospendere temporaneamente la relazione per impedire a una Live Copy di ricevere le modifiche apportate alla risorsa o alla cartella di origine. La relazione può anche essere ripresa per la Live Copy per iniziare a ricevere le modifiche dalla sorgente.

Per sospendere o riprendere, apri la pagina **[!UICONTROL Proprietà]** di una Live Copy, fai clic su **[!UICONTROL Live Copy]** e nella barra degli strumenti fai clic sull’azione desiderata.

In alternativa, puoi sospendere o riprendere rapidamente le relazioni tra più risorse in una cartella Live Copy della console **[!UICONTROL Panoramica Live Copy]**. Consulta la sezione [Azioni su numerose risorse presenti nelle cartelle Live Copy](#take-actions-on-many-assets-in-lcfolder).

## Apportare modifiche locali a una Live Copy {#make-local-modifications-to-live-copy}

Una Live Copy è una replica dell’origine originale al momento della creazione. I valori dei metadati di una Live Copy vengono ereditati dall’origine. I campi di metadati mantengono l’ereditarietà individualmente con i rispettivi campi della risorsa sorgente.

Tuttavia, puoi apportare modifiche locali a una Live Copy per cambiare alcune proprietà selezionate. Per eseguire modifiche locali, annulla l’ereditarietà della proprietà desiderata. Quando l’ereditarietà di uno o più campi di metadati viene annullata, si mantiene la relazione live della risorsa e l’ereditarietà degli altri campi di metadati. Qualsiasi sincronizzazione o rollout non sovrascrive le modifiche locali. Per farlo, apri **[!UICONTROL Proprietà]** di una risorsa Live Copy, fai clic sul pulsante **[!UICONTROL annulla ereditarietà]** accanto a un campo di metadati.

Puoi annullare tutte le modifiche locali e ripristinare lo stato della risorsa all’origine. L’azione Reimposta sostituisce irrevocabilmente e istantaneamente tutte le modifiche locali e ristabilisce l’ereditarietà su tutti i campi di metadati. Per ripristinare, dal **[!UICONTROL Proprietà]** pagina di una risorsa Live Copy, fai clic su **[!UICONTROL Reimposta]** dalla barra degli strumenti.

![L’azione Reimposta sovrascrive le modifiche locali e porta la Live Copy in parte con la relativa origine](assets/lc_reset.png)

## Rimuovi relazione live {#remove-live-relationship}

È possibile rimuovere completamente la relazione tra un&#39;origine e una Live Copy utilizzando l&#39;azione Stacca. La Live Copy diventa una risorsa o una cartella autonoma dopo essere stata staccata. Viene visualizzato come nuova risorsa in [!DNL Experience Manager] immediatamente dopo lo scollegamento. Per scollegare una Live Copy dall’origine, effettua le seguenti operazioni.

1. Seleziona una risorsa o una cartella Live Copy. Fai clic su **[!UICONTROL Proprietà]** dalla barra degli strumenti. In alternativa, utilizza la scelta rapida da tastiera `p`.
1. Fai clic su **[!UICONTROL Live Copy]**. Fai clic su **[!UICONTROL Stacca]** nella barra degli strumenti. Fai clic su **[!UICONTROL Stacca]** dalla finestra di dialogo presentata.
   ![L&#39;azione Scollega rimuove completamente la relazione tra l&#39;origine e la Live Copy](assets/lc_detach.png)

>[!CAUTION]
>
>La relazione viene rimossa immediatamente quando fai clic su [!UICONTROL Stacca] dalla finestra di dialogo. Non è possibile annullarlo facendo clic su [!UICONTROL Annulla] nella pagina Proprietà.

In alternativa, è possibile scollegare rapidamente più risorse in una cartella Live Copy da **[!UICONTROL Panoramica di Live Copy]** console. Consulta la sezione [Azioni su numerose risorse presenti nelle cartelle Live Copy](#take-actions-on-many-assets-in-lcfolder).

## Azioni su più risorse in una cartella Live Copy {#take-actions-on-many-assets-in-lcfolder}

Se una cartella Live Copy contiene più risorse, l’avvio di azioni su ciascuna risorsa può risultare noioso. Puoi avviare rapidamente le azioni di base su molte risorse dalla console Live Copy. I metodi di cui sopra continuano a funzionare per le singole risorse.

1. Selezionare una cartella di origine. Fai clic su **[!UICONTROL Proprietà]** dalla barra degli strumenti. In alternativa, utilizzare la scelta rapida da tastiera p.
1. Fai clic su Origine Live Copy. Per aprire la console, fai clic su **[!UICONTROL Panoramica Live Copy]**.
1. In questo dashboard, seleziona una risorsa Live Copy da una cartella Live Copy. Nella barra degli strumenti, scegli le azioni desiderate. Le azioni disponibili sono **[!UICONTROL Modifica]**, **[!UICONTROL Sincronizza]**, **[!UICONTROL Reimposta]**, **[!UICONTROL Sospendi]** e **[!UICONTROL Stacca]**. Puoi avviare rapidamente queste azioni su qualsiasi risorsa presente in un numero qualsiasi di cartelle Live Copy che si trovano in una relazione diretta con la cartella sorgente selezionata.
   ![Aggiornare facilmente molte risorse nelle cartelle Live Copy dalla console Panoramica Live Copy](assets/lc_console_update_assets.png)

## Estendere MSM per Assets {#extend-msm-for-assets}

[!DNL Experience Manager] consente di estendere la funzionalità utilizzando le API Java MSM. Per Assets, l’estensione funziona esattamente come con MSM per Site. Per maggiori dettagli, vedi [Estensione dell&#39;MSM](../sites-developing/extending-msm.md) e le sezioni seguenti per informazioni sulle attività specifiche:

* [Panoramica delle API](../sites-developing/extending-msm.md#overview-of-the-java-api)
* [Crea una nuova azione di sincronizzazione](../sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Creare una nuova configurazione di rollout](../sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [Creare e utilizzare una semplice classe LiveActionFactory](../sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* La blueprint in MSM per il sito è denominata sorgente Live Copy in MSM per le risorse.
>* La rimozione del passaggio dei capitoli nella procedura guidata di creazione del sito non è supportata in MSM per Assets.
>* La configurazione dei blocchi MSM sulle proprietà di pagina (interfaccia touch) non è supportata in MSM per Assets.


## Impatto delle attività di gestione delle risorse sulle Live Copy {#impact-of-asset-management-tasks-on-live-copies}

Le Live Copy e le origini sono risorse o cartelle che possono essere gestite, in una certa misura, come risorse digitali. Alcune attività di gestione delle risorse in [!DNL Experience Manager] hanno un impatto specifico sulle Live Copy.

* Copiando una Live Copy, crea una risorsa Live Copy con la stessa origine della prima Live Copy.
* Quando si sposta un&#39;origine o la relativa Live Copy, la relazione live viene mantenuta.
* L’azione Modifica non funziona per le risorse Live Copy.
* L’azione di estrazione non è disponibile per le risorse Live Copy.
* Per la cartella di origine è disponibile l’opzione per creare attività di revisione.
* Quando visualizzi l’elenco delle risorse nella vista a elenco e nella vista a colonne, una risorsa o una cartella Live Copy visualizza la dicitura &quot;Live Copy&quot;. Questo consente di identificare facilmente le Live Copy in una cartella.

## Confrontare MSM per risorse e siti {#compare-msm-for-assets-and-sites}

In più scenari, MSM per Assets corrisponde al comportamento della funzionalità MSM per Sites. Alcune differenze chiave da notare sono:

* In Sites puoi confrontare una blueprint e la relativa Live Copy, ma non è possibile in Assets confrontare un’origine con la relativa Live Copy.
* In genere i siti hanno elementi figlio, ma non le risorse. L’opzione per includere o escludere elementi figlio non è presente quando si creano Live Copy di singole risorse.
* La rimozione del passaggio dei capitoli nella procedura guidata di creazione del sito non è supportata in MSM per Assets.
* La configurazione dei blocchi MSM sulle proprietà di pagina (interfaccia touch) non è supportata in MSM per Assets.
* Per MSM per Assets, utilizza solo la configurazione di rollout standard. Le altre configurazioni di rollout non sono disponibili per MSM per Assets.

## Limitazioni di MSM per Assets {#limitations-of-msm-for-assets}

Di seguito sono riportate le limitazioni di MSM per Assets.

* I frammenti di contenuto (CF) non sono supportati per il caso d’uso. Quando tenti di creare le loro Live Copy, i CF vengono copiati così come sono senza alcuna relazione. I CF copiati sono un&#39;istantanea nel tempo e non si aggiornano quando i CF originali vengono aggiornati.

* MSM non funziona con il write-back dei metadati abilitato. Al successivo ripristino, l&#39;ereditarietà si interrompe.
