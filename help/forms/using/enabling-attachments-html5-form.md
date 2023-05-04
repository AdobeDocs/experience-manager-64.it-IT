---
title: Abilitazione degli allegati per un modulo HTML5
seo-title: Enabling attachments for an HTML5 form
description: Per impostazione predefinita, il supporto allegato per i moduli HTML5 è disattivato.
seo-description: By default, the attachment support for HTML5 forms is disabled.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 82a843c4-5cb2-4f5e-ad4d-cf2e9ea6cdb8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---

# Abilitazione degli allegati per un modulo HTML5 {#enabling-attachments-for-an-html-form}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile caricare, visualizzare in anteprima e inviare allegati con moduli HTML5. Per impostazione predefinita, il supporto per gli allegati è disattivato. Per abilitare il supporto allegato:

1. Crea un [profilo personalizzato](/help/forms/using/custom-profile.md) con proprietà stringa mutiselect `mfAttachmentOptions`.
1. Nel profilo personalizzato, specifica le proprietà `fileSizeLimit`, `multiSelect`e `buttonTex`per configurare le opzioni del widget di file allegato. Se necessario, puoi anche specificare altre proprietà personalizzate.

1. Nel profilo personalizzato, utilizza le seguenti configurazioni:

   * **multiSelect** -> true o false (true per impostazione predefinita)
   * **fileSizeLimit** -> value_in_mb (diciamo 5) (2 MB per impostazione predefinita)
   * **buttonText** -> Testo del pulsante per la finestra a comparsa (&quot;Allega&quot; per impostazione predefinita)
   * **accettare** -> tipi di file da accettare (&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot; per impostazione predefinita)

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9, gli utenti possono allegare file di dimensioni superiori al limite specificato. È un problema noto.

1. Utilizza la [editor di metadati](/help/forms/using/manage-form-metadata.md) per selezionare il profilo personalizzato creato in precedenza per HTML 5 forms.
1. Eseguire il rendering del modello di modulo con un profilo personalizzato e l’icona degli allegati viene visualizzata sulla barra degli strumenti dei moduli.

   >[!NOTE]
   >
   >Con il portale dei moduli è disponibile un profilo personalizzato con le bozze e le funzionalità degli allegati abilitate. Per ulteriori informazioni sulla **Salva come bozza** profilo, vedi [Salvataggio di moduli HTML5 come bozza](/help/forms/using/saving-html5-form-draft.md).

1. Fare clic sull&#39;icona dell&#39;allegato per visualizzare una finestra di dialogo per la selezione dell&#39;allegato. Sfoglia e seleziona l&#39;allegato e fai clic su **Allega**.

   >[!NOTE]
   >
   >Per visualizzare l&#39;anteprima di un allegato, fare clic sul nome dell&#39;allegato.

   >[!NOTE]
   >
   >L’opzione di anteprima del file non è disponibile per gli utenti anonimi.

## Formato di invio allegato {#attachment-submission-format}

Quando gli allegati sono attivati, il modulo HTML5 invia dati in più parti. I dati di invio in più parti sono suddivisi in due parti **dataXml** e **allegati**.

>[!NOTE]
>
>Per compatibilità con le versioni precedenti, se `mfAllowAttachments`se questa opzione è disattivata, i moduli di HTML5 non inviano i dati in più parti. Invia dati xml semplici in **application/xml** formato.

Se il flag mfAllowAttachments è attivato, il [invia servizio proxy](/help/forms/using/service-proxy.md) inoltre pubblica dati multipart con dataXml e allegati.
