---
title: Configurazione dei componenti in modalità Progettazione
seo-title: Configuring Components in Design Mode
description: Quando AEM’istanza è installata out-of-the-box, nella barra laterale è immediatamente disponibile una selezione di componenti. Oltre a questi, sono disponibili anche vari altri componenti. È possibile utilizzare la modalità Progettazione per attivarli o disattivarli.
seo-description: When AEM instance is installed out-of-the-box, a selection of components are immediately available in the sidekick. In addition to these, various other components are also available. You can use Design mode to Enable/disable such components.
page-status-flag: de-activated
uuid: 57249965-3a30-49ce-9fb0-864c5daaa262
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 93f98f7b-7ab8-4d9c-b179-dc99b80ffc91
exl-id: af6c383b-f8fd-442c-8fc5-3cdd40657c6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---

# Configurazione dei componenti in modalità Progettazione{#configuring-components-in-design-mode}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando AEM’istanza è installata out-of-the-box, nella barra laterale è immediatamente disponibile una selezione di componenti.

Oltre a questi, sono disponibili anche vari altri componenti. È possibile utilizzare la modalità Progettazione per [Attiva/disattiva tali componenti](#enabledisablecomponentsusingdesignmode). Quando è attivata e si trova sulla pagina, è possibile utilizzare la modalità Progettazione per [configurare gli aspetti della progettazione del componente](#configuringcomponentsusingdesignmode) modificando i parametri degli attributi.

>[!NOTE]
>
>Presta attenzione quando modifichi questi componenti. Le impostazioni di progettazione sono spesso una parte integrante della progettazione dell’intero sito web e dovrebbero quindi essere modificate solo da un utente con le autorizzazioni e l’esperienza appropriate, spesso da un amministratore o sviluppatore. Vedi [Sviluppo di componenti](/help/sites-developing/components.md) per ulteriori informazioni.

Ciò comporta l’aggiunta o la rimozione dei componenti consentiti nel sistema di paragrafi per la pagina. Il sistema paragrafo ( `parsys`) è un componente composto che contiene tutti gli altri componenti paragrafo. Il sistema di paragrafi consente agli autori di aggiungere a una pagina componenti di tipi diversi e contiene tutti gli altri componenti paragrafo. Ciascun tipo di paragrafo è rappresentato da un componente.

Ad esempio, il contenuto di una pagina prodotto può contenere un sistema paragrafo contenente i seguenti elementi:

* Un’immagine del prodotto (sotto forma di un paragrafo immagine o testo)
* Descrizione del prodotto (come paragrafo di testo)
* Tabella con dati tecnici (come paragrafo di una tabella)
* Un modulo compilato dagli utenti (come paragrafo iniziale, elemento modulo e fine modulo)

>[!NOTE]
>
>Vedi [Sviluppo di componenti](/help/sites-developing/components.md#paragraphsystem) e [Linee guida per l’utilizzo di modelli e componenti](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) per ulteriori informazioni `parsys`.

## Attivare/disattivare i componenti {#enable-disable-components}

In modalità Progettazione, la barra laterale viene ridotta a icona ed è possibile configurare i componenti accessibili per l’authoring:

1. Per passare alla modalità Progettazione, apri una pagina da modificare e utilizza l’icona Barra laterale:

   ![](do-not-localize/chlimage_1.png)

1. Fai clic su **Modifica** sul sistema Paragrafo (**Progettazione di par**).

   ![screen_shot_2012-02-08at102726am](assets/screen_shot_2012-02-08at102726am.png)

1. Viene visualizzata una finestra di dialogo in cui sono elencati i gruppi di componenti visualizzati nella barra laterale e i singoli componenti in essi contenuti.

   Seleziona in base alle esigenze per aggiungere o rimuovere i componenti disponibili nella barra laterale.

   ![screen_shot_2012-02-08at103407am](assets/screen_shot_2012-02-08at103407am.png)

1. La barra laterale viene ridotta a icona in modalità Progettazione. Facendo clic sulla freccia è possibile ingrandire la barra laterale e tornare alla modalità di modifica:

   ![](do-not-localize/sidekick-collapsed.png)

## Configurazione della progettazione di un componente {#configuring-the-design-of-a-component}

In modalità Progettazione è inoltre possibile configurare gli attributi per i singoli componenti. Ogni componente ha i propri parametri, nell’esempio seguente viene illustrato il **Immagine** componente:

1. Per passare alla modalità Progettazione, apri una pagina da modificare e utilizza l’icona Barra laterale:

   ![](do-not-localize/chlimage_1-1.png)

1. Puoi configurare la progettazione dei componenti.

   Ad esempio, se fai clic su **Modifica** sul componente Immagine (**Progettazione di immagini**) puoi configurare i parametri specifici del componente:

   ![chlimage_1-12](assets/chlimage_1-12.png)

1. Fai clic su **OK** per salvare le modifiche.

1. La barra laterale viene ridotta a icona in modalità Progettazione. Facendo clic sulla freccia è possibile ingrandire la barra laterale e tornare alla modalità di modifica:

   ![](do-not-localize/sidekick-collapsed-1.png)
