---
title: Gestione delle richieste RGPD per la AEM Foundation
seo-title: Handling GDPR Requests for the AEM Foundation
description: Gestione delle richieste RGPD per la AEM Foundation
seo-description: null
uuid: d470061c-bbcf-4d86-9ce3-6f24a764ca39
contentOwner: sarchiz
discoiquuid: 8ee843b6-8cea-45fc-be6c-99c043f075d4
exl-id: dcd67a1e-b20f-4ed4-b154-dd250cbd8320
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 52%

---

# Gestione delle richieste RGPD per la AEM Foundation{#handling-gdpr-requests-for-the-aem-foundation}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

>[!IMPORTANT]
>
>Il RGPD è utilizzato come esempio nelle sezioni seguenti, ma i dettagli trattati sono applicabili a tutte le normative sulla protezione dei dati e sulla privacy; come RGPD, CCPA, ecc.

## Supporto per il RGPD in AEM Foundation {#aem-foundation-gdpr-support}

A livello di AEM Foundation, i Dati Personali memorizzati sono il Profilo utente. Pertanto, le informazioni contenute in questo articolo si occupano principalmente di come accedere e eliminare i profili utente, rispettivamente per soddisfare le richieste di accesso e cancellazione RGPD.

## Accesso a un profilo utente {#accessing-a-user-profile}

### Passaggi manuali {#manual-steps}

1. Apri la console di amministrazione degli utenti sfogliando **[!UICONTROL Impostazioni - Sicurezza - Utenti]** o navigando direttamente in `https://<serveraddress>:<serverport>/libs/granite/security/content/useradmin.html`

   ![useradmin2](assets/useradmin2.png)

1. Quindi, cerca l’utente in questione digitando il nome nella barra di ricerca nella parte superiore della pagina:

   ![ricerca utente](assets/usersearch.png)

1. Infine, apri il profilo utente facendo clic su di esso, quindi seleziona la scheda **[!UICONTROL Dettagli]**.

   ![userprofile_small](assets/userprofile_small.png)

### API HTTP {#http-api}

Come accennato, Adobe fornisce API per l’accesso ai dati utente, al fine di facilitare l’automazione. Esistono diversi tipi di API che puoi utilizzare:

**API UserProperties**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**API Sling**

*Individuazione della home utente:*

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

*Recupero dati utente*

Utilizzo del percorso del nodo dalla proprietà home del payload JSON restituito dal comando precedente:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Disabilitazione di un utente ed eliminazione dei profili associati {#disabling-a-user-and-deleting-the-associated-profiles}

### Disattiva utente {#disable-user}

1. Apri la console User Administration e cerca l’utente in questione, come descritto sopra.
1. Passa il puntatore del mouse sull’utente e fai clic sull’icona di selezione. Il profilo diventa grigio e indica che è selezionato.

1. Premi il pulsante Disattiva nel menu superiore per disabilitare l’utente:

   ![userdisable](assets/userdisable.png)

1. Infine, conferma l’azione:

   ![image2018-2-6_1-40-58](assets/image2018-2-6_1-40-58.png)

   L’interfaccia utente indica quindi che l’utente è stato disattivato disattivando la visualizzazione in grigio e aggiungendo un blocco alla scheda del profilo:

   ![disabilitato](assets/disableduser.png)

### Eliminare informazioni sul profilo utente {#delete-user-profile-information}

1. Accedi a CRXDE Lite, quindi cerca il `[!UICONTROL userId]`:

   ![image2018-2-6_1-57-11](assets/image2018-2-6_1-57-11.png)

1. Apri il nodo utente che si trova in `[!UICONTROL /home/users]` per impostazione predefinita:

   ![image2018-2-6_1-58-25](assets/image2018-2-6_1-58-25.png)

1. Elimina i nodi del profilo e tutti i relativi elementi figlio. Esistono due formati per i nodi del profilo, a seconda della versione AEM:

   1. Il profilo privato predefinito in `[!UICONTROL /profile]`
   1. `[!UICONTROL /profiles]`, per i nuovi profili creati con AEM 6.4.

   ![image2018-2-6_2-0-4](assets/image2018-2-6_2-0-4.png)

### API HTTP {#http-api-1}

Le procedure seguenti utilizzano lo `curl` strumento della riga di comando per illustrare come disabilitare l’utente con **[!UICONTROL cavery]** `userId` ed eliminare i profili disponibili nel percorso predefinito.

* *Individuazione della home utente*

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

* *Disabilitazione dell’utente*

Utilizzo del percorso del nodo dalla proprietà home del payload JSON restituito dal comando precedente:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (GDPR in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

* *Eliminazione dei profili utente*

Utilizzo del percorso del nodo dalla proprietà home del payload JSON restituito dal comando di individuazione account e dalle posizioni note dei nodi del profilo predefinite:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
