---
title: Importazione ed esportazione di impostazioni globali
seo-title: Importing and exporting global settings
description: È possibile importare ed esportare le definizioni dei modelli di ricerca e le impostazioni globali per Workspace.
seo-description: You can import and export search template definitions and global settings for Workspace.
uuid: 8f1f210d-e850-4b2c-bb5a-942fa8299791
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 72fe5749-2fa2-442f-b679-7889faeafcac
exl-id: 9eabafbe-2193-4799-9bdd-c2be42ead0b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1229'
ht-degree: 0%

---

# Importazione ed esportazione di impostazioni globali {#importing-and-exporting-global-settings}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

È possibile importare ed esportare le definizioni dei modelli di ricerca e le impostazioni globali per Workspace.

>[!NOTE]
>
>Flex Workspace è obsoleto per AEM versione dei moduli.

Ad esempio, puoi passare da un ambiente di sviluppo a un ambiente di produzione esportando le definizioni dei modelli di ricerca e le impostazioni globali da un ambiente e importandole nell’altro.

Dopo aver esportato il file delle impostazioni globali, è possibile modificare le impostazioni in un editor XML o di testo. Tuttavia, le uniche impostazioni che è possibile modificare sono le impostazioni JChannelConnectionProperties, formViewOnly e specialRoutes. Per ulteriori informazioni, consulta [Impostazioni globali di Workspace](importing-exporting-global-settings.md#workspace-global-settings).

>[!NOTE]
>
>Se si modificano le proprietà dell&#39;evento nel file delle impostazioni globali, è necessario riavviare il server.

## Importare una definizione di modello di ricerca {#import-a-search-template-definition}

1. Nella console di amministrazione, fai clic su Servizi > Area di lavoro > Amministrazione globale.
1. Nella casella Importa definizione modello di ricerca fare clic su Scegli file e selezionare il modello di ricerca. È possibile importare solo le definizioni dei modelli di ricerca originariamente esportate da un’istanza di Workspace.
1. Fai clic su Importa.

## Esportare una definizione di modello di ricerca {#export-a-search-template-definition}

1. Nella pagina Amministrazione globale fare clic su Elenco tutto nella sezione Definizione del modello di ricerca Esportazione.
1. Nell’elenco dei modelli di ricerca, seleziona il modello da esportare.

   >[!NOTE]
   >
   >È possibile selezionare più di un modello, ma viene esportato solo l’ultimo modello selezionato.

1. Fare clic su Esporta, quindi salvare il file sul computer.

## Importa impostazioni globali {#import-global-settings}

1. Nella pagina Amministrazione globale, in Importa impostazioni globali fare clic su Scegli file e selezionare il file di impostazioni globali. Il file delle impostazioni globali deve essere in formato XML.
1. Fai clic su Importa.

## Esporta impostazioni globali {#export-global-settings}

1. Nella pagina Amministrazione globale fare clic su Esporta impostazioni globali in Esporta impostazioni globali.
1. Salvare il file sul computer.

## Impostazioni globali di Workspace {#workspace-global-settings}

È possibile modificare il file delle impostazioni globali; tuttavia, le uniche impostazioni che è possibile modificare sono le impostazioni JChannelConnectionProperties, formViewOnly e specialRoutes.

>[!NOTE]
>
>Flex Workspace è obsoleto per AEM versione dei moduli.

Il file delle impostazioni globali di Workspace include le seguenti impostazioni:

### impostazioni specialiRoutes {#specialroutes-settings}

La *specialRoutes* le impostazioni specificano le proprietà delle route speciali, approvate e negate, in Workspace. In alcune situazioni, i pulsanti relativi a tali percorsi vengono visualizzati sulle schede attività in Workspace e l’utente può selezionarli senza aprire il modulo. È possibile modificare le impostazioni specialRoutes nel file delle impostazioni globali per aggiungere nomi personalizzati per l&#39;approvazione e la negazione o per creare percorsi aggiuntivi.

**client_specialRoutes_route_authorization_style:** Nome dello stile che si trova nel tema Workspace, che identifica le icone dei pulsanti di approvazione. Lo stile deve includere valori per un’icona abilitata e disabilitata. Per definire uno stile per un pulsante personalizzato, è necessario utilizzare il modello seguente:
` .buttonApprove {  icon: Embed('images/LC_DirectApprove_Sm_N.png');  disabledIcon: Embed('images/LC_DirectApprove_Sm_D.png');  paddingLeft: 5;  }` Il file CSS Workspace è incorporato nel file workspace-theme.swf, che si trova nel file adobe-workspace-client.ear > adobe-workspace-client.war . Per modificare l&#39;aspetto di Workspace, è necessario ricompilare il file workspace-theme.swf.

**client_specialRoutes_route_deny_names:** La varietà di stringhe che un utente di Workbench può utilizzare per essere interpretata come &quot;negazione&quot;. Le stringhe distinguono tra maiuscole e minuscole. Ad esempio, il valore predefinito è deny. Se l’utente di Workbench utilizza la parola Rifiuta in un processo, la parola non verrà riconosciuta. Per personalizzare il pulsante di route è necessario aggiungere la parola Rifiuta a questa impostazione e applicare lo stile al pulsante.

**client_specialRoutes_route_deny_style:** Nome dello stile che si trova nel file tema Workspace, che identifica le icone del pulsante di rifiuto. Lo stile deve includere valori per un’icona abilitata e disabilitata. Per definire uno stile per un pulsante personalizzato, è necessario utilizzare il modello seguente:
`  .buttonDeny {   icon: Embed('images/LC_DirectDeny_Sm_N.png');   disabledIcon: Embed('images/LC_DirectDeny_Sm_D.png');   paddingLeft: 0;   }` **client_specialRoutes_route_authorization_names:** La varietà di stringhe che un utente di Workbench può utilizzare per essere interpretata come &quot;approvata&quot;. Le stringhe distinguono tra maiuscole e minuscole. Ad esempio, il valore predefinito è Approvato. Se l’utente di Workbench utilizza la parola Approva in un processo, la parola non verrà riconosciuta. Per personalizzare il pulsante di route, è necessario aggiungere la parola Approva a questa impostazione e applicare lo stile desiderato.

**client_specialRoutes_names:** Le chiavi utilizzate per individuare il valore stringa personalizzato dai file di risorse. Ogni voce in questa impostazione deve includere i valori per i nomi e lo stile.

### Impostazioni del gruppo di lavoro {#jgroup-settings}

Queste impostazioni vengono visualizzate solo se si è eseguito l&#39;aggiornamento da Adobe LiveCycle ES 2.5 o versioni precedenti.

**server_remoteevents_ClientTimeoutMilliseconds:** Tempo massimo di attesa dei messaggi evento da parte del gruppo JG. Questa impostazione non deve essere modificata.

**server_remoteevents_ServerTimeoutMilliseconds:** Timeout della ricezione dei messaggi JGroup sul server. Questa opzione imposta il ritardo per l’invio dei messaggi dal server al client.

**server_remoteevents_JChannelConnectionProperties:** Proprietà di connessione per il gruppo JG utilizzato per comunicare tra il server (in cui un evento di servizio viene elaborato dal servizio RemoteEvent) e tutte le istanze di Workspace.

Potrebbe essere necessario modificare i valori UDP per l&#39;indirizzo IP multicast (mcast_addr), la porta IP multicast (mcast_port) e il TTL per i pacchetti multicast (ip_ttl). Per impostazione predefinita, i valori dell&#39;indirizzo IP multicast e della porta vengono generati in modo casuale e, in genere, non è necessario modificare i valori. Tuttavia, se la tua azienda dispone di criteri di rete relativi a intervalli multicast specifici per gli indirizzi IP multicast, potrebbe essere necessario modificare i valori.

>[!NOTE]
>
>Il TTL deve essere maggiore del numero di switch di rete tra i server del cluster; tuttavia, se il valore è troppo alto, può causare il trasferimento dei pacchetti multicast nelle subnet, dove verranno scartati.

Le proprietà rimanenti in questa impostazione non devono essere modificate.

**server_remoteevents_JGroupName:** Nome del gruppo JG utilizzato per la comunicazione degli eventi remoti. Questo valore viene generato in modo casuale per evitare conflitti nei cluster. Questo valore non deve essere modificato.

### impostazioni formView {#formview-settings}

**client_formView_openFormInFullScreen:** Per visualizzare tutti i moduli in Workspace in modalità a schermo intero, imposta questa opzione su true. Per impostazione predefinita, questa opzione è impostata su false e i moduli non vengono visualizzati in modalità a schermo intero. Il servizio Utente contiene un&#39;opzione per aprire il documento associato a un&#39;attività in modalità a schermo intero. Questo consente di controllare la visualizzazione in base al processo.

**client_route_formViewOnly:** Se impostato su True, le route non vengono visualizzate nella vista a schede o a elenco in Workspace. Il valore predefinito è False, il che significa che le route vengono visualizzate nella vista a schede e nella vista a elenco.

### Altre impostazioni {#other-settings}

**client_mimeTypes_openOutsideBrowser:** Tipo MIME di documenti che verranno aperti al di fuori dell’istanza del browser Workspace. Se i processi della tua organizzazione richiedono un tipo MIME aggiuntivo, specificalo qui. I valori predefiniti sono:

* `application/msword`
* `application/msexcel`
* `application/ms-powerpoint`

**client_customUI_caching:** Memorizza in cache un&#39;interfaccia utente personalizzata dell&#39;attività.

**server_debugLevel:** Non modificare questa impostazione.

**client_pollingInterval:** Imposta l’intervallo di polling (in secondi) utilizzato in Flex Workspace (Obsoleto per i moduli AEM su JEE) per rilevare le attività nuove e modificate. Il valore predefinito è 3 secondi. Questo non funziona per AEM Forms Workspace.

**client_systemContext_name:** Specificare un nome personalizzato (ad esempio, Cittadino) da visualizzare nel campo Aggiunto da (nella scheda Allegati) per gli allegati di un’attività in AEM Forms Workspace.

Per definire il nome personalizzato:

`<client_systemContext_name>[custom name to display]</client_systemContext_name>`

>[!NOTE]
>
>Per l’applicazione Demo, il nome visualizzato predefinito è **Cittadino**. Per un&#39;applicazione personalizzata creata, il nome visualizzato predefinito è **Account di contesto del sistema**.
