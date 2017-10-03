---
title: "Configurer un client de liaison pour le système SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxy programming, creating a proxy
- creating a proxy
- how to, create a proxy
ms.assetid: bceef132-29ff-4207-a37d-bf94fab484dd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f75253251d18049363255f553ded833748e33875
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-sap-system"></a><span data-ttu-id="e12a2-102">Configurer un client de liaison pour le système SAP</span><span class="sxs-lookup"><span data-stu-id="e12a2-102">Configure a client binding for the SAP system</span></span>
<span data-ttu-id="e12a2-103">Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e12a2-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span> <span data-ttu-id="e12a2-104">Pour plus d’informations sur la génération de la classe d’assistance et de code de client WCF pour les opérations qui les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="e12a2-104">For information about how to generate the WCF client class and helper code for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="e12a2-105">Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="e12a2-105">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="e12a2-106">L’adresse de point de terminaison doit contenir un URI de connexion SAP valide, et la liaison doit être une instance d’une liaison de SAP (**SAPBinding**).</span><span class="sxs-lookup"><span data-stu-id="e12a2-106">The endpoint address must contain a valid SAP connection URI, and the binding must be an instance of an SAP Binding (**SAPBinding**).</span></span> <span data-ttu-id="e12a2-107">Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="e12a2-107">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
 <span data-ttu-id="e12a2-108">Vous pouvez spécifier la liaison de SAP et de l’adresse de point de terminaison dans votre code ou dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e12a2-108">You can specify the SAP Binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="e12a2-109">Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="e12a2-109">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="e12a2-110">Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté au système SAP avec la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e12a2-110">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the SAP system with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="e12a2-111">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="e12a2-111">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="e12a2-112">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="e12a2-112">The following code shows how to create a WCF client by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="e12a2-113">Il est conseillé de spécifier les informations d’identification du système SAP à l’aide de la **ClientCredentials** propriété du client WCF, plutôt que dans l’URI fourni pour l’adresse de point de terminaison de connexion.</span><span class="sxs-lookup"><span data-stu-id="e12a2-113">It is good practice to specify the SAP system credentials by using the **ClientCredentials** property of the WCF client rather than in the connection URI supplied for the endpoint address.</span></span>  
  
```  
// A WCF client that targets an RFC is created  
// by using a binding object and endpoint address  
SAPBinding sapBinding = new SAPBinding();  
EndpointAddress sapAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00");  
  
RfcClient rfcClient = new RfcClient(sapBinding, sapAddress);  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="e12a2-114">Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="e12a2-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="e12a2-115">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="e12a2-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
// A WCF client that targets an RFC is created  
// by specifying the client endpoint information in app.config  
RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
rfcClient.Open();  
```  
  
 <span data-ttu-id="e12a2-116">Le code XML suivant montre le fichier de configuration créé pour la table EMP par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e12a2-116">The following XML shows the configuration file created for the EMP table by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="e12a2-117">Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="e12a2-117">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" receiveIdocFormat="Typed"  
                    generateFlatFileCompatibleIdocSchema="true" maxConnectionsPerSystem="50"  
                    enableConnectionPooling="true" idleConnectionTimeout="00:15:00"  
                    flatFileSegmentIndicator="SegmentDefinition" enablePerformanceCounters="false"  
                    autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false" padReceivedIdocWithSpaces="false"  
                    enableBizTalkCompatibilityMode="false" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="Rfc"  
                name="SAPBinding_Rfc" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e12a2-118">Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e12a2-118">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="e12a2-119">Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et les artefacts du système SAP cible (par exemple, Rfc et Trfc) ; par exemple, « SAPBinding_Rfc ».</span><span class="sxs-lookup"><span data-stu-id="e12a2-119">Each WCF client entry will have a unique name based on its binding configuration and target SAP system artifacts (such as Rfc and Trfc); for example, "SAPBinding_Rfc".</span></span> <span data-ttu-id="e12a2-120">Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="e12a2-120">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="e12a2-121">Ces entrées de configuration de liaison seront nommées de la manière suivante : SAPBinding1, SAPBinding2, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e12a2-121">These binding configuration entries will be named in the following manner: SAPBinding1, SAPBinding2, and so on.</span></span> <span data-ttu-id="e12a2-122">Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.</span><span class="sxs-lookup"><span data-stu-id="e12a2-122">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e12a2-123">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence les artefacts SAP différentes du même type (par exemple, RFC, TRFC et IDOC) en tant qu’opérations différentes du même contrat de service.</span><span class="sxs-lookup"><span data-stu-id="e12a2-123">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces different SAP artifacts of the same type (such as RFC, TRFC, and IDOC) as different operations of the same service contract.</span></span> <span data-ttu-id="e12a2-124">Par exemple, deux RFC différents, RFC_EXAMPLE_A et RFC_EXAMPLE_B, seront à la fois visible sous le même contrat de service (« Rfc »).</span><span class="sxs-lookup"><span data-stu-id="e12a2-124">For example, two different RFCs, RFC_EXAMPLE_A and RFC_EXAMPLE_B, will both be surfaced under the same service contract ("Rfc").</span></span> <span data-ttu-id="e12a2-125">Cela signifie que les deux documents RFC seront appelés par la même classe de client WCF, **RfcClient**, et que les paramètres pour les deux documents RFC seront déclarés dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e12a2-125">This means that both RFCs will be invoked by the same WCF client class, **RfcClient**, and that the parameters for both RFCs will be declared in the same namespace.</span></span> <span data-ttu-id="e12a2-126">Par conséquent, vous devez générer le client WCF pour les deux documents RFC pendant la même [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] session (connexion) pour éviter de rencontrer une collision d’espace de noms lorsque vous générez votre solution.</span><span class="sxs-lookup"><span data-stu-id="e12a2-126">Therefore, you must generate the WCF client for both RFCs during the same [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] session (connection) to avoid experiencing a namespace collision when you build your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12a2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e12a2-127">See Also</span></span>  
<span data-ttu-id="e12a2-128">[Développer des applications SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="e12a2-128">[Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 <span data-ttu-id="e12a2-129">[Générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md) </span><span class="sxs-lookup"><span data-stu-id="e12a2-129">[Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md) </span></span>  
 [<span data-ttu-id="e12a2-130">Créer l’URI de connexion au système SAP</span><span class="sxs-lookup"><span data-stu-id="e12a2-130">Create the SAP system connection URI</span></span>](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)