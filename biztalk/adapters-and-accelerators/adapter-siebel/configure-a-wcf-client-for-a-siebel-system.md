---
title: "Configurer un Client WCF pour un système Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, create a WCF client by specifying binding and endpoint address in a configuration file
- how to, create a WCF client by specifying binding and endpoint address in code
- WCF service model, configuring a WCF client for a Siebel system
ms.assetid: 6b4c5b06-d5ff-4dbf-8dc2-89c547a59864
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2395f8698c31a51466cfc98834cec137bf58a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-wcf-client-for-a-siebel-system"></a><span data-ttu-id="80aff-102">Configurer un Client WCF pour un système Siebel</span><span class="sxs-lookup"><span data-stu-id="80aff-102">Configure a WCF Client for a Siebel System</span></span>
<span data-ttu-id="80aff-103">Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80aff-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="80aff-104">Pour plus d’informations sur la génération de la classe d’assistance et de code de client WCF pour les opérations qui les [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose, consultez [générer un Client WCF ou un contrat de service WCF pour Siebel solution artefacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="80aff-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes, see [Generate a WCF Client or a WCF service contract for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="80aff-105">Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="80aff-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="80aff-106">L’adresse de point de terminaison doit contenir un URI de connexion Siebel valide, et la liaison doit être une instance d’une liaison Siebel (**SiebelBinding**).</span><span class="sxs-lookup"><span data-stu-id="80aff-106">The endpoint address must contain a valid Siebel connection URI, and the binding must be an instance of a Siebel Binding (**SiebelBinding**).</span></span> <span data-ttu-id="80aff-107">Pour plus d’informations sur l’URI de connexion Siebel, consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="80aff-107">For more information about the Siebel connection URI, see [Connect to the Siebel System in Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="80aff-108">Vous pouvez spécifier la liaison de Siebel et l’adresse de point de terminaison dans votre code ou dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="80aff-108">You can specify the Siebel Binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="80aff-109">Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="80aff-109">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="80aff-110">Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté au système Siebel avec le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80aff-110">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Siebel system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="80aff-111">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="80aff-111">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="80aff-112">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="80aff-112">The following code shows how to create a WCF client by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="80aff-113">Il est conseillé de spécifier les informations d’identification Siebel à l’aide de la **ClientCredentials** propriété du client WCF, plutôt que dans l’URI fourni pour l’adresse de point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="80aff-113">It is good practice to specify the Siebel credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.</span></span>  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by using a binding object and endpoint address  
SiebelBinding sblBinding = new SiebelBinding();  
EndpointAddress sblAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu");  
  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient(sblBinding, sblAddress);  
  
    client.ClientCredentials.UserName.UserName = "SADMIN";  
    client.ClientCredentials.UserName.Password = "SADMIN";  
  
    client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="80aff-114">Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="80aff-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="80aff-115">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="80aff-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
// A WCF client that targets the TimeStamp business service is created  
// by specifying the client endpoint information in app.config  
BusinessServices_TimeStamp_OperationClient client =   
    new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
client.ClientCredentials.UserName.UserName = "SADMIN";  
client.ClientCredentials.UserName.Password = "SADMIN";  
  
client.Open();  
```  
  
### <a name="the-appconfig-file"></a><span data-ttu-id="80aff-116">Le fichier App.config</span><span class="sxs-lookup"><span data-stu-id="80aff-116">The App.config File</span></span>  
 <span data-ttu-id="80aff-117">Le code XML suivant montre le fichier de configuration créé pour le service d’entreprise TimeStamp par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80aff-117">The following XML shows the configuration file created for the TimeStamp business service by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="80aff-118">Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="80aff-118">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <siebelBinding>  
                <binding name="SiebelBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    enablePerformanceCounters="false" enableConnectionPooling="true"  
                    maxConnectionsPerSystem="5" idleConnectionTimeout="00:01:00"  
                    acceptCredentialsInUri="false" />  
            </siebelBinding>  
        </bindings>  
        <client>  
            <endpoint address="siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=ent_server&Language=enu"  
                binding="siebelBinding" bindingConfiguration="SiebelBinding"  
                contract="BusinessServices_TimeStamp_Operation" name="SiebelBinding_BusinessServices_TimeStamp_Operation" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="80aff-119">Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="80aff-119">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="80aff-120">Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et d’un artefact de Siebel cible ; par exemple, « SiebelBinding_BusinessServices_TimeStamp_Operation ».</span><span class="sxs-lookup"><span data-stu-id="80aff-120">Each WCF client entry will have a unique name based on its binding configuration and target Siebel artifact; for example, " SiebelBinding_BusinessServices_TimeStamp_Operation ".</span></span> <span data-ttu-id="80aff-121">Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="80aff-121">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="80aff-122">Ces entrées de configuration de liaison seront nommées de la manière suivante : SiebelBinding, SiebelBinding1, SiebelBinding2, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="80aff-122">These binding configuration entries will be named in the following manner: SiebelBinding, SiebelBinding1, SiebelBinding2, and so on.</span></span> <span data-ttu-id="80aff-123">Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.</span><span class="sxs-lookup"><span data-stu-id="80aff-123">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80aff-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80aff-124">See Also</span></span>  
 [<span data-ttu-id="80aff-125">Développer des Applications Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="80aff-125">Develop Siebel Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)