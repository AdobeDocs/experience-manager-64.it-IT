---
title: Console Badge
seo-title: Console Badge
description: La console dei badge delle community consente di aggiungere dei simboli personalizzati che possono essere visualizzati per i membri al momento della loro acquisizione (assegnazione) o di un ruolo specifico nella comunità (assegnazione)
seo-description: La console dei badge delle community consente di aggiungere dei simboli personalizzati che possono essere visualizzati per i membri al momento della loro acquisizione (assegnazione) o di un ruolo specifico nella comunità (assegnazione)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---


# Console Badge {#badges-console}

## Informazioni sui simboli {#about-badges}

La console Community Badges consente di aggiungere distintivi personalizzati che possono essere visualizzati per un membro quando guadagnato (assegnato) o assume un ruolo specifico nella comunità (assegnato).

### Visibilità del badge {#badge-visibility}

Attualmente, i simboli assegnati a un membro della comunità o assegnati a un membro della stessa verranno visualizzati insieme al nome e all&#39;avatar nei seguenti percorsi:

* Profili
* [Forum](forum.md)
* [D/R](working-with-qna.md)
* [Leaderboards](enabling-leaderboard.md)
* [Ideazione](ideation-feature.md)

Nell’ambiente di authoring, per accedere alla console Badges

* Dalla navigazione globale: **[!UICONTROL Strumenti > Community > Badge]**

In questa console vengono visualizzati i simboli attualmente disponibili e dai quali è possibile aggiungere nuovi simboli.

![chlimage_1-242](assets/chlimage_1-242.png)

## Crea badge {#create-badge}

Un contrassegno viene creato caricando un’immagine di dimensioni appropriate (72 dpi con un’altezza compresa tra 26 e 32 pixel) e fornendo un nome. L&#39;immagine del contrassegno viene memorizzata nella directory archivio in `/etc/community/badging/images` e replicata automaticamente nell&#39;ambiente di pubblicazione.

Se l&#39;ambiente di pubblicazione è una farm di editori, è necessario configurare [sincronizzazione utente](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Carica immagine]**

   (*Richiesto*) Un&#39;immagine con un contrassegno di 32 x 32 pixel a 72 dpi consigliati in formato JPEG o PNG.

* **[!UICONTROL Nome]**

   (*Obbligatorio*) Il nome del contrassegno. È il nome predefinito `Display Name` e il nome del nodo del repository. Se `Name` non è un nome di nodo del repository valido, verrà modificato.

* **[!UICONTROL Nome visualizzato]**

   (*Facoltativo*) Nome da visualizzare per il contrassegno nell&#39;interfaccia utente. Il valore predefinito è il testo inalterato immesso per il simbolo `Name`.

* **[!UICONTROL Descrizione]**

   (*Facoltativo*) Una descrizione per il contrassegno.

## Informazioni aggiuntive {#additional-information}

Per informazioni dettagliate sulla configurazione delle regole di punteggio e contrassegno, vedere [Punteggio e Badge](implementing-scoring.md).

Per gestire i simboli per i membri, vedere [Console Membri](members.md).
