---
title: "Recevoir des Notifications de requête par incréments de SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6972e01-80be-47be-986a-c2e4e0fb0cd1
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc9eda3ba1bee61b4737428f41870fc31504e3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-query-notifications-incrementally-from-sql-using-biztalk-server"></a>Recevoir des Notifications de requête par incréments de SQL à l’aide de BizTalk Server
> [!IMPORTANT]
>  Pour plus de concision, cette rubrique décrit uniquement comment recevoir des notifications de façon incrémentielle. Dans les scénarios d’entreprise, l’orchestration doit inclure dans l’idéal, de la logique permettant d’extraire le type de message de notification reçu, puis effectuez toutes les opérations suivantes. En d’autres termes, l’orchestration décrite dans cette rubrique doit être générée sur l’orchestration décrite dans [traiter les messages de notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md).  
  
 Cette rubrique montre comment configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de notification de requête incrémentielle à partir d’une base de données SQL Server. Pour illustrer les notifications incrémentielles, considérez une table Employee, avec une colonne « État ». Lorsqu’un nouvel enregistrement est inséré à cette table, la valeur de la colonne d’état est définie sur 0. Vous pouvez configurer l’adaptateur pour recevoir des notifications incrémentielles en procédant comme suit :  
  
-   S’inscrire pour les notifications à l’aide d’une instruction SQL qui Récupère tous les enregistrements dont la colonne d’état en tant que 0. Vous pouvez le faire en spécifiant l’instruction SQL pour le **NotificationStatement** propriété de liaison.  
  
-   Pour les lignes pour la notification des messages ont été reçus, vous devez mettre à jour la colonne d’état à 1.  
  
 Cette rubrique montre comment créer une orchestration BizTalk et de configurer une application BizTalk pour y parvenir.  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a>Configuration des Notifications à l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés de liaison qui vous permet de configurer la réception des notifications à partir de SQL Server. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!NOTE]
>  Vous pouvez choisir de spécifier ces propriétés de liaison lors de la génération du schéma pour le **Notification** opération, même si elle n’est pas obligatoire. Si vous procédez ainsi, la liaison du port de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère comme partie de la génération de métadonnées contient également les valeurs spécifiées pour les propriétés de liaison. Vous pouvez importer ultérieurement ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] port de réception de la console Administration pour créer le WCF-custom ou WCF-SQL avec la liaison de propriétés déjà définies. Pour plus d’informations sur la création d’un port à l’aide du fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie l’opération entrante que vous souhaitez effectuer. Pour recevoir des messages de notification, affectez la valeur **Notification**.|  
|**NotificationStatement**|Spécifie l’instruction SQL (SELECT ou EXEC \<procédure stockée\>) permet de s’inscrire aux notifications de requête. L’adaptateur reçoit un message de notification de SQL Server que lorsque le jeu de résultats pour que les modifications d’instruction SQL spécifiées.|  
|**NotifyOnListenerStart**|Spécifie si l’adaptateur envoie une notification pour les clients de la carte au démarrage de l’écouteur.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications à partir de SQL Server, poursuivre la lecture.  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a>Comment cette rubrique illustre la réception de Messages de Notification  
 Pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de messages de notification à partir de SQL Server, cette rubrique va vous montrer comment configurer l’adaptateur pour recevoir des notifications de modifications apportées à une table Employee. Supposons que la table Employee possède des colonnes Employee_ID, nom et l’état. Chaque fois qu’un nouvel employé est ajouté, la valeur de la colonne d’état est définie sur 0.  
  
 Pour illustrer la réception des notifications, procédez comme suit :  
  
-   Génération du schéma pour le **Notification** (opération entrante), et **sélectionnez** (opération sortante) sur la table Employee.  
  
