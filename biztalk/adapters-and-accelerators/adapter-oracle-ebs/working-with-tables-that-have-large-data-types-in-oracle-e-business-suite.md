---
title: "Utilisation des tables qui possèdent des types de données volumineuses dans Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501aa302-0f82-4221-b99f-423bc8621a6a
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cc357809ecc446c0c282f6a4f8fa46ad7392a53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-tables-that-have-large-data-types-in-oracle-e-business-suite"></a>Utilisation des tables qui possèdent des types de données volumineuses dans Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur effectuer des opérations sur les tables de l’interface et de vues avec les types de données de grande taille telles que les objets BLOB, CLOB, NCLOB et BFILE.  
  
-   Pour les colonnes de type BLOB, CLOB et NCLOB l’adaptateur permet les clients à lire ainsi que de mettre à jour des données. L’adaptateur expose Read_\<LOBColName > et en attente_\<LOBColName > operations pour lire et mettre à jour les données respectivement, où \<LOBColName > est le nom de colonne avec le type de données de grande taille. S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose la plupart lire et mettre à jour des opérations pour cette table d’interface.  
  
-   Pour les colonnes de type BFILE, les clients de l’adaptateur peuvent uniquement lire les données. L’adaptateur expose Read_\<LOBColName > opération lire les données des colonnes de type BFILE. S’il existe plusieurs colonnes avec le type de données de grande taille dans une table d’une interface unique, l’adaptateur expose plusieurs opérations de lecture pour la table d’interface.  
  
 Pour plus d’informations sur ces opérations, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB des données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md). Pour plus d’informations sur les schémas de message pour effectuer ces opérations, consultez [des schémas de Message pour des opérations spéciales LOB](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md).  
  
## <a name="how-to-perform-operations-on-columns-with-large-data-types"></a>Comment effectuer des opérations sur des colonnes avec les Types de données volumineuses  
 Une opération sur Oracle E-Business Suite à l’aide de [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour effectuer des opérations sur les tables d’interface et les vues de l’interface dans Oracle E-Business Suite qui contiennent des types de données volumineuses, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour l’opération (Read_\<LOBColName > ou en attente_\<LOBColName >) à appeler sur une table ou vue.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir d’Oracle E-Business Suite.  
  
3.  Créez une orchestration pour appeler l’opération sur la table d’interface ou la vue.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="how-this-topic-demonstrates-reading-and-writing-data-into-columns-of-large-data-types"></a>Comment cette rubrique montre comment lire et écrire des données dans des colonnes de Types de données volumineuses  
 Pour illustrer la lecture et l’écriture des données dans des colonnes de types de données de grande taille, cette rubrique fournit des instructions pour créer une orchestration qui effectue les opérations suivantes :  
  
-   Mettre à jour la colonne PHOTO (de type de données objet BLOB) de la table CUSTOMER.  
  
-   Lire la valeur de la colonne PHOTO de l’enregistrement mis à jour.  
  
 Cette orchestration est conçue de manière à ce que vous fournissez uniquement le message de demande pour l’opération de mise à jour au moment de l’exécution. Le message pour l’opération de lecture à construire dans l’opération.  
  
> [!NOTE]
>  Lit de l’orchestration dans cette rubrique et les mises à jour des données à partir de la table CUSTOMER, qui est une table de base de données est créé en exécutant les scripts fournis avec les exemples. Vous devez effectuer les procédures similaires comme décrit dans cette rubrique pour effectuer la lecture ou de mettre à jour des opérations sur n’importe quelle vue de table ou une interface interface.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment effectuer la lecture de base et de mettre à jour des opérations sur une colonne PHOTO (de type de données objet BLOB) dans une table CUSTOMER. Cette table est créée en exécutant les scripts fournis avec les exemples.  
  
 Pour illustrer comment lire et écrire des données dans une colonne de type de données de grande taille, le schéma est généré pour le **Update_PHOTO** et **Read_PHOTO** opérations pour la table CUSTOMER. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour plus d’informations sur la façon de générer des schémas.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
 Dans cette orchestration, vous devez créer quatre messages — une réception-réponse est définie pour le **Update_PHOTO** opération et l’autre réception-réponse définies pour le **Read_PHOTO** opération.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`UpdateMessage`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *LOBOperations.OracleEBSBinding.Update_PHOTO*, où LOBOperations est le nom de votre projet BizTalk. OracleEBSBindingSchema est le schéma généré pour appeler le **Update_PHOTO** opération sur la table CUSTOMER.|  
  
6.  Répétez l’étape 3 pour créer trois nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |UpdateResponse|*LOBOperations.OracleEBSBinding.Update_PHOTOResponse*|  
    |LueMessage|*LOBOperations.OracleEBSBinding1.Read_PHOTO*|  
    |ReadResponse|*LOBOperations.OracleEBSBinding1.Read_PHOTOResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Dans cette orchestration, l’adaptateur reçoit un message de demande d’effectuer une opération Update_PHOTO sur une table. Le message de notification est reçu au niveau d’un emplacement de fichier. L’adaptateur traite ce message et le transmet à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Une fois que la réponse est reçue, l’orchestration génère un message d’appeler l’opération Read_PHOTO, qui lit la valeur de la colonne PHOTO mis à jour par l’opération Update_PHOTO. La réponse de ce message est reçue également au même emplacement de fichier.  
  
 Par conséquent, l’orchestration doit contenir les éléments suivants :  
  
-   Un fichier de port de réception pour déplacer un message de demande pour **Update_PHOTO** opération.  
  
-   WCF-Custom bidirectionnelle de WCF-OracleEBS port d’envoi pour envoyer des messages à exécuter la **Update_PHOTO** opération.  
  
-   WCF-Custom bidirectionnelle de WCF-OracleEBS port d’envoi pour envoyer des messages à exécuter la **Read_PHOTO** opération. Vous pouvez également effectuer les deux **Read_PHOTO** et **Update_PHOTO** à l’aide de la même WCF-Custom ou WCF-OracleEBS port d’envoi. Dans cette rubrique, vous utiliserez un port d’envoi unique pour les opérations.  
  
-   A **construire un Message** forme pour construire des messages au sein de l’orchestration.  
  
-   Un fichier de port d’envoi pour enregistrer les messages de réponse pour **Update_PHOTO** et **Read_PHOTO** operations.  
  
-   Formes réception et envoi.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration permettant d’opérer sur une colonne de type de données de grande taille](../../adapters-and-accelerators/adapter-oracle-ebs/media/1976ab27-94c3-4039-a1ca-8790e8897ad5.gif "1976ab27-94c3-4039-a1ca-8790e8897ad5")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveUpdateMessage|Recevoir|-Définissez **nom** à *ReceiveUpdateMessage*<br />-Définissez **activer** à *True*|  
|SendUpdateMessage|Send|-Définissez **nom** à *SendUpdateMessage*|  
|ReceiveUpdateResponse|Recevoir|-Définissez **nom** à *ReceiveUpdateResponse*|  
|SendUpdateResponse|Recevoir|-Définissez **nom** à *SendUpdateResponse*|  
|SendReadMessage|Send|-Définissez **nom** à *SendReadMessage*|  
|ReceiveReadResponse|Recevoir|-Définissez **nom** à *ReceiveReadResponse*|  
|SaveReadResponse|Send|-Définissez **nom** à *SaveReadResponse*|  
  
