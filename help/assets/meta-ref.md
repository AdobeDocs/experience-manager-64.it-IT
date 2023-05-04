---
title: Riferimento schema metadati
description: Scopri le convenzioni standard per la descrizione dei metadati delle risorse, inclusi Dublin Core, IPTC e altri schemi di metadati.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 3%

---

# Riferimento schema metadati {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Il riferimento seguente include informazioni su uno specifico schema di metadati (in ordine alfabetico), nonché un elenco di proprietà e relative definizioni.

## Dublin Core {#dublin-core}

I metadati Dublin Core forniscono un set standardizzato di convenzioni per la descrizione delle risorse al fine di facilitarne la ricerca. In [!DNL Experience Manager] Assets, Dublin Core descrive risorse digitali quali video, audio, immagini e documenti.

Il semplice set di elementi di metadati di base di Dublino (DCMES) contiene 15 elementi di metadati, come indicato nella tabella seguente. Ogni elemento Dublin Core è facoltativo e può essere ripetuto. Puoi aggiungere o eliminare le informazioni sui metadati di base di Dublino come faresti per i metadati specifici per i tipi di file multimediali.

Oltre al DCMES, esistono altri elementi di metadati creati dall&#39;iniziativa di base di Dublino. Consulta la sezione [Iniziativa di base di Dublino](https://dublincore.org/) per ulteriori informazioni.

| Proprietà | Descrizione |
|---|---|
| collaboratore | La persona o la società responsabile del contributo al contenuto. |
| copertura | La posizione geografica o il periodo di tempo coperto dall&#39;attività. |
| creatore | La persona o l’azienda responsabile della creazione del contenuto. |
| data | Data o periodo di tempo associato all’attività. |
| descrizione | Ulteriori informazioni sulla risorsa. |
| format | Il formato file, il supporto fisico o le dimensioni della risorsa. [!DNL Experience Manager] utilizza dc:format per indicare il tipo mime della risorsa. |
| identifier | Un riferimento univoco alla risorsa. |
| lingua | La lingua della risorsa (ad esempio, en per inglese). |
| editore | La persona o l’azienda responsabile della messa a disposizione del bene. |
| relation | Una risorsa correlata. |
| diritti | Informazioni su chi ha i diritti per questa risorsa. |
| source | Attività correlata da cui deriva l’attività. |
| soggetto | Argomento della risorsa. |
| titolo | Nome della risorsa. |
| tipo | La natura o il genere del bene. |

## IPTC {#iptc}

L&#39;International Press Telecommunications Council (IPTC) è un consorzio di agenzie di stampa in tutto il mondo - uno dei suoi obiettivi è quello di sviluppare e mantenere standard tecnici. L&#39;IPTC ha definito una serie di standard di metadata per le immagini che sono quasi universalmente accettati dai fotografi. Questi standard di metadati facevano parte dello standard più ampio noto come IPTC Information Interchange Model (IIM) creato negli anni &#39;90.

Sebbene le informazioni di intestazione IPTC siano state sostituite principalmente da XMP, per XMP sono disponibili uno schema di base IPTC e uno schema di estensione. Nei programmi immagine, le proprietà XMP e IPTC sono sincronizzate.
