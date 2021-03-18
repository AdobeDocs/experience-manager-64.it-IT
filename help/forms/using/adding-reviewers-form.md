---
title: Associazione dei revisori per l’invio a un modulo
seo-title: Associazione dei revisori per l’invio a un modulo
description: Scopri come associare i revisori per l’invio a un modulo in AEM Forms. I revisori associati esaminano un modulo inviato tramite il portale dei moduli.
seo-description: Scopri come associare i revisori per l’invio a un modulo in AEM Forms. I revisori associati esaminano un modulo inviato tramite il portale dei moduli.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Moduli adattivi
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Associazione dei revisori per l’invio a un modulo {#associating-submission-reviewers-with-a-form}

Quando si crea un modulo, è possibile specificare gli utenti che esaminano l’invio del modulo tramite il portale dei moduli e forniscono un feedback. L’organizzazione può raccogliere feedback e lavorare nuovamente sui moduli inviati.

AEM Forms consente di associare un gruppo di revisori a un modulo. Gli utenti aggiunti a un gruppo di revisione di un modulo visualizzano gli invii del modulo e forniscono un feedback.

I gruppi di revisori assegnati a un modulo possono esaminare solo gli invii del modulo specificato.

## Prerequisito {#prerequisite}

### Abilitazione della proprietà dei gruppi di revisori per i moduli adattivi tramite l&#39;editor dello schema metadati {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Per associare un gruppo di revisori a un modulo, modificare lo schema metadati dei moduli adattivi. Per impostazione predefinita, non è possibile aggiungere un gruppo di revisori a un modulo inviato.

Per modificare lo schema metadati:

1. In modalità di authoring, in Experience Manager, fai clic su **[!UICONTROL Strumenti > Risorse > Schemi di metadati]**.
1. Nella pagina Forms schema, passa a **[!UICONTROL Forms > Forms Authored in AEM]**.

   L’url della pagina è:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Seleziona **[!UICONTROL Modulo adattivo]** e fai clic su **[!UICONTROL Modifica]**.
1. Nella pagina Modifica modulo fare clic su **[!UICONTROL Avanzate]**.
1. Nella scheda Avanzate , trascina il componente **[!UICONTROL Testo a riga singola]** disponibile in Genera modulo.
1. Seleziona il componente di testo aggiunto per visualizzarne le impostazioni.

   In Impostazioni, immetti `./jcr:content/metadata/form-submission-reviewer-group` nel campo Mappa su proprietà .

   Il campo del gruppo di revisori per l’invio nelle proprietà avanzate del modulo adattivo viene attivato con il nome specificato in Etichetta campo.

## Associazione dei revisori per l’invio a un modulo {#associating-submission-reviewers-with-a-form-1}

Per associare i revisori per l’invio a un modulo adattivo, creare un gruppo di revisori e aggiungere gli utenti a tale gruppo. Aggiungere il gruppo di revisori creato nel campo del revisore dell’invio del modulo nelle proprietà avanzate del modulo.\
I gruppi di utenti consentono di associare diversi set di revisori per l’invio a diversi moduli adattivi. Questa funzione impedisce la revisione dell’invio da parte di un utente non autorizzato.

Prima di eseguire i seguenti passaggi, consulta [Prerequisito](/help/forms/using/adding-reviewers-form.md#prerequisite).

Per creare un gruppo e aggiungere membri, passare a **[!UICONTROL Strumenti > Operazioni > Protezione > Gruppi]**.\
Per ulteriori informazioni, consulta [Amministrazione utente e servizi](/help/sites-administering/security.md).\
Assicurati di aggiungere il gruppo creato come membro del gruppo di utenti predefinito: **forms-submit-reviewers**. Questo gruppo di utenti viene fornito con AEM Forms e assicura che gli utenti vengano aggiunti come revisori per l’invio.

Per associare gruppi di utenti a un modulo adattivo:

1. In modalità di authoring, passa a **[!UICONTROL Forms > Forms &amp; Documents]**.
1. Utilizza l&#39;opzione **[!UICONTROL Seleziona]** per selezionare un modulo adattivo, quindi fai clic su **[!UICONTROL Visualizza proprietà]**.
1. Nella finestra Proprietà del modulo, fare clic su **[!UICONTROL Modifica]**, quindi su **[!UICONTROL AVANZATO]**.
1. Immettere il gruppo nel campo relativo al gruppo di revisori per l&#39;invio e fare clic su **[!UICONTROL Fine]**.

   Il campo del gruppo di revisori per l’invio viene visualizzato con il nome specificato nello schema di metadati modificato dei moduli adattivi.

>[!NOTE]
>
>Replicare utenti e moduli per garantire la disponibilità di utenti e moduli nell’implementazione remota di AEM Forms.
>
>Assicurati che tutti gli utenti vengano replicati come membri di revisione dei gruppi di utenti nell&#39;implementazione remota.

