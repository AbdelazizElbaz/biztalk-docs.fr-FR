---
title: "Traiter les messages de notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8538cb89-1cca-45ad-b6f4-041e117963ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efed30f3e65c4f58a060f67539672c95b3d6df59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk-server"></a>Traiter les messages de notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server
Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications de modifications apportées aux tables de base de données SQL Server. Toutefois, l’adaptateur seulement vous envoie une notification que certains enregistrements ont été insérées, mises à jour ou supprimées dans une table de base de données donnée. Tout traitement sur ces enregistrements doit être gérée par les applications clientes eux-mêmes. Cette rubrique présente une description de scénario basé sur la façon de traiter les enregistrements dans la table en fonction du type de notification reçue à partir de la base de données SQL Server.  
  
## <a name="scenarios-for-performing-subsequent-actions-after-receiving-notification"></a>Scénarios permettant d’effectuer les Actions suivantes après avoir reçu la Notification  
 Voici quelques scénarios dans lesquels les clients de l’adaptateur doivent effectuer certaines tâches de post-notification.  
  
-   **Scénario 1**. Considérez un scénario dans lequel le client de l’adaptateur doit effectuer certaines tâches en fonction du type de notification que vous recevez à partir de SQL Server. Par exemple, l’application cliente doit mettre à jour les enregistrements dans la table « A » si les enregistrements sont insérés dans la table « B ». De même, l’application cliente doit supprimer des enregistrements à partir de la table « A » si les enregistrements sont supprimés de la table « B ».  
  
     Dans ce scénario, à partir du message de notification reçu, les clients de l’adaptateur doivent extraire le type de notification pour décider si la notification a été pour une opération d’insertion ou une opération de suppression. Une fois que le type de notification est établi, les clients de l’adaptateur doivent effectuer les actions suivantes pour insérer ou mettre à jour les tables concernées.  
  
-   **Scénario 2**. Considérez un scénario dans lequel l’emplacement de réception qui reçoit les messages de notification pour les modifications apportées à une table tombe en panne. Alors que l’emplacement de réception est arrêté, certains enregistrements sont ajoutés à la table. Toutefois, pour ces enregistrements le client de l’adaptateur ne reçoit pas de notification. Lorsque l’emplacement de réception est sauvegarder, l’adaptateur informe le client en envoyant un message spécifique et puis l’application cliente doit rechercher tous les enregistrements qui ont été insérées dans la table de base de données lors de l’emplacement de réception vers le bas.  
  
     Dans ce scénario, à partir du message de notification reçu, les clients de l’adaptateur doivent extraire les informations concernant si la notification est une modification apportée à une table de base de données ou pour le démarrage de l’emplacement de réception. Si la notification est pour le démarrage de l’emplacement de réception, les clients de l’adaptateur doivent implémenter la logique pour traiter les enregistrements qui peuvent ont été insérées, mises à jour ou supprimés lors de l’emplacement de réception vers le bas.  
  
> [!NOTE]
>  Voici quelques exemples de scénarios qui sont répertoriés pour mieux comprendre comment utiliser la fonctionnalité de notification dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Toutefois, l’ensemble des tâches requises pour extraire le type de notification reçue de base sera similaire pour tous les scénarios. Cette rubrique fournit des instructions sur la façon d’extraire le type de notification à partir d’un message de notification.  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages-and-extracting-notification-type"></a>Comment cette rubrique illustre la réception de Messages de Notification et d’extraction d’un Type de Notification  
 Dans cette rubrique, pour illustrer comment traiter les messages de notification pour effectuer les tâches suivantes, nous considérons un scénario de base où un client de l’adaptateur utilise l’application BizTalk pour recevoir des messages de notification pour les modifications apportées à la table Employee. Une fois la notification est reçue, le client filtre le type de notification reçue et effectue les actions suivantes. Pour illustrer un scénario très simple, pensez que le client de l’adaptateur copie les messages de notification dans des dossiers différents en fonction du type de notification reçue. Par conséquent :  
  
-   Si le message de notification est pour une opération d’insertion ou de mise à jour, le client de l’adaptateur copie le message vers le dossier de C:\TestLocation\UpsertNotification.  
  
-   Si le message de notification est pour toute autre opération, par exemple supprimer, le client de l’adaptateur copie le message vers le dossier de C:\TestLocation\OtherNotificaiton.  
  
 Pour cela dans le cadre d’une application BizTalk, l’orchestration doit contenir les éléments suivants :  
  
-   Port pour recevoir des messages de notification de réception unidirectionnel.  
  