### <a name="adding-construct-message-shape"></a>Ajout de forme construire un Message  
 Vous pouvez utiliser la **construire un Message** forme pour générer un message de demande dans l’orchestration d’exécuter le **Read_PHOTO** opération. Pour ce faire, vous devez ajouter un **construire un Message** forme dans laquelle un **assignation du Message** forme à votre orchestration. Pour cet exemple, le **assignation du Message** forme appelle le code qui génère un message qui est envoyé pour Oracle E-Business Suite pour exécuter la **Read_PHOTO** opération. Le **assignation du Message** forme définit également l’action pour le message à envoyer à Oracle E-Business Suite.  
  
 Pour la forme construire un message, définissez la **Message construit** propriété **lueMessage**.  
  
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
  
 Pour l’extrait de code ci-dessus être en mesure de générer un message de demande, vous devez disposer d’un message de demande XML (pour le **Read_PHOTO** opération) dans l’emplacement spécifié pour le `XmlFileLocation` variable.  
  
> [!NOTE]
>  Une fois que vous générez le projet, MessageCreator.dll sera créé dans le répertoire du projet. Vous devez ajouter cette DLL dans le global assembly cache (GAC). En outre, vous devez ajouter le MessageCreator.dll en tant que référence dans le projet BizTalk.  
  
 Ajoutez l’expression suivante pour appeler ce code à partir de la **assignation du Message** forme et à définir l’action de message. Pour ajouter une expression, double-cliquez sur le **assignation du Message** forme pour ouvrir l’éditeur d’Expression.  
  
