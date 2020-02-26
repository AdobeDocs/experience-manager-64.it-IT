---
title: Associazione di revisori per l'invio a un modulo
seo-title: Associazione di revisori per l'invio a un modulo
description: Scoprite come associare i revisori all'invio di un modulo in AEM Forms. I revisori associati rivedono un modulo inviato tramite il portale dei moduli.
seo-description: Scoprite come associare i revisori all'invio di un modulo in AEM Forms. I revisori associati rivedono un modulo inviato tramite il portale dei moduli.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Associazione di revisori per l&#39;invio a un modulo {#associating-submission-reviewers-with-a-form}

Quando si crea un modulo, è possibile specificare gli utenti che rivedono gli invii del modulo tramite il portale dei moduli e fornire feedback. L&#39;organizzazione può raccogliere i commenti e rielaborare i moduli inviati.

AEM Forms consente di associare un gruppo di revisori a un modulo. Gli utenti aggiunti a un gruppo di revisione di un modulo possono vedere gli invii del modulo e fornire feedback.

I gruppi di revisori assegnati a un modulo possono esaminare solo gli invii del modulo specificato.

## Prerequisito {#prerequisite}

### Attivazione della proprietà dei gruppi di revisori per l&#39;invio di moduli adattivi tramite l&#39;editor dello schema di metadati {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Per associare un gruppo di revisori a un modulo, modificare lo schema di metadati dei moduli adattivi. Per impostazione predefinita, non è possibile aggiungere un gruppo di revisori a un modulo inviato.

Per modificare lo schema di metadati:

1. In modalità di creazione, in Experience Manager, fate clic su **[!UICONTROL Strumenti > Risorse > Schemi]** metadati.
1. Nella pagina Moduli schema, passa a **[!UICONTROL Moduli > Moduli creati in AEM]**.

   L’URL della pagina è:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Selezionare Modulo **** adattivo e fare clic su **[!UICONTROL Modifica]**.
1. Nella pagina Modifica modulo fare clic su **[!UICONTROL Avanzate]**.
1. Nella scheda Avanzate, trascinare il componente Testo **[!UICONTROL su riga]** singola disponibile in Modulo di creazione.
1. Selezionate il componente di testo aggiunto per visualizzarne le impostazioni.

   In Impostazioni, immettete `./jcr:content/metadata/form-submission-reviewer-group` il campo Mappa su proprietà.

   Il campo del gruppo di revisori per l&#39;invio nelle proprietà Avanzate del modulo adattivo è attivato con il nome specificato in Etichetta campo.

## Associazione di revisori per l&#39;invio a un modulo {#associating-submission-reviewers-with-a-form-1}

Per associare i revisori all’invio a un modulo adattivo, create un gruppo di revisori e aggiungeteli. Aggiungere il gruppo di revisori creato nel campo del revisore per l&#39;invio del modulo nelle proprietà avanzate del modulo.\
I gruppi di utenti consentono di associare diversi set di revisori per l’invio a diversi moduli adattivi. Questa funzione impedisce la revisione dell&#39;invio da parte di un utente non autorizzato.

Prima di eseguire i seguenti passaggi, vedete [Prerequisito](/help/forms/using/adding-reviewers-form.md#prerequisite).

Per creare un gruppo e aggiungervi dei membri, andate a **[!UICONTROL Strumenti > Operazioni > Protezione > Gruppi]**.\
Per ulteriori informazioni, consulta Amministrazione [utente e servizi](/help/sites-administering/security.md).\
Assicuratevi di aggiungere il gruppo creato come membro del gruppo di utenti predefinito: **form-submit-reviewers**. Questo gruppo di utenti viene fornito con AEM Forms e garantisce che gli utenti vengano aggiunti come revisori per l&#39;invio.

Per associare gruppi di utenti a un modulo adattivo:

1. In modalità di creazione, passare a **[!UICONTROL Moduli > Moduli e documenti]**.
1. Utilizzare l&#39;opzione **[!UICONTROL Seleziona]** per selezionare un modulo adattivo, quindi fare clic su **[!UICONTROL Visualizza proprietà]**.
1. Nella finestra Proprietà del modulo fare clic su **[!UICONTROL Modifica]**, quindi su **[!UICONTROL AVANZATO]**.
1. Immettete il gruppo nel campo del gruppo di revisori per l’invio e fate clic su **[!UICONTROL Fine]**.

   Il campo del gruppo di revisori per l&#39;invio viene visualizzato con il nome specificato nello schema di metadati modificato dei moduli adattivi.

>[!NOTE]
>
>Replicare utenti e moduli per garantire la disponibilità di utenti e moduli nell&#39;implementazione remota di AEM Forms.
>
>Assicurati che tutti gli utenti vengano replicati come membri di revisione dei gruppi di utenti nell&#39;implementazione remota.

