---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke operations on the Siebel system with a WCF client
- WCF service model, overview of
ms.assetid: 0e812473-0f50-4972-8b07-ec8edc2ef000
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c638255b103a9c588f22d6ddcb2a75b81619b73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-siebel-adapter"></a><span data-ttu-id="fcc6d-102">Vue d’ensemble du modèle de service WCF avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="fcc6d-102">Overview of the WCF service model with the Siebel adapter</span></span>
<span data-ttu-id="fcc6d-103">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose un système Siebel comme service WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes a Siebel system as a WCF service.</span></span> <span data-ttu-id="fcc6d-104">Pour effectuer des opérations sur les artefacts du système Siebel, par exemple, pour appeler une méthode d’un service d’entreprise Siebel, vous appelez une opération sur la carte, qui, à son tour, exécute l’opération sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-104">To perform operations on Siebel system artifacts, for example to invoke a method of a Siebel business service, you invoke an operation on the adapter, which, in turn, performs the operation on the Siebel system.</span></span> <span data-ttu-id="fcc6d-105">Votre code est par conséquent agit comme un client au service WCF présenté par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-105">Your code therefore acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="fcc6d-106">Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="fcc6d-107">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="fcc6d-108">Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="fcc6d-109">Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span>  
  
 <span data-ttu-id="fcc6d-110">La section suivante explique comment utiliser le modèle de service WCF pour appeler des opérations avec un client WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-110">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-siebel-system-with-a-wcf-client"></a><span data-ttu-id="fcc6d-111">Appel d’opérations sur le système Siebel avec un Client WCF</span><span class="sxs-lookup"><span data-stu-id="fcc6d-111">Invoking Operations on the Siebel System with a WCF Client</span></span>  
 <span data-ttu-id="fcc6d-112">Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-112">To use the WCF service model to invoke operations on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="fcc6d-113">Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer ces opérations sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-113">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Siebel system.</span></span>  
  
#### <a name="to-invoke-operations-on-the-siebel-adapter"></a><span data-ttu-id="fcc6d-114">Pour appeler des opérations sur l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="fcc6d-114">To invoke operations on the Siebel adapter</span></span>  
  
1.  <span data-ttu-id="fcc6d-115">Générer un code de classe et d’assistance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-115">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="fcc6d-116">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts du système Siebel avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-116">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the Siebel system artifacts with which you want to work.</span></span> <span data-ttu-id="fcc6d-117">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de service WCF pour les artefacts de Solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="fcc6d-117">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF service contract for Siebel Solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="fcc6d-118">Créer une instance de client WCF et configurer le client WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-118">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="fcc6d-119">Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison (URI de connexion) utilisé par le client.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-119">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="fcc6d-120">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-120">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="fcc6d-121">Pour plus d’informations sur la façon de configurer le client WCF, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).</span><span class="sxs-lookup"><span data-stu-id="fcc6d-121">For more information about how to configure the WCF client, see [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).</span></span> <span data-ttu-id="fcc6d-122">Le code suivant crée un client WCF qui cible le service d’entreprise Siebel TimeStamp.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-122">The following code creates a WCF client that targets the Siebel TimeStamp business service.</span></span> <span data-ttu-id="fcc6d-123">Il définit également les informations d’identification pour le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-123">It also sets the credentials for the Siebel system.</span></span> <span data-ttu-id="fcc6d-124">Le client WCF est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-124">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    BusinessServices_TimeStamp_OperationClient client =  
        new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
    client.ClientCredentials.UserName.UserName = "YourUserName";  
    client.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="fcc6d-125">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-125">Open the WCF client.</span></span>  
  
    ```  
    client.Open();  
    ```  
  
4.  <span data-ttu-id="fcc6d-126">Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-126">Invoke methods on the WCF client created in step 2 to perform operations on the Siebel system.</span></span> <span data-ttu-id="fcc6d-127">Le code suivant appelle la **Execute** méthode du client WCF pour appeler le **Execute** méthode du service métier TimeStamp sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-127">The following code invokes the **Execute** method of the WCF client to invoke the **Execute** method of the TimeStamp business service on the Siebel system.</span></span>  
  
    ```  
    // Create a parameter to hold the results and then invoke the Execute method of the TimeStamp business service.  
    microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp.ExecuteResponseRecord er;  
    er = client.Execute();  
    ```  
  
5.  <span data-ttu-id="fcc6d-128">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="fcc6d-128">Close the WCF client.</span></span>  
  
    ```  
    client.Close();  
    ```  
  
 <span data-ttu-id="fcc6d-129">Pour plus d’informations sur l’appel des méthodes de service d’entreprise Siebel, consultez [appeler des méthodes de Service métier avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)</span><span class="sxs-lookup"><span data-stu-id="fcc6d-129">For more information about invoking Siebel business service methods, see [Invoke Business Service Methods with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="fcc6d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcc6d-130">See Also</span></span>  
 [<span data-ttu-id="fcc6d-131">Développer des Applications Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="fcc6d-131">Develop Siebel Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)