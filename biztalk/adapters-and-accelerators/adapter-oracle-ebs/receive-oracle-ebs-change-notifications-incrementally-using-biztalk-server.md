---
title: "Recevoir des notifications de modification d’Oracle E-Business Suite incrémentielle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63dbeacc-ecde-497d-b12d-d5f9944a33f0
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e21bbb02c7952f1735896ede6de6f0cf85ed22f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-oracle-e-business-suite-change-notifications-incrementally-using-biztalk-server"></a>Recevoir des notifications de modification d’Oracle E-Business Suite incrémentielle à l’aide de BizTalk Server
> [!IMPORTANT]
>  Pour plus de concision, cette rubrique décrit uniquement comment recevoir des notifications de façon incrémentielle. Dans les scénarios d’entreprise, l’orchestration doit inclure dans l’idéal, de la logique permettant d’extraire le type de message de notification reçu, puis effectuez toutes les opérations suivantes. En d’autres termes, l’orchestration décrite dans cette rubrique doit être générée sur l’orchestration décrite dans [traiter les Messages de Notification pour effectuer des tâches spécifiques dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md).  
  
 Cette rubrique montre comment configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de notification de requête incrémentielle à partir d’Oracle. Pour illustrer les notifications incrémentielles, prenons une table, ACCOUNTACTIVITY, avec une colonne « Traitement ». Lorsqu’un nouvel enregistrement est inséré à cette table, la valeur de la colonne « Traitement » est définie ' n '. Vous pouvez configurer l’adaptateur pour recevoir des notifications incrémentielles en procédant comme suit :  
  
-   S’inscrire aux notifications à l’aide d’une instruction SELECT qui Récupère tous les enregistrements dont la colonne « Traitement » en tant que ' n '. Vous pouvez le faire en spécifiant l’instruction SELECT pour le **NotificationStatement** propriété de liaison.  
  
-   Pour les lignes qui ont été notifiés pour, mettre à jour la colonne « Traité » à 'y'.  
  
 Cette rubrique montre comment créer une orchestration BizTalk et de configurer une application BizTalk pour y parvenir.  
  
## <a name="configuring-notifications-with-the-oracle-e-business-adapter-binding-properties"></a>Configuration des Notifications avec l’adaptateur Oracle E-Business propriétés de liaison  
 Le tableau ci-dessous récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés de liaison qui vous permet de configurer la réception des notifications à partir d’Oracle E-Business Suite. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