-   Une forme Expression qui contient une requête xpath pour extraire les informations sur le type de message de notification reçu.  
  
-   Une forme décider à inclure un bloc de décision dans l’orchestration. Dans ce bloc de décision, l’application décide que pour effectuer les opérations suivantes selon le message de notification reçu.  
  
-   Unidirectionnel deux ports d’envoi qui enfin de recevoir les messages de notification.  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a>Configuration des Notifications à l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés de liaison qui vous permet de configurer la réception des notifications à partir de SQL Server. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!NOTE]
>  Vous pouvez choisir de spécifier ces propriétés de liaison lors de la génération du schéma pour le **Notification** opération, même si elle n’est pas obligatoire. Si vous procédez ainsi, la liaison du port de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère comme partie de la génération de métadonnées contient également les valeurs spécifiées pour les propriétés de liaison. Vous pouvez importer ultérieurement ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] port de réception de la console Administration pour créer le WCF-custom ou WCF-SQL avec la liaison de propriétés déjà définies. Pour plus d’informations sur la création d’un port à l’aide du fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie l’opération entrante que vous souhaitez effectuer. Pour recevoir des messages de notification, affectez la valeur **Notification**.|  
|**NotificationStatement**|Spécifie l’instruction SQL (SELECT ou EXEC \<procédure stockée >) permet de s’inscrire aux notifications de requête. L’adaptateur reçoit un message de notification de SQL Server que lorsque le jeu de résultats pour que les modifications d’instruction SQL spécifiées.|  
|**NotifyOnListenerStart**|Spécifie si l’adaptateur envoie une notification pour les clients de la carte au démarrage de l’écouteur.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications à partir de SQL Server, poursuivre la lecture.  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a>La réception des Messages de Notification à partir de la base de données SQL Server  
 Une opération sur la base de données SQL Server à l’aide [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour configurer l’adaptateur pour recevoir des messages de notification, ces tâches sont :  
  
1.  Créez un projet BizTalk, puis générer le schéma pour le **Notification** opération entrante. Si vous le souhaitez, vous pouvez spécifier des valeurs pour le **InboundOperationType** et **NotificationStatement** propriétés de liaison.  
  
2.  Créez un message dans le projet BizTalk pour la réception des notifications de la base de données SQL Server.  
  
3.  Créez une orchestration comme décrit dans la section précédente.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!NOTE]
    >  Pour les opérations entrantes, tels que la réception des messages de notification, vous devez configurer uniquement un WCF-Custom unidirectionnel ou port de réception WCF-SQL. Ports de réception bidirectionnel WCF-Custom ou WCF-SQL ne sont pas pris en charge pour les opérations entrantes.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **Notification** opération entrante. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer le schéma. Effectuer les tâches suivantes lors de la génération du schéma. Ignorer la première étape si vous ne souhaitez pas spécifier les propriétés de liaison au moment du design.  
  
1.  Spécifiez une valeur pour **InboundOperationType** et **NotificationStatement** propriétés de liaison lors de la génération du schéma. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir des instructions sur la façon de spécifier les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
2.  Sélectionnez le type de contrat **Service (opérations entrantes)**.  
  
3.  Génération du schéma pour le **Notification** opération.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer un message à recevoir des notifications à partir de la base de données SQL Server.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis **ajouter**.  
  
2.  Ouvrez la fenêtre Vue orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Tapez `NotifyReceive`.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Process_Notification.Notification*, où *Process_Notification* est le nom de votre projet BizTalk. *Notification* est le schéma généré pour le **Notification** opération.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages de notification à partir de la base de données SQL Server et puis en effectuant les tâches en fonction du type de notification reçue. Dans cette orchestration, l’adaptateur reçoit le message de notification en fonction de l’instruction SELECT spécifiée pour le **NotificationStatement** propriété de liaison. La requête xpath spécifiée dans la forme Expression extrait le type de notification dans une variable, par exemple **NotificationType**. La forme décider utilise la valeur de cette variable pour décider du type de notification reçue et prend le « chemin » approprié pour effectuer les opérations suivantes. Comme mentionné dans la section précédente, l’orchestration effectue les opérations suivantes en fonction du type de message de notification reçu.  
  
-   Si le message de notification est pour une opération d’insertion ou de mise à jour, le client de l’adaptateur copie le message vers le dossier de C:\TestLocation\UpsertNotification.  
  
-   Si le message de notification est pour toute autre opération, par exemple supprimer, le client de l’adaptateur copie le message vers le dossier de C:\TestLocation\OtherNotificaiton.  
  
 Par conséquent, l’orchestration doit contenir les éléments suivants :  
  
