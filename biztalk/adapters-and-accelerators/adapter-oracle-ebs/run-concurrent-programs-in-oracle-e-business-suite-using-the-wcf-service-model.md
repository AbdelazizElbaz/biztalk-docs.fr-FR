---
title: "Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e227c60f-f6fe-40bf-bf41-2784a4428ad0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed2b50eab9612e5a2a610047e41560e1dc24576
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="b2bba-102">Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="b2bba-102">Invoke concurrent programs in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="b2bba-103">Oracle E-Business Suite expose des programmes simultanés que vous pouvez exécuter pour effectuer des opérations spécifiques sur les applications Oracle.</span><span class="sxs-lookup"><span data-stu-id="b2bba-103">Oracle E-Business Suite exposes concurrent programs that you can execute to perform specific operations on Oracle applications.</span></span> <span data-ttu-id="b2bba-104">Chaque application Oracle a un ensemble de programmes simultanés standard (qui sont les mêmes pour toutes les opérations) et certains programmes simultanés qui sont spécifiques à une application Oracle.</span><span class="sxs-lookup"><span data-stu-id="b2bba-104">Each Oracle application has a set of standard concurrent programs (that are same across all operations) and certain concurrent programs that are specific to an Oracle application.</span></span> <span data-ttu-id="b2bba-105">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose tous les programmes simultanés en tant qu’opérations que les clients de l’adaptateur peuvent appeler.</span><span class="sxs-lookup"><span data-stu-id="b2bba-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes all concurrent programs as operations that adapter clients can invoke.</span></span> <span data-ttu-id="b2bba-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge des programmes simultanés, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-106">For more information about how the adapter supports concurrent programs, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2bba-107">Pour les programmes simultanés qui n’exposent pas leurs métadonnées, l’adaptateur Oracle E-Business expose 100 paramètres facultatifs pour chacun de ces programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-107">For the concurrent programs that do not expose their metadata, the Oracle E-Business adapter exposes 100 optional parameters for each of these concurrent programs.</span></span> <span data-ttu-id="b2bba-108">Pour appeler ces programmes simultanés avec succès, l’utilisateur doit consultez la documentation d’Oracle E-Business Suite pour déterminer les paramètres pour un programme simultané qui nécessitent une valeur et puis de les spécifier.</span><span class="sxs-lookup"><span data-stu-id="b2bba-108">To invoke these concurrent programs successfully, the user must consult the Oracle E-Business Suite documentation to figure out the parameters for a concurrent program that require a value, and then specify them.</span></span> <span data-ttu-id="b2bba-109">Est un exemple d’un tel programme simultané **importation du Journal** (nom réel : **GLLEZL**) dans le **comptabilité** application.</span><span class="sxs-lookup"><span data-stu-id="b2bba-109">An example of such a concurrent program is **Journal Import** (actual name: **GLLEZL**) in the **General Ledger** application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="b2bba-110">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="b2bba-110">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="b2bba-111">L’exemple dans cette rubrique appelle la **MS_SAMPLE_COPY_EMP_DATA** simultanées du programme, suivi par le **Get_Status** simultanées du programme pour connaître l’état de la première simultanées du programme.</span><span class="sxs-lookup"><span data-stu-id="b2bba-111">The example in this topic invokes the **MS_SAMPLE_COPY_EMP_DATA** concurrent program, followed by the **Get_Status** concurrent program to know the status of the first concurrent program.</span></span> <span data-ttu-id="b2bba-112">Ces programmes simultanés sont appelées à partir de la **bibliothèque d’objets Application** application.</span><span class="sxs-lookup"><span data-stu-id="b2bba-112">These concurrent programs are invoked from the **Application Object Library** application.</span></span> <span data-ttu-id="b2bba-113">Le **MS_SAMPLE_COPY_EMP_DATA** est créée en exécutant le script fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="b2bba-113">The **MS_SAMPLE_COPY_EMP_DATA** is created by running the script provided with the samples.</span></span> <span data-ttu-id="b2bba-114">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-114">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="b2bba-115">Un exemple, **ConcurrentProgram_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="b2bba-115">A sample, **ConcurrentProgram_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="b2bba-116">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="b2bba-116">The WCF Client Class</span></span>  
 <span data-ttu-id="b2bba-117">Le nom du client WCF généré pour l’appel des programmes simultanés par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2bba-117">The name of the WCF client generated for invoking the concurrent programs by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="b2bba-118">Artefact</span><span class="sxs-lookup"><span data-stu-id="b2bba-118">Artifact</span></span>|<span data-ttu-id="b2bba-119">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="b2bba-119">WCF Client Name</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="b2bba-120">Simultanées du programme</span><span class="sxs-lookup"><span data-stu-id="b2bba-120">Concurrent Program</span></span>|<span data-ttu-id="b2bba-121">Client de ConcurrentPrograms_ [nom_application]</span><span class="sxs-lookup"><span data-stu-id="b2bba-121">ConcurrentPrograms_[APP_NAME]Client</span></span>|  
  
 <span data-ttu-id="b2bba-122">[Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.</span><span class="sxs-lookup"><span data-stu-id="b2bba-122">[APP_NAME] = Actual name of the Oracle E-Business Suite application; for example, FND.</span></span>  
  
### <a name="method-signature-for-invoking-concurrent-programs"></a><span data-ttu-id="b2bba-123">Signature de méthode pour appeler des programmes simultanés</span><span class="sxs-lookup"><span data-stu-id="b2bba-123">Method Signature for Invoking Concurrent Programs</span></span>  
 <span data-ttu-id="b2bba-124">Le tableau suivant montre la signature de méthode pour les programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-124">The following table shows the method signature for the concurrent programs.</span></span>  
  
|<span data-ttu-id="b2bba-125">Opération</span><span class="sxs-lookup"><span data-stu-id="b2bba-125">Operation</span></span>|<span data-ttu-id="b2bba-126">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="b2bba-126">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="b2bba-127">Simultanées du programme</span><span class="sxs-lookup"><span data-stu-id="b2bba-127">Concurrent program</span></span>|<span data-ttu-id="b2bba-128">public \<type de retour >< Concurrent_program_name > (param 1, param 2,...)</span><span class="sxs-lookup"><span data-stu-id="b2bba-128">public \<return type> <Concurrent_program_name>(param 1, param 2, …)</span></span>|  
  
 <span data-ttu-id="b2bba-129">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-129">As an example, the following code shows the method signatures for a WCF client class generated for the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
```  
public partial class ConcurrentPrograms_FNDClient : System.ServiceModel.ClientBase<ConcurrentPrograms_FND>, ConcurrentPrograms_FND {      
  
    public string MS_SAMPLE_COPY_EMP_DATA(schemas.microsoft.com.OracleEBS._2008._05.Options.SetOptions SetOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,  
      string Description, string StartTime);  
  
    public bool GetStatusForConcurrentProgram(string RequestId, out string Phase, out string Status,  
      out string DevPhase, out string DevStatus, out string Message);  
}  
```  
  
 <span data-ttu-id="b2bba-130">Dans cet extrait de code, **ConcurrentPrograms_FNDClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2bba-130">In this snippet, **ConcurrentPrograms_FNDClient** is the name of the WCF class in the OracleEBSBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="b2bba-131">**MS_SAMPLE_COPY_EMP_DATA** est le nom de la méthode à appeler le programme simultané.</span><span class="sxs-lookup"><span data-stu-id="b2bba-131">**MS_SAMPLE_COPY_EMP_DATA** is the name of the method to invoke the concurrent program.</span></span> <span data-ttu-id="b2bba-132">**GetStatusForConcurrentProgram** est le nom de la méthode à appeler le programme simultané pour obtenir l’état de la première simultanées du programme.</span><span class="sxs-lookup"><span data-stu-id="b2bba-132">**GetStatusForConcurrentProgram** is the name of the method to invoke the concurrent program to get the status of the first concurrent program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2bba-133">**GetStatusForConcurrentProgram** est le nom réel de la **Get_Status** simultanées du programme.</span><span class="sxs-lookup"><span data-stu-id="b2bba-133">**GetStatusForConcurrentProgram** is the actual name of the **Get_Status** concurrent program.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-concurrent-programs"></a><span data-ttu-id="b2bba-134">Création d’un Client WCF pour appeler des programmes simultanés</span><span class="sxs-lookup"><span data-stu-id="b2bba-134">Creating a WCF Client to Invoke Concurrent Programs</span></span>  
 <span data-ttu-id="b2bba-135">L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-135">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="b2bba-136">Cette section décrit comment créer un client WCF pour appeler le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-136">This section describes how to create a WCF client to invoke the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="b2bba-137">Pour créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="b2bba-137">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="b2bba-138">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2bba-138">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="b2bba-139">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="b2bba-139">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="b2bba-140">Générer la classe de client WCF pour le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-140">Generate the WCF client class for the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span> <span data-ttu-id="b2bba-141">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-141">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b2bba-142">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="b2bba-142">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="b2bba-143">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="b2bba-143">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="b2bba-144">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="b2bba-144">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="b2bba-145">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b2bba-145">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    ConcurrentPrograms_FNDClient client = new ConcurrentPrograms_FNDClient(binding, address);  
    ```  
  
     <span data-ttu-id="b2bba-146">Dans cet extrait de code, `ConcurrentPrograms_FNDClient` est le client WCF défini dans OracleEBSBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="b2bba-146">In this snippet, `ConcurrentPrograms_FNDClient` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="b2bba-147">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2bba-147">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2bba-148">Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application.</span><span class="sxs-lookup"><span data-stu-id="b2bba-148">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="b2bba-149">Vous pouvez également utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2bba-149">You can also use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="b2bba-150">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-150">For more information on the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="b2bba-151">Définir les informations d’identification pour le client.</span><span class="sxs-lookup"><span data-stu-id="b2bba-151">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="b2bba-152">Étant donné que vous appelez des programmes simultanés dans une application Oracle E-Business Suite, vous devez définir le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="b2bba-152">Because you are invoking concurrent programs in an Oracle E-Business Suite application, you must set the application context.</span></span> <span data-ttu-id="b2bba-153">Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="b2bba-153">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="b2bba-154">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="b2bba-154">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="b2bba-155">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b2bba-155">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="b2bba-156">Appeler le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.</span><span class="sxs-lookup"><span data-stu-id="b2bba-156">Invoke the **MS_SAMPLE_COPY_EMP_DATA** and **Get_Status** concurrent programs.</span></span>  
  
    ```  
    string RequestID;  
    bool Result;  
    string Phase;  
    string Status;  
    string DevPhase;  
    string DevStatus;  
    string Message;  
  
    try  
    {  
        Console.WriteLine("Invoking the MS_SAMPLE_COPY_EMP_DATA concurrent program");  
        RequestID = client.MS_SAMPLE_COPY_EMP_DATA(null, null, null, null, null);  
        Console.WriteLine("The request ID generated for the concurrent program is : " + RequestID);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nWaiting for 60 seconds for the concurrent program to be complete");  
        System.Threading.Thread.Sleep(60000);  
        Console.WriteLine("\nInvoking the Get_Status concurrent program");  
        Result = client.GetStatusForConcurrentProgram(RequestID, out Phase, out Status, out DevPhase, out DevStatus, out Message);  
        Console.WriteLine("\nResult is  : " + Result);  
        Console.WriteLine("Phase is     : " + Phase);  
        Console.WriteLine("Status is    : " + Status);  
        Console.WriteLine("DevPhase is  : " + DevPhase);  
        Console.WriteLine("DevStatus is : " + DevStatus);  
        Console.WriteLine("Message is   : " + Message);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;                 
    }  
    ```  
  
10. <span data-ttu-id="b2bba-157">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b2bba-157">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    ```  
  
11. <span data-ttu-id="b2bba-158">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="b2bba-158">Build the project and then run it.</span></span> <span data-ttu-id="b2bba-159">L’application appelle la **MS_SAMPLE_COPY_EMP_DATA** et retourne un ID de demande.</span><span class="sxs-lookup"><span data-stu-id="b2bba-159">The application invokes the **MS_SAMPLE_COPY_EMP_DATA** and returns a request ID.</span></span> <span data-ttu-id="b2bba-160">L’ID est ensuite transmise à la **Get_Status** simultanées du programme, qui enfin fournit l’état de la **MS_SAMPLE_COPY_EMP_DATA** programme de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b2bba-160">The ID is then passed to the **Get_Status** concurrent program, which finally provides the status of the **MS_SAMPLE_COPY_EMP_DATA** column program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bba-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2bba-161">See Also</span></span>  
 [<span data-ttu-id="b2bba-162">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="b2bba-162">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)