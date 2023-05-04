---
title: Associazione dei revisori per l’invio a un modulo
seo-title: Associating submission reviewers with a form
description: Scopri come associare i revisori per l’invio a un modulo in AEM Forms. I revisori associati esaminano un modulo inviato tramite il portale dei moduli.
seo-description: Learn how to associate submission reviewers with a form in AEM Forms. Associated reviewers review a form submitted via forms portal.
uuid: 66834c2b-ae70-4a6e-ae8e-07d0e38de06b
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 7c39383b-b430-40a1-9bcb-f5aaccb616ad
feature: Adaptive Forms
exl-id: b45d844e-acf9-4da2-b54e-08c67aa183a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# Associazione dei revisori per l’invio a un modulo  {#associating-submission-reviewers-with-a-form}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando si crea un modulo, è possibile specificare gli utenti che esaminano l’invio del modulo tramite il portale dei moduli e forniscono un feedback. L’organizzazione può raccogliere feedback e lavorare nuovamente sui moduli inviati.

AEM Forms consente di associare un gruppo di revisori a un modulo. Gli utenti aggiunti a un gruppo di revisione di un modulo visualizzano gli invii del modulo e forniscono un feedback.

I gruppi di revisori assegnati a un modulo possono esaminare solo gli invii del modulo specificato.

## Prerequisito {#prerequisite}

### Abilitazione della proprietà dei gruppi di revisori per i moduli adattivi tramite l’editor dello schema dei metadati {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Per associare un gruppo di revisori a un modulo, modificare lo schema metadati dei moduli adattivi. Per impostazione predefinita, non è possibile aggiungere un gruppo di revisori a un modulo inviato.

Per modificare lo schema metadati:

1. In modalità di authoring, in Experience Manager, fai clic su **[!UICONTROL Strumenti > Risorse > Schemi di metadati]**.
1. Nella pagina Forms schema , passa a **[!UICONTROL Forms > Forms Authoring in AEM]**.

   L’url della pagina è:

   ```
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/dam/content/schemaeditors/forms/forms/
    aem-authored
   ```

1. Seleziona **[!UICONTROL Modulo adattivo]** e fai clic su **[!UICONTROL Modifica]**.
1. Nella pagina Modifica modulo fare clic su **[!UICONTROL Avanzate]**.
1. Nella scheda Avanzate , trascina **[!UICONTROL Testo a riga singola]** componente disponibile in Genera modulo.
1. Seleziona il componente di testo aggiunto per visualizzarne le impostazioni.

   In Impostazioni, immetti `./jcr:content/metadata/form-submission-reviewer-group` nel campo Mappa su proprietà .

   Il campo del gruppo di revisori per l’invio nelle proprietà avanzate del modulo adattivo viene attivato con il nome specificato in Etichetta campo.

## Associazione dei revisori per l’invio a un modulo {#associating-submission-reviewers-with-a-form-1}

Per associare i revisori per l’invio a un modulo adattivo, creare un gruppo di revisori e aggiungere gli utenti a tale gruppo. Aggiungere il gruppo di revisori creato nel campo del revisore dell’invio del modulo nelle proprietà avanzate del modulo.\
I gruppi di utenti consentono di associare diversi set di revisori per l’invio a diversi moduli adattivi. Questa funzione impedisce la revisione dell’invio da parte di un utente non autorizzato.

Prima di eseguire i seguenti passaggi, vedi [Prerequisito](/help/forms/using/adding-reviewers-form.md#prerequisite).

Per creare un gruppo e aggiungervi membri, vai a **[!UICONTROL Strumenti > Operazioni > Protezione > Gruppi]**.\
Per ulteriori informazioni, consulta [Amministrazione e servizi utente](/help/sites-administering/security.md).\
Assicurati di aggiungere il gruppo creato come membro del gruppo di utenti predefinito: **moduli-sottomissione-revisori**. Questo gruppo di utenti viene fornito con AEM Forms e assicura che gli utenti vengano aggiunti come revisori per l’invio.

Per associare gruppi di utenti a un modulo adattivo:

1. In modalità di authoring, passa a **[!UICONTROL Forms > Forms e documenti]**.
1. Utilizza la **[!UICONTROL Seleziona]** per selezionare un modulo adattivo e fare clic su **[!UICONTROL Visualizza proprietà]**.
1. Nella finestra Proprietà del modulo, fare clic su **[!UICONTROL Modifica]**, quindi fai clic su **[!UICONTROL AVANZATO]**.
1. Inserire il gruppo nel campo Gruppo di revisori per l&#39;invio e fare clic su **[!UICONTROL Fine]**.

   Il campo del gruppo di revisori per l’invio viene visualizzato con il nome specificato nello schema di metadati modificato dei moduli adattivi.

>[!NOTE]
>
>Replicare utenti e moduli per garantire la disponibilità di utenti e moduli nell’implementazione remota di AEM Forms.
>
>Assicurati che tutti gli utenti vengano replicati come membri di revisione dei gruppi di utenti nell&#39;implementazione remota.
