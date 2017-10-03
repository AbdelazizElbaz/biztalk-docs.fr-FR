---
title: "Étape 3c : insérer des détails d’opportunité dans une base de données SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f6f9bbe-6f25-4393-8f92-aeeba9736acf
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33d0055c05e0c9af9f4dddc4a7275c01ff49d779
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-insert-opportunity-details-into-a-sql-server-database"></a>Étape 3c : insérer des détails d’opportunité dans une base de données SQL Server
À présent, nous avons créé l'orchestration pour envoyer une requête à Salesforce et recevoir une réponse. Dans cette section, nous allons mettre à jour cette orchestration pour insérer la réponse de Salesforce dans une **OrderDetails** table dans une base de données SQL Server sur site, **commandes**. Pour y parvenir, nous allons effectuer les différentes étapes suivantes :  
  
-   Créer un **OrderDetails** de table dans une **commandes** base de données dans une base de données SQL Server sur site.  
  
-   Utilisez le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] disponible avec [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour générer le schéma pour l’opération d’insertion sur la **OrderDetails** table.  
  
-   Créer un mappage pour transformer le message de réponse de Salesforce pour le message à insérer dans **OrderDetails** table dans SQL Server.  
  
-   Mettre à jour de l’orchestration pour utiliser la transformation pour insérer le message de réponse dans le **OrderDetails** table.  
  
## <a name="create-sql-server-database-and-table"></a>Créer une table et une base de données SQL Server  
  
#### <a name="to-create-the-database-and-table"></a>Pour créer la base de données et la table  
  
1.  Ouvrez SQL Server Management Studio et connectez-vous en tant qu'administrateur.  
  
2.  Cliquez sur le **bases de données** nœud et cliquez sur **nouvelle base de données**. Spécifiez le nom de base de données `Orders` et spécifier d’autres détails pour créer une nouvelle base de données.  
  
3.  Ouvrez un éditeur de requête et exécutez la requête suivante pour créer un **OrderDetails** de table dans le **commandes** base de données :  
  
    ```  
    USE [Orders]  
    GO  
    /****** Object:  Table [dbo].[OrderDetails]    Script Date: 07-12-2012 22:15:47 ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
    SET ANSI_PADDING ON  
    GO  
    CREATE TABLE [dbo].[OrderDetails]([ID] [int] IDENTITY(1,1) NOT NULL,  
    [TITLE] [varchar](200) NULL,  
    [ProductName] [varchar](200) NULL,  
    [Quantity] [float] NULL,  
    [Amount] [float] NULL,  
    PRIMARY KEY CLUSTERED   
    (  
    [ID] ASC  
    )WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
    GO  
    SET ANSI_PADDING OFF  
    GO  
    ```  
  
## <a name="create-schema-for-insert-operation-on-orderdetails-table"></a>Créer un schéma pour réaliser l'opération Insert sur la table OrderDetails  
 Installation [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] fournit un [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] qui peut être utilisé dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet pour générer le schéma pour l’opération d’insertion sur la **OrderDetails** table. Cette section présente les étapes à suivre pour créer le schéma de message.  
  
#### <a name="to-create-the-schema-for-insert-operation"></a>Pour créer le schéma de l'opération Insert  
  
1.  Cliquez sur le **BtsSalesforceIntegration** de projet, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**. Dans le **ajouter les éléments générés** boîte de dialogue, cliquez sur **Consume Adapter Service**, puis cliquez sur **ajouter**.  
  
2.  Dans le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)], à partir de l’instruction Select une liaison liste déroulante, cliquez sur **sqlBinding**, puis cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue **sécurité** onglet, pour **type d’informations d’identification du Client**, sélectionnez **Windows** utilisation de Windows authentification pour se connecter à la base de données SQL Server.  
  
4.  Dans le **configurer l’adaptateur** boîte de dialogue **propriétés URI** onglet, pour **Initial Catalog** spécifier le nom de la base de données (Orders) pour se connecter à. Pour **Server** spécifier le nom de l’ordinateur où est installé SQL Server, vous êtes connecté. Si la base de données SQL Server est sur le même ordinateur que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet, vous pouvez tout simplement entrer une période (**.**). Cliquez sur **OK**.  
  
5.  Dans le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] cliquez sur **connexion**. Une fois la connexion est établie, sélectionnez le type de contrat **Client (Outbound operations)**. Sous le **sélectionner une catégorie** , développez **Tables**, cliquez sur **OrderDetails** table et dans le volet droit, cliquez sur **insérer** puis cliquez sur **Ajouter**.  
  
6.  Spécifiez un **préfixe de nom de fichier** si vous voulez préfixer les schémas générés avec un identificateur. Pour ce didacticiel, nous allons spécifier comme préfixe **InsertOrders** puis cliquez sur **OK**.  
  
     Un tas de schémas sont ajoutés au projet. Le schéma que nous allons utiliser pour insérer des messages dans la **OrderDetails** table est **InsertOrdersTableOperation.dbo.OrderDetails.xsd**.  
  
