---
title: "Configurer une liaison de Client de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 146e6f51-e33b-45be-a302-8c9250e79501
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af27363e5156ca88f2c6b3e06a67d0609bf52afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-sql-adapter"></a><span data-ttu-id="92ef7-102">Configurer une liaison de Client de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="92ef7-102">Configure a Client Binding for the SQL Adapter</span></span>
<span data-ttu-id="92ef7-103">Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92ef7-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].</span></span> <span data-ttu-id="92ef7-104">Pour plus d’informations sur la génération de la classe d’assistance et de code de client WCF pour les opérations qui les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="92ef7-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
 <span data-ttu-id="92ef7-105">Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="92ef7-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="92ef7-106">L’adresse de point de terminaison doit contenir un URI de connexion SQL valide, et la liaison doit être une instance d’une liaison SQL (**sqlBinding**).</span><span class="sxs-lookup"><span data-stu-id="92ef7-106">The endpoint address must contain a valid SQL connection URI, and the binding must be an instance of a SQL Binding (**sqlBinding**).</span></span> <span data-ttu-id="92ef7-107">Pour plus d’informations sur l’URI de connexion SQL, consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="92ef7-107">For more information about the SQL connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span> <span data-ttu-id="92ef7-108">Vous devez spécifier les informations d’identification de l’utilisateur dans le cadre de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="92ef7-108">You must specify the user credentials as part of the connection URI.</span></span> <span data-ttu-id="92ef7-109">Vous pouvez utiliser la **ClientCredentials** propriété du client WCF, comme expliqué dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="92ef7-109">You may use the **ClientCredentials** property of the WCF client, as explained in this topic.</span></span>  
  
 <span data-ttu-id="92ef7-110">Vous pouvez spécifier la liaison de SQL et l’adresse de point de terminaison dans votre code ou dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="92ef7-110">You can specify the SQL binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="92ef7-111">Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="92ef7-111">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="92ef7-112">Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté à la base de données SQL avec la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92ef7-112">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the SQL database with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="92ef7-113">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="92ef7-113">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="92ef7-114">Le code suivant montre comment créer un client WCF en spécifiant l’adresse de liaison et le point de terminaison dans le code à l’aide de la **ClientCredentials** propriété du client WCF.</span><span class="sxs-lookup"><span data-stu-id="92ef7-114">The following code shows how to create a WCF client by specifying the binding and endpoint address in code by using the **ClientCredentials** property of the WCF client.</span></span>  
  
```  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress sqlAddress = new EndpointAddress("mssql://<sql_server_name>//<database_name>?");  
  
TableOp_dbo_CustomerClient client = new TableOp_dbo_CustomerClient (binding, sqlAddress);  
  
client.ClientCredentials.UserName.UserName = "USER";  
client.ClientCredentials.UserName.Password = "PASSWORD";  
  
client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="92ef7-115">Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="92ef7-115">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="92ef7-116">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="92ef7-116">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
TableOp_dbo_CustomerClient client = new TableOp_dbo_CustomerClient("SqlAdapterBinding_TableOp_dbo_Customer");  
  
client.ClientCredentials.UserName.UserName = "USER";  
client.ClientCredentials.UserName.Password = "PASSWORD";  
  
client.Open();  
```  
  
 <span data-ttu-id="92ef7-117">Le code XML suivant montre le fichier de configuration créé pour la table Customer par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92ef7-117">The following XML shows the configuration file created for the Customer table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="92ef7-118">Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="92ef7-118">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <sqlBinding>  
                <binding name="SqlAdapterBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" maxConnectionPoolSize="100"  
                    encrypt="false" useAmbientTransaction="true" batchSize="20"  
                    polledDataAvailableStatement="" pollingStatement="" pollingIntervalInSeconds="30"  
                    pollWhileDataFound="false" notificationStatement="" notifyOnListenerStart="true"  
                    enableBizTalkCompatibilityMode="true" chunkSize="4194304"  
                    inboundOperationType="Polling" useDatabaseNameInXsdNamespace="false"  
                    allowIdentityInsert="false" enablePerformanceCounters="false"  
                    xmlStoredProcedureRootNodeName="" xmlStoredProcedureRootNodeNamespace="" />  
            </sqlBinding>  
        </bindings>  
        <client>  
            <endpoint address="mssql://<sql_server_name>//<database_name>?" binding="sqlBinding"  
                bindingConfiguration="SqlAdapterBinding" contract="TableOp_dbo_Customer"  
                name="SqlAdapterBinding_TableOp_dbo_Customer" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="92ef7-119">Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="92ef7-119">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="92ef7-120">Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et d’un artefact de SQL Server cible ; par exemple, «`SqlAdapterBinding_TableOp_dbo_Customer`».</span><span class="sxs-lookup"><span data-stu-id="92ef7-120">Each WCF client entry will have a unique name based on its binding configuration and target SQL Server artifact; for example, "`SqlAdapterBinding_TableOp_dbo_Customer`".</span></span> <span data-ttu-id="92ef7-121">Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="92ef7-121">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="92ef7-122">Ces entrées de configuration de liaison seront nommées de la manière suivante : SqlAdapterBinding, SqlAdapterBinding1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="92ef7-122">These binding configuration entries will be named in the following manner: SqlAdapterBinding, SqlAdapterBinding1, and so on.</span></span> <span data-ttu-id="92ef7-123">Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.</span><span class="sxs-lookup"><span data-stu-id="92ef7-123">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ef7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92ef7-124">See Also</span></span>  
<span data-ttu-id="92ef7-125">[Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="92ef7-125">[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md) </span></span>  
 <span data-ttu-id="92ef7-126">[Générer un Client WCF ou le contrat de Service WCF pour les artefacts SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md) </span><span class="sxs-lookup"><span data-stu-id="92ef7-126">[Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md) </span></span>  
[<span data-ttu-id="92ef7-127">Créer l’URI de connexion SQL Server</span><span class="sxs-lookup"><span data-stu-id="92ef7-127">Create the SQL Server connection URI</span></span>](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)