> [!NOTE]
>  Vous pouvez choisir de spécifier ces propriétés de liaison lors de la génération du schéma pour le **Notification** opération, même si elle n’est pas obligatoire. Si vous procédez ainsi, la liaison du port de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère comme partie de la génération de métadonnées contient également les valeurs spécifiées pour les propriétés de liaison. Vous pouvez importer ultérieurement ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] port de réception de la console Administration pour créer le WCF-custom ou WCF-OracleEBS avec la liaison de propriétés déjà définies. Pour plus d’informations sur la création d’un port de réception à l’aide du fichier de liaison, consultez [configurer d’une liaison de Port physique à l’aide d’un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie l’opération entrante que vous souhaitez effectuer. Pour recevoir des messages de notification, affectez la valeur **Notification**.|  
|**NotificationPort**|Spécifie le numéro de port ODP.NET doit ouvrir pour l’écoute de notification de modification de base de données à partir de la base de données Oracle.|  
|**NotificationStatement**|Spécifie l’instruction SELECT utilisée pour s’inscrire aux notifications de requête. L’adaptateur reçoit un message de notification uniquement lorsque le jeu de résultats pour que les modifications de l’instruction SELECT spécifiée.|  
|**NotifyOnListenerStart**|Spécifie si l’adaptateur envoie une notification pour les clients de la carte au démarrage de l’écouteur.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des notifications d’Oracle E-Business Suite, poursuivre la lecture.  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a>Comment cette rubrique illustre la réception de Messages de Notification  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de messages de notification de modification incrémentielle de la base de données à partir d’Oracle E-Business Suite, nous allons configurer l’adaptateur pour recevoir des notifications de modifications à la table ACCOUNTACTIVTY. Supposons que la table ACCOUNTACTIVITY comporte les colonnes « TID », « Compte » et « Traitement ». Chaque fois qu’un nouvel enregistrement est ajouté, la valeur de la colonne « Traitement » est définie sur n ». Par conséquent, pour obtenir des notifications incrémentielles, vous devrez effectuer les tâches suivantes dans le cadre de l’orchestration BizTalk :  
  
-   Obtenir une notification pour tous les enregistrements où « Traitement » est n '. Pour cela, en spécifiant une instruction SELECT comme une instruction de notification.  
  
-   Une fois la notification est reçue pour un enregistrement de certain, la valeur « Traitement » « y ». Pour cela, en exécutant une procédure stockée, PROCESS_RECORDS, qui met à jour la colonne « Traitement ».  
  
 Pour illustrer la réception des notifications incrémentielles, nous les opérations suivantes :  
  
-   Génération du schéma pour le **Notification** (opération entrante), et **PROCESS_RECORDS** (opération sortante) sur la table ACCOUNTACTIVITY.  
  
-   Créer une orchestration qui a les éléments suivants :  
  
    -   Un emplacement de réception pour recevoir les messages de notification. Vous pouvez configurer pour la notification en spécifiant l’instruction SELECT en tant que :  
  
        ```  
        SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
        ```  
  
        > [!NOTE]
        >  Vous devez spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `SCOTT.ACCOUNTACTIVITY`.  
  
    -   Un port d’envoi pour mettre à jour les lignes pour lesquelles des notifications a déjà été envoyée. Vous allez exécuter la procédure stockée de PROCESS_RECORDS sur ce port pour définir la valeur de colonne « Traité » à « o » pour les enregistrements pour lesquels la notification est reçue.  
  
         Notez que cette opération doit être exécutée après que réception de la notification des messages afin que les lignes traitées sont mis à jour. Pour effectuer immédiatement avec la surcharge de la réponse de notification en attente et puis la supprimer manuellement un message de demande pour exécuter la procédure PROCESS_RECORDS, vous allez générer le message de demande pour la procédure PROCESS_RECORDS au sein de l’orchestration lui-même. Vous pouvez le faire à l’aide de la **construire un Message** forme dans une orchestration.  
  
## <a name="how-to-receive-notification-messages-from-oracle-e-business-suite"></a>La réception des Messages de Notification à partir d’Oracle E-Business Suite  
 Une opération sur l’utilisation d’Oracle E-Business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des Applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour configurer l’adaptateur pour recevoir des messages de notification, ces tâches sont :  
  
1.  Créez un projet BizTalk, puis générer le schéma pour le **Notification** (opération entrante) et **PROCESS_RECORDS** procédure (opération sortante) sur la table ACCOUNTACTIVITY. Si vous le souhaitez, vous pouvez spécifier des valeurs pour le **InboundOperationType**, **NotificationPort**, et **NotificationStatement** propriétés de liaison.  
  
2.  Créez un message dans le projet BizTalk pour la réception de notifications provenant d’Oracle E-Business Suite.  
  
3.  Créer des messages dans le projet BizTalk pour l’exécution de la procédure stockée de PROCESS_RECORDS et de recevoir des messages de réponse.  
  
4.  Créer une orchestration qui effectue les opérations suivantes :  
  
    -   Reçoit le message de notification à partir d’Oracle E-Business Suite.  
  
    -   Crée un message pour exécuter la procédure PROCESS_RECORDS.  
  
    -   Envoie ce message pour Oracle E-Business Suite pour sélectionner et mettre à jour les enregistrements et recevoir une réponse.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!NOTE]
    >  Pour les opérations entrantes, tels que la réception des messages de notification, vous devez configurer uniquement un WCF-Custom unidirectionnel ou port de réception WCF-OracleEBS. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
