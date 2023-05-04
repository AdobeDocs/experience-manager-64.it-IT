---
title: Console dei badge
seo-title: Badges Console
description: La console dei badge delle community consente di aggiungere badge personalizzati che possono essere visualizzati per i membri guadagnati (assegnati) o quando assumono un ruolo specifico nella comunità (assegnati)
seo-description: The Communities Badges console lets you add custom badges that can be displayed for members when earned (awarded) or when they take on a specific role in the community (assigned)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Admin
exl-id: b6aa9d73-4e20-446a-a1fc-78f8968d6844
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 7%

---

# Console dei badge {#badges-console}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

## Informazioni sui badge {#about-badges}

La console dei badge per le comunità consente di aggiungere badge personalizzati che possono essere visualizzati per un membro al momento della maturazione (assegnazione) o quando assume un ruolo specifico nella comunità (assegnazione).

### Visibilità del badge {#badge-visibility}

Attualmente, i badge che un membro della community guadagna o è assegnato verranno visualizzati insieme al suo nome e al suo avatar nelle seguenti posizioni:

* Profili
* [Forum](forum.md)
* [D/R](working-with-qna.md)
* [Leadership](enabling-leaderboard.md)
* [Ideazione](ideation-feature.md)

Nell’ambiente di authoring, per accedere alla console Badge

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Badge]**

In questa console vengono visualizzati i badge attualmente disponibili e da cui è possibile aggiungere nuovi badge.

![chlimage_1-242](assets/chlimage_1-242.png)

## Crea badge {#create-badge}

Un badge viene creato caricando un’immagine di dimensioni adeguate (72 dpi con un’altezza compresa tra 26 e 32 pixel) e specificando un nome. L’immagine del badge viene memorizzata nell’archivio all’indirizzo `/etc/community/badging/images` e viene replicato automaticamente nell’ambiente di pubblicazione.

Se l’ambiente di pubblicazione è una farm di editori, è necessario configurare [sincronizzazione utente](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Carica immagine]**

   (*Obbligatorio*) Immagine di badge con dimensioni consigliate di 32 x 32 pixel a 72 dpi in formato JPEG o PNG.

* **[!UICONTROL Nome]**

   (*Obbligatorio*) Il nome del badge. È il valore predefinito `Display Name` nonché il nome del nodo del repository. Se la `Name` non è un nome di nodo di archivio valido, verrà modificato.

* **[!UICONTROL Nome visualizzato]**

   (*Facoltativo*) Nome da visualizzare per il badge nell’interfaccia utente. Il valore predefinito è il testo non alterato immesso per `Name`.

* **[!UICONTROL Descrizione]**

   (*Facoltativo*) Una descrizione del badge.

## Informazioni aggiuntive {#additional-information}

Per informazioni dettagliate sull’impostazione delle regole di valutazione e contrassegno, consulta [Punteggio e badge](implementing-scoring.md).

Per gestire i badge per i membri, vedere [Console dei membri](members.md).
