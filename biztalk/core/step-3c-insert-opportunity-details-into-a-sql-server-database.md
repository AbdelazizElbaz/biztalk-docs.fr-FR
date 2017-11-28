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
# <a name="step-3c-insert-opportunity-details-into-a-sql-server-database"></a><span data-ttu-id="e4ba7-102">Étape 3c : insérer des détails d’opportunité dans une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="e4ba7-102">Step 3c: Insert Opportunity Details into a SQL Server Database</span></span>
<span data-ttu-id="e4ba7-103">À présent, nous avons créé l'orchestration pour envoyer une requête à Salesforce et recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-103">By now we have built the orchestration to send a query to Salesforce and receive a response.</span></span> <span data-ttu-id="e4ba7-104">Dans cette section, nous allons mettre à jour cette orchestration pour insérer la réponse de Salesforce dans une **OrderDetails** table dans une base de données SQL Server sur site, **commandes**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-104">In this section, we’ll update that orchestration to insert the response from Salesforce into an **OrderDetails** table in an on-premise SQL Server database, **Orders**.</span></span> <span data-ttu-id="e4ba7-105">Pour y parvenir, nous allons effectuer les différentes étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4ba7-105">To achieve this, we’ll perform the following broad set of steps:</span></span>  
  
-   <span data-ttu-id="e4ba7-106">Créer un **OrderDetails** de table dans une **commandes** base de données dans une base de données SQL Server sur site.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-106">Create an **OrderDetails** table in an **Orders** database in an on-premise SQL Server database.</span></span>  
  
-   <span data-ttu-id="e4ba7-107">Utilisez le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] disponible avec [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour générer le schéma pour l’opération d’insertion sur la **OrderDetails** table.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-107">Use the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] available with [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to generate the schema for the Insert operation on the **OrderDetails** table.</span></span>  
  
-   <span data-ttu-id="e4ba7-108">Créer un mappage pour transformer le message de réponse de Salesforce pour le message à insérer dans **OrderDetails** table dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-108">Create a map to transform the Salesforce response message to the message for inserting into **OrderDetails** table in SQL Server.</span></span>  
  
-   <span data-ttu-id="e4ba7-109">Mettre à jour de l’orchestration pour utiliser la transformation pour insérer le message de réponse dans le **OrderDetails** table.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-109">Update the orchestration to use the transform to insert the response message into the **OrderDetails** table.</span></span>  
  
## <a name="create-sql-server-database-and-table"></a><span data-ttu-id="e4ba7-110">Créer une table et une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="e4ba7-110">Create SQL Server Database and Table</span></span>  
  
#### <a name="to-create-the-database-and-table"></a><span data-ttu-id="e4ba7-111">Pour créer la base de données et la table</span><span class="sxs-lookup"><span data-stu-id="e4ba7-111">To create the database and table</span></span>  
  
1.  <span data-ttu-id="e4ba7-112">Ouvrez SQL Server Management Studio et connectez-vous en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-112">Open SQL Server Management Studio and connect as an administrator.</span></span>  
  
2.  <span data-ttu-id="e4ba7-113">Cliquez sur le **bases de données** nœud et cliquez sur **nouvelle base de données**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-113">Right-click the **Databases** node and click **New Database**.</span></span> <span data-ttu-id="e4ba7-114">Spécifiez le nom de base de données `Orders` et spécifier d’autres détails pour créer une nouvelle base de données.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-114">Specify the database name as `Orders` and specify other details to create a new database.</span></span>  
  
3.  <span data-ttu-id="e4ba7-115">Ouvrez un éditeur de requête et exécutez la requête suivante pour créer un **OrderDetails** de table dans le **commandes** base de données :</span><span class="sxs-lookup"><span data-stu-id="e4ba7-115">Open a query editor and run the following query to create an **OrderDetails** table in the **Orders** database:</span></span>  
  
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
  
## <a name="create-schema-for-insert-operation-on-orderdetails-table"></a><span data-ttu-id="e4ba7-116">Créer un schéma pour réaliser l'opération Insert sur la table OrderDetails</span><span class="sxs-lookup"><span data-stu-id="e4ba7-116">Create Schema for Insert Operation on OrderDetails Table</span></span>  
 <span data-ttu-id="e4ba7-117">Installation [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] fournit un [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] qui peut être utilisé dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet pour générer le schéma pour l’opération d’insertion sur la **OrderDetails** table.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-117">Installing [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] provides a [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] that can be used within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project to generate the schema for the Insert operation on the **OrderDetails** table.</span></span> <span data-ttu-id="e4ba7-118">Cette section présente les étapes à suivre pour créer le schéma de message.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-118">This section provides steps to follow to create the message schema.</span></span>  
  
#### <a name="to-create-the-schema-for-insert-operation"></a><span data-ttu-id="e4ba7-119">Pour créer le schéma de l'opération Insert</span><span class="sxs-lookup"><span data-stu-id="e4ba7-119">To create the schema for Insert operation</span></span>  
  
1.  <span data-ttu-id="e4ba7-120">Cliquez sur le **BtsSalesforceIntegration** de projet, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-120">Right-click the **BtsSalesforceIntegration** project, point to **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="e4ba7-121">Dans le **ajouter les éléments générés** boîte de dialogue, cliquez sur **Consume Adapter Service**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-121">In the **Add Generated Items** dialog box, click **Consume Adapter Service**, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="e4ba7-122">Dans le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)], à partir de l’instruction Select une liaison liste déroulante, cliquez sur **sqlBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-122">In the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)], from the Select a binding drop-down, click **sqlBinding**, and then click **Configure**.</span></span>  
  