7.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **Notification** opération et **PROCESS_RECORDS** procédure. Consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour plus d’informations sur la façon de générer le schéma. Effectuer les tâches suivantes lors de la génération du schéma. Ignorer la première étape si vous ne souhaitez pas spécifier les propriétés de liaison au moment du design.  
  
1.  Spécifiez une valeur pour **InboundOperationType**, **NotificationPort**, et **NotificationStatement** propriétés de liaison lors de la génération du schéma. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir des instructions sur la façon de spécifier les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).  
  
2.  Sélectionnez le type de contrat **Service (opérations entrantes)**.  
  
3.  Génération du schéma pour le **Notification** opération.  
  
4.  Sélectionnez le type de contrat **Client (Outbound operations)**.  
  
5.  Génération du schéma pour le **PROCESS_RECORDS** procédure. Cette procédure est disponible sous la **ACCOUNT_PKG** package.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer trois messages : un pour recevoir des notifications à partir d’Oracle E-Business Suite, un pour exécuter la procédure PROCESS_RECORDS et un pour recevoir la réponse pour la procédure.  
  
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
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *OracleNotifyIncremental.OracleEBSBinding.Notification*, où *OracleNotifyIncremental* est le nom de votre projet BizTalk. *OracleEBSBinding* est le schéma généré pour le **Notification** opération.|  
  
6.  Répétez l’étape 3 pour créer deux nouveaux messages. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Procédure|*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDS*, où *OracleEBSBinding1* est le schéma généré pour le **PROCESS_RECORDS** procédure.|  
    |ProcedureResponse|*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDSResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des messages de notification à partir d’Oracle E-Business Suite et mise à jour des lignes pour lesquelles la notification a été reçue. Dans cette orchestration, l’adaptateur reçoit le message de notification en fonction de l’instruction SELECT spécifiée pour le **NotificationStatement** propriété de liaison. Le message de notification est reçu au niveau d’un emplacement de fichier. Une fois que la réponse est reçue, l’orchestration génère un message pour appeler la procédure PROCESS_RECORDS, qui met à jour les lignes pour lesquelles la notification est reçue. La réponse de ce message est reçue également au même emplacement de fichier.  
  
 Par conséquent, l’orchestration doit contenir les éléments suivants :  
  
-   Un unidirectionnel WCF-Custom ou WCF-OracleEBS port de réception pour recevoir des messages de notification.  
  
-   Un bidirectionnel WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages pour exécuter la procédure PROCESS_RECORDS.  
  
-   A **construire un Message** forme pour construire des messages, pour exécuter la procédure PROCESS_RECORDS, dans l’orchestration.  
  
-   Un fichier de port d’envoi pour enregistrer le message de notification et la réponse pour la procédure PROCESS_RECORDS.  
  
-   Formes réception et envoi.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration pour recevoir des notifications à partir d’Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveNotification|Recevoir|-Définissez **nom** à *ReceiveNotification*<br /><br /> -Définissez **activer** à *True*|  
|SaveNotification|Send|-Définissez **nom** à *SaveNotification*|  
|SendProcMessage|Send|-Définissez **nom** à *SendProcMessage*|  
|ReceiveProcResponse|Recevoir|-Définissez **nom** à *ReceiveProcResponse*|  
|SaveProcResponse|Send|-Définissez **nom** à *SaveProcResponse*|  
  
