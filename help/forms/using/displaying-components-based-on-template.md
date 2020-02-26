---
title: Visualizzazione dei componenti in base al modello utilizzato
seo-title: Visualizzazione dei componenti in base al modello utilizzato
description: Quando si crea un modulo, è possibile apprendere come abilitare i componenti nella barra laterale in base al modello selezionato.
seo-description: Quando si crea un modulo, è possibile apprendere come abilitare i componenti nella barra laterale in base al modello selezionato.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
translation-type: tm+mt
source-git-commit: 74d51d46d61b005930f382a33278ae0bea6435e2

---


# Visualizzazione dei componenti in base al modello utilizzato {#displaying-components-based-on-the-template-used}

Quando un autore crea un modulo adattivo utilizzando un [modello](/help/forms/using/template-editor.md), l&#39;autore del modulo può visualizzare e utilizzare componenti specifici in base ai criteri per i modelli. È possibile specificare un criterio per il contenuto del modello che consente di scegliere un gruppo di componenti che l&#39;autore del modulo vede al momento della creazione del modulo.

## Modifica dei criteri di contenuto di un modello {#changing-the-content-policy-of-a-template}

Quando create un modello, questo viene creato `/conf` nell’archivio dei contenuti. In base alle cartelle create nella `/conf` directory, il percorso del modello è: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Effettuate le seguenti operazioni per mostrare i componenti nella barra laterale in base ai criteri di contenuto di un modello:

1. Aprire CRXDE lite.

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. In CRXDE, individuate la cartella in cui viene creato il modello.

   Ad esempio: `/conf/<your-folder>/`

1. In CRXDE, passa a: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Per selezionare un gruppo di componenti, è necessario un nuovo criterio di contenuto. Per creare un nuovo criterio, copiate e incollate il criterio predefinito, quindi rinominatelo.

   Percorso del criterio contenuto predefinito: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   Nella `gridFluidLayout` cartella, copiate e incollate il criterio predefinito, quindi rinominatelo. Ad esempio, `myPolicy`.

   ![Copia dei criteri predefiniti](assets/crx-default1.png)

1. Selezionate il nuovo criterio creato, quindi selezionate la proprietà **components** nel pannello a destra con il tipo `string[]`.

   Quando si seleziona e si apre la proprietà components, viene visualizzata la finestra di dialogo Modifica componenti. La finestra di dialogo Modifica componenti consente di aggiungere o rimuovere gruppi di componenti utilizzando i **+** e **** i pulsanti. È possibile aggiungere un gruppo di componenti che include i componenti che gli autori desiderano usare.

   ![Aggiunta o rimozione di componenti nel criterio](assets/add-components-list1.png)

   Dopo aver aggiunto un gruppo di componenti, fate clic su **OK** per aggiornare l’elenco, quindi fate clic su **Salva tutto** sopra la barra degli indirizzi CRXDE e aggiornate.

1. Nel modello, modificate il criterio del contenuto da predefinito al nuovo criterio creato. ( `myPolicy` in questo esempio).

   Per modificare il criterio, in CRXDE, passare a `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   Nella `cq:policy` proprietà, passate `default` al nuovo nome del criterio ( `myPolicy`).

   ![Aggiornamento dei criteri per il contenuto dei modelli](assets/updated-policy.png)

   Quando si crea un modulo creato utilizzando il modello, è possibile vedere i componenti aggiunti nella barra laterale.

