---
title: "Vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aeeac8a4-a4bc-4963-951c-0c806e232f1e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40b22865ca45cbd10823f6c514f75e5965f1df5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="941cc-102">Vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="941cc-102">Overview of the WCF service model with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="941cc-103">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose un système Oracle E-Business Suite comme service WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes an Oracle E-Business Suite system as a WCF service.</span></span> <span data-ttu-id="941cc-104">Pour effectuer des opérations sur les artefacts d’Oracle E-Business Suite, par exemple, pour appeler une procédure stockée, vous appelez une opération sur la carte, qui, à son tour, exécute l’opération sur Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-104">To perform operations on Oracle E-Business Suite artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the Oracle E-Business Suite.</span></span> <span data-ttu-id="941cc-105">Votre code agit comme un client au service WCF présenté par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="941cc-105">Your code acts as a client to the WCF service presented by the adapter.</span></span>  
  
 <span data-ttu-id="941cc-106">Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface.</span><span class="sxs-lookup"><span data-stu-id="941cc-106">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="941cc-107">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="941cc-107">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="941cc-108">Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service.</span><span class="sxs-lookup"><span data-stu-id="941cc-108">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="941cc-109">Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="941cc-109">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span>  
  
 <span data-ttu-id="941cc-110">La section suivante explique comment utiliser le modèle de service WCF pour appeler des opérations avec un client WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-110">The following section explains how to use the WCF service model to invoke operations with a WCF client.</span></span>  
  
## <a name="invoking-operations-on-the-oracle-e-business-suite-with-a-wcf-client"></a><span data-ttu-id="941cc-111">Appel d’opérations sur Oracle E-Business Suite avec un Client WCF</span><span class="sxs-lookup"><span data-stu-id="941cc-111">Invoking Operations on the Oracle E-Business Suite with a WCF Client</span></span>  
 <span data-ttu-id="941cc-112">Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="941cc-112">To use the WCF service model to invoke operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="941cc-113">Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer ces opérations sur Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-113">You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the Oracle E-Business Suite.</span></span>  
  
#### <a name="to-invoke-operations-on-the-oracle-e-business-adapter"></a><span data-ttu-id="941cc-114">Pour appeler des opérations sur l’adaptateur Oracle E-Business</span><span class="sxs-lookup"><span data-stu-id="941cc-114">To invoke operations on the Oracle E-Business adapter</span></span>  
  
1.  <span data-ttu-id="941cc-115">Générer un code de classe et d’assistance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-115">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="941cc-116">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts d’Oracle E-Business Suite avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="941cc-116">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at Oracle E-Business Suite artifacts with which you want to work.</span></span> <span data-ttu-id="941cc-117">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="941cc-117">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="941cc-118">Créer une instance de client WCF et configurer le client WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-118">Create a WCF client instance and configure the WCF client.</span></span> <span data-ttu-id="941cc-119">Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison (URI de connexion) utilisé par le client.</span><span class="sxs-lookup"><span data-stu-id="941cc-119">Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use.</span></span> <span data-ttu-id="941cc-120">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="941cc-120">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="941cc-121">Le code suivant crée un client WCF qui cible le **Interface client** simultanées du programme dans le **des comptes clients** application dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-121">The following code creates a WCF client that targets the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span> <span data-ttu-id="941cc-122">Il définit également les informations d’identification pour Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-122">It also sets the credentials for the Oracle E-Business Suite.</span></span> <span data-ttu-id="941cc-123">Le client WCF est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="941cc-123">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR"); //picking the binding and address from app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="941cc-124">Vous pouvez spécifier l’adresse de liaison et le point de terminaison client dans le code ou déclarer dans le fichier de configuration app.config.</span><span class="sxs-lookup"><span data-stu-id="941cc-124">You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file.</span></span> <span data-ttu-id="941cc-125">L’extrait de code précédent utilise ce dernier.</span><span class="sxs-lookup"><span data-stu-id="941cc-125">The preceding code snippet uses the latter.</span></span> <span data-ttu-id="941cc-126">Pour plus d’informations sur l’utilisation des deux approches, consultez [configurer une liaison de Client d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="941cc-126">For more information on how to use either approaches, see [Configure a Client Binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
3.  <span data-ttu-id="941cc-127">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-127">Open the WCF client.</span></span>  
  
    ```  
    client.Open();  
    ```  
  
4.  <span data-ttu-id="941cc-128">Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-128">Invoke methods on the WCF client created in step 2 to perform operations on the Oracle E-Business Suite.</span></span> <span data-ttu-id="941cc-129">Le code suivant appelle la **Interface client** simultanées du programme dans le **des comptes clients** application dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="941cc-129">The following code invokes the **Customer Interface** concurrent program in the **Receivables** application in the Oracle E-Business Suite.</span></span>  
  
    ```  
    string Result = client.RACUST(null, null, null, description, null, recipro_cust, org_id);  
    ```  
  
     <span data-ttu-id="941cc-130">**RACUST** est le nom réel du programme client Interface simultané.</span><span class="sxs-lookup"><span data-stu-id="941cc-130">**RACUST** is the actual name of the Customer Interface concurrent program.</span></span> <span data-ttu-id="941cc-131">**Interface client** est le nom convivial du programme simultané.</span><span class="sxs-lookup"><span data-stu-id="941cc-131">**Customer Interface** is the friendly name of the concurrent program.</span></span>  
  
5.  <span data-ttu-id="941cc-132">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="941cc-132">Close the WCF client.</span></span>  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="941cc-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="941cc-133">See Also</span></span>  
 [<span data-ttu-id="941cc-134">Développer à l’aide du modèle de canal WCF les Applications Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="941cc-134">Develop Oracle E-Business Suite Applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)