### <a name="adding-construct-message-shape"></a>Ajout de forme construire un Message  
 Vous pouvez utiliser la **construire un Message** forme pour générer un message de demande dans l’orchestration d’exécuter la procédure PROCESS_RECORDS. Pour ce faire, vous devez ajouter un **construire un Message** forme dans laquelle un **assignation du Message** forme à votre orchestration. Pour cet exemple, le **assignation du Message** forme appelle le code qui génère un message qui est envoyé pour Oracle E-Business Suite pour exécuter la procédure. Le **assignation du Message** forme définit également l’action pour le message à envoyer à Oracle E-Business Suite.  
  
 Pour la forme construire un message, définissez la **Message construit** propriété **procédure**.  
  
 Le code pour générer la réponse peut faire partie de la même solution Visual Studio en tant que votre projet BizTalk. Un exemple de code pour générer un message de réponse ressemble à ceci.  
  
```  
namespace MessageCreator  
{  
    public class MessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\TestLocation\\MessageIn";  
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
  
 Pour l’extrait de code ci-dessus être en mesure de générer un message de demande, vous devez disposer d’un message de demande XML (pour la procédure PROCESS_RECORDS) dans l’emplacement spécifié pour le `XmlFileLocation` variable.  
  
> [!NOTE]
>  Une fois que vous générez le projet, MessageCreator.dll sera créé dans le répertoire du projet. Vous devez ajouter cette DLL dans le global assembly cache (GAC). En outre, vous devez ajouter le MessageCreator.dll en tant que référence dans le projet BizTalk.  
  
 Ajoutez l’expression suivante pour appeler ce code à partir de la **assignation du Message** forme et à définir l’action de message. Pour ajouter une expression, double-cliquez sur le **assignation du Message** forme pour ouvrir l’éditeur d’Expression.  
  
```  
Procedure = MessageCreator.MessageCreator.XMLMessageCreator();  
Procedure(WCF.Action) = "PackageApis/SCOTT/ACCOUNT_PKG/PROCESS_RECORDS";  
```  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|OracleNotifyPort|-Définissez **identificateur** à *OracleNotifyPort*<br /><br /> -Définissez **Type** à *OracleNotifyPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*<br /><br /> -Créer une opération *notifier*. Cette opération est utilisée pour les messages de notification.<br /><br /> -Créer une opération *procédure*. Cette opération est utilisée pour les messages de réponse select.|  
|OracleOutboundPort|-Définissez **identificateur** à *OracleOutboundPort*<br /><br /> -Définissez **Type** à *OracleOutboundPortType*<br /><br /> -Définissez **modèle de Communication** à *demande-réponse*<br /><br /> -Définissez **Direction de Communication** à *envoi / réception*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *OracleNotifyPort.Notify.Request*|  
|SaveNotification|-Définissez **Message** à *NotifyReceive*<br /><br /> -Définissez **opération** à *SaveMessagePort.Notify.Request*|  
|SendProcMessage|-Définissez **Message** à *procédure*<br /><br /> -Définissez **opération** à *OracleOutboundPort.Procedure.Request*|  
|ReceiveProcResponse|-Définissez **Message** à *ProcedureResponse*<br /><br /> -Définissez **opération** à *OracleOutboundPort.Procedure.Response*|  
|SaveProcResponse|-Définissez **Message** à *ProedureResponse*<br /><br /> -Définissez **opération** à *SaveMessagePort.Procedure.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez « Création et exécution des Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=102359](http://go.microsoft.com/fwlink/?LinkId=102359).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un WCF-Custom physique ou port de réception WCF-OracleEBS à sens unique. Ce port d’écoute pour les notifications provenant d’Oracle E-Business Suite. Pour plus d’informations sur la création des ports de réception, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        > [!IMPORTANT]
        >  Vous n’avez pas besoin d’effectuer cette étape si vous avez spécifié les propriétés de liaison au moment du design. Dans ce cas, vous pouvez créer un port de réception avec le jeu de propriétés de liaison requis, en important le fichier de liaison créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Affectez la valeur **Notification**.|  
        |**NotificationPort**|Spécifie le numéro de port ODP.NET doit ouvrir pour l’écoute de notification de modification de base de données à partir de la base de données Oracle. Définissez cette propriété sur le même numéro de port que vous devez avoir ajouté à la liste d’exceptions de pare-feu Windows. Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).<br /><br /> **Important :** si vous affectez la valeur par défaut -1, vous devez désactiver le pare-feu Windows pour recevoir des messages de notification.|  
        |**NotificationStatement**|Affectez la valeur :<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> **Remarque :** vous devez spécifier le nom de table, ainsi que le nom du schéma. Par exemple, `SCOTT.ACCOUNTACTIVITY`.|  
        |**NotifyOnListenerStart**|Affectez la valeur **True**.|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
        > [!IMPORTANT]
        >  Si vous configurez des notifications pour une table d’interface, vous devez définir le contexte d’application en spécifiant les propriétés de liaison requis. Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Vous pouvez le faire en ajoutant le comportement de service lors de la configuration WCF-Custom ou WCF-OracleEBS port de réception. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer au niveau d’Isolation de Transaction et le délai d’attente de Transaction avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleEBS physique pour envoyer des messages pour Oracle E-Business Suite pour exécuter la procédure PROCESS_REOCRDS. Vous devez également spécifier l’action dans le port d’envoi.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera les messages à partir d’Oracle E-Business Suite. Ces paramètres seront les messages de notification reçues à partir d’Oracle E-Business Suite et le port d’envoi de messages pour la procédure PROCESS_RECORDS que vous exécutez via le WCF-Custom ou WCF-OracleEBS.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour la réception des messages de notification à partir d’Oracle E-Business Suite et de l’exécution de la procédure PROCESS_RECORDS. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez « Démarrage d’une Orchestration » à [http://go.microsoft.com/fwlink/?LinkId=102387](http://go.microsoft.com/fwlink/?LinkId=102387).  
  
 À ce stade, vérifiez que :  
  
-   Port de réception le WCF-Custom ou WCF-OracleEBS à sens unique qui reçoit les messages de notification à partir d’Oracle E-Business Suite est en cours d’exécution.  
  
-   Le WCF-Custom ou un port d’envoi WCF-OracleEBS à exécuter la procédure PROCESS_RECORDS est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir d’Oracle E-Business Suite, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Supposons que la table ACCOUNTACTIVITY possède déjà des enregistrements. En outre, assurez-vous que le message XML pour exécuter la procédure PROCESS_RECORDS est disponible à l’adresse C:\TestLocation\MessageIn. Le fichier XML doit ressembler au suivant :  
  
```  
<PROCESS_RECORDS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG" />  
```  
  
 Une fois l’orchestration BizTalk est démarré, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur reçoit un message de notification qui ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>OracleEBSBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     Ce message avertit que le port de réception pour recevoir les messages de notification est démarré. Notez que la valeur de la `<Info>` élément est « ListnerStarted ».  
  
-   L’adaptateur exécute la procédure PROCESS_RECORDS. La réponse suivante à partir d’Oracle E-Business Suite est pour la procédure.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
        <NewDataSet xmlns="">  
          <NewTable>  
            <TID>1</TID>   
            <ACCOUNT>100001</ACCOUNT>   
            <PROCESSED>n</PROCESSED>   
          </NewTable>  
          <NewTable>  
            ......  
            ......  
          </NewTable>  
          ......  
          ......  
        </NewDataSet>  
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
     Il s’agit de la réponse pour l’instruction SELECT s’exécute dans le cadre de la procédure PROCESS_RECORDS.  
  
-   La procédure PROCESS_RECORDS met également à jour les lignes pour définir traités à 'y'. Par conséquent, l’adaptateur reçoit une autre notification pour l’opération de mise à jour.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>32</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Update</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Notez que le `Info` élément contient « Update ».  
  
-   Après la deuxième notification, l’adaptateur exécute à nouveau la procédure PROCESS_RECORDS. Toutefois, maintenant, car il n’existe aucun enregistrement où traités colonne est définie sur n », la procédure retourne une réponse vide qui ressemble à ce qui suit.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="" />   
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de la modification de base de données Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)