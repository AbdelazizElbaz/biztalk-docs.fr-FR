---
title: "Appeler les RFC dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invoking RFCs, using the WCF service model
- WCF service model, invoking RFCs
ms.assetid: 06a373e2-5d16-4480-81ec-611bd0b9749c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8a18e9ae4990ecd5e85c57fc86919f239d51cbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-rfcs-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="94f44-102">Appeler les RFC dans SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="94f44-102">Invoke RFCs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="94f44-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] met en évidence les RFC sur le système SAP en tant qu’opérations qui peuvent être appelées par un programme client.</span><span class="sxs-lookup"><span data-stu-id="94f44-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces RFCs on the SAP system as operations that can be invoked by a client program.</span></span> <span data-ttu-id="94f44-104">Dans le modèle de service WCF, ces opérations sont appelées en tant que méthodes d’une classe de client WCF générée.</span><span class="sxs-lookup"><span data-stu-id="94f44-104">In the WCF service model, these operations are invoked as methods of a generated WCF client class.</span></span> <span data-ttu-id="94f44-105">Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF qui contient des méthodes pour chaque RFC que vous souhaitez appeler dans votre code.</span><span class="sxs-lookup"><span data-stu-id="94f44-105">You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class that contains methods for each RFC that you want to invoke in your code.</span></span> <span data-ttu-id="94f44-106">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également des types .NET pour encapsuler les paramètres et types de données qui sont utilisés par chaque RFC.</span><span class="sxs-lookup"><span data-stu-id="94f44-106">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates .NET types to encapsulate the parameters and data types that are used by each RFC.</span></span> <span data-ttu-id="94f44-107">Vous pouvez ensuite créer une instance de cette classe de client WCF et appeler ses méthodes pour appeler la cible de RFC.</span><span class="sxs-lookup"><span data-stu-id="94f44-107">You can then create an instance of this WCF client class and call its methods to invoke the target RFCs.</span></span>  
  
 <span data-ttu-id="94f44-108">Les sections suivantes vous montrent comment appeler les RFC sur le système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94f44-108">The following sections show you how to invoke RFCs on the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="94f44-109">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="94f44-109">The WCF Client Class</span></span>  
 <span data-ttu-id="94f44-110">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] couvre toutes les opérations de RFC sous un contrat de service unique, « Rfc ».</span><span class="sxs-lookup"><span data-stu-id="94f44-110">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all RFC operations under a single service contract, "Rfc".</span></span> <span data-ttu-id="94f44-111">Cela signifie qu’une seule classe de client WCF, **RfcClient**, est créé pour toutes les opérations RFC que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="94f44-111">This means that a single WCF client class, **RfcClient**, is created for all of the RFC operations that you want to invoke.</span></span> <span data-ttu-id="94f44-112">Chaque cible RFC est représentée comme une méthode de cette classe.</span><span class="sxs-lookup"><span data-stu-id="94f44-112">Each target RFC is represented as a method of this class.</span></span> <span data-ttu-id="94f44-113">Dans chaque méthode :</span><span class="sxs-lookup"><span data-stu-id="94f44-113">In each method:</span></span>  
  
-   <span data-ttu-id="94f44-114">Paramètres d’exportation SAP sont exposés en tant que **hors** paramètres</span><span class="sxs-lookup"><span data-stu-id="94f44-114">SAP export parameters are surfaced as **out** parameters</span></span>  
  
-   <span data-ttu-id="94f44-115">Les paramètres de modification de SAP sont exposés en tant que **ref** paramètres.</span><span class="sxs-lookup"><span data-stu-id="94f44-115">SAP changing parameters are surfaced as **ref** parameters.</span></span>  
  
-   <span data-ttu-id="94f44-116">Les types SAP complexes telles que les structures sont signalées en tant que classes .NET avec des propriétés qui correspondent aux champs de type SAP.</span><span class="sxs-lookup"><span data-stu-id="94f44-116">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="94f44-117">Ces classes sont définies dans l’espace de noms suivant : microsoft.lobservices.sap._2007._03.Types.Rfc.</span><span class="sxs-lookup"><span data-stu-id="94f44-117">These classes are defined in the following namespace: microsoft.lobservices.sap._2007._03.Types.Rfc.</span></span>  
  
 <span data-ttu-id="94f44-118">Le code suivant montre une partie de la **RfcClient** classe et la méthode qui appelle SD_RFC_CUSTOMER_GET sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="94f44-118">The following code shows part of the **RfcClient** class and the method that invokes SD_RFC_CUSTOMER_GET on the SAP system.</span></span>  
  
```  
 [System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class RfcClient : System.ServiceModel.ClientBase<Rfc>, Rfc {  
  
    ...  
  
    /// <summary>The metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="KUNNR">Customer number</param>  
    /// <param name="NAME1">Name of the customer</param>  
    /// <param name="CUSTOMER_T">Table of the selected customers</param>  
    /// <returns></returns>  
    public void SD_RFC_CUSTOMER_GET(string KUNNR, string NAME1, ref microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] CUSTOMER_T) {...}  
}  
```  
  
