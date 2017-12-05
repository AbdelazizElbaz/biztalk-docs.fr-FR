---
title: "Exécuter des opérations sur les tables et vues avec les types de données de grande taille à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cec15b01-7a57-4917-8c21-44a1cfaadc59
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 692cd1466353e366a1c8e806dba9f1070eadd065
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter"></a>Exécuter des opérations sur les tables et vues avec les types de données de grande taille à l’aide de l’adaptateur SQL
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet à des clients de l’adaptateur pour lire et mettre à jour des données dans des colonnes de types de données volumineuses, autrement dit, varchar (max), nvarchar (max) ou varbinary (max). Pour lire des données à partir de ces colonnes, les clients de la carte peuvent utiliser l’opération de sélection. Pour insérer ou mettre à jour des données dans ces colonnes, l’adaptateur expose une opération Set < nom_colonne >, où < nom_colonne > est le nom de la colonne de type varchar (max), nvarchar (max) ou varbinary (max).  
  
 En outre, dans SQL Server 2008, vous pouvez avoir la colonne varbinay(max) stocker des données non structurées, telles que des documents de texte et des images. Ces données non structurées sont appelées données FILESTREAM. Les données FILESTREAM peuvent être stockées en tant que fichiers sur le système de fichiers. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet au client d’entrer des données FILESTREAM dans des colonnes de type varbinary (max). Pour plus d’informations sur le stockage FILESTREAM, consultez [vue d’ensemble de FILESTREAM](https://msdn.microsoft.com/library/bb933993(SQL.100).aspx).  
  
 Cette rubrique fournit des informations sur certaines tâches, vous devez effectuer sur l’ordinateur exécutant SQL Server et l’ordinateur exécutant le client de l’adaptateur pour être en mesure d’insérer ou de mettre à jour les données FILESTREAM. Cette rubrique fournit également des instructions sur l’exécution d’opérations de jeu < nom_colonne > pour insérer des données FILESTREAM.  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer les tâches suivantes sur l’ordinateur exécutant SQL Server et de l’ordinateur exécutant le client de la carte.  

  
-   **Sur l’ordinateur exécutant SQL Server**  
  
    -   Vous devez l’activer sur l’instance de SQL Server. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=122486](http://go.microsoft.com/fwlink/?LinkId=122486).  
  
    -   Vous devez créer une base de données FILESTREAM. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=122487](http://go.microsoft.com/fwlink/?LinkId=122487).  
  
    -   Vous devez disposer d’une table pour stocker les données FILESTREAM. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=122488](http://go.microsoft.com/fwlink/?LinkId=122488).  
  
    -   Vous devez configurer MSDTC sur l’ordinateur qui héberge la base de données SQL Server. Pour obtenir des instructions sur la façon de configurer MSDTC, consultez [configurer le MSDTC sur un client SQL Server et de la carte](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md).  
  
-   **Sur l’ordinateur exécutant le client de carte**  
  
    -   Vous devez disposer de la connectivité du Client SQL SDK installé. Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server 2008 et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant. L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.  
  
    -   Vous devez configurer MSDTC sur l’ordinateur exécutant le client de la carte. Pour obtenir des instructions sur la façon de configurer MSDTC, consultez [configurer le MSDTC sur un client SQL Server et de la carte](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md).  
  
 Une fois ces tâches terminées, vous sont tous définis pour insérer ou mettre à jour les données FILESTREAM dans les tables de base de données SQL Server 2008.  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a>Comment cette rubrique illustre les opérations sur les Types de données de grande taille  
 Pour montrer comment effectuer des opérations de jeu < nom_colonne > sur les tables avec des types de données volumineuses, prend une table, les enregistrements dont les colonnes Id et le Document. La colonne Id est de type uniqueidentifier et accepte un GUID. La colonne du Document est de type varbinary (max). Supposons que la colonne d’Id possède déjà un GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'. Pour mettre à jour la colonne du Document, l’adaptateur expose l’opération SetDocument.  
  
> [!NOTE]
>  Pour SQL Server 2008, pour illustrer les opérations FILESTREAM, supposons que la colonne Document peut stocker des données FILESTREAM.  
  
## <a name="how-to-perform-operations-on-a-sql-server-database"></a>Comment effectuer des opérations sur une base de données SQL Server  
 Une opération sur une base de données SQL Server à l’aide de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour effectuer des opérations sur les tables avec des types de données volumineuses, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour l’opération de définition < nom_colonne >. Pour cette rubrique, génération du schéma pour le **SetDocument** opération pour le **enregistrements** table.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données SQL Server.  
  
3.  Créez une orchestration pour appeler l’opération SetDocument sur la table d’enregistrements.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple FILESTREAMOperation, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Pour illustrer comment mettre à jour les valeurs des colonnes de types de données volumineuses, génération du schéma pour l’opération SetDocument de la table d’enregistrements. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SetOperation.TableOperation_dbo_Records.SetDocument*, où SetOperation est le nom de votre projet BizTalk. TableOperation_dbo_Records est le schéma généré pour l’opération SetDocument sur la table d’enregistrements.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SetOperation.TableOperation_dbo_Records.SetDocumentResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur SQL Server. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consomme ce message et le transmet à SQL Server. La réponse à partir de SQL Server est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à SQL Server et de recevoir des réponses, respectivement. Un exemple d’orchestration pour l’opération SetDocument ressemble à ceci :  
  
 ![Orchestration permettant d’effectuer les opérations FILESTREAM](../../adapters-and-accelerators/adapter-sql/media/b8c1c04c-142f-44a0-a545-8ec0cfdd9a5b.gif "b8c1c04c-142f-44a0-a545-8ec0cfdd9a5b")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.FileStream.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.FileStream.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.FileStream.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.FileStream.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
        > [!IMPORTANT]
        >  L’opération d’entrer des données FILESTREAM doit être effectuée dans une transaction. Par conséquent, assurez-vous que le **UseAmbientTransaction** liaison de la propriété est définie sur **True** port d’envoi sur le WCF-Custom ou WCF-SQL. Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
        > [!IMPORTANT]
        >  Pour effectuer une opération pour insérer des données FILESTREAM, vous devez toujours utiliser l’authentification Windows pour se connecter à SQL Server sur WCF-Custom ou port d’envoi WCF-SQL. Ainsi, dans le **informations d’identification** onglet dans la boîte de dialogue Propriétés du port, sélectionnez le **n’utilisez pas l’authentification unique sur** option et laissez le nom d’utilisateur et un mot de passe vide.  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer le **SetDocument** opération sur le **enregistrements** table. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour envoyer des messages à la base de données SQL Server est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour l’opération SetDocument que vous avez créé précédemment. Par exemple, le message de demande pour mettre à jour la colonne du Document est la suivante :  
  
```  
<SetDocument xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Records">  
  <Filter>WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'</Filter>  
  <Data>UwBlAHQAdgBfAHYAYQByAGIAaQBuAGEAcgB5AE0AQQBYAA==</Data>  
</SetDocument>  
```  
  
> [!IMPORTANT]
>  Le `Filter` élément doit contenir la clause WHERE reposant sur lequel l’adaptateur met à jour les enregistrements. Le `Data` élément doit contenir une valeur codée en base64 que vous souhaitez insérer dans la colonne du Document.  
  
 Ce message de requête met à jour la colonne Document avec la valeur spécifiée. L’orchestration consomme le message et l’envoie à la base de données SQL Server. La réponse à partir de la base de données SQL Server est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données SQL Server pour le précédent message de demande est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<SetDocumentResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Records" />  
```  
  
 L’adaptateur envoie une réponse vide le **définir < nom_colonne >** opération.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)