```  
ReadMessage = MessageCreator.MessageCreator.XMLMessageCreator();  
ReadMessage(WCF.Action) = "Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO ";  
```  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*<br />-Créer une opération *Read_LOB*. Cette opération est utilisée pour les messages pour lire les valeurs des colonnes de type de données de grande taille.<br />-Créer une opération *Update_LOB*. Cette opération est utilisée pour les messages à mettre à jour les valeurs dans les colonnes de type de données de grande taille.|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*<br />-Créer une opération *Read_LOB*. Cette opération est utilisée pour les messages pour lire les valeurs des colonnes de type de données de grande taille.<br />-Créer une opération *Update_LOB*. Cette opération est utilisée pour les messages à mettre à jour les valeurs dans les colonnes de type de données de grande taille.|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveUpdateMessage|-Définissez **Message** à *UpdateMessage*<br />-Définissez **opération** à *MessageIn.Update_LOB. Demande*|  
|SendUpdateMessage|-Définissez **Message** à *UpdateMessage*<br />-Définissez **opération** à *LOBPort.Update_LOB. Demande*|  
|ReceiveUpdateResponse|-Définissez **Message** à *UpdateResponse*<br />-Définissez **opération** à *LOBPort.Update_LOB. Réponse*|  
|SendUpdateResponse|-Définissez **Message** à *UpdateResponse*<br />-Définissez **opération** à *ResponseOut.Update_LOB. Demande*|  
|SendReadMessage|-Définissez **Message** à *lueMessage*<br />-Définissez **opération** à *LOBPort.Read_LOB. Demande*|  
|ReceiveReadResponse|-Définissez **Message** à *ReadResponse*<br />-Définissez **opération** à *LOBPort.Read_LOB. Réponse*|  
|SendReadResponse|-Définissez **Message** à *ReadResponse*<br />-Définissez **opération** à *ResponseOut.Read_LOB. Demande*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir de la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleEBS physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Vous devez tenir compte des points suivants lors de la configuration WCF-Custom ou WCF-OracleEBS port d’envoi.  
  
        -   Une `Update_<LOBColName>` opération doit être effectuée dans le cadre de la transaction. Pour garantir cela, le **UseAmbientTransaction** liaison de la propriété doit être définie sur **True**.  
  
        -   Étant donné que le WCF-Custom ou WCF-OracleEBS ports d’envoi envoie et reçoit des messages conformes à plusieurs schémas et effectue deux opérations, vous devez définir une action dynamique pour les opérations de. Pour plus d’informations sur les actions, consultez [configurer l’Action SOAP pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md). Pour cette orchestration, l’action doit être définie comme suit :  
  
            ```  
            \<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
              <Operation Name="Update_LOB" Action="Tables/UpdateBlob/SCOTT/CUSTOMER/PHOTO" />  
              <Operation Name="Read_LOB" Action="Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO" />  
            </BtsActionMapping>  
            ```  
  
            > [!IMPORTANT]
            >  Notez que le nom de l’opération dans une action dynamique doit être identique au nom d’opération que vous avez spécifié sur les ports logiques lors de la création de l’orchestration BizTalk.  
  
        > [!NOTE]
        >  Pour effectuer des opérations sur les tables d’interface ou des vues de l’interface, vous devez également définir le contexte d’application. Pour plus d’informations sur la façon dont l’adaptateur prend en charge la définition du contexte de l’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md). Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Avant de démarrer l’orchestration BizTalk, assurez-vous que la demande XML pour appeler le **Read_PHOTO** opération est disponible à l’adresse C:\TestLocation\MessageIn. La requête XML doit ressembler à ceci :  
  
```  
<Read_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE NAME='Mindy Martin'</FILTER>  
</Read_PHOTO>  
```  
  
> [!NOTE]
>  Le message de demande possède un filtre sur le nom spécifique, car dans le message de demande pour **Update_PHOTO** opération, la valeur de la colonne PHOTO est mis à jour pour le même nom. Par conséquent, l’opération de lecture lit la même valeur que vous insérez à l’aide de l’opération de mise à jour.  
  
 Vous devez maintenant démarrer l’application BizTalk pour lire et écrire des valeurs de types de données de grande taille à partir d’une base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour envoyer des messages à Oracle de base de données est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir démarré l’application, vous devez supprimer un message de demande dans le fichier emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour le **Update_PHOTO** opération que vous avez généré précédemment. Par exemple, un message de demande qui met à jour la colonne PHOTO de la table CUSTOMER ressemble à ceci :  
  
```  
<Update_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE Name='Mindy Martin'</FILTER>  
  <DATA>U2FtcGxlIERhdGE=</DATA>  
</Update_PHOTO>  
```  
  
> [!NOTE]
>  Lors de la mise à jour des colonnes BLOB, l’élément de données doit toujours contenir une valeur codée en base64. Pour CLOB et NCLOB, l’élément de données peut avoir des valeurs de chaîne.  
  
 Le précédent message de requête met à jour la valeur dans la colonne PHOTO de l’enregistrement correspondant à la clause WHERE. Consultez les schémas de Message pour les opérations sur les Types de données volumineux pour plus d’informations sur le schéma de message de demande pour effectuer des opérations sur les types de données de grande taille à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 L’orchestration consomme le message et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données Oracle pour le précédent message de demande ressemble à ceci :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<Update_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER" />  
```  
  
 L’orchestration maintenant construit un message de demande pour le **Read_PHOTO** opération à l’aide du message de demande disponible à C:\TestLocation\MessageIn. Le message de demande est envoyé à la base de données Oracle et la réponse est enregistrée dans le même emplacement. La réponse pour l’opération de lecture sur la colonne PHOTO ressemble à ceci :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<Read_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <Read_PHOTOResult>U2FtcGxlIERhdGE=</Read_PHOTOResult>  
</Read_PHOTOResponse>  
```  
  
> [!NOTE]
>  Notez que la réponse contient la même valeur pour la colonne PHOTO que vous avez transmise dans le **Update_PHOTO** opération.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)