## <a name="how-to-create-an-rfc-client-application"></a><span data-ttu-id="94f44-119">Comment créer une Application cliente RFC</span><span class="sxs-lookup"><span data-stu-id="94f44-119">How to Create an RFC Client Application</span></span>  
 <span data-ttu-id="94f44-120">Pour créer une application cliente RFC, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="94f44-120">To create an RFC client application, perform the following steps.</span></span>  
  
#### <a name="to-create-an-rfc-client-application"></a><span data-ttu-id="94f44-121">Pour créer une application cliente RFC</span><span class="sxs-lookup"><span data-stu-id="94f44-121">To create an RFC client application</span></span>  
  
1.  <span data-ttu-id="94f44-122">Générer un **RfcClient** classe.</span><span class="sxs-lookup"><span data-stu-id="94f44-122">Generate an **RfcClient** class.</span></span> <span data-ttu-id="94f44-123">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un **RfcClient** classe ciblant les RFC avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="94f44-123">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate an **RfcClient** class that targets the RFCs with which you want to work.</span></span> <span data-ttu-id="94f44-124">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="94f44-124">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="94f44-125">Créez une instance de la **RfcClient** classe généré à l’étape 1, et spécifier une liaison de client.</span><span class="sxs-lookup"><span data-stu-id="94f44-125">Create an instance of the **RfcClient** class generated in step 1, and specify a client binding.</span></span> <span data-ttu-id="94f44-126">Spécification d’une liaison de client implique la spécification de la liaison et le point de terminaison adresse utilisée par le **RfcClient** utilisera.</span><span class="sxs-lookup"><span data-stu-id="94f44-126">Specifying a client binding involves specifying the binding and endpoint address that the **RfcClient** will use.</span></span> <span data-ttu-id="94f44-127">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="94f44-127">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="94f44-128">Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="94f44-128">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="94f44-129">Le code suivant initialise les **RfcClient** à partir de la configuration et définit les informations d’identification pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="94f44-129">The following code initializes the **RfcClient** from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="94f44-130">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="94f44-130">Open the WCF client.</span></span>  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  <span data-ttu-id="94f44-131">Appeler des méthodes sur le **RfcClient** créé à l’étape 2 pour effectuer des opérations sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="94f44-131">Invoke methods on the **RfcClient** created in step 2 to perform operations on the SAP system.</span></span> <span data-ttu-id="94f44-132">Le code suivant appelle la **SD_RFC_CUSTOMER_GET** méthode de la **RfcClient** pour appeler le RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="94f44-132">The following code invokes the **SD_RFC_CUSTOMER_GET** method of the **RfcClient** to invoke the RFC on the SAP system.</span></span>  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  <span data-ttu-id="94f44-133">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="94f44-133">Close the WCF client.</span></span>  
  
    ```  
    rfcClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="94f44-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="94f44-134">Example</span></span>  
 <span data-ttu-id="94f44-135">Voici un exemple de code complet qui appelle SD_RFC_CUSTOMER_GET pour retourner une liste de clients avec des noms qui commencent par « AB » et écrit le nom et l’ID de chaque client dans la console.</span><span class="sxs-lookup"><span data-stu-id="94f44-135">The following is a complete code example that invokes SD_RFC_CUSTOMER_GET to return a list of customers with names that begin with "AB" and then writes the name and ID for each customer to the console.</span></span> <span data-ttu-id="94f44-136">Cet exemple crée la **RfcClient** à l’intérieur d’un **à l’aide de** instruction.</span><span class="sxs-lookup"><span data-stu-id="94f44-136">This example creates the **RfcClient** inside a **using** statement.</span></span> <span data-ttu-id="94f44-137">Il n’est pas nécessaire de fermer explicitement le **RfcClient**; va être fermée lorsque le chemin d’exécution quitte le contexte.</span><span class="sxs-lookup"><span data-stu-id="94f44-137">There is no need to explicitly close the **RfcClient**; it will be closed when the execution path exits the context.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
namespace SapRfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                // Create client from configuration  
                using (RfcClient rfcClient = new RfcClient("SAPBinding_Rfc"))  
                {  
  
                    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                    // Open client  
                    rfcClient.Open();  
  
                    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers = new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
                    // Invoke SD_RFC_CUSTOMER_GET  
                    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
  
                    // Write the results to the console  
                    foreach (microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST customer in customers)  
                    {  
                        Console.WriteLine("Customer Name = " + customer.NAME1);  
                        Console.WriteLine("         Id   = " + customer.KUNNR);  
                        Console.WriteLine();  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
                if (ex.InnerException != null)  
                    Console.WriteLine("Inner exception is :" + ex.InnerException);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="94f44-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94f44-138">See Also</span></span>  
<span data-ttu-id="94f44-139">[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="94f44-139">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="94f44-140">Schémas de message pour des opérations RFC</span><span class="sxs-lookup"><span data-stu-id="94f44-140">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)