---
title: "Envoyer des IDOC à SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, sending IDOCs to SAP
- IDOCs, sending to SAP by using the WCF service model
ms.assetid: 84077234-b82b-4e88-b858-ce2cb1383fb4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbe77a313cf5913a33878ba82d9ed086936e2c98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-idocs-to-sap-using-the-wcf-service-model"></a><span data-ttu-id="448c8-102">Envoyer des IDOC à SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="448c8-102">Send IDOCs to SAP using the WCF Service Model</span></span>
<span data-ttu-id="448c8-103">En interne, le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] envoie IDOC au système SAP en appelant une des deux normes RFC suivantes :</span><span class="sxs-lookup"><span data-stu-id="448c8-103">Internally, the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sends IDOCs to the SAP system by invoking one of the two following RFCs:</span></span>  
  
-   <span data-ttu-id="448c8-104">IDOC_INBOUND_ASYNCHRONOUS des IDOC de version 3.</span><span class="sxs-lookup"><span data-stu-id="448c8-104">IDOC_INBOUND_ASYNCHRONOUS for version 3 IDOCs.</span></span>  
  
-   <span data-ttu-id="448c8-105">INBOUND_IDOC_PROCESS des IDOC de version 2.</span><span class="sxs-lookup"><span data-stu-id="448c8-105">INBOUND_IDOC_PROCESS for version 2 IDOCs.</span></span>  
  
 <span data-ttu-id="448c8-106">Vous pouvez envoyer un IDOC à l’adaptateur en appelant le RFC (ou tRFC) ; Toutefois, vous pouvez également utiliser les deux opérations suivantes pour envoyer des IDOC à la carte :</span><span class="sxs-lookup"><span data-stu-id="448c8-106">You can send an IDOC to the adapter by invoking the appropriate RFC (or tRFC); however, you can also use the two following operations to send IDOCs to the adapter:</span></span>  
  
-   <span data-ttu-id="448c8-107">**SendIdoc** apparaissent directement sous le nœud racine IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-107">**SendIdoc** is surfaced directly under the IDOC root node.</span></span> <span data-ttu-id="448c8-108">L’opération SendIdoc envoie l’IDOC comme données (faiblement typée) de chaîne pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="448c8-108">The SendIdoc operation sends the IDOC as string (weakly-typed) data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="448c8-109">**Envoyer** apparaissent individuellement pour chaque IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-109">**Send** is surfaced individually for each IDOC.</span></span> <span data-ttu-id="448c8-110">L’opération d’envoi envoie l’IDOC en tant que données fortement typées pour les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="448c8-110">The Send operation sends the IDOC as strongly-typed data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="448c8-111">Ces opérations de déterminent la façon dont les données IDOC sont envoyées à l’adaptateur, pas comment il est envoyé au système SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-111">These operations determine how the IDOC data is sent to the adapter, not how it is sent to the SAP system.</span></span> <span data-ttu-id="448c8-112">L’adaptateur envoie toujours l’IDOC au système SAP à l’aide de la tRFC appropriée.</span><span class="sxs-lookup"><span data-stu-id="448c8-112">The adapter always sends the IDOC to the SAP system by using the appropriate tRFC.</span></span>  
  
 <span data-ttu-id="448c8-113">Étant donné que le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] envoie l’IDOC comme un tRFC, les opérations de l’envoi et la SendIdoc présentent un paramètre GUID qui vous permet de confirmer (commit) l’IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-113">Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sends the IDOC as a tRFC, both the Send and SendIdoc operations expose a GUID parameter that you use to confirm (commit) the IDOC.</span></span> <span data-ttu-id="448c8-114">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en interne mappe ce GUID à l’aide de la transaction SAP ID (TID) qui est associé à le tRFC.</span><span class="sxs-lookup"><span data-stu-id="448c8-114">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] internally maps this GUID with the SAP transaction ID (TID) that is associated with the tRFC.</span></span> <span data-ttu-id="448c8-115">Vous pouvez vérifier l’IDOC de deux manières :</span><span class="sxs-lookup"><span data-stu-id="448c8-115">You can confirm the IDOC in one of two ways:</span></span>  
  