3.  <span data-ttu-id="e4ba7-123">Dans le **configurer l’adaptateur** boîte de dialogue **sécurité** onglet, pour **type d’informations d’identification du Client**, sélectionnez **Windows** utilisation de Windows authentification pour se connecter à la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-123">In the **Configure Adapter** dialog box, under **Security** tab, for **Client credential type**, select **Windows** to use Windows authentication to connect to SQL Server database.</span></span>  
  
4.  <span data-ttu-id="e4ba7-124">Dans le **configurer l’adaptateur** boîte de dialogue **propriétés URI** onglet, pour **Initial Catalog** spécifier le nom de la base de données (Orders) pour se connecter à.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-124">In the **Configure Adapter** dialog box, under **URI Properties** tab, for **Initial Catalog** specify the database name (Orders) to connect to.</span></span> <span data-ttu-id="e4ba7-125">Pour **Server** spécifier le nom de l’ordinateur où est installé SQL Server, vous êtes connecté.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-125">For **Server** specify the computer name where SQL Server you are connecting to is installed.</span></span> <span data-ttu-id="e4ba7-126">Si la base de données SQL Server est sur le même ordinateur que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet, vous pouvez tout simplement entrer une période (**.**).</span><span class="sxs-lookup"><span data-stu-id="e4ba7-126">If the SQL Server database is on the same computer as the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, you can just put a period (**.**).</span></span> <span data-ttu-id="e4ba7-127">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-127">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e4ba7-128">Dans le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-128">In the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] click **Connect**.</span></span> <span data-ttu-id="e4ba7-129">Une fois la connexion est établie, sélectionnez le type de contrat **Client (Outbound operations)**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-129">After the connection is established, select the contract type as **Client(Outbound operations)**.</span></span> <span data-ttu-id="e4ba7-130">Sous le **sélectionner une catégorie** , développez **Tables**, cliquez sur **OrderDetails** table et dans le volet droit, cliquez sur **insérer** puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-130">Under the **Select a category** box, expand **Tables**, click **OrderDetails** table, and in the right pane click **Insert** and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="e4ba7-131">Spécifiez un **préfixe de nom de fichier** si vous voulez préfixer les schémas générés avec un identificateur.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-131">Specify a **Filename Prefix** if you want to prefix the generated schemas with an identifier.</span></span> <span data-ttu-id="e4ba7-132">Pour ce didacticiel, nous allons spécifier comme préfixe **InsertOrders** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-132">For this tutorial, let’s specify the prefix as **InsertOrders** and then click **OK**.</span></span>  
  
     <span data-ttu-id="e4ba7-133">Un tas de schémas sont ajoutés au projet.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-133">A bunch of schemas are added to the project.</span></span> <span data-ttu-id="e4ba7-134">Le schéma que nous allons utiliser pour insérer des messages dans la **OrderDetails** table est **InsertOrdersTableOperation.dbo.OrderDetails.xsd**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-134">The schema that we’ll use for inserting messages into the **OrderDetails** table is **InsertOrdersTableOperation.dbo.OrderDetails.xsd**.</span></span>  
  
## <a name="map-salesforce-response-and-insert-schemas"></a><span data-ttu-id="e4ba7-135">Mapper une réponse de Salesforce et insérer des schémas</span><span class="sxs-lookup"><span data-stu-id="e4ba7-135">Map Salesforce Response and Insert Schemas</span></span>  
 <span data-ttu-id="e4ba7-136">Maintenant que nous avons deux schémas (réponse de Salesforce et insertion dans **OrderDetails**), nous devons mapper le schéma de réponse de Salesforce dans le schéma d’insertion pour **OrderDetails** afin que le message de réponse de Salesforce peut être inséré dans la table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-136">Now that we have both the schemas (response from Salesforce and inserting into **OrderDetails**), we must map the response schema from Salesforce into the insert schema for **OrderDetails** so that the response message from Salesforce can be inserted in the SQL Server database table.</span></span>  
  
