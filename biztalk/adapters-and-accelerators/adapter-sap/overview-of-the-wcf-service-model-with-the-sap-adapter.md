---
title: Vue d’ensemble du modèle de service WCF avec l’adaptateur SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, overview of using
ms.assetid: 02a4b43e-ade0-4dba-b8f6-074bca7cbe5c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da5b2f7cc8e38eb8afd211a2008c0f740760cd4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-sap-adapter"></a><span data-ttu-id="21e5e-102">Vue d’ensemble du modèle de service WCF avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="21e5e-102">Overview of the WCF service model with the SAP adapter</span></span>
<span data-ttu-id="21e5e-103">Lorsque vous consommez des opérations qui les [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces, votre code agit comme un client ou un service à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="21e5e-103">When you consume operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces, your code acts either as a client or a service to the adapter.</span></span>  
  
 <span data-ttu-id="21e5e-104">Votre code agit comme un client pour appeler les types d’opérations sur le système SAP suivants :</span><span class="sxs-lookup"><span data-stu-id="21e5e-104">Your code acts as a client to invoke the following kinds of operations on the SAP system:</span></span>  
  
-   <span data-ttu-id="21e5e-105">Appeler un appel de fonction distant (RFC).</span><span class="sxs-lookup"><span data-stu-id="21e5e-105">Invoke a Remote Function Call (RFC).</span></span>  
  
-   <span data-ttu-id="21e5e-106">Appeler un transactionnelle distante appel de fonction (tRFC).</span><span class="sxs-lookup"><span data-stu-id="21e5e-106">Invoke a Transactional Remote Function Call (tRFC).</span></span>  
  
-   <span data-ttu-id="21e5e-107">Appeler une Application Programming Interface (BAPI).</span><span class="sxs-lookup"><span data-stu-id="21e5e-107">Invoke a Business Application Programming Interface (BAPI).</span></span>  
  
-   <span data-ttu-id="21e5e-108">Envoyer un Document intermédiaire (IDOC)</span><span class="sxs-lookup"><span data-stu-id="21e5e-108">Send an Intermediate Document (IDOC)</span></span>  
  
 <span data-ttu-id="21e5e-109">Votre code fonctionne comme un service à recevoir les types d’opérations suivants :</span><span class="sxs-lookup"><span data-stu-id="21e5e-109">Your code acts as a service to receive the following kinds of operations:</span></span>  
  
-   <span data-ttu-id="21e5e-110">Réception d’une demande de changement (serveur RFC)</span><span class="sxs-lookup"><span data-stu-id="21e5e-110">Receive an RFC (RFC server)</span></span>  
  
-   <span data-ttu-id="21e5e-111">Réception d’un tRFC (tRFC server)</span><span class="sxs-lookup"><span data-stu-id="21e5e-111">Receive a tRFC (tRFC server)</span></span>  
  
-   <span data-ttu-id="21e5e-112">Recevoir un IDOC.</span><span class="sxs-lookup"><span data-stu-id="21e5e-112">Receive an IDOC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21e5e-113">Étant donné que les interfaces BAPI sont des méthodes exposées par le système SAP sur des objets métier situé dans le référentiel d’objet métier (BOR), vous ne recevez pas BAPI.</span><span class="sxs-lookup"><span data-stu-id="21e5e-113">Because BAPIs are methods exposed by the SAP system on business objects located in the Business Object Repository (BOR), you cannot receive BAPIs.</span></span>  
  
 <span data-ttu-id="21e5e-114">Dans la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le contrat de service qui existe entre un client et un service est représenté sous la forme d’une interface .NET et les opérations sont représentées en tant que méthodes sur cette interface.</span><span class="sxs-lookup"><span data-stu-id="21e5e-114">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="21e5e-115">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et WCF fournissent des outils qui vous permettent de générer cette interface pour les opérations ciblées à partir des métadonnées qui expose de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="21e5e-115">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="21e5e-116">Ces outils créent également une classe de client WCF qui peut être utilisée pour appeler les opérations exposées dans l’interface de service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-116">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="21e5e-117">Une application cliente peut appeler les méthodes de la classe de client WCF pour appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="21e5e-117">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span> <span data-ttu-id="21e5e-118">Pour implémenter un service pour recevoir des opérations à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous implémentez l’interface générée pour l’opération de la cible.</span><span class="sxs-lookup"><span data-stu-id="21e5e-118">To implement a service to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you implement the interface generated for the target operation.</span></span>  
  
 <span data-ttu-id="21e5e-119">Les sections suivantes expliquent comment utiliser le modèle de service WCF pour créer un code client et le service pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21e5e-119">The following sections explain how to use the WCF service model to create client and service code for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="creating-a-wcf-client-and-invoking-operations-on-sap"></a><span data-ttu-id="21e5e-120">Création d’un Client WCF et d’appeler des opérations sur SAP</span><span class="sxs-lookup"><span data-stu-id="21e5e-120">Creating a WCF Client and Invoking Operations on SAP</span></span>  
 <span data-ttu-id="21e5e-121">Pour utiliser le modèle de service WCF pour appeler des opérations sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez commencer par générer une classe de client WCF pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="21e5e-121">To use the WCF service model to invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="21e5e-122">Vous pouvez ensuite créer une instance de cette classe, un client WCF et appeler ses méthodes pour effectuer des opérations sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="21e5e-122">You can then create an instance of this class, a WCF client, and call its methods to perform operations on the SAP system.</span></span>  
  
#### <a name="to-invoke-operations-on-the-sap-adapter"></a><span data-ttu-id="21e5e-123">Pour appeler des opérations sur l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="21e5e-123">To invoke operations on the SAP adapter</span></span>  
  
1.  <span data-ttu-id="21e5e-124">Générer un code de classe et d’assistance de client WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-124">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="21e5e-125">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ciblée sur les artefacts du système SAP avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="21e5e-125">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the SAP system artifacts with which you want to work.</span></span> <span data-ttu-id="21e5e-126">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="21e5e-126">For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="21e5e-127">Créez une instance du client WCF en spécifiant une liaison de client.</span><span class="sxs-lookup"><span data-stu-id="21e5e-127">Create a WCF client instance by specifying a client binding.</span></span> <span data-ttu-id="21e5e-128">Spécification d’une liaison de client implique la spécification de la liaison et l’adresse de point de terminaison utilisé par le client WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-128">Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use.</span></span> <span data-ttu-id="21e5e-129">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="21e5e-129">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="21e5e-130">Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer un client de liaison pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="21e5e-130">For more information about how to specify a client binding, see [Configure a client binding for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="21e5e-131">Le code suivant crée un client WCF qui peut être utilisé pour appeler une commande RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="21e5e-131">The following code creates a WCF client that can be used to invoke an RFC on the SAP system.</span></span> <span data-ttu-id="21e5e-132">Il définit également les informations d’identification pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="21e5e-132">It also sets the credentials for the SAP system.</span></span> <span data-ttu-id="21e5e-133">Le client WCF est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="21e5e-133">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="21e5e-134">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-134">Open the WCF client.</span></span>  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  <span data-ttu-id="21e5e-135">Appeler des méthodes sur le client WCF créé à l’étape 2 pour effectuer des opérations sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="21e5e-135">Invoke methods on the WCF client created in step 2 to perform operations on the SAP system.</span></span> <span data-ttu-id="21e5e-136">Le code suivant appelle la **SD_RFC_CUSTOMER_GET** méthode du client WCF pour appeler le RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="21e5e-136">The following code invokes the **SD_RFC_CUSTOMER_GET** method of the WCF client to invoke the RFC on the SAP system.</span></span>  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  <span data-ttu-id="21e5e-137">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-137">Close the WCF client.</span></span>  
  
    ```  
    rfcClient.Close();  
  
    ```  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-sap-adapter"></a><span data-ttu-id="21e5e-138">Création et implémentation d’un Service WCF à l’aide de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="21e5e-138">Creating and Implementing a WCF Service by Using the SAP Adapter</span></span>  
 <span data-ttu-id="21e5e-139">Pour utiliser le modèle de service WCF pour recevoir des opérations à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez commencer par générer l’interface .NET (également appelé le contrat de service WCF) qui représente le contrat de service exposé par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="21e5e-139">To use the WCF service model to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate the .NET interface (also called the WCF service contract) that represents the service contract exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the operation.</span></span> <span data-ttu-id="21e5e-140">Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="21e5e-140">For more information about how to do this, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="21e5e-141">Ensuite, vous implémentez un service WCF en implémentant l’interface générée.</span><span class="sxs-lookup"><span data-stu-id="21e5e-141">You then implement a WCF service by implementing the generated interface.</span></span> <span data-ttu-id="21e5e-142">Cette classe contient la logique métier pour traiter l’opération et renvoie une réponse à la carte.</span><span class="sxs-lookup"><span data-stu-id="21e5e-142">This class contains the business logic to process the operation and return a response to the adapter.</span></span> <span data-ttu-id="21e5e-143">Puis vous utilisez un hôte de service (**System.ServiceModel.ServiceHost**) pour héberger une instance de ce service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-143">Then you use a service host (**System.ServiceModel.ServiceHost**) to host an instance of this service.</span></span>  
  
#### <a name="to-create-and-implement-a-wcf-service"></a><span data-ttu-id="21e5e-144">Pour créer et implémenter un service WCF</span><span class="sxs-lookup"><span data-stu-id="21e5e-144">To create and implement a WCF service</span></span>  
  
1.  <span data-ttu-id="21e5e-145">Générer une classe de contrat et d’assistance de service WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-145">Generate a WCF service contract and helper classes.</span></span> <span data-ttu-id="21e5e-146">Utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou svcutil.exe pour générer un contrat de service WCF (interface) ciblé sur les artefacts du système SAP avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="21e5e-146">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) targeted at the SAP system artifacts with which you want to work.</span></span> <span data-ttu-id="21e5e-147">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="21e5e-147">For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="21e5e-148">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="21e5e-148">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="21e5e-149">Si une erreur s’est produite le traitement des données pour l’opération, la méthode qui gère cette opération peut lever une exception pour retourner une erreur sur le système SAP. dans le cas contraire, la méthode doit retourner une instance de la classe de la réponse (généré) appropriée pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="21e5e-149">If an error is encountered processing the data for the operation, the method that handles that operation can throw an exception to return a fault to the SAP system; otherwise the method must return an instance of the appropriate (generated) response class for the operation.</span></span> <span data-ttu-id="21e5e-150">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="21e5e-150">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  <span data-ttu-id="21e5e-151">Si vous avez utilisé le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer l’interface, vous pouvez implémenter votre logique directement dans la méthode appropriée dans le texte généré **SAPBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="21e5e-151">If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the appropriate method in the generated **SAPBindingService** class.</span></span> <span data-ttu-id="21e5e-152">Cette classe peut être trouvée dans SAPBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="21e5e-152">This class can be found in SAPBindingService.cs.</span></span> <span data-ttu-id="21e5e-153">Le code suivant sous-classes le **SAPBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="21e5e-153">The following code sub-classes the **SAPBindingService** class.</span></span>  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
        class RfcServerClass : SAPBindingNamespace.SAPBindingService  
        {  
            public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
            {  
                // If either parameter is null throw an exception   
                if (request.X == null || request.Y == null)  
                    throw new System.ArgumentNullException();  
  
                // Add the two operands  
                int result = (int) (request.X + request.Y);  
  
                return new Z_RFC_MKD_ADDResponse(result);  
            }  
        }  
        ```  
  
    2.  <span data-ttu-id="21e5e-154">Si vous utilisez svcutil.exe pour générer l’interface, vous devez créer une classe qui implémente l’interface et implémenter votre logique dans l’appropriatemethod de cette classe.</span><span class="sxs-lookup"><span data-stu-id="21e5e-154">If you used svcutil.exe to generate the interface, you must create a class that implements the interface and implement your logic in the appropriatemethod of this class.</span></span>  
  
3.  <span data-ttu-id="21e5e-155">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="21e5e-155">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    RfcServerClass rfcServerInstance = new RfcServerClass();  
    ```  
  
4.  <span data-ttu-id="21e5e-156">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="21e5e-156">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="21e5e-157">L’URI de la connexion de base ne peut pas contenir userinfoparams ou un query_string.</span><span class="sxs-lookup"><span data-stu-id="21e5e-157">The base connection URI cannot contain userinfoparams or a query_string.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("sap://a/YourSAPHost/00") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  <span data-ttu-id="21e5e-158">Créer un **SAPBinding** et le configurer pour l’opération en définissant ses propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="21e5e-158">Create an **SAPBinding** and configure it for the operation by setting its binding properties.</span></span> <span data-ttu-id="21e5e-159">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="21e5e-159">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="21e5e-160">Au minimum, vous devez définir **AcceptCredentialsInUri** à **true**.</span><span class="sxs-lookup"><span data-stu-id="21e5e-160">At a minimum, you must set **AcceptCredentialsInUri** to **true**.</span></span>  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    SAPBinding binding = new SAPBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
6.  <span data-ttu-id="21e5e-161">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-161">Add a service endpoint to the service host.</span></span> <span data-ttu-id="21e5e-162">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="21e5e-162">To do this:</span></span>  
  
    -   <span data-ttu-id="21e5e-163">Utilisez la liaison créée à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="21e5e-163">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="21e5e-164">Spécifiez une URI qui contient des informations d’identification et spécifie une connexion de port d’écoute de la connexion (SAP de passerelle, le service de passerelle et l’ID de programme) dans query_string.</span><span class="sxs-lookup"><span data-stu-id="21e5e-164">Specify a connection URI that contains credentials and specifies a listener connection (SAP gateway, gateway service and program ID) in the query_string.</span></span> <span data-ttu-id="21e5e-165">Pour plus d’informations sur l’URI de connexion SAP, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="21e5e-165">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    -   <span data-ttu-id="21e5e-166">Spécifiez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-166">Specify the service contract.</span></span> <span data-ttu-id="21e5e-167">Il s’agit du nom de l’interface qui représente le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="21e5e-167">This is the name of the interface that represents the WCF service contract.</span></span> <span data-ttu-id="21e5e-168">Pour les RFC, il est « Rfc ».</span><span class="sxs-lookup"><span data-stu-id="21e5e-168">For RFCs, it is "Rfc".</span></span>  
  
    ```  
    // Add service endpoint   
    // NOTE: The contract for the service endpoint is "Rfc".  
    //       This is the generated WCF service contract (interface) -- see SAPBindingInterface.cs.  
    Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGW00&ListenerGwHost=YourSapHost&ListenerProgramId=SAPAdapter");  
    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
    ```  
  
7.  <span data-ttu-id="21e5e-169">Pour l’opération de réception à partir du système SAP, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-169">To receive the operation from the SAP system, open the service host.</span></span> <span data-ttu-id="21e5e-170">Votre service WCF est appelé chaque fois que le système SAP appelle l’opération sur l’ID de programme et le système spécifié dans l’URI de service à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="21e5e-170">Your WCF service will be invoked whenever the SAP system invokes the operation on the program ID and system specified in the service URI in step 6.</span></span>  
  
    ```  
    // Open the service host to begin receiving the operation.  
    srvHost.Open();  
    ```  
  
8.  <span data-ttu-id="21e5e-171">Pour arrêter la réception de l’opération, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="21e5e-171">To stop receiving the operation, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="21e5e-172">L’adaptateur continue de recevoir l’opération jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="21e5e-172">The adapter will continue to receive the operation until the service host is closed.</span></span> <span data-ttu-id="21e5e-173">Vous devez toujours fermer l’hôte de service lorsque vous ne souhaitez plus recevoir de l’opération.</span><span class="sxs-lookup"><span data-stu-id="21e5e-173">You should always close the service host when you no longer want to receive the operation.</span></span>  
  
    ```  
    srvHost.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="21e5e-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21e5e-174">See Also</span></span>  
[<span data-ttu-id="21e5e-175">Développer des applications SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="21e5e-175">Develop SAP applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)