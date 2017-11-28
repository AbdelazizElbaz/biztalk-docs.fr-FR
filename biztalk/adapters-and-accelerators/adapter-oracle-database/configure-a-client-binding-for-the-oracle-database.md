---
title: "Configurer une liaison pour la base de données Oracle de client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client binding, specifying in code
- WCF client, creating
- client binding, specifying in configuration file
ms.assetid: f18c7296-c28a-4dec-9514-5299c8c2dffe
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de5eeb9a7b0022ce4da5f56591e863f48bd0b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-oracle-database"></a><span data-ttu-id="664d5-102">Configurer un client de liaison pour la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="664d5-102">Configure a client binding for the Oracle Database</span></span>
<span data-ttu-id="664d5-103">Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="664d5-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="664d5-104">Pour plus d’informations sur la génération de la classe d’assistance et de code de client WCF pour les opérations qui les [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="664d5-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes, see [Generate a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="664d5-105">Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="664d5-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="664d5-106">L’adresse de point de terminaison doit contenir un URI de connexion Oracle valide, et la liaison doit être une instance d’une liaison de base de données Oracle (**OracleDBBinding**).</span><span class="sxs-lookup"><span data-stu-id="664d5-106">The endpoint address must contain a valid Oracle connection URI, and the binding must be an instance of an Oracle DB Binding (**OracleDBBinding**).</span></span> <span data-ttu-id="664d5-107">Pour plus d’informations sur l’URI de connexion Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="664d5-107">For more information about the Oracle connection URI, see [Create the Oracle Database Connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span> <span data-ttu-id="664d5-108">Nous recommandons que vous ne spécifiez pas les informations d’identification de l’utilisateur dans le cadre de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="664d5-108">We recommend that you do not specify the user credentials as part of the connection URI.</span></span> <span data-ttu-id="664d5-109">Vous pouvez utiliser à la place la **ClientCredentials** propriété du client WCF, comme expliqué dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="664d5-109">You may instead use the **ClientCredentials** property of the WCF client, as explained in this topic.</span></span>  
  
 <span data-ttu-id="664d5-110">Vous pouvez spécifier l’adresse de point de terminaison et de la liaison de base de données Oracle dans votre code ou dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="664d5-110">You can specify the Oracle DB Binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="664d5-111">Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="664d5-111">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="664d5-112">Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté à la base de données Oracle avec le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="664d5-112">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Oracle database with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="664d5-113">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="664d5-113">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="664d5-114">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="664d5-114">The following code shows how to create a WCF client by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="664d5-115">Il est conseillé de spécifier les informations d’identification Oracle à l’aide de la **ClientCredentials** propriété du client WCF, plutôt que dans l’URI fourni pour l’adresse de point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="664d5-115">It is good practice to specify the Oracle credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.</span></span>  
  
```  
// A WCF client that targets the /SCOTT/EMP table is created  
// by using a binding object and endpoint address  
OracleDBBinding odbBinding = new OracleDBBinding();  
EndpointAddress odbAddress = new EndpointAddress("OracleDb://ADAPTER");  
  
SCOTTTableEMPClient empClient = new SCOTTTableEMPClient(odbBinding, odbAddress);  
  
empClient.ClientCredentials.UserName.UserName = "SCOTT";  
empClient.ClientCredentials.UserName.Password = "TIGER";  
  
empClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="664d5-116">Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="664d5-116">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="664d5-117">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="664d5-117">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
// A WCF client that targets the /SCOTT/EMP table is created  
// by specifying the client endpoint information in app.config  
SCOTTTableEMPClient empClient = new SCOTTTableEMPClient("OracleDBBinding_SCOTT.Table.EMP");  
  
empClient.ClientCredentials.UserName.UserName = "SCOTT";  
empClient.ClientCredentials.UserName.Password = "TIGER";  
  
empClient.Open();  
```  
  
 <span data-ttu-id="664d5-118">Le code XML suivant montre le fichier de configuration créé pour la table EMP par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="664d5-118">The following XML shows the configuration file created for the EMP table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="664d5-119">Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="664d5-119">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00"  
                    dataFetchSize="65536" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" longDatatypeColumnSize="32767" pollingStatement=""  
                    postPollStatement="" pollingInterval="500" useOracleConnectionPool="false"  
                    minPoolSize="1" maxPoolSize="100" incrPoolSize="5" decrPoolSize="1"  
                    connectionLifetime="0" transactionIsolationLevel="ReadCommitted"  
                    enablePerformanceCounters="false" acceptCredentialsInUri="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </oracleDBBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracledb://adapter/" binding="oracleDBBinding"  
                bindingConfiguration="OracleDBBinding" contract="SCOTTTableEMP"  
                name="OracleDBBinding_SCOTT.Table.EMP" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="664d5-120">Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="664d5-120">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="664d5-121">Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et d’un artefact de base de données Oracle cible ; par exemple, « OracleDBBinding_SCOTT. Table.EMP ».</span><span class="sxs-lookup"><span data-stu-id="664d5-121">Each WCF client entry will have a unique name based on its binding configuration and target Oracle database artifact; for example, "OracleDBBinding_SCOTT.Table.EMP".</span></span> <span data-ttu-id="664d5-122">Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="664d5-122">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="664d5-123">Ces entrées de configuration de liaison seront nommées de la manière suivante : OracleDBBinding1, OracleDBBinding2, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="664d5-123">These binding configuration entries will be named in the following manner: OracleDBBinding1, OracleDBBinding2, and so on.</span></span> <span data-ttu-id="664d5-124">Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.</span><span class="sxs-lookup"><span data-stu-id="664d5-124">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664d5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="664d5-125">See Also</span></span>  
 <span data-ttu-id="664d5-126">[Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="664d5-126">[Develop Oracle Database Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) </span></span>  
 <span data-ttu-id="664d5-127">[Générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md) </span><span class="sxs-lookup"><span data-stu-id="664d5-127">[Generate a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md) </span></span>  
 <span data-ttu-id="664d5-128">[Créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) </span><span class="sxs-lookup"><span data-stu-id="664d5-128">[Create the Oracle Database Connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) </span></span>  
 [<span data-ttu-id="664d5-129">Développer des Applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="664d5-129">Develop Oracle Database Applications by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)