#### <a name="to-map-the-schemas"></a><span data-ttu-id="e4ba7-137">Pour mapper les schémas</span><span class="sxs-lookup"><span data-stu-id="e4ba7-137">To map the schemas</span></span>  
  
1.  <span data-ttu-id="e4ba7-138">Avec le bouton droit le **BtsSalesforceIntegration** de projet, pointez sur **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-138">Right-click the **BtsSalesforceIntegration** project, point to **Add**, click **New Item**, and then click **Map**.</span></span> <span data-ttu-id="e4ba7-139">Spécifiez le nom de mappage `QueryResult_Orders.btm` puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-139">Specify the map name as `QueryResult_Orders.btm` and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="e4ba7-140">Sur la surface de mappage pour le schéma source, sélectionnez **QueryResult** pour le schéma de destination, sélectionnez **InsertOrdersTableOperation.dbo.OrderDetails.xsd** , puis, dans ce cas, le  **Insérer** nœud.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-140">On the map surface, for the source schema, select **QueryResult** and for the destination schema, select **InsertOrdersTableOperation.dbo.OrderDetails.xsd** and then within that, the **Insert** node.</span></span>  
  
3.  <span data-ttu-id="e4ba7-141">Mappez  les deux schémas comme le montre la capture d'écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e4ba7-141">Map the two schemas as shown in the following screenshot:</span></span>  
  
     <span data-ttu-id="e4ba7-142">![Mapper une réponse de Salesforce pour schéma d’insertion](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")</span><span class="sxs-lookup"><span data-stu-id="e4ba7-142">![Map Salesforce response to Insert schema](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")</span></span>  
  
     <span data-ttu-id="e4ba7-143">Notez que la carte utilise un **bouclage** fonctoid entre le **enregistrements** et **OrderDetails** lien.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-143">Notice that the map uses a **Looping** functoid between the **records** and the **OrderDetails** link.</span></span> <span data-ttu-id="e4ba7-144">Cela garantit que toutes les une ou plusieurs occurrences de nœuds sous **enregistrements** sont mappées aux occurrences de nœuds sous similaires le **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-144">This ensures that all one or more than one occurrences of nodes under **records** are mapped to similar occurrences of nodes under the **OrderDetails**.</span></span>  
  
4.  <span data-ttu-id="e4ba7-145">Enregistrez les modifications apportées au mappage.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-145">Save changes to the map.</span></span>  
  
## <a name="update-the-orchestration-to-insert-messages-into-sql-server"></a><span data-ttu-id="e4ba7-146">Mettre à jour l'orchestration pour insérer des messages dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="e4ba7-146">Update the Orchestration to Insert Messages into SQL Server</span></span>  
 <span data-ttu-id="e4ba7-147">Dans cette section, nous allons utiliser le mappage de l'orchestration pour transformer le message de réponse de Salesforce en message pour insérer des détails de la commande dans une table SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-147">In this section, we’ll use the map in the orchestration to transform the Salesforce response message into a message for inserting order details in a SQL Server table.</span></span> <span data-ttu-id="e4ba7-148">Nous allons également ajouter un port pour envoyer ce message à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-148">We’ll also add a port to send that message to SQL Server.</span></span>  
  
#### <a name="to-update-the-orchestration"></a><span data-ttu-id="e4ba7-149">Pour mettre à jour l'orchestration</span><span class="sxs-lookup"><span data-stu-id="e4ba7-149">To update the orchestration</span></span>  
  
1.  <span data-ttu-id="e4ba7-150">Créez un message variable pour le schéma d'insertion.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-150">Create a message variable for the insert schema.</span></span> <span data-ttu-id="e4ba7-151">À partir de la vue orchestration, cliquez sur le **Messages** nœud, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-151">From the orchestration view, right-click the **Messages** node, and then click **New Message**.</span></span> <span data-ttu-id="e4ba7-152">Définissez le nom du message en tant que **InsertOrders** et le type de message **BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-152">Set the message name as **InsertOrders** and message type as **BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**.</span></span>  
  
2.  <span data-ttu-id="e4ba7-153">Ajoutez une forme construire un Message après le **ReceiveQueryResult** forme.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-153">Add a Construct Message shape after the **ReceiveQueryResult** shape.</span></span> <span data-ttu-id="e4ba7-154">Définissez le nom de la forme à `ConstructOrders` et définir le **Messages construits** propriété **InsertOrders**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-154">Set the name of the shape to `ConstructOrders` and set the **Messages Constructed** property to **InsertOrders**.</span></span>  
  