-   <span data-ttu-id="448c8-116">À l’aide de la **AutoConfirmSentIdocs** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="448c8-116">By using the **AutoConfirmSentIdocs** binding property.</span></span> <span data-ttu-id="448c8-117">Si cette propriété de liaison est définie à **true**, l’adaptateur confirme automatiquement le tRFC permet d’envoyer l’IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-117">If this binding property is set to **true**, the adapter automatically confirms the tRFC used to send the IDOC.</span></span>  
  
-   <span data-ttu-id="448c8-118">En appelant RfcConfirmTransID.</span><span class="sxs-lookup"><span data-stu-id="448c8-118">By invoking RfcConfirmTransID.</span></span> <span data-ttu-id="448c8-119">Vous appelez cette opération avec le GUID associé à l’IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-119">You invoke this operation with the GUID associated with the IDOC.</span></span>  
  
 <span data-ttu-id="448c8-120">Les sections suivantes vous montrent comment envoyer des IDOC à un système SAP en utilisant les opérations SendIdoc et d’envoi.</span><span class="sxs-lookup"><span data-stu-id="448c8-120">The following sections show you how to send IDOCs to an SAP system by using the SendIdoc and Send operations.</span></span> <span data-ttu-id="448c8-121">Pour plus d’informations pour vous aider à envoyer un IDOC comme un tRFC, consultez [appeler tRFCs dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="448c8-121">For more information to help you send an IDOC as a tRFC, see [Invoke tRFCs in SAP by using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="448c8-122">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="448c8-122">The WCF Client Class</span></span>  
  
### <a name="the-sendidoc-operation"></a><span data-ttu-id="448c8-123">L’opération SendIdoc</span><span class="sxs-lookup"><span data-stu-id="448c8-123">The SendIdoc Operation</span></span>  
 <span data-ttu-id="448c8-124">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence une seule opération (et le contrat de service) pour envoyer un IDOC sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="448c8-124">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a single operation (and service contract) to send an IDOC in string format.</span></span> <span data-ttu-id="448c8-125">Le nom du contrat de service est « Idoc » et de la classe de client WCF est **IdocClient**.</span><span class="sxs-lookup"><span data-stu-id="448c8-125">The name of the service contract is "Idoc" and the WCF client class is **IdocClient**.</span></span>  
  
 <span data-ttu-id="448c8-126">Vous pouvez envoyer n’importe quel IDOC à SAP à l’aide de ce client.</span><span class="sxs-lookup"><span data-stu-id="448c8-126">You can send any IDOC to SAP by using this client.</span></span> <span data-ttu-id="448c8-127">Il contient une méthode unique, **SendIdoc**, qui accepte deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="448c8-127">It contains a single method, **SendIdoc**, that takes two parameters:</span></span>  
  
-   <span data-ttu-id="448c8-128">**idocData** est une chaîne qui contient les données IDOC</span><span class="sxs-lookup"><span data-stu-id="448c8-128">**idocData** is a string that contains the IDOC data</span></span>  
  
-   <span data-ttu-id="448c8-129">**GUID** GUID qui est mappé sur le TID SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-129">**guid** is the GUID that is mapped to the SAP TID.</span></span>  
  
 <span data-ttu-id="448c8-130">Le code suivant illustre le client WCF qui est généré pour l’opération SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="448c8-130">The following code shows the WCF client that is generated for the SendIdoc operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocClient : System.ServiceModel.ClientBase<Idoc>, Idoc {  
  
    public void SendIdoc(string idocData, ref System.Nullable\<System.Guid> guid) {…}  
}  
```  
  
### <a name="the-send-operation"></a><span data-ttu-id="448c8-131">L’opération d’envoi</span><span class="sxs-lookup"><span data-stu-id="448c8-131">The Send Operation</span></span>  
 <span data-ttu-id="448c8-132">Étant donné que l’opération d’envoi utilise les données fortement typées, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence un contrat de service unique pour chaque IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-132">Because the Send operation uses strongly-typed data, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a unique service contract for each IDOC.</span></span> <span data-ttu-id="448c8-133">Le nom de l’interface (et la classe de client WCF) généré pour ce contrat est basé sur le type IDOC, une version, un numéro de version et un type CIM (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="448c8-133">The name of the interface (and the WCF client class) generated for this contract is based on the IDOC type, version, release number, and CIM type (if relevant).</span></span> <span data-ttu-id="448c8-134">Par exemple pour l’IDOC ORDERS03.v3.620, l’interface est nommé « IdocORDERS03V3R620 » et la classe de client WCF est **IdocORDERS03V3R620Client**.</span><span class="sxs-lookup"><span data-stu-id="448c8-134">For example for the ORDERS03.v3.620 IDOC, the interface is named "IdocORDERS03V3R620" and the WCF client class is **IdocORDERS03V3R620Client**.</span></span>  
  
 <span data-ttu-id="448c8-135">Vous devez générer un client unique pour chaque type d’IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-135">You must generate a unique client for each different type of IDOC.</span></span> <span data-ttu-id="448c8-136">Ce client contient une méthode unique, **envoyer**, qui accepte deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="448c8-136">This client contains a single method, **Send**, that takes two parameters:</span></span>  
  
-   <span data-ttu-id="448c8-137">**idocData** est une classe qui représente les données IDOC fortement typée.</span><span class="sxs-lookup"><span data-stu-id="448c8-137">**idocData** is a class that represents the strongly-typed IDOC data.</span></span>  
  
-   <span data-ttu-id="448c8-138">**GUID** est une représentation de chaîne du GUID qui est mappé sur le TID SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-138">**guid** is a string representation of the GUID that is mapped to the SAP TID.</span></span>  
  
 <span data-ttu-id="448c8-139">Le code suivant illustre le client WCF qui est généré pour l’opération d’envoi signalée pour l’IDOC ORDERS03.v3.620.</span><span class="sxs-lookup"><span data-stu-id="448c8-139">The following code shows the WCF client that is generated for the Send operation surfaced for the ORDERS03.v3.620 IDOC.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocORDERS03V3R620Client : System.ServiceModel.ClientBase<IdocORDERS03V3R620>, IdocORDERS03V3R620 {  
  
    ...  
  
    public void Send(ORDERS03 idocData, ref string guid) { ... }  
}  
```  
  
## <a name="how-to-create-an-application-to-send-idocs"></a><span data-ttu-id="448c8-140">Comment créer une Application pour envoyer des IDOC</span><span class="sxs-lookup"><span data-stu-id="448c8-140">How to Create an Application to Send IDOCs</span></span>  
 <span data-ttu-id="448c8-141">Pour envoyer un IDOC à un système SAP, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="448c8-141">To send an IDOC to an SAP system, perform the following steps.</span></span>  
  
#### <a name="to-send-an-idoc-to-an-sap-system"></a><span data-ttu-id="448c8-142">Pour envoyer un IDOC à un système SAP</span><span class="sxs-lookup"><span data-stu-id="448c8-142">To send an IDOC to an SAP system</span></span>  
  
1.  <span data-ttu-id="448c8-143">Générer une classe de client WCF.</span><span class="sxs-lookup"><span data-stu-id="448c8-143">Generate a WCF client class.</span></span> <span data-ttu-id="448c8-144">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF qui cible l’IDOC avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="448c8-144">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class that targets the IDOCs with which you want to work.</span></span> <span data-ttu-id="448c8-145">Pour plus d’informations sur la façon de générer un client WCF, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="448c8-145">For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span> <span data-ttu-id="448c8-146">Si vous souhaitez confirmer explicitement IDOC, assurez-vous que vous générez le client WCF pour l’opération RfcConfirmTransID.</span><span class="sxs-lookup"><span data-stu-id="448c8-146">If you want to explicitly confirm IDOCs, make sure that you generate the WCF client for the RfcConfirmTransID operation.</span></span> <span data-ttu-id="448c8-147">Vous trouverez des opérations sous les nœuds suivants :</span><span class="sxs-lookup"><span data-stu-id="448c8-147">Operations can be found under the following nodes:</span></span>  
  
    -   <span data-ttu-id="448c8-148">Opération SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="448c8-148">SendIdoc operation.</span></span> <span data-ttu-id="448c8-149">Directement sous le nœud IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-149">Directly under the IDOC node.</span></span>  
  
    -   <span data-ttu-id="448c8-150">Opération d’envoi.</span><span class="sxs-lookup"><span data-stu-id="448c8-150">Send operation.</span></span> <span data-ttu-id="448c8-151">Sous le nœud correspondant au numéro de version, la version et type de la cible IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-151">Under the node corresponding to the type, version and release number of the target IDOC.</span></span>  
  
    -   <span data-ttu-id="448c8-152">Opération RfcConfirmTransID.</span><span class="sxs-lookup"><span data-stu-id="448c8-152">RfcConfirmTransID operation.</span></span> <span data-ttu-id="448c8-153">Directement sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="448c8-153">Directly under the TRFC node.</span></span>  
  
2.  <span data-ttu-id="448c8-154">Créez une instance de la classe de client WCF générée à l’étape 1, et spécifier une liaison de client.</span><span class="sxs-lookup"><span data-stu-id="448c8-154">Create an instance of the WCF client class generated in step 1, and specify a client binding.</span></span> <span data-ttu-id="448c8-155">Spécification d’une liaison de client implique la spécification de la liaison et l’adresse de point de terminaison utilisé par le client WCF.</span><span class="sxs-lookup"><span data-stu-id="448c8-155">Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use.</span></span> <span data-ttu-id="448c8-156">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="448c8-156">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="448c8-157">Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="448c8-157">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="448c8-158">Le code suivant initialise un IdocClient (pour l’opération d’envoi) à partir de la configuration et définit les informations d’identification pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-158">The following code initializes an IdocClient (for the Send operation) from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    SAPBinding binding = new SAPBinding();  
  
    // Set endpoint address  
    EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
    // Create client and set credentials  
    idocClient = new IdocClient(binding, endpointAddress);  
    idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
    idocClient.ClientCredentials.UserName.Password = "YourPassword";;  
    ```  
  
3.  <span data-ttu-id="448c8-159">Si vous souhaitez que la carte pour confirmer la tRFC sur le système SAP après qu’il envoie l’IDOC, définissez la **AutoConfirmSentIdocs** liaison de propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="448c8-159">If you want the adapter to confirm the tRFC on the SAP system after it sends the IDOC, set the **AutoConfirmSentIdocs** binding property to **true**.</span></span> <span data-ttu-id="448c8-160">Vous devez le faire avant d’ouvrir le client WCF.</span><span class="sxs-lookup"><span data-stu-id="448c8-160">You must do this before you open the WCF client.</span></span>  
  
    ```  
    // Set AutoConfirmSentIdocs property to true  
    binding.AutoConfirmSentIdocs = true;  
    ```  
  
4.  <span data-ttu-id="448c8-161">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="448c8-161">Open the WCF client.</span></span>  
  
    ```  
    idocClient.Open();  
    ```  
  
5.  <span data-ttu-id="448c8-162">Appelez la méthode appropriée sur le client WCF créé à l’étape 2 pour envoyer l’IDOC au système SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-162">Invoke the appropriate method on the WCF client created in step 2 to send the IDOC to the SAP system.</span></span> <span data-ttu-id="448c8-163">Vous pouvez passer une variable qui contient un GUID ou qui a la valeur **null** pour le **guid** paramètre.</span><span class="sxs-lookup"><span data-stu-id="448c8-163">You can pass a variable that contains a GUID or that is set to **null** for the **guid** parameter.</span></span> <span data-ttu-id="448c8-164">Si vous ne spécifiez pas un GUID, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère un pour l’opération (**guid** est un **ref** paramètre).</span><span class="sxs-lookup"><span data-stu-id="448c8-164">If you do not specify a GUID, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one for the operation (**guid** is a **ref** parameter).</span></span> <span data-ttu-id="448c8-165">Le code suivant lit un IDOC (au format de chaîne) à partir d’un fichier et l’envoie au système SAP à l’aide de l’opération SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="448c8-165">The following code reads an IDOC (in string format) from a file and sends it to the SAP system by using the SendIdoc operation.</span></span>  
  
    ```  
    // Read IDOC into string variable  
    using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
    {  
    idocData = reader.ReadToEnd();  
    }  
  
    //Get a new GUID to pass to SendIdoc. You can also assign a null  
    //value to have the adapter generate a GUID.  
    adapterTxGuid = Guid.NewGuid();  
  
    //Invoke SendIdoc on the client to send the IDOC to the SAP system  
    idocClient.SendIdoc(idocData, ref adapterTxGuid);  
    ```  
  
6.  <span data-ttu-id="448c8-166">Si vous n’avez pas défini la **AutoConfirmSentIdocs** liaison de propriété **true** (à l’étape 3), vous devez confirmer le tRFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="448c8-166">If you did not set the **AutoConfirmSentIdocs** binding property to **true** (in step 3), then you must confirm the tRFC on the SAP system.</span></span> <span data-ttu-id="448c8-167">Pour cela, vous devez appeler la **RfcConfirmTransID** méthode sur un **TrfcClient** (création ne pas affichée).</span><span class="sxs-lookup"><span data-stu-id="448c8-167">To do this you must invoke the **RfcConfirmTransID** method on a **TrfcClient** (creation not shown).</span></span> <span data-ttu-id="448c8-168">Spécifiez que le GUID est renvoyé à l’étape 4 pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="448c8-168">Specify the GUID returned in step 4 for the parameter.</span></span>  
  
    ```  
    trfcClient.RfcConfirmTransID(adapterTxGuid);  
    ```  
  
7.  <span data-ttu-id="448c8-169">Fermez le client WCF (et **TrfcClient**, le cas échéant) quand vous avez terminé l’utiliser (une fois que vous avez terminé l’envoi IDOC).</span><span class="sxs-lookup"><span data-stu-id="448c8-169">Close the WCF client (and **TrfcClient**, if used) when you are done using it (after you have finished sending IDOCs).</span></span>  
  
    ```  
    idocClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="448c8-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="448c8-170">Example</span></span>  
 <span data-ttu-id="448c8-171">L’exemple suivant envoie un IDOC à un système SAP à l’aide de la méthode SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="448c8-171">The following example sends an IDOC to an SAP system by using the SendIdoc method.</span></span> <span data-ttu-id="448c8-172">L’IDOC est lu à partir d’un fichier, ORDERS03.txt.</span><span class="sxs-lookup"><span data-stu-id="448c8-172">The IDOC is read from a file, ORDERS03.txt.</span></span> <span data-ttu-id="448c8-173">Ce fichier contient un ORDERS03. V3.620 IDOC et est inclus avec les exemples ; Toutefois, l’opération de SendIdoc peut être utilisée pour envoyer n’importe quel IDOC.</span><span class="sxs-lookup"><span data-stu-id="448c8-173">This file contains an ORDERS03.V3.620 IDOC and is included with the samples; however, the SendIdoc operation can be used to send any IDOC.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This example sends a flat IDOC to the SAP system by using the SendIdoc operation.  
namespace SapIdocStringClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // variable for the IDOC client  
            IdocClient idocClient = null;  
  
            Console.WriteLine("IDOC string client sample started");  
            try  
            {  
                // Variable for the GUID  
                System.Nullable\<System.Guid> adapterTxGuid;  
                // string to hold the Idoc data  
                string idocData;  
                // string to hold the SAP transaction ID (TID)  
                string sapTxId;  
  
                // The client can be configured from app.config, but it is   
                // explicitly configured here for demonstration.  
                // set AutoConfirmSentIdocs property to true  
                SAPBinding binding = new SAPBinding();  
                binding.AutoConfirmSentIdocs = true;  
  
                // Set endpoint address  
                EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPServer/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
                // Create client and set credentials  
                idocClient = new IdocClient(binding, endpointAddress);  
                idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
                idocClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the client and send the Idoc  
                idocClient.Open();  
  
                // Read IDOC into string variable  
                using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
                {  
                    idocData = reader.ReadToEnd();  
                }  
  
                //Get a new GUID to pass to SendIdoc. You can also assign a null.  
                //value to have the adapter generate a GUID.  
                adapterTxGuid = Guid.NewGuid();  
  
                //Invoke SendIdoc on the client to send the IDOC to the SAP system.  
                idocClient.SendIdoc(idocData, ref adapterTxGuid);  
  
                // The AutoConfirmSentIdocs binding property is set to true, so there is no need to  
                // confirm the IDOC. If this property is not set to true, you must call the   
                // RfcConfirmTransID method of a TrfcClient with adapterTxGuid to   
                // confirm the transaction on the SAP system.   
  
                // Get SAP tx id from GUID  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid((Guid) adapterTxGuid);  
  
                Console.WriteLine("IDOC sent");  
                Console.WriteLine("The SAP Transaction Id is : " + sapTxId);  
  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // Close the IDOC client  
                if (idocClient != null)  
                {  
                    if (idocClient.State == CommunicationState.Opened)  
                        idocClient.Close();  
                    else  
                        idocClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="448c8-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="448c8-174">See Also</span></span>  
[<span data-ttu-id="448c8-175">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="448c8-175">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)