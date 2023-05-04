---
title: Modificare l’aspetto (HBS)
seo-title: Alter the Appearance
description: Modificare gli script HBS
seo-description: Modify the HBS scripts
uuid: 6e1030af-f170-4a60-9d3f-439afd05de57
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 70be208d-185b-4b27-8e01-74e62f656344
exl-id: 358b70b8-8122-4eda-baa7-d9a58d6901f9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 3%

---

# Modificare l’aspetto (HBS) {#alter-the-appearance-hbs}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Ora che i componenti per il sistema di commento personalizzato nella directory dell&#39;applicazione (/apps) sono in posizione, con una risorsaSuperType che fa riferimento al sistema di commento predefinito e il modello/vista personalizzato registrato, è possibile modificare l&#39;implementazione.

Per una semplice dimostrazione, viene rimosso l’avatar visualizzato dall’utente che ha effettuato l’accesso e che ha pubblicato un commento.

>[!NOTE]
>
>Per utilizzare l’estensione , l’istanza del sistema di commenti in un sito web interessato (/content) deve impostare il relativo resourceType come sistema di commenti personalizzato.

## Modificare gli script HBS {#modify-the-hbs-scripts}

Utilizzo [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Apri [/apps/custom/components/comments/comment/comment.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Aggiungi un commento al tag che include l&#39;avatar per un commento (~ riga 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* Apri [/apps/custom/components/comments/comments.hbs](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Aggiungi un commento al tag che include l&#39;avatar per la voce di commento successiva (~ riga 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Seleziona **Salva tutto**

## Replicare l&#39;app personalizzata {#replicate-custom-app}

Dopo che l’applicazione è stata modificata, è necessario replicare nuovamente il componente personalizzato.

Un modo per farlo è

* Dal menu principale

   * Seleziona **[!UICONTROL Strumenti > Operazioni > Replica]**
   * Seleziona `Activate Tree`
   * Imposta `Start Path`: a `/apps/custom`
   * Deseleziona `Only Modified`
   * Seleziona `Activate` pulsante

## Visualizza commento modificato sulla pagina di esempio pubblicata {#view-modified-comment-on-published-sample-page}

[Continuazione dell’esperienza](extend-sample-page.md#publish-sample-page) nell’istanza di pubblicazione, ancora connesso come lo stesso utente, è ora possibile aggiornare la pagina nell’ambiente di pubblicazione per visualizzare la modifica per rimuovere l’avatar:

![chlimage_1-81](assets/chlimage_1-81.png)

## Pacchetto di estensione dei commenti di esempio {#sample-comment-extension-package}

In allegato è presente un pacchetto dell’applicazione di commenti personalizzati creata in questa esercitazione.

[Ottieni file](assets/sample-comment-extension-6-1-fp3.zip)
