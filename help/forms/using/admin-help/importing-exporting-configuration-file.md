---
title: Importazione ed esportazione del file di configurazione
seo-title: Importing and exporting the configuration file
description: Scopri come importare ed esportare il file di configurazione per modificare le preferenze del server o configurare un’altra istanza di prodotto AEM forms.
seo-description: Learn how to import and export the configuration file in order to edit server preferences or configure another AEM forms product instance.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---

# Importazione ed esportazione del file di configurazione {#importing-and-exporting-the-configuration-file}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Utilizzare la pagina Configurazione manuale per scaricare una copia delle impostazioni di configurazione in formato XML. Le impostazioni in questo file controllano tutte le preferenze del server. Puoi quindi modificare il file e caricarlo nuovamente sul server. È inoltre possibile utilizzare il file per configurare un’altra istanza di prodotto AEM forms.

Per evitare rischi di sicurezza, il valore della password di binding per il server delle directory non è incluso in un file di configurazione esportato. Aggiornare la password nel file XML prima di importare il file in un nuovo sistema.

>[!NOTE]
>
>L’importazione del file di configurazione configura AEM moduli in base alle informazioni contenute nel file. Solo un amministratore di sistema o un consulente di servizi professionali che abbia familiarità con il prodotto AEM forms e con XML deve considerare la possibilità di modificare il file di configurazione. Potrebbe essere necessario modificare il file di configurazione, ad esempio, per riconfigurare un&#39;impostazione danneggiata.

**Esporta le informazioni di configurazione**

1. In Console di amministrazione, fai clic su Impostazioni > Gestione utente > Configurazione > Importa ed esporta file di configurazione.
1. Fai clic su Esporta. Se si utilizza Microsoft Internet Explorer, viene richiesto di specificare un percorso in cui salvare il file. Se utilizzi Firefox, il file viene salvato sul desktop.

**Importare le informazioni di configurazione**

1. In Console di amministrazione, fai clic su Impostazioni > Gestione utente > Configurazione > Importa ed esporta file di configurazione.
1. Fare clic su Sfoglia per trovare il file di configurazione, fare clic su Importa e quindi su OK.
