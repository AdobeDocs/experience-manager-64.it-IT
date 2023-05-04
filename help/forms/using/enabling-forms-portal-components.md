---
title: Abilitazione dei componenti del portale moduli
seo-title: Enabling forms portal components
description: I componenti di Forms Portal sono disattivati. Abilitare i gruppi Document Services e Document Services Predicates per abilitare i componenti di Forms Portal.
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
exl-id: 01c5eb6b-b097-4354-84b2-8bee7b7626f2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 2%

---

# Abilitazione dei componenti del portale moduli {#enabling-forms-portal-components}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

I componenti del portale dei moduli non sono disponibili per l’uso. Per visualizzare i componenti nell’elenco dei componenti disponibili AEM barra laterale, esegui le seguenti operazioni:

1. Accedi all’istanza di authoring del tuo sito web e apri una pagina AEM Sites.

1. Per le pagine che utilizzano un modello statico, esegui i seguenti passaggi:

   1. Nell’intestazione della pagina, tocca ![elenco a discesa canvas](assets/canvas-drop-down.png) > **Progettazione** per aprire la pagina in modalità Progettazione.
   1. Tocca un componente (con bordo blu) e quindi tocca ![a livello di campo](assets/field-level.png) per selezionare il sistema paragrafo contenente il componente corrente.
   1. Nel sistema di paragrafi, tocca ![settings_icon](assets/settings_icon.png) per aprire la finestra di dialogo Modifica per il sistema paragrafo.
   1. Dall&#39;elenco di **[!UICONTROL Componenti consentiti]**, abilita le caselle di controllo per **[!UICONTROL Servizi basati su documenti]** e **[!UICONTROL Predicati di Document Services]** componenti. Tocca **[!UICONTROL OK]**.

1. Per le pagine che utilizzano un modello dinamico, esegui i seguenti passaggi:

   1. Nell’intestazione della pagina, tocca ![proprietà](assets/properties.png) > **Modifica modello** per aprire il modello della pagina.
   1. Tocca **Contenitore di layout** e toccare ![FeedManagement](assets/FeedManagement.png). In **Componenti consentiti** abilita **Predicati servizi basati su documenti e servizi basati su documenti** opzioni e tocca ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>Puoi anche abilitare componenti specifici da queste categorie selezionando i componenti. Per ulteriori informazioni sui componenti e sul loro utilizzo, consulta [Creazione di una pagina del portale dei moduli](/help/forms/using/creating-form-portal-page.md) e [Incorporazione di un componente collegamento in una pagina](/help/forms/using/embedding-link-component-page.md).

Ora le categorie di componenti Servizi documenti e Predicati servizi documenti sono disponibili nel browser Componenti. I componenti sono abilitati per tutte le pagine che utilizzano lo stesso modello.

## Articoli correlati

* [Abilitare i componenti del portale moduli](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina del portale dei moduli](/help/forms/using/creating-form-portal-page.md)
* [Elencare moduli in una pagina web utilizzando le API](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Usa componente Bozze e invii](/help/forms/using/draft-submission-component.md)
* [Personalizzare l’archiviazione delle bozze e dei moduli inviati](/help/forms/using/draft-submission-component.md)
* [Esempio per l&#39;integrazione del componente bozze e invii con il database](/help/forms/using/integrate-draft-submission-database.md)
* [Personalizzazione dei modelli per i componenti del portale dei moduli](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Introduzione alla pubblicazione di moduli su un portale](/help/forms/using/introduction-publishing-forms.md)