3.  <span data-ttu-id="e4ba7-155">Dans le **ConstructOrders** mettre en forme, ajouter un **transformer** forme.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-155">Within the **ConstructOrders** shape, add a **Transform** shape.</span></span> <span data-ttu-id="e4ba7-156">Double-cliquez sur la forme Transformer pour ouvrir la boîte de dialogue Configuration de la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-156">Double-click the Transform shape to open the Transform Configuration dialog box.</span></span> <span data-ttu-id="e4ba7-157">Dans la boîte de dialogue, sélectionnez le **mappage existant** option, puis, dans la liste déroulante, sélectionnez **BtsSalesforceIntegration.QueryResult_Orders**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-157">In the dialog box, select the **Existing Map** option, and then from the drop-down select **BtsSalesforceIntegration.QueryResult_Orders**.</span></span> <span data-ttu-id="e4ba7-158">Définissez **Source** à **QueryResultMsg**, **Destination** à **InsertOrders**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-158">Set **Source** to **QueryResultMsg**, **Destination** to **InsertOrders**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e4ba7-159">Après le **ConstructOrders** mettre en forme, ajoutez une forme envoi.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-159">After the **ConstructOrders** shape, add a Send shape.</span></span> <span data-ttu-id="e4ba7-160">Nommez la forme `SendOrders` et définissez le type de message **InsertOrders**.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-160">Name the shape `SendOrders` and set the message type as **InsertOrders**.</span></span>  
  
5.  <span data-ttu-id="e4ba7-161">Ajoutez un port pour insérer des détails de la commande dans Salesforce.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-161">Add a port to insert order details into Salesforce.</span></span> <span data-ttu-id="e4ba7-162">Dans l'assistant Configuration du port, sélectionnez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4ba7-162">In the Port Configuration wizard, select the following options:</span></span>  
  
    -   <span data-ttu-id="e4ba7-163">Spécifiez le nom de port `SendToSQL`.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-163">Specify the port name as `SendToSQL`.</span></span>  
  
    -   <span data-ttu-id="e4ba7-164">Sélectionnez l'option pour créer un nouveau type de port.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-164">Select the option to create a new port type.</span></span>  
  
    -   <span data-ttu-id="e4ba7-165">Définissez **modèle de Communication** à *unidirectionnel*.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-165">Set **Communication Pattern** to *One-Way*.</span></span>  
  
    -   <span data-ttu-id="e4ba7-166">Définissez **direction de communication du Port** à *toujours envoyer les messages sur ce port* et **liaison de Port** à *spécifier plus tard*.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-166">Set **Port direction of communication** to *I’ll always be sending messages on this port* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="e4ba7-167">Connecter le **demande** opération du port à la **SendOrders** forme pour terminer l’orchestration d’envoi.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-167">Connect the **Request** operation of port to the **SendOrders** Send shape to complete the orchestration.</span></span> <span data-ttu-id="e4ba7-168">La capture d'écran ci-dessous illustre l'orchestration de bout en bout terminée.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-168">The following screenshot depicts the completed orchestration, end-to-end.</span></span>  
  
     <span data-ttu-id="e4ba7-169">![Effectuer une orchestration pour l’intégration de Salesforce](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")</span><span class="sxs-lookup"><span data-stu-id="e4ba7-169">![Complete orchesration for Salesforce integration](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")</span></span>  
  
     <span data-ttu-id="e4ba7-170">Ajoutez un fichier de clé de nom fort pour le projet et enregistrez les modifications apportées au projet.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-170">Add a strong name key file to the project and save changes to the project.</span></span>  
  
 <span data-ttu-id="e4ba7-171">Avec les étapes de cette rubrique, nous avons réalisé l'orchestration pour recevoir une notification d'opportunité de Salesforce, envoyer une requête à Salesforce pour obtenir davantage de détails sur l'opportunité, puis insérer la réponse à la requête dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-171">With the steps in this topic, we have completed the orchestration, to receive an opportunity notification from Salesforce, query Salesforce for more details about the opportunity, and then insert the query response into a SQL Server database.</span></span> <span data-ttu-id="e4ba7-172">Dans les rubriques suivantes, nous allons construire d'autres composants clés de la solution qui serviront à l'authentification auprès de Salesforce et au traitement de la réponse de Salesforce dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-172">In the subsequent topics, we’ll build some other key components of the solution that are used to authenticate with Salesforce and process Salesforce response within BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ba7-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4ba7-173">See Also</span></span>  
 [<span data-ttu-id="e4ba7-174">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e4ba7-174">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)