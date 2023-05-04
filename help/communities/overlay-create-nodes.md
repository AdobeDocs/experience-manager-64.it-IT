---
title: Crea nodi
seo-title: Create Nodes
description: Sovrapponi il sistema dei commenti
seo-description: Overlay the comments system
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
exl-id: fc044a4e-0037-405f-8c26-b388c6a98733
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 12%

---

# Crea nodi {#create-nodes}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Sovrapponi il sistema di commenti con una versione personalizzata copiando il numero minimo di file necessari da /libs in /apps e modificandoli in /apps.

>[!CAUTION]
>
>Il contenuto della cartella /libs non viene mai modificato perché la reinstallazione o l&#39;aggiornamento possono eliminare o sostituire la cartella /libs mentre il contenuto della cartella /apps rimane intatto.

Utilizzo [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) in un&#39;istanza di authoring, inizia creando un percorso nella cartella /apps identico al percorso dei componenti sovrapposti nella cartella /libs .

Il percorso da duplicare è

* `/libs/social/commons/components/hbs/comments/comment`

Alcuni nodi nel percorso sono cartelle e alcuni sono componenti.

1. Sfoglia per [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Crea `/apps/social` (se non esiste già)
   * Seleziona `/apps` nodo
   * **[!UICONTROL Crea > Cartella ...]**
      * Inserisci il nome: `social`
1. Seleziona `social` nodo
   * **[!UICONTROL Crea > Cartella...]**
      * Inserisci il nome: `commons`
1. Seleziona `commons` nodo
   * **[!UICONTROL Crea > Cartella...]**
      * Inserisci il nome: `components`
1. Seleziona `components` nodo
   * **[!UICONTROL Crea > Cartella...]**.
      * Inserisci il nome: `hbs`
1. Seleziona `hbs` nodo
   * **[!UICONTROL Crea > Crea componente...]**
      * Inserisci etichetta: `comments`
      * Inserisci titolo: `Comments`
      * Immetti la descrizione: `List of comments without showing avatars`
      * Super Type: `social/commons/components/comments`
      * Inserisci gruppo: `Communities`
      * Fai clic su **[!UICONTROL Successivo]** fino a **[!UICONTROL OK]**
1. Seleziona `comments` nodo

   * **[!UICONTROL Crea > Crea componente...]**

      * Inserisci etichetta: `comment`
      * Inserisci titolo: `Comment`
      * Immetti la descrizione: `A comment instance without avatars`
      * Super Type: `social/commons/components/comments/comment`
      * Inserisci gruppo: `.hidden`
      * Fai clic su **[!UICONTROL Successivo]** fino a **[!UICONTROL OK]**
   * Seleziona **[!UICONTROL Salva tutto]**
1. Elimina il valore predefinito `comments.jsp`
   * Seleziona nodo `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Seleziona **[!UICONTROL Elimina]**
1. Elimina il commento predefinito.jsp
   * seleziona nodo `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Seleziona **[!UICONTROL Elimina]**
   * Seleziona **[!UICONTROL Salva tutto]**

>[!NOTE]
>
>Al fine di preservare la catena di ereditarietà, la `Super Type` (proprietà `sling:resourceSuperType`) dei componenti sovrapposti sono impostati sullo stesso valore del `Super Type` dei componenti sovrapposti, in questo caso
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`
>


La sovrapposizione è propria `Type`(proprietà `sling:resourceType`) deve essere un riferimento autonomo relativo in modo che tutti i contenuti non trovati in /apps vengano poi cercati in /libs.
* Nome: `sling:resourceType`
* Tipo: `String`
* Valore: `social/commons/components/hbs/comments`

1. Seleziona il verde `[+] Add`
   * Nome: `sling:resourceType`
   * Tipo: `String`
   * Valore: `social/commons/components/hbs/comments/comment`
1. Seleziona il verde `[+] Add`
   * Seleziona **[!UICONTROL Salva tutto]**

![chlimage_1-4](assets/chlimage_1-4.png)
