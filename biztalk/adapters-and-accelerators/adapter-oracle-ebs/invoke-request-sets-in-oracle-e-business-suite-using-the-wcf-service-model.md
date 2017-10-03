---
title: "Appeler des ensembles de requêtes dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb6ec551-c069-4133-add5-2ba83d20405d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b01765cc47b0d8eafffcf30160ce9ee6c840003d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="d33c3-102">Appeler des ensembles de requêtes dans Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="d33c3-102">Invoke request sets in Oracle E-Business Suite using the WCF service model</span></span>
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="d33c3-103">vous permet d’exécuter la demande définit dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="d33c3-103"> enables you to execute request sets in Oracle E-Business Suite.</span></span> <span data-ttu-id="d33c3-104">Demander des jeux sont divisées en une ou plusieurs étapes, et chaque étape contient un ensemble de rapports et des programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="d33c3-104">Request sets are divided into one or more stages, and each stage contains a set of reports and concurrent programs.</span></span> <span data-ttu-id="d33c3-105">Pour plus d’informations sur comment l’adaptateur prend en charge les ensembles de requêtes, consultez [opérations sur demande définit](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d33c3-105">For more information about how the adapter supports request sets, see [Operations on Request Sets](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="d33c3-106">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="d33c3-106">The WCF Client Class</span></span>  
 <span data-ttu-id="d33c3-107">Le nom du client WCF généré pour l’appel de la demande définit le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d33c3-107">The name of the WCF client generated for invoking the request sets by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="d33c3-108">Artefact</span><span class="sxs-lookup"><span data-stu-id="d33c3-108">Artifact</span></span>|<span data-ttu-id="d33c3-109">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="d33c3-109">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="d33c3-110">Ensemble de la demande</span><span class="sxs-lookup"><span data-stu-id="d33c3-110">Request Set</span></span>|<span data-ttu-id="d33c3-111">Client de RequestSets_ [nom_application]</span><span class="sxs-lookup"><span data-stu-id="d33c3-111">RequestSets_[APP_NAME]Client</span></span>|  
  
 <span data-ttu-id="d33c3-112">[Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, SQLAP.</span><span class="sxs-lookup"><span data-stu-id="d33c3-112">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, SQLAP.</span></span>  
  
### <a name="method-signature-for-invoking-request-sets"></a><span data-ttu-id="d33c3-113">Signature de méthode pour appeler des ensembles de requêtes</span><span class="sxs-lookup"><span data-stu-id="d33c3-113">Method Signature for Invoking Request Sets</span></span>  
 <span data-ttu-id="d33c3-114">Le tableau suivant montre la signature de méthode pour les ensembles de requêtes.</span><span class="sxs-lookup"><span data-stu-id="d33c3-114">The following table shows the method signature for request sets.</span></span>  
  
|<span data-ttu-id="d33c3-115">Opération</span><span class="sxs-lookup"><span data-stu-id="d33c3-115">Operation</span></span>|<span data-ttu-id="d33c3-116">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="d33c3-116">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="d33c3-117">Ensemble de la demande</span><span class="sxs-lookup"><span data-stu-id="d33c3-117">Request Set</span></span>|<span data-ttu-id="d33c3-118">public \<type de retour > \<demande nommez > (param 1, param 2,...)</span><span class="sxs-lookup"><span data-stu-id="d33c3-118">public \<return type> \<request set name>(param 1, param 2, …)</span></span>|  
  
 <span data-ttu-id="d33c3-119">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **reqset_singlestage** demander ensemble.</span><span class="sxs-lookup"><span data-stu-id="d33c3-119">As an example, the following code shows the method signatures for a WCF client class generated for the **reqset_singlestage** request set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d33c3-120">Ceci est un ensemble personnalisé de demande et ne peut-être pas être disponible sur votre instance Oracle E-Business Solution.</span><span class="sxs-lookup"><span data-stu-id="d33c3-120">This is a custom request set and might not be available on your Oracle E-Business Solution instance.</span></span>  
  
```  
public partial class RequestSets_SQLAPClient : System.ServiceModel.ClientBase<RequestSets_SQLAP>, RequestSets_SQLAP{      
  
    public string REQSTG(  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRelClassOptions SetRelClassOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,   
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,   
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetNlsOptions SetNlsOptions,  
      string StartTime,  
      schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1 set1_set1);  
}  
```  
  
 <span data-ttu-id="d33c3-121">Dans cet extrait de code, **RequestSets_SQLAPClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d33c3-121">In this snippet, **RequestSets_SQLAPClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="d33c3-122">**REQSTG** est le nom de la méthode à appeler l’ensemble de la demande.</span><span class="sxs-lookup"><span data-stu-id="d33c3-122">**REQSTG** is the name of the method to invoke the request set.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-request-sets"></a><span data-ttu-id="d33c3-123">Création d’un Client WCF pour appeler des ensembles de requêtes</span><span class="sxs-lookup"><span data-stu-id="d33c3-123">Creating a WCF Client to Invoke Request Sets</span></span>  
 <span data-ttu-id="d33c3-124">L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="d33c3-124">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="d33c3-125">Cette section décrit comment créer un client WCF pour appeler le **reqset_singlestage** demander ensemble.</span><span class="sxs-lookup"><span data-stu-id="d33c3-125">This section describes how to create a WCF client to invoke the **reqset_singlestage** request set.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="d33c3-126">Pour créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="d33c3-126">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="d33c3-127">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d33c3-127">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="d33c3-128">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="d33c3-128">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="d33c3-129">Générer la classe de client WCF pour le **reqset_singlestage** demander ensemble.</span><span class="sxs-lookup"><span data-stu-id="d33c3-129">Generate the WCF client class for the **reqset_singlestage** request set.</span></span> <span data-ttu-id="d33c3-130">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="d33c3-130">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d33c3-131">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="d33c3-131">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="d33c3-132">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="d33c3-132">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="d33c3-133">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="d33c3-133">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="d33c3-134">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d33c3-134">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    RequestSets_SQLAPClient client = new RequestSets_SQLAPClient(binding, address);  
    ```  
  
     <span data-ttu-id="d33c3-135">Dans cet extrait de code, `RequestSets_SQLAPClient` est le client WCF défini dans OracleEBSBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="d33c3-135">In this snippet, `RequestSets_SQLAPClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="d33c3-136">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d33c3-136">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d33c3-137">Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application.</span><span class="sxs-lookup"><span data-stu-id="d33c3-137">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="d33c3-138">Vous pouvez également utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d33c3-138">You can also use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="d33c3-139">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="d33c3-139">For more information about the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="d33c3-140">Définir les informations d’identification pour le client.</span><span class="sxs-lookup"><span data-stu-id="d33c3-140">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="d33c3-141">Étant donné que vous appelez demande définit dans une application Oracle E-Business Suite, vous devez définir le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="d33c3-141">Because you are invoking request sets in an Oracle E-Business Suite application, you must set the application context.</span></span> <span data-ttu-id="d33c3-142">Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="d33c3-142">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="d33c3-143">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="d33c3-143">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="d33c3-144">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d33c3-144">Open the client as described in the snippet below:</span></span>  
  
    ```  
    try  
    {  
       Console.WriteLine("Opening Client...");  
       client.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    ```  
  
9. <span data-ttu-id="d33c3-145">Appeler le **reqset_singlestage** demander ensemble.</span><span class="sxs-lookup"><span data-stu-id="d33c3-145">Invoke the **reqset_singlestage** request set.</span></span>  
  
    ```  
    string RequestID;  
  
    schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1 param =  
        new schemas.microsoft.com.OracleEBS._2008._05.RequestSetStage.SQLAP.REQSTG.set1();  
  
    param.INSPARAMPROG = new schemas.microsoft.com.OracleEBS._2008._05.RequestSetConcurrentProgram.SQLAP.REQSTG.set1.SQLAP1.INSPARAMPROG();  
    param.INSPARAMPROG.p_id = "123";  
    param.INSPARAMPROG.p_name = "MyName";  
  
    try  
    {  
        Console.WriteLine("Invoking the reqset_singlestage request set");  
        RequestID = client.REQSTG(null, null, null, null, null, param);  
        Console.WriteLine("The request ID generated for the request set is : " + RequestID);  
        Console.WriteLine("*****************************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;  
    }  
    ```  
  
10. <span data-ttu-id="d33c3-146">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d33c3-146">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    ```  
  
11. <span data-ttu-id="d33c3-147">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="d33c3-147">Build the project and then run it.</span></span> <span data-ttu-id="d33c3-148">L’application appelle la **reqset_singlestage** demande définie et retourne un ID de demande, ce qui est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="d33c3-148">The application invokes the **reqset_singlestage** request set and returns a request ID, which is written to the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33c3-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d33c3-149">See Also</span></span>  
 [<span data-ttu-id="d33c3-150">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="d33c3-150">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)