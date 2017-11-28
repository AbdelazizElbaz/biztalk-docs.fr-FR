---
title: "Configurer un client de liaison d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1347cbca-5567-43f8-a75e-a23b108692bc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dadf91973bdee181050f420ed611eb0c502fc988
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-client-binding-for-the-oracle-e-business-suite"></a><span data-ttu-id="e7cde-102">Configurer un client de liaison d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="e7cde-102">Configure a client binding for the Oracle E-Business Suite</span></span>
<span data-ttu-id="e7cde-103">Une fois que vous avez généré la classe de client WCF, vous pouvez créer un client WCF (instance) et appeler ses méthodes pour consommer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7cde-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
 <span data-ttu-id="e7cde-104">Pour créer le client WCF, vous devez spécifier une adresse de point de terminaison et d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="e7cde-104">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="e7cde-105">L’adresse de point de terminaison doit contenir un URI de connexion Oracle E-Business Suite valide, et la liaison doit être une instance d’une liaison d’Oracle E-Business Suite (**OracleEBSBinding**).</span><span class="sxs-lookup"><span data-stu-id="e7cde-105">The endpoint address must contain a valid Oracle E-Business Suite connection URI, and the binding must be an instance of an Oracle E-Business Suite binding (**OracleEBSBinding**).</span></span> <span data-ttu-id="e7cde-106">Pour plus d’informations sur l’URI de connexion Oracle E-Business Suite, consultez [créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="e7cde-106">For more information about the Oracle E-Business Suite connection URI, see [Create a Connection to the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).</span></span> <span data-ttu-id="e7cde-107">Nous recommandons que vous ne spécifiez pas les informations d’identification de l’utilisateur dans le cadre de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="e7cde-107">We recommend that you do not specify the user credentials as part of the connection URI.</span></span> <span data-ttu-id="e7cde-108">Vous pouvez utiliser à la place la **ClientCredentials** propriété du client WCF, comme expliqué dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e7cde-108">You may instead use the **ClientCredentials** property of the WCF client, as explained in this topic.</span></span>  
  
 <span data-ttu-id="e7cde-109">Vous pouvez spécifier l’adresse de point de terminaison et de la liaison d’Oracle E-Business Suite dans votre code ou dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e7cde-109">You can specify the Oracle E-Business Suite binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="e7cde-110">Lorsque vous utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer la classe de client WCF, un fichier de configuration (app.config) est également créé pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="e7cde-110">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="e7cde-111">Ce fichier contient les paramètres de configuration qui reflètent les propriétés et connexion informations de liaison (à l’exception des informations d’identification) que vous avez spécifié lorsque vous connecté à Oracle E-Business Suite avec le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7cde-111">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Oracle E-Business Suite with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="e7cde-112">Spécification de la liaison et l’adresse de point de terminaison dans le Code</span><span class="sxs-lookup"><span data-stu-id="e7cde-112">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="e7cde-113">Le code suivant montre comment créer un client WCF en spécifiant l’adresse de liaison et le point de terminaison dans le code à l’aide du **ClientCredentials** propriété du client WCF.</span><span class="sxs-lookup"><span data-stu-id="e7cde-113">The following code shows how to create a WCF client by specifying the binding and endpoint address in code using the **ClientCredentials** property of the WCF client.</span></span>  
  
```  
//Create an Oracle EBS binding and set the binding properties  
OracleEBSBinding binding = new OracleEBSBinding();  
binding.OracleUserName = "myOracleEBSUser";  
binding.OraclePassword = "myOracleEBSPassword";  
binding.OracleEBSResponsibilityName = "Responsibility";  
binding.OracleEBSOrganizationId = "204";  
  
//Create the client endpoint   
EndpointAddress address = new EndpointAddress("oracleebs://<oracleebs_instance_name>/");  
  
//Create the client and specify the credentials  
ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient(binding,address);  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
//Open the client  
client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="e7cde-114">Spécification de la liaison et l’adresse de point de terminaison dans un fichier de Configuration</span><span class="sxs-lookup"><span data-stu-id="e7cde-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="e7cde-115">Le code suivant montre comment créer un client WCF en spécifiant la liaison et l’adresse de point de terminaison dans un fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="e7cde-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
//Create the client by specifying the endpoint name in the app.config. In this case, the binding properties  
//must also be specified in the app.config.  
ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR");  
  
//Specify the credentials   
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
client.Open();  
```  
  
 <span data-ttu-id="e7cde-116">Le code XML suivant montre le fichier de configuration créé pour le **Interface client** simultanées du programme par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7cde-116">The following XML shows the configuration file created for the **Customer Interface** concurrent program by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="e7cde-117">Ce fichier contient la configuration du point de terminaison client référencée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="e7cde-117">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
        <bindings>  
            <oracleEBSBinding>  
                <binding openTimeout="00:05:00" name="OracleEBSBinding" closeTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" clientCredentialType="Database"  
                    inboundOperationType="Polling" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" pollWhileDataFound="false" pollingInterval="30"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" notifyOnListenerStart="true"  
                    notificationPort="-1" dataFetchSize="65536" longDatatypeColumnSize="32512"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="20" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="true">  
                    <mlsSettings language="" dateFormat="" dateLanguage="" numericCharacters=""  
                        sort="" territory="" comparison="" currency="" dualCurrency=""  
                        iSOCurrency="" calendar="" lengthSemantics="" nCharConversionException="true"  
                        timeStampFormat="" timeStampTZFormat="" timeZone="" />  
                </binding>  
            </oracleEBSBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracleebs://ebs-70-12/" binding="oracleEBSBinding"  
                bindingConfiguration="OracleEBSBinding" contract="ConcurrentPrograms_AR"  
                name="OracleEBSBinding_ConcurrentPrograms_AR" />  
        </client>  
    \</system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e7cde-118">Si un projet a plus d’un client WCF, il y aura plusieurs entrées de point de terminaison définies dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e7cde-118">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="e7cde-119">Chaque entrée de client WCF a un nom unique en fonction de sa configuration de liaison et d’un artefact d’Oracle E-Business Suite cible.</span><span class="sxs-lookup"><span data-stu-id="e7cde-119">Each WCF client entry will have a unique name based on its binding configuration and target Oracle E-Business Suite artifact.</span></span> <span data-ttu-id="e7cde-120">Si vous vous connectez plusieurs fois pour créer les clients WCF dans votre projet, plusieurs entrées de configuration de liaison sont créés, un pour chaque connexion.</span><span class="sxs-lookup"><span data-stu-id="e7cde-120">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="e7cde-121">Ces entrées de configuration de liaison seront nommées de la manière suivante : OracleEBSBinding, OracleEBSBinding1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e7cde-121">These binding configuration entries will be named in the following manner: OracleEBSBinding, OracleEBSBinding1, and so on.</span></span> <span data-ttu-id="e7cde-122">Chaque entrée de point de terminaison de client créée lors d’une connexion spécifique fait référence à l’entrée de liaison créée au cours de cette connexion.</span><span class="sxs-lookup"><span data-stu-id="e7cde-122">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cde-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cde-123">See Also</span></span>  
 [<span data-ttu-id="e7cde-124">Développer des Applications de Suite Oracle E-Business à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="e7cde-124">Develop Oracle E-Business Suite Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)