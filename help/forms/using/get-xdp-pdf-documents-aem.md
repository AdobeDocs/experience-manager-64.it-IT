---
title: Ottenimento di documenti XDP e PDF in AEM Forms
seo-title: Getting XDP and PDF documents in AEM Forms
description: AEM Forms consente di caricare moduli e risorse supportate da utilizzare con i moduli adattivi. Puoi anche caricare in massa moduli e risorse correlate come file ZIP.
seo-description: AEM Forms allows you to upload forms and supported assets to use with adaptive forms. You can also bulk upload forms and related resources as a ZIP.
uuid: c2a86d89-0c56-4d29-932a-dd09277fa7cb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 99da0d37-726e-42b9-b98a-5dd6c2165af6
role: Admin
exl-id: 50bf178d-7a3c-41df-9d13-99c74d944700
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---

# Ottenimento di documenti XDP e PDF in AEM Forms {#getting-xdp-and-pdf-documents-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Panoramica {#overview}

Puoi importare i moduli dal file system locale nell’archivio CRX, effettuando il caricamento in AEM Forms. L’operazione di caricamento è supportata per i seguenti tipi di risorse:

* Modelli di modulo (moduli XFA)
* PDF forms
* Documento (documenti Flat PDF)

Puoi caricare i tipi di risorse supportati singolarmente o come archivio ZIP. Puoi caricare una risorsa del tipo `Resource`, solo accanto a un modulo XFA in un archivio ZIP.

>[!NOTE]
>
>Assicurati di essere un membro del `form-power-users` per poter caricare file XDP. Contatta l’amministratore per diventare membro del gruppo.

## Caricamento dei moduli {#uploading-forms}

1. Accedi all’interfaccia utente di AEM Forms accedendo a `https://[server]:[port]/aem/forms.html`.
1. Passa alla cartella in cui desideri caricare il modulo o la cartella che contiene i moduli.
1. Nella barra degli strumenti Azioni, tocca **Crea > Caricamento file**.

   ![File dall&#39;opzione di archiviazione locale in Crea](assets/step.png)

1. La finestra di dialogo Carica moduli o pacchetto consente di sfogliare e scegliere il file da caricare. Il browser dei file visualizza solo i formati di file supportati (ZIP, XDP e PDF).

   >[!NOTE]
   >
   >Un nome file può contenere solo caratteri alfanumerici, trattini o caratteri di sottolineatura.

1. Fai clic su Carica dopo la selezione del file per caricare i file o fai clic su &#39;Annulla&#39; per annullare il caricamento. Una finestra a comparsa elenca le risorse aggiunte e quelle aggiornate nella posizione corrente.

   >[!NOTE]
   >
   >Per un file ZIP, vengono visualizzati i percorsi relativi di tutte le risorse supportate. Le risorse non supportate all&#39;interno dello ZIP vengono ignorate e non elencate. Tuttavia, se l’archivio ZIP contiene solo le risorse non supportate, viene visualizzato un messaggio di errore invece della finestra di dialogo a comparsa.

   ![Finestra di dialogo Carica durante il caricamento di un modulo XFA](assets/upload-scr.png)

1. Se una o più risorse hanno un nome di file non valido, viene visualizzato un errore. Correggi i nomi dei file evidenziati in rosso e ricarica.

   ![Messaggio di errore durante il caricamento di un modulo XFA](assets/upload-scr-err.png)

Una volta completato il caricamento, un flusso di lavoro in background genera le miniature per ogni risorsa, in base all’anteprima della risorsa. Le nuove versioni delle risorse, se caricate, sostituiscono le risorse esistenti.

### Modalità protetta {#protected-mode}

Il server AEM Forms ti consente di eseguire il codice JavaScript. Un codice JavaScript dannoso può danneggiare un ambiente AEM Forms. La modalità protetta limita AEM Forms all’esecuzione di file XDP solo da risorse e posizioni affidabili. Tutte le XDP disponibili nell’interfaccia utente di AEM Forms sono considerate risorse affidabili.

Per impostazione predefinita, la modalità protetta è attivata. Se necessario, puoi disattivare la modalità protetta:

1. Accedi a AEM console Web come amministratore. L’URL è `https://[server]:[port]/system/console/configMgr`
1. Apri Configurazioni Forms per dispositivi mobili per la modifica.
1. Deseleziona l’opzione Modalità protetta e fai clic su **Salva**. La modalità protetta è disabilitata.

## Aggiornamento dei moduli XFA di riferimento {#updating-referenced-xfa-forms}

In AEM Forms, un modello di modulo XFA può essere indirizzato da un modulo adattivo o da un altro modello di modulo XFA. Inoltre, un modello può fare riferimento a una risorsa o a un altro modello XFA.

Un modulo adattivo che fa riferimento a un XFA presenta i suoi campi associati ai campi disponibili in XFA. Quando si aggiorna un modello di modulo, il modulo adattivo associato tenta di eseguire la sincronizzazione con XFA. Per ulteriori dettagli, consulta [Sincronizzazione dei moduli adattivi con XFA associato](/help/forms/using/synchronizing-adaptive-forms-xfa.md).

La rimozione di un modello di modulo corrompe il modulo adattivo o il modello di modulo dipendente. Tale modulo adattivo viene talvolta definito informalmente come un modulo sporco. Nell’interfaccia utente di AEM Forms è possibile trovare i moduli sporchi in due modi.

* Un’icona di avviso viene visualizzata sulla miniatura del modulo adattivo nell’elenco delle risorse e il seguente messaggio viene visualizzato quando passi il puntatore sull’icona di avviso.

   `Schema/Form Template for this adaptive form has been updated so please go to Authoring mode and rebase it with new version.`

![Avviso per un modulo adattivo non sincronizzato dopo l&#39;aggiornamento dell&#39;XFA associato](assets/dirtyaf.png)

Viene mantenuto un flag per indicare se un modulo adattivo è sporco. Queste informazioni sono disponibili nella pagina delle proprietà del modulo, insieme ai metadati del modulo. Solo per i moduli adattivi sporchi, proprietà metadati `Model Refresh` display `Recommended` valore.

![Indicazione di un modulo adattivo non sincronizzato con il modello XFA](assets/model-refresh.png)