## <a name="map-salesforce-response-and-insert-schemas"></a>Mapper une réponse de Salesforce et insérer des schémas  
 Maintenant que nous avons deux schémas (réponse de Salesforce et insertion dans **OrderDetails**), nous devons mapper le schéma de réponse de Salesforce dans le schéma d’insertion pour **OrderDetails** afin que le message de réponse de Salesforce peut être inséré dans la table de base de données SQL Server.  
  
#### <a name="to-map-the-schemas"></a>Pour mapper les schémas  
  
1.  Avec le bouton droit le **BtsSalesforceIntegration** de projet, pointez sur **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **carte**. Spécifiez le nom de mappage `QueryResult_Orders.btm` puis cliquez sur **ajouter**.  
  
2.  Sur la surface de mappage pour le schéma source, sélectionnez **QueryResult** pour le schéma de destination, sélectionnez **InsertOrdersTableOperation.dbo.OrderDetails.xsd** , puis, dans ce cas, le  **Insérer** nœud.  
  
3.  Mappez  les deux schémas comme le montre la capture d'écran ci-dessous :  
  
     ![Mapper une réponse de Salesforce pour schéma d’insertion](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")  
  
     Notez que la carte utilise un **bouclage** fonctoid entre le **enregistrements** et **OrderDetails** lien. Cela garantit que toutes les une ou plusieurs occurrences de nœuds sous **enregistrements** sont mappées aux occurrences de nœuds sous similaires le **OrderDetails**.  
  
4.  Enregistrez les modifications apportées au mappage.  
  
## <a name="update-the-orchestration-to-insert-messages-into-sql-server"></a>Mettre à jour l'orchestration pour insérer des messages dans SQL Server  
 Dans cette section, nous allons utiliser le mappage de l'orchestration pour transformer le message de réponse de Salesforce en message pour insérer des détails de la commande dans une table SQL Server. Nous allons également ajouter un port pour envoyer ce message à SQL Server.  
  
#### <a name="to-update-the-orchestration"></a>Pour mettre à jour l'orchestration  
  
1.  Créez un message variable pour le schéma d'insertion. À partir de la vue orchestration, cliquez sur le **Messages** nœud, puis cliquez sur **nouveau Message**. Définissez le nom du message en tant que **InsertOrders** et le type de message **BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**.  
  
2.  Ajoutez une forme construire un Message après le **ReceiveQueryResult** forme. Définissez le nom de la forme à `ConstructOrders` et définir le **Messages construits** propriété **InsertOrders**.  
  
3.  Dans le **ConstructOrders** mettre en forme, ajouter un **transformer** forme. Double-cliquez sur la forme Transformer pour ouvrir la boîte de dialogue Configuration de la forme Transformer. Dans la boîte de dialogue, sélectionnez le **mappage existant** option, puis, dans la liste déroulante, sélectionnez **BtsSalesforceIntegration.QueryResult_Orders**. Définissez **Source** à **QueryResultMsg**, **Destination** à **InsertOrders**, puis cliquez sur **OK**.  
  
4.  Après le **ConstructOrders** mettre en forme, ajoutez une forme envoi. Nommez la forme `SendOrders` et définissez le type de message **InsertOrders**.  
  
5.  Ajoutez un port pour insérer des détails de la commande dans Salesforce. Dans l'assistant Configuration du port, sélectionnez les options suivantes :  
  
    -   Spécifiez le nom de port `SendToSQL`.  
  
    -   Sélectionnez l'option pour créer un nouveau type de port.  
  
    -   Définissez **modèle de Communication** à *unidirectionnel*.  
  
    -   Définissez **direction de communication du Port** à *toujours envoyer les messages sur ce port* et **liaison de Port** à *spécifier plus tard*.  
  
     Connecter le **demande** opération du port à la **SendOrders** forme pour terminer l’orchestration d’envoi. La capture d'écran ci-dessous illustre l'orchestration de bout en bout terminée.  
  
     ![Effectuer une orchestration pour l’intégration de Salesforce](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")  
  
     Ajoutez un fichier de clé de nom fort pour le projet et enregistrez les modifications apportées au projet.  
  
 Avec les étapes de cette rubrique, nous avons réalisé l'orchestration pour recevoir une notification d'opportunité de Salesforce, envoyer une requête à Salesforce pour obtenir davantage de détails sur l'opportunité, puis insérer la réponse à la requête dans une base de données SQL Server. Dans les rubriques suivantes, nous allons construire d'autres composants clés de la solution qui serviront à l'authentification auprès de Salesforce et au traitement de la réponse de Salesforce dans BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer la Solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)