-   Port pour recevoir des messages de notification de réception unidirectionnel.  
  
-   Une forme Expression qui contient une requête xpath pour extraire le type de notification reçue.  
  
-   Une forme décider à inclure un bloc de décision dans l’orchestration. Dans ce bloc de décision, l’application décide que pour effectuer les opérations suivantes selon le message de notification reçu.  
  
-   Unidirectionnel deux ports d’envoi qui enfin de recevoir les messages de notification.  
  
-   Forme réception.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration permettant d’effectuer la publication &#45; tâches de notification](../../adapters-and-accelerators/adapter-sql/media/20f62716-603d-4293-84f7-8c8f6d82ccd0.gif "20f62716-603d-4293-84f7-8c8f6d82ccd0")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveNotification|Recevoir|-Définissez **nom** à *ReceiveNotification*<br /><br /> -Définissez **activer** à *True*|  
  
### <a name="adding-an-expression-shape"></a>Ajout d’une forme Expression  
 L’objectif d’intégration d’une forme Expression dans l’orchestration est d’avoir une requête xpath pour extraire le type de message de notification reçue. Avant de créer une requête xpath, examinons le format d’un message de notification. Un message de notification classique ressemble à ceci :  
  
```  
<Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
  <Info>Insert</Info>   
  <Source>Data</Source>   
  <Type>Change</Type>   
</Notification>  
```  
  
 Comme vous le voir, les informations sur le type de la notification sont disponibles dans le `<info>` balise, au sein du parent `<Notification>` balise. Par conséquent, dans le cadre de cette forme d’expression, vous devez :  
  
-   Créez une variable qui contient la valeur dans la `<Info>` de balise et définissez son type sur System.String. Pour plus d’informations sur la création des variables, consultez [à l’aide de Variables dans les Orchestrations](../../core/using-variables-in-orchestrations.md).
  
     Pour cette rubrique, nom de la variable en tant que **NotificationType**.  
  
-   Créer une requête xpath pour extraire la valeur de la \<Info > balise. La requête xpath ressemble à ceci :  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     Dans cette requête xpath, **NotifyReceive** est le message que vous avez créé pour la réception des messages de notification. L’extrait de code dans le `string` fonction indique que la requête doit extraire la valeur dans la `<Info>` balise, qui à son tour se trouve dans le `<Notification>` balise. Enfin, la valeur extraite par la requête est affectée à la **NotificaitonType** variable.  
  
### <a name="adding-a-decide-shape"></a>Ajout d’une forme décider  
 L’objectif de l’ajout d’une forme décider doit inclure un bloc de décision dans l’orchestration afin de déterminer les pour effectuer les opérations suivantes en fonction du type de message de notification reçu. La décision est prise en fonction de la valeur de la **NotificationType** variable. Dans cette rubrique, l’orchestration prend une décision en fonction du type de message de notification reçu. Par conséquent, la condition de la forme de la règle est spécifiée comme suit :  
  
```  
NotificationType.Equals("Insert") | NotificationType.Equals("Update")  
```  
  
 Cette condition suggère que se la valeur de **NotificaitonType** variable est Insert ou Update, l’orchestration effectue un ensemble de tâches. Si la valeur de **NotificationType** variable est autre chose, l’orchestration exécutera un autre ensemble de tâches.  
  
 Comme indiqué dans les sections précédentes, pour illustrer une approche simple, l’orchestration de copier les messages dans des dossiers différents en fonction du type de message de notification. C’est le cas, dans la règle et les blocs Else, vous devez ajouter des formes d’envoi pour envoyer les messages vers différents ports. Pour cette rubrique, nom de la forme envoi dans le bloc de règle comme **SendUpsertNotification** et la forme envoi dans le bloc Else comme **SendOtherNotification**.  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Vous devez maintenant ajouter les ports logiques suivants à l’orchestration :  
  
-   Unidirectionnel port de réception pour recevoir des messages de notification de SQL Server.  
  
-   Port d’envoi unidirectionnel pour envoyer des messages de notification pour les opérations Insert et Update dans un dossier spécifique.  
  
-   Port d’envoi unidirectionnel pour envoyer des messages de notification pour toutes les autres opérations à un dossier spécifique.  
  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|SQLNotifyPort|-Définissez **identificateur** à *SQLNotifyPort*<br /><br /> -Définissez **Type** à *SQLNotifyPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|NotificationUpsertPort|-Définissez **identificateur** à *NotificationUpsertPort*<br /><br /> -Définissez **Type** à *NotificationUpsertPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
