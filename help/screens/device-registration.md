---
title: Registrazione dispositivo
seo-title: Registrazione dispositivo
description: Questa pagina descrive il processo di registrazione del dispositivo in un progetto AEM Screens.
seo-description: Questa pagina descrive il processo di registrazione del dispositivo in un progetto AEM Screens.
uuid: babf0de1-1f39-4e22-82aa-ce7fa7052659
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: a1534cfd-66a1-4e28-8938-e09a24dec8ee
translation-type: tm+mt
source-git-commit: 3addef2141ebb831f8677d011d68faf88e648dc2

---


# Registrazione dispositivo{#device-registration}

La pagina seguente descrive il processo di registrazione del dispositivo in un progetto AEM Screens.

## Registrazione di un dispositivo {#registering-a-device}

Il processo di registrazione del dispositivo viene eseguito su due computer separati:

* Il dispositivo da registrare, ad esempio il display del segnale
* Server AEM utilizzato per registrare il dispositivo

>[!NOTE]
>
>Dopo aver scaricato l’ultimo Windows Player (*.exe*), dalla pagina dei download [**di **](https://download.macromedia.com/screens/)AEM 6.4 Player, segui i passaggi del lettore per completare l’installazione ad hoc:
>
>1. Tenete premuto sull’angolo in alto a sinistra per aprire il pannello di amministrazione.
>1. Andate a **Configurazione** dal menu delle azioni a sinistra e immettete l&#39;indirizzo della posizione dell&#39;istanza AEM in **Server** , quindi fate clic su **Salva**.
   >
   >
1. Fai clic sul collegamento **Registrazione** dal menu delle azioni a sinistra e dai passaggi sottostanti per completare il processo di registrazione del dispositivo.
>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sul dispositivo, avvia AEM Screens Player. Viene visualizzata l’interfaccia utente di registrazione.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. In AEM, andate alla cartella **Dispositivi** del progetto.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di un nuovo progetto per schermi nel dashboard di AEM, consulta [Creazione e gestione di schermi Progetto](/help/screens/creating-a-screens-project.md).

1. Toccate/fate clic sul pulsante **Gestione** dispositivi nella barra delle azioni.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toccate/fate clic sul pulsante Registrazione **** dispositivo in alto a destra.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Seleziona il dispositivo richiesto (come al punto 1) e tocca o fai clic su **Registra dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. In AEM, attendete che il dispositivo invii il codice di registrazione.

   ![screen_shot_2018-11-26at105150 am](assets/screen_shot_2018-11-26at105150am.png)

1. Nel dispositivo, controllate il codice **di** registrazione.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se il codice **di** registrazione è lo stesso su entrambi i computer, tocca o fai clic sul pulsante **Convalida** in AEM, come illustrato nel passaggio (6).
1. Impostate il nome desiderato per il dispositivo e fate clic su** Register*.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Toccate/fate clic** Fine** per completare il processo di registrazione.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >La funzione **Registra nuovo** consente di registrare un nuovo dispositivo.
   >
   >L&#39;opzione **Assegna visualizzazione** consente di aggiungere direttamente il dispositivo a uno schermo.

   Se si fa clic su **Fine**, sarà necessario assegnare il dispositivo a un display.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione e la gestione di una visualizzazione per il progetto Screens, vedere [Creazione e gestione dei display](/help/screens/managing-displays.md).

### Assegnazione del dispositivo a uno schermo {#assigning-device-to-a-display}

Se il dispositivo non è stato assegnato a un display, segui i passaggi seguenti per assegnare il dispositivo a uno schermo nel progetto AEM Screens:

1. Selezionate il dispositivo e fate clic su **Assegna dispositivo** dalla barra delle azioni.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Selezionare il percorso della visualizzazione nel percorso **Visualizza/Configurazione dispositivo**.

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. Fate clic su **Assegna** quando selezionate il percorso.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Fare clic su **Fine** una volta che il dispositivo è stato assegnato correttamente, come illustrato nella figura seguente.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Inoltre, è possibile visualizzare il dashboard di visualizzazione facendo clic su **Fine**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Limitazioni per la registrazione del dispositivo {#limitations-on-device-registration}

Limitazioni della password utente a livello di sistema potrebbero causare errori nella registrazione del dispositivo. La registrazione del dispositivo utilizza una password generata in modo casuale per creare l&#39;utente del dispositivo.

Se la password è limitata dalla configurazione *AuthorizableActionProvider* , la creazione dell&#39;utente del dispositivo potrebbe non riuscire.

>[!NOTE]
>
>La password casuale generata corrente è composta da 36 caratteri ASCII, compresi tra 33 e 122 (include quasi tutti i caratteri speciali).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Additional Resources {#additional-resources}

Per informazioni su AEM Screens Player, consulta [AEM Screens Player](/help/screens/working-with-screens-player.md).