-   Créer une orchestration qui a les éléments suivants :  
  
    -   Un emplacement de réception pour recevoir les messages de notification. Vous pouvez configurer pour la notification en spécifiant l’instruction SELECT en tant que :  
  
        ```  
        SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
        ```  
  
        > [!NOTE]
        >  Vous devez spécifiquement spécifier les noms de colonnes dans l’instruction comme indiqué dans cette instruction de sélection. En outre, vous devez toujours spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `dbo.Employee`.  
  
    -   Un port d’envoi pour mettre à jour les lignes pour lesquelles des notifications a déjà été envoyée. Pour faire en définissant la valeur dans la colonne État 1. Vous pouvez cela dans le cadre de l’opération de sélection en envoyant le message suivant à l’adaptateur.  
  
        ```  
        <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
          <Columns>Employee_ID,Name,Status</Columns>  
          <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
        </Select>  
        ```  
  
         Dans ce message, dans le cadre de la `<Query>` élément, vous spécifiez l’instruction de mise à jour pour mettre à jour la colonne d’état. Notez que cette opération doit être exécutée après que réception de la notification des messages afin que les lignes traitées sont mis à jour. Pour effectuer immédiatement avec la surcharge de la réponse de notification en attente et puis la supprimer manuellement un message de demande pour mettre à jour les lignes, vous allez générer le message de demande de mise à jour les lignes dans l’orchestration lui-même. Vous pouvez le faire à l’aide de la **construire un Message** forme dans une orchestration.  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a>La réception des Messages de Notification à partir de la base de données SQL Server  
 Une opération sur la base de données SQL Server à l’aide [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour configurer l’adaptateur pour recevoir des messages de notification, ces tâches sont :  
  
1.  Créez un projet BizTalk, puis générer le schéma pour le **Notification** (opération entrante) et **sélectionnez** (opération sortante) sur la table Employee. Si vous le souhaitez, vous pouvez spécifier des valeurs pour le **InboundOperationType** et **NotificationStatement** propriétés de liaison.  
  
2.  Créez un message dans le projet BizTalk pour la réception des notifications de la base de données SQL Server.  
  
3.  Créer des messages dans le projet BizTalk pour effectuer les sélection d’informations sur la base de données SQL Server et de recevoir des messages de réponse.  
  
4.  Créer une orchestration qui effectue les opérations suivantes :  
  
    -   Reçoit le message de notification à partir de SQL Server.  
  
    -   Crée un message pour sélectionner et mettre à jour les lignes pour lesquelles la notification est reçue.  
  
    -   Envoie ce message à SQL Server pour mettre à jour les lignes et reçoit une réponse.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!NOTE]
    >  Pour les opérations entrantes, tels que la réception des messages de notification, vous devez configurer uniquement un WCF-Custom unidirectionnel ou port de réception WCF-SQL. Ports de réception bidirectionnel WCF-Custom ou WCF-SQL ne sont pas pris en charge pour les opérations entrantes.  
  
7.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple IncrementalNotification, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **Notification** opération et **sélectionnez** opération sur la table Employee. Consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer le schéma. Effectuer les tâches suivantes lors de la génération du schéma. Ignorer la première étape si vous ne souhaitez pas spécifier les propriétés de liaison au moment du design.  
  
1.  Spécifiez une valeur pour **InboundOperationType** et **NotificationStatement** propriétés de liaison lors de la génération du schéma. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir des instructions sur la façon de spécifier les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
2.  Sélectionnez le type de contrat **Service (opérations entrantes)**.  
  
3.  Génération du schéma pour le **Notification** opération.  
  
4.  Sélectionnez le type de contrat **Client (Outbound operations)**.  
  
5.  Génération du schéma pour le **sélectionnez** opération sur **employé** table.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer trois messages : un pour recevoir des notifications à partir de la base de données SQL Server, un pour effectuer l’opération de sélection et un pour recevoir la réponse pour l’opération de sélection.  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SQLNotify.Notification*, où *SQLNotify* est le nom de votre projet BizTalk. *Notification* est le schéma généré pour le **Notification** opération.|  
  
