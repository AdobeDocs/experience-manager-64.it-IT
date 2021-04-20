---
title: Componente separatore nei moduli adattivi
seo-title: Componente separatore nei moduli adattivi
description: È possibile utilizzare il componente separatore per separare visivamente sezioni di un modulo.
seo-description: È possibile utilizzare il componente separatore per separare visivamente sezioni di un modulo.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Componente separatore nei moduli adattivi {#separator-component-in-adaptive-forms}

È possibile utilizzare il componente separatore per separare visivamente i pannelli di un modulo. È possibile definire l’aspetto e lo stile generali di un componente separatore specificando le seguenti proprietà del componente separatore:

* **Nome elemento:** specifica il nome del componente. Le espressioni SOM si rivolgono al componente con il valore specificato nel campo Nome elemento .
* **Spessore:** specifica lo spessore in pixel del componente separatore.
* **Colspan:** specifica il numero di colonne su cui si estende un componente separatore.
* **Classe CSS:** specifica la classe CSS personalizzata per il componente separatore
* **Stili in linea:** con AEM Forms, ora puoi applicare gli stili CSS in linea ai singoli componenti dei moduli adattivi e visualizzare in anteprima le modifiche in tempo reale.

Per specificare le proprietà di un componente separatore:

1. Seleziona un componente separatore e tocca ![cmppr](assets/cmppr.png). Le proprietà si aprono nella barra laterale.
1. Fai clic su una scheda nella sezione Proprietà CSS in linea per specificare le proprietà CSS. Ad esempio: a) Nella scheda Campo, fai clic su **Aggiungi elemento**. Viene aggiunta una riga con due campi.
1. Nel primo campo da sinistra, specifica una proprietà CSS3 da applicare. Ad esempio, **border**. È inoltre possibile selezionare una proprietà facendo clic sul pulsante freccia giù. L’elenco a discesa non è esaustivo e puoi specificare qualsiasi nome di proprietà CSS3 supportato in questo campo.
1. Nel campo adiacente, specifica un valore valido per la proprietà CSS3 specificata. Ad esempio, **3px solid black**.
1. Fare clic su **Aggiungi elemento** per specificare un&#39;altra proprietà e il relativo valore.
1. Fare clic su **Anteprima** per visualizzare in anteprima le modifiche apportate al modulo.
1. Fai clic su **OK** per confermare le modifiche o su **Annulla **per uscire dalla finestra di dialogo senza apportare alcuna modifica.

