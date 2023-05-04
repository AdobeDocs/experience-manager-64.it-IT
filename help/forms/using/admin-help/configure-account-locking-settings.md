---
title: Configurare le impostazioni di blocco dell’account
seo-title: Configure account-locking settings
description: Utilizzare l'opzione Abilita blocco account per bloccare gli account utente dopo un numero specificato di errori di autenticazione consecutivi.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# Configurare le impostazioni di blocco dell’account {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4 ha raggiunto la fine del supporto esteso e questa documentazione non viene più aggiornata. Per maggiori dettagli, consulta la nostra [periodi di assistenza tecnica](https://helpx.adobe.com/it/support/programs/eol-matrix.html). Trova le versioni supportate [qui](https://experienceleague.adobe.com/docs/).

Quando aggiungi un dominio, specifica se abilitare il blocco dell’account. Quando l’opzione Abilita blocco account è selezionata, gli account utente vengono bloccati dopo un numero specificato di errori di autenticazione consecutivi. Dopo un periodo di tempo specificato, l&#39;utente può tentare di nuovo l&#39;autenticazione. Questa funzione impedisce agli utenti di provare diverse combinazioni di credenziali per accedere al sistema.

Utilizzare le impostazioni nella pagina Gestione dominio per specificare il numero massimo di errori di autenticazione e il periodo di tempo in cui gli account vengono bloccati. Queste impostazioni si applicano a tutti i domini che hanno abilitato il blocco dell&#39;account.

1. Nella console di amministrazione, fai clic su **[!UICONTROL Impostazioni > Gestione utente > Gestione dominio]**.
1. Nella casella Errori di autenticazione consecutivi massimi immettere il numero di tentativi consecutivi per cui un utente può tentare di effettuare l&#39;accesso prima che l&#39;account sia bloccato. Il valore predefinito è 20.
1. Nella casella Sblocca l&#39;account dopo (minuti) immettere il numero di minuti in cui l&#39;account utente è bloccato. Dopo il numero specificato di minuti, l&#39;utente può tentare di nuovo l&#39;accesso. Il valore predefinito è 30.
1. Fai clic su **[!UICONTROL Salva]**.