|OtherNotificationPort|-Définissez **identificateur** à *OtherNotificationPort*<br /><br /> -Définissez **Type** à *OtherNotificationPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *SQLNotifyPort.Notify.Request*|  
|SendUpsertNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *NotificationUpsertPort.Upsert.Request*|  
|SendOtherNotification|-Définissez **Message** à *sélectionner*<br /><br /> -Définissez **opération** à *OtherNotificationPort.Other.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un WCF-Custom physique ou le port de réception unidirectionnel WCF-SQL. Ce port d’écoute pour les notifications provenant de la base de données SQL Server. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        > [!IMPORTANT]
        >  Vous n’avez pas besoin d’effectuer cette étape si vous avez spécifié les propriétés de liaison au moment du design. Dans ce cas, vous pouvez créer un WCF-custom ou WCF-SQL port de réception, avec le jeu de propriétés de liaison requis, en important le fichier de liaison créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Affectez la valeur **Notification**.|  
        |**NotificationStatement**|Affectez la valeur :<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **Remarque :** vous devez spécifier plus précisément les noms de colonnes dans l’instruction comme indiqué dans l’instruction SELECT suivante. En outre, vous devez toujours spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `dbo.Employee`.|  
        |**NotifyOnListenerStart**|Affectez la valeur **True**.|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez effectuer afin d’en ajoutant le service de port de réception comportement lors de la configuration WCF-Custom ou WCF-SQL. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer Transaction Isolation Level et délai de Transaction SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprime les messages de notification à partir de la base de données SQL Server pour les opérations Insert et Update. Configurer ce port pour supprimer les messages de notification dans le dossier C:\TestLocation\UpsertNotification.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprime les messages de notification à partir de la base de données SQL Server pour toutes les autres opérations. Configurer ce port pour supprimer les messages de notification dans le dossier C:\TestLocation\OtherNotification.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour la réception des messages de notification à partir de la base de données SQL Server et pour effectuer les opérations Select et de mise à jour ultérieures. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SQL unidirectionnel port de réception, qui reçoit les messages de notification à partir de la base de données est en cours d’exécution de SQL Server.  
  
-   Les deux ports d’envoi de fichier, qui permet de recevoir des messages à partir de SQL Server, sont en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Une fois que vous démarrez l’orchestration BizTalk, l’ensemble d’actions suivantes ont lieu :  
  
-   Étant donné que la **NotifyOnListenerStart** liaison de la propriété est définie sur **True**, le message d’erreur suivant :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>SqlBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     Notez que la valeur dans la `<Info>` balise est « ListnerStarted ». Par conséquent, ce message est reçu dans le dossier de C:\TestLocation\OtherNotification.  
  
-   Insérer un enregistrement dans la table Employee. Vous recevez un message de notification qui ressemble à la suivante :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Notez que la valeur dans la `<Info>` balise est « Insert ». Par conséquent, ce message est reçu dans le dossier de C:\TestLocation\UpsertNotification.  
  
-   Mettre à jour un enregistrement dans la table Employee. Vous recevez un message de notification qui ressemble à la suivante :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Notez que la valeur dans la `<Info>` balise est « Update ». Par conséquent, ce message est reçu dans le dossier de C:\TestLocation\UpsertNotification.  
  
-   Supprimer un enregistrement de la table Employee. Vous recevez un message de notification qui ressemble à la suivante :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Delete</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Notez que la valeur dans la `<Info>` balise est « Delete ». Par conséquent, ce message est reçu dans le dossier de C:\TestLocation\OtherNotification.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="performing-complex-operations-after-receiving-notification-messages"></a>Exécution d’opérations complexes après la réception des Messages de Notification  
 Pour plus de simplicité et de mieux comprendre, l’orchestration dans cette rubrique copie des messages dans des dossiers différents selon le type de notification. Toutefois, dans les scénarios réels, vous souhaiterez effectuer des opérations plus complexes. Vous pouvez effectuer les procédures similaires comme indiqué dans cette rubrique, la build sur ces derniers pour effectuer les opérations que vous le souhaitez. Par exemple, vous pouvez modifier l’orchestration pour insérer des enregistrements dans une autre table si vous obtenez un message de notification pour une opération d’insertion sur la table Employee. Dans ce cas, vous pouvez apporter des modifications appropriées au sein de la forme décider.  
  
 Un tel scénario est expliqué en détail dans [didacticiel 2 : employé - processus de bon de commande à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)