6.  Répétez l’étape 3 pour créer deux nouveaux messages. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Select|*SQLNotify.TableOperation_dbo_Employee.Select*, où *TableOperation_dbo_Employee* est le schéma généré pour le **sélectionnez** opération|  
    |SelectResponse|*SQLNotify.TableOperation_dbo_Employee.SelectResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages de notification à partir de la base de données SQL Server et mise à jour des lignes pour lesquelles la notification a été reçue. Dans cette orchestration, l’adaptateur reçoit le message de notification en fonction de l’instruction SELECT spécifiée pour le **NotificationStatement** propriété de liaison. Le message de notification est reçu au niveau d’un emplacement de fichier. Une fois que la réponse est reçue, l’orchestration génère un message qui sera utilisé pour mettre à jour les lignes pour lesquelles la notification est reçue. La réponse de ce message est reçue également au même emplacement de fichier.  
  
 Par conséquent, l’orchestration doit contenir les éléments suivants :  
  
-   Port pour recevoir des messages de notification de réception unidirectionnel.  
  
-   Pour envoyer des messages pour mettre à jour des lignes et de recevoir de réponse pour le même port d’envoi bidirectionnel.  
  
-   A **construire un Message** forme pour construire des messages, pour exécuter l’opération de mise à jour, dans l’orchestration.  
  
-   Un fichier de port d’envoi pour enregistrer la réponse pour l’opération de mise à jour.  
  
-   Formes réception et envoi.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration pour recevoir des notifications de SQL Server](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveNotification|Recevoir|-Définissez **nom** à *ReceiveNotification*<br /><br /> -Définissez **activer** à *True*|  
|SaveNotification|Send|-Définissez **nom** à *SaveNotification*|  
|SendSelectMessage|Send|-Définissez **nom** à *SendSelectMessage*|  
|ReceiveSelectResponse|Recevoir|-Définissez **nom** à *ReceiveSelectResponse*|  
|SaveSelectResponse|Send|-Définissez **nom** à *SaveSelectResponse*|  
  
### <a name="adding-construct-message-shape"></a>Ajout de forme construire un Message  
 Vous pouvez utiliser la **construire un Message** forme pour générer un message de demande au sein de l’opération à effectuer l’opération de sélection. Pour ce faire, vous devez ajouter un **construire un Message** forme dans laquelle un **assignation du Message** forme à votre orchestration. Pour cet exemple, le **assignation du Message** forme appelle le code qui génère un message est envoyé à SQL Server pour effectuer l’opération de sélection. Le **assignation du Message** forme définit également l’action pour le message à envoyer à SQL Server.  
  
 Pour la forme construire un message, définissez la **Message construit** propriété **sélectionnez**.  
  
 Le code pour générer la réponse peut faire partie de la même solution Visual Studio en tant que votre projet BizTalk. Un exemple de code pour générer un message de réponse ressemble à ceci.  
  
```  
namespace SampleMessageCreator  
{  
    public class SampleMessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\TestLocation\\CreateMessage";  
            try  
            {  
                ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                Console.WriteLine("EXCEPTION: " + ex.ToString());  
                throw ex;  
            }  
            //Create Message From XML  
            Message = new XmlDocument();  
            Message.PreserveWhitespace = true;  
            Message.Load(ResponseDoc);  
            return Message;  
        }   
    }  
}  
```  
  
 Pour l’extrait de code précédent être en mesure de générer un message de demande, vous devez disposer d’un message de demande XML (pour l’opération Select sur la table Employee) dans l’emplacement spécifié pour le `XmlFileLocation` variable.  
  
> [!NOTE]
>  Une fois que vous générez le projet, SampleMessageCreator.dll sera créé dans le répertoire du projet. Vous devez ajouter cette DLL dans le global assembly cache (GAC). En outre, vous devez ajouter le SampleMessageCreator.dll en tant que référence dans le projet BizTalk.  
  
 Ajoutez l’expression suivante pour appeler ce code à partir de la **assignation du Message** forme et à définir l’action de message. Pour ajouter une expression, double-cliquez sur le **assignation du Message** forme pour ouvrir l’éditeur d’Expression.  
  
```  
Select = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Select(WCF.Action) = "TableOp/Select/dbo/Employee";  
```  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|SQLNotifyPort|-Définissez **identificateur** à *SQLNotifyPort*<br /><br /> -Définissez **Type** à *SQLNotifyPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*<br /><br /> -Créer une opération *notifier*. Cette opération est utilisée pour les messages de notification.<br /><br /> -Créer une opération *sélectionnez*. Cette opération est utilisée pour les messages de réponse select.|  
|SQLOutboundPort|-Définissez **identificateur** à *SQLOutboundPort*<br /><br /> -Définissez **Type** à *SQLOutboundPortType*<br /><br /> -Définissez **modèle de Communication** à *demande-réponse*<br /><br /> -Définissez **Direction de Communication** à *envoi / réception*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *SQLNotifyPort.Notify.Request*|  
|SaveNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *SaveMessagePort.Notify.Request*|  
|SendSelectMessage|-Définissez **Message** à *sélectionner*<br /><br /> -Définissez **opération** à *SQLOutboundPort.Select.Request*|  
|ReceiveSelectResponse|-Définissez **Message** à *SelectResponse*<br /><br /> -Définissez **opération** à *SQLOutboundPort.Select.Response*|  
|SaveSelectResponse|-Définissez **Message** à *SelectResponse*<br /><br /> -Définissez **opération** à *SaveMessagePort.Select.Request*|  
  
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
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Vous devez également spécifier l’action dans le port d’envoi.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera les messages à partir de la base de données SQL Server. Ils vous seront les messages de notification reçues de SQL Server et les messages pour la sélectionner et port d’envoi opération de mise à jour que vous effectuez par le biais WCF-Custom ou WCF-SQL.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour la réception des messages de notification à partir de la base de données SQL Server et pour effectuer les opérations Select et de mise à jour ultérieures. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SQL unidirectionnel port de réception, qui reçoit les messages de notification à partir de la base de données est en cours d’exécution de SQL Server.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour effectuer sélectionnez et les opérations de mise à jour sur la table Employee est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de SQL Server, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Pour exécuter cette opération, vous devez insérer un enregistrement dans la table Employee. Supposons que vous insérez un enregistrement avec les détails suivants :  
  
```  
Name = John Smith  
Designation = Manager  
Salary = 100000  
```  
  
 En outre, assurez-vous que le message XML pour exécuter la sélection et les opérations de mise à jour est disponible à l’adresse C:\TestLocation\MessageIn. Le fichier XML doit ressembler au suivant :  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>Employee_ID,Name,Status</Columns>  
  <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
</Select>  
```  
  
 Une fois que l’enregistrement est inséré, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur reçoit un message de notification qui ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Ce message indique qu’un enregistrement a été inséré dans la table Employee. Notez que la valeur de la `<Info>` élément est « Insert ».  
  
-   L’adaptateur exécute l’opération de sélection. Étant donné que l’opération Select XML inclut également une instruction Update, l’instruction de mise à jour est également exécutée. La réponse suivante à partir de SQL Server est de l’instruction Select.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult>  
        <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10006</Employee_ID>   
          <Name>John</Name>   
          <Status>0</Status>  
        </Employee>  
      </SelectResult>  
    </SelectResponse>  
    ```  
  
     Cette réponse indique qu’un enregistrement a été inséré dans la table Employee et l’état de cet enregistrement est 0.  
  
-   Dans le cadre de l’instruction Select, l’instruction de mise à jour est également exécutée et la colonne d’état pour le nouvel enregistrement est remplacée par 1. Cette option force à nouveau une autre notification à partir de SQL Server et l’adaptateur reçoit un message de notification correspondant, qui ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Ce message avertit que l’utilisation d’un enregistrement a été mis à jour dans la table Employee. Notez que la valeur de la `<Info>` élément est « Update ».  
  
-   Après la deuxième notification, l’adaptateur exécute l’instruction Select. Toutefois, comme il n’existe aucun enregistrement qui ont l’état en tant que 0, l’adaptateur reçoit une réponse vide qui ressemble à la suivante.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult />   
    </SelectResponse>  
    ```  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SQL de réutiliser](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)