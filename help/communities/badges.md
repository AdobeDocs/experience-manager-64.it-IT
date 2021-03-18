---
title: Console dei badge
seo-title: Console dei badge
description: La console dei badge per le comunità consente di aggiungere badge personalizzati che possono essere visualizzati per i membri guadagnati (assegnati) o quando assumono un ruolo specifico nella comunità (assegnati)
seo-description: La console dei badge per le comunità consente di aggiungere badge personalizzati che possono essere visualizzati per i membri guadagnati (assegnati) o quando assumono un ruolo specifico nella comunità (assegnati)
uuid: 9eeba240-f0d4-4937-baba-8bac0e0b2a36
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4194278f-5127-4105-b181-60961c7a1def
role: Administrator
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 5%

---


# Console Badge {#badges-console}

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

Un badge viene creato caricando un’immagine di dimensioni adeguate (72 dpi con un’altezza compresa tra 26 e 32 pixel) e specificando un nome. L’immagine del badge viene memorizzata nell’archivio in `/etc/community/badging/images` e replicata automaticamente nell’ambiente di pubblicazione.

Se l&#39;ambiente di pubblicazione è una farm di editori, è necessario configurare [la sincronizzazione utente](sync.md).

![chlimage_1-243](assets/chlimage_1-243.png)

* **[!UICONTROL Carica immagine]**

   (*Obbligatorio*) Un&#39;immagine di badge con dimensioni consigliate di 32 x 32 pixel a 72 dpi in formato JPEG o PNG.

* **[!UICONTROL Nome]**

   (*Obbligatorio*) Il nome del badge. È il nome predefinito `Display Name` e il nome del nodo del repository. Se il `Name` non è un nome di nodo di archivio valido, verrà modificato.

* **[!UICONTROL Nome visualizzato]**

   (*Facoltativo*) Nome da visualizzare per il badge nell&#39;interfaccia utente. Il valore predefinito è il testo non alterato immesso per `Name`.

* **[!UICONTROL Descrizione]**

   (*Facoltativo*) Una descrizione del badge.

## Informazioni aggiuntive {#additional-information}

Per informazioni dettagliate sull’impostazione delle regole di punteggio e contrassegno, consulta [Punteggio e badge](implementing-scoring.md).

Per la gestione dei badge per i membri, vedere [Console membri](members.md).
