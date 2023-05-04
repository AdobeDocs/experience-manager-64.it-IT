---
title: Minificazione dei file JavaScript
seo-title: Minification of the JavaScript files
description: Istruzioni per generare codice minimizzato dopo le personalizzazioni dell’area di lavoro di AEM Forms per ottimizzare i file JS per il web.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 3%

---

# Minificazione dei file JavaScript {#minification-of-the-javascript-files}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

La minimizzazione rimuove dal codice sorgente i caratteri ridondanti, ad esempio lo spazio vuoto, la nuova riga e i commenti. Questo migliora le prestazioni riducendo le dimensioni del codice. Anche se la minimizzazione non influisce sulla funzionalità, riduce la leggibilità del codice.

Per generare codice minimizzato per le modifiche semantiche segui questi passaggi.

1. Copia `client-html/src/main/webapp/js` da src-package su filesystem.

   >[!NOTE]
   >
   >Vedi [Introduzione alla personalizzazione dell’area di lavoro di AEM Forms](/help/forms/using/introduction-customizing-html-workspace.md) per ulteriori dettagli sui pacchetti.

1. Aggiorna percorsi in `main.js` in client-html/src/main/webapp/js, per modelli/visualizzazioni aggiunti/aggiornati.

   Ad esempio, l&#39;aggiunta di un nuovo modello Sharequeue, ad esempio mySharequeue, cambia:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Aggiorna `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` nel caso in cui si verifichi una modifica/aggiunta dell&#39;alias in `main.js`.

   Ad esempio, l&#39;aggiunta di un nuovo modello Sharequeue, ad esempio mySharequeue, cambia:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. In client-html/src/main/webapp/js/minifier, esegui il comando:

   ```shell
   mvn clean install
   ```

   Genera una cartella minified-files, sotto client-html/src/main/webapp/js con minified main.js e register.js.

>[!NOTE]
>
>La minimizzazione funziona solo su JVM a 64 bit.

>[!NOTE]
>
>Se si minimizza, l’aggiornamento è interessato.
