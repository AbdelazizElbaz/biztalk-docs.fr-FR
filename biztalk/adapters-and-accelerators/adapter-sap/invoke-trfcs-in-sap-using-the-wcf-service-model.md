---
title: "Appeler tRFCs dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFCs, invoking by using the WCF service model
- WCF service model, invoking tRFCs
ms.assetid: 456fa869-2f1a-42e0-adbf-86bfe0876846
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f23ee3e863318c9d75be9136e7b7fc0fa37b921
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-trfcs-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="5890d-102">Appeler tRFCs dans SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="5890d-102">Invoke tRFCs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="5890d-103">Appels de fonction distants transactionnelle (tRFCs) garantit une *à usage unique* l’exécution d’une commande RFC sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-103">Transactional Remote Function Calls (tRFCs) guarantee a *one-time* execution of an RFC on an SAP system.</span></span> <span data-ttu-id="5890d-104">Vous pouvez appeler une des RFC exposés par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme un tRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-104">You can invoke any of the RFCs surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a tRFC.</span></span> <span data-ttu-id="5890d-105">Appel d’un tRFC dans le modèle de service WCF est similaire à l’appel d’une commande RFC avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="5890d-105">Invoking a tRFC in the WCF service model is similar to invoking an RFC with the following differences:</span></span>  
  
-   <span data-ttu-id="5890d-106">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces tRFCs sous un nœud différent (TRFC) que les documents RFC (RFC).</span><span class="sxs-lookup"><span data-stu-id="5890d-106">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces tRFCs under a different node (TRFC) than RFCs (RFC).</span></span>  
  
-   <span data-ttu-id="5890d-107">appels du client tRFC ne retournent pas de valeurs pour l’exportation SAP et la modification des paramètres.</span><span class="sxs-lookup"><span data-stu-id="5890d-107">tRFC client calls do not return values for SAP export and changing parameters.</span></span>  
  
-   <span data-ttu-id="5890d-108">les opérations tRFC incluent un paramètre GUID qui est mappé à l’ID de transaction SAP (TID) pour le tRFC par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5890d-108">tRFC operations include a GUID parameter that is mapped to the SAP transaction ID (TID) for the tRFC by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="5890d-109">Une fois que vous appelez un tRFC, vous devez appeler l’opération RfcConfirmTransID pour confirmer (commit) le tRFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-109">After you invoke a tRFC, you must invoke the RfcConfirmTransID operation to confirm (commit) the tRFC on the SAP system.</span></span> <span data-ttu-id="5890d-110">Cette opération apparaissent directement sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-110">This operation is surfaced directly under the TRFC node.</span></span>  
  
 <span data-ttu-id="5890d-111">Pour plus d’informations sur les opérations tRFC et l’opération RfcConfirmTransID, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="5890d-111">For more information about tRFC operations and the RfcConfirmTransID operation, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
 <span data-ttu-id="5890d-112">Les sections suivantes vous montrent comment appeler tRFCs sur le système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5890d-112">The following sections show you how to invoke tRFCs on the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="5890d-113">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="5890d-113">The WCF Client Class</span></span>  
 <span data-ttu-id="5890d-114">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] couvre toutes les opérations tRFC sous un contrat de service unique, « Trfc ».</span><span class="sxs-lookup"><span data-stu-id="5890d-114">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all tRFC operations under a single service contract, "Trfc".</span></span> <span data-ttu-id="5890d-115">Cela signifie qu’une seule classe de client WCF, **TrfcClient**, est créé pour toutes les opérations tRFC que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="5890d-115">This means that a single WCF client class, **TrfcClient**, is created for all of the tRFC operations that you want to invoke.</span></span> <span data-ttu-id="5890d-116">Chaque tRFC cible est représentée comme une méthode de cette classe.</span><span class="sxs-lookup"><span data-stu-id="5890d-116">Each target tRFC is represented as a method of this class.</span></span> <span data-ttu-id="5890d-117">Pour chaque méthode :</span><span class="sxs-lookup"><span data-stu-id="5890d-117">For each method:</span></span>  
  
-   <span data-ttu-id="5890d-118">Les types SAP complexes telles que les structures sont signalées en tant que classes .NET avec des propriétés qui correspondent aux champs de type SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-118">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="5890d-119">Ces classes sont définies dans l’espace de noms suivant : **microsoft.lobservices.sap._2007._03.Types.Rfc**.</span><span class="sxs-lookup"><span data-stu-id="5890d-119">These classes are defined in the following namespace: **microsoft.lobservices.sap._2007._03.Types.Rfc**.</span></span>  
  
 <span data-ttu-id="5890d-120">Le code suivant montre une partie de la **TrfcClient** classe et la méthode qui appelle BAPI_SALESORDER_CREATEFROMDAT2 (comme un tRFC) sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-120">The following code shows part of the **TrfcClient** class and the method that invokes BAPI_SALESORDER_CREATEFROMDAT2 (as a tRFC) on the SAP system.</span></span> <span data-ttu-id="5890d-121">Le **TransactionalRfcOperationIdentifier** paramètre contient le GUID qui est mappé sur le TID SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-121">The **TransactionalRfcOperationIdentifier** parameter contains the GUID that is mapped to the SAP TID.</span></span> <span data-ttu-id="5890d-122">Pas tous les paramètres à la méthode sont affichés.</span><span class="sxs-lookup"><span data-stu-id="5890d-122">Not all of the parameters to the method are shown.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class TrfcClient : System.ServiceModel.ClientBase<Trfc>, Trfc {  
  
    ....  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    public void BAPI_SALESORDER_CREATEFROMDAT2(  
                string BEHAVE_WHEN_ERROR,   
                string BINARY_RELATIONSHIPTYPE,   
                string CONVERT,   
                string INT_NUMBER_ASSIGNMENT,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDLS LOGIC_SWITCH,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1 ORDER_HEADER_IN,   
  
                …  
  
               microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIADDR1[] PARTNERADDRESSES,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2[] RETURN,   
                ref System.Guid TransactionalRfcOperationIdentifier) { ...  }  
}  
```  
  
 <span data-ttu-id="5890d-123">Le code suivant montre la méthode qui est générée pour l’opération RfcConfirmTransID.</span><span class="sxs-lookup"><span data-stu-id="5890d-123">The following code shows the method that is generated for the RfcConfirmTransID operation.</span></span> <span data-ttu-id="5890d-124">Vous devez vous assurer que cette méthode est générée dans le cadre de la **TrfcClient**.</span><span class="sxs-lookup"><span data-stu-id="5890d-124">You must ensure that this method is generated as part of the **TrfcClient**.</span></span> <span data-ttu-id="5890d-125">L’opération RfcConfirmTransID apparaissent directement sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-125">The RfcConfirmTransID operation is surfaced directly under the TRFC node.</span></span>  
  
```  
public void RfcConfirmTransID(System.Guid TransactionalRfcOperationIdentifier) {…}  
```  
  
## <a name="how-to-create-a-trfc-client-application"></a><span data-ttu-id="5890d-126">Comment créer une Application cliente tRFC</span><span class="sxs-lookup"><span data-stu-id="5890d-126">How to Create a tRFC Client Application</span></span>  
 <span data-ttu-id="5890d-127">Les étapes pour créer une application qui appelle tRFCs sont semblables aux étapes vous suivez pour appeler les RFC, avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5890d-127">The steps to create an application that invokes tRFCs are similar to the steps you follow to invoke RFCs, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="5890d-128">Vous devez récupérer les opérations de la cible sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-128">You must retrieve the target operations under the TRFC node.</span></span>  
  
-   <span data-ttu-id="5890d-129">Vous devez récupérer l’opération RfcConfirmTransID.</span><span class="sxs-lookup"><span data-stu-id="5890d-129">You must retrieve the RfcConfirmTransID operation.</span></span> <span data-ttu-id="5890d-130">Cela apparaissent directement sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-130">This is surfaced directly under the TRFC node.</span></span>  
  
-   <span data-ttu-id="5890d-131">Pour confirmer (commit) une opération tRFC sur le système SAP, vous devez appeler l’opération RfcConfirmTransID avec le GUID qui a été retournée pour cette opération tRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-131">To confirm (commit) a tRFC operation on the SAP system, you must invoke the RfcConfirmTransID operation with the GUID that was returned for that tRFC operation.</span></span>  
  
#### <a name="to-create-a-trfc-client-application"></a><span data-ttu-id="5890d-132">Pour créer une application de client tRFC</span><span class="sxs-lookup"><span data-stu-id="5890d-132">To create a tRFC client application</span></span>  
  
1.  <span data-ttu-id="5890d-133">Générer un **TrfcClient** classe.</span><span class="sxs-lookup"><span data-stu-id="5890d-133">Generate a **TrfcClient** class.</span></span> <span data-ttu-id="5890d-134">Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un **TrfcClient** classe ciblant les RFC avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="5890d-134">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a **TrfcClient** class that targets the RFCs with which you want to work.</span></span> <span data-ttu-id="5890d-135">Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour la solution SAP artefacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="5890d-135">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for SAP solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span> <span data-ttu-id="5890d-136">Assurez-vous que l’opération RfcConfirmTransID est incluse dans le **TrfcClient** classe.</span><span class="sxs-lookup"><span data-stu-id="5890d-136">Ensure that the RfcConfirmTransID operation is included in the **TrfcClient** class.</span></span>  
  
2.  <span data-ttu-id="5890d-137">Créez une instance de la **TrfcClient** classe généré à l’étape 1 et spécifier une liaison de client.</span><span class="sxs-lookup"><span data-stu-id="5890d-137">Create an instance of the **TrfcClient** class generated in step 1 and specify a client binding.</span></span> <span data-ttu-id="5890d-138">Spécification d’une liaison de client implique la spécification de la liaison et le point de terminaison adresse utilisée par le **TrfcClient** utilisera.</span><span class="sxs-lookup"><span data-stu-id="5890d-138">Specifying a client binding involves specifying the binding and endpoint address that the **TrfcClient** will use.</span></span> <span data-ttu-id="5890d-139">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="5890d-139">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="5890d-140">Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="5890d-140">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="5890d-141">Le code suivant initialise les **TrfcClient** à partir de la configuration et définit les informations d’identification pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-141">The following code initializes the **TrfcClient** from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    TrfcClient trfcClient = new TrfcClient("SAPBinding_Rfc");  
  
    trfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    trfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="5890d-142">Ouvrez le **TrfcClient**.</span><span class="sxs-lookup"><span data-stu-id="5890d-142">Open the **TrfcClient**.</span></span>  
  
    ```  
    trfcClient.Open();  
    ```  
  
4.  <span data-ttu-id="5890d-143">Appeler la méthode appropriée sur le **TrfcClient** créé à l’étape 2 pour appeler le tRFC cible sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="5890d-143">Invoke the appropriate method on the **TrfcClient** created in step 2 to invoke the target tRFC on the SAP system.</span></span> <span data-ttu-id="5890d-144">Vous pouvez passer une variable qui contient un GUID ou qui contient un GUID vide pour le **TransactionalRrcOperationIdentifier** paramètre.</span><span class="sxs-lookup"><span data-stu-id="5890d-144">You can pass a variable that contains a GUID or that contains an empty GUID for the **TransactionalRrcOperationIdentifier** parameter.</span></span> <span data-ttu-id="5890d-145">Si vous passez un GUID vide, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère une pour vous.</span><span class="sxs-lookup"><span data-stu-id="5890d-145">If you pass an empty GUID, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one for you.</span></span> <span data-ttu-id="5890d-146">Le code suivant appelle BAPI_SALESORDER_CREATEFROMDAT2 comme un tRFC sur le système SAP (pas tous les paramètres de la méthode sont affichés).</span><span class="sxs-lookup"><span data-stu-id="5890d-146">The following code invokes BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC on the SAP system (not all parameters to the method are shown).</span></span> <span data-ttu-id="5890d-147">Un GUID est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5890d-147">A GUID is specified.</span></span>  
  
    ```  
    transactionalRfcOperationIdentifier = Guid.NewGuid();  
  
    //invoke RFC_CUSTOMER_GET as a tRFC  
    trfcClient.BAPI_SALESORDER_CREATEFROMDAT2(  
                                    request.BEHAVE_WHEN_ERROR,  
                                    request.BINARY_RELATIONSHIPTYPE,  
                                    request.CONVERT,  
  
                                    ...  
  
                                    ref transactionalRfcOperationIdentifier);  
    ```  
  
5.  <span data-ttu-id="5890d-148">Pour confirmer le TID associé à le tRFC sur le système SAP, appelez le **RfcConfirmTransID** méthode sur le **TrfcClient**.</span><span class="sxs-lookup"><span data-stu-id="5890d-148">To confirm the TID associated with the tRFC on the SAP system, invoke the **RfcConfirmTransID** method on the **TrfcClient**.</span></span> <span data-ttu-id="5890d-149">Spécifiez le GUID retourné à l’étape 4 pour le **TransactionRfcOperationIdentifier**paramètre.</span><span class="sxs-lookup"><span data-stu-id="5890d-149">Specify the GUID returned in step 4 for the **TransactionRfcOperationIdentifier**parameter.</span></span>  
  
    ```  
    trfcClient.RfcConfirmTransID(transactionalRfcOperationIdentifier);  
    ```  
  
6.  <span data-ttu-id="5890d-150">Fermer le **TrfcClient** lorsque vous avez terminé l’utiliser (une fois que vous avez terminé d’appel de tous les tRFCs).</span><span class="sxs-lookup"><span data-stu-id="5890d-150">Close the **TrfcClient** when you are done using it (after you have finished invoking all tRFCs).</span></span>  
  
    ```  
    trfcClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="5890d-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="5890d-151">Example</span></span>  
 <span data-ttu-id="5890d-152">L’exemple suivant montre comment appeler BAPI_SALESORDER_CREATE comme un tRFC.</span><span class="sxs-lookup"><span data-stu-id="5890d-152">The following example shows how to invoke BAPI_SALESORDER_CREATE as a tRFC.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, the WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using microsoft.lobservices.sap._2007._03.Types.Rfc;  
  
// This example demonstrates sending BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC. The client has   
// methods to:  
//      send the BAPI (BAPI_SALESORDER_CREATEFROMDAT2)and to  
//      Confirm the transaction (RfcConfirmTransID)  
// An instance of BAPI_SALESORDER_CREATEFROMDAT2Request (generated)   
// is used to format the BAPI before invoking BAPI_SALESORDER_CREATEFROMDAT2. This   
// is not necessary, but is done to make it easier to read the code.  
// tRFC invocations always includes a ref parameter that contains a GUID. You can optionally   
// set this parameter when you invoke the method; however, you must use the value returned by  
// the adapter when you call RfcConfirmTransID to confirm the transaction on the SAP system.   
// You can call the utility method, SAPAdapterUtilities.ConvertGuidToTid, to get the value  
// of the SAP transaction Id from the GUID that the adapter returns.  
namespace SapTrfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            TrfcClient sapTrfcClient = null;  
  
            try  
            {  
                Console.WriteLine("SAP TRFC client sample started");  
                Console.WriteLine("Creating the TRFC client");  
                // Create the SAP Trfc Client from configuration  
                sapTrfcClient = new TrfcClient("SAPBinding_Trfc");  
                sapTrfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                sapTrfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                Console.WriteLine("Opening the TRFC client");  
                // Open the Trfc Client  
                sapTrfcClient.Open();  
  
                // Create a GUID -- note: this is optional. If you do not pass a GUID,  
                // for the TransactionalRfcOperationIdentifier parameter, the SAP adapter will   
                // generate one, associate it with the SAP TID, and set the   
                // TransactionalRfcOperationIdentifier parameter.  
                Guid tidGuid = Guid.NewGuid();  
  
                BAPI_SALESORDER_CREATEFROMDAT2Request request = new BAPI_SALESORDER_CREATEFROMDAT2Request();  
  
                request.ORDER_HEADER_IN = new BAPISDHD1();  
                request.ORDER_HEADER_IN.DOC_TYPE = "TA";  
                request.ORDER_HEADER_IN.SALES_ORG = "1000";  
                request.ORDER_HEADER_IN.DISTR_CHAN = "10";  
                request.ORDER_HEADER_IN.DIVISION = "00";  
                request.ORDER_HEADER_IN.SALES_OFF = "1000";  
                request.ORDER_HEADER_IN.REQ_DATE_H = DateTime.Now;  
                request.ORDER_HEADER_IN.PURCH_DATE = DateTime.Now;  
                request.ORDER_HEADER_IN.PURCH_NO_C = "Cust PO";  
                request.ORDER_HEADER_IN.CURRENCY = "EUR";  
  
                BAPISDITM[] orderItems = new BAPISDITM[1];  
                orderItems[0] = new BAPISDITM();  
                orderItems[0].MATERIAL = "P-109";  
                orderItems[0].PLANT = "1000";  
                orderItems[0].TARGET_QU = "ST";  
                request.ORDER_ITEMS_IN = orderItems;  
  
                BAPIPARNR[] orderPartners = new BAPIPARNR[1];  
                orderPartners[0] = new microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPARNR();  
                orderPartners[0].PARTN_ROLE = "AG";  
                orderPartners[0].PARTN_NUMB = "0000001390";  
                request.ORDER_PARTNERS = orderPartners;  
  
                // Create a GUID -- note: this is optional. If you do not pass a GUID,  
                // for the TransactionalRfcOperationIdentifier parameter, the SAP adapter will   
                // generate one, associate it with the SAP TID, and set the   
                // TransactionalRfcOperationIdentifier parameter.  
                request.TransactionalRfcOperationIdentifier = Guid.NewGuid();  
  
                Console.WriteLine("Invoking BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC");  
  
                //invoke RFC_CUSTOMER_GET as a tRFC  
                sapTrfcClient.BAPI_SALESORDER_CREATEFROMDAT2(request.BEHAVE_WHEN_ERROR,  
                                                                request.BINARY_RELATIONSHIPTYPE,  
                                                                request.CONVERT,  
                                                                request.INT_NUMBER_ASSIGNMENT,  
                                                                request.LOGIC_SWITCH,  
                                                                request.ORDER_HEADER_IN,  
                                                                request.ORDER_HEADER_INX,  
                                                                request.SALESDOCUMENTIN,  
                                                                request.SENDER,  
                                                                request.TESTRUN,  
                                                                request.EXTENSIONIN,  
                                                                request.ORDER_CCARD,  
                                                                request.ORDER_CFGS_BLOB,  
                                                                request.ORDER_CFGS_INST,  
                                                                request.ORDER_CFGS_PART_OF,  
                                                                request.ORDER_CFGS_REF,  
                                                                request.ORDER_CFGS_REFINST,  
                                                                request.ORDER_CFGS_VALUE,  
                                                                request.ORDER_CFGS_VK,  
                                                                request.ORDER_CONDITIONS_IN,  
                                                                request.ORDER_CONDITIONS_INX,  
                                                                request.ORDER_ITEMS_IN,  
                                                                request.ORDER_ITEMS_INX,  
                                                                request.ORDER_KEYS,  
                                                                request.ORDER_PARTNERS,  
                                                                request.ORDER_SCHEDULES_IN,  
                                                                request.ORDER_SCHEDULES_INX,  
                                                                request.ORDER_TEXT,  
                                                                request.PARTNERADDRESSES,  
                                                                request.RETURN,  
                                                                ref request.TransactionalRfcOperationIdentifier);  
  
                string sapTxId = null;  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid(request.TransactionalRfcOperationIdentifier);  
  
                Console.WriteLine("BAPI_SALESORDER_CREATEFROMDAT2 Sent");  
                Console.WriteLine("The SAP Transaction Id is " + sapTxId);  
  
                // Invoke the RfcConfirmTransID method to confirm (commit) the transaction on  
                // the SAP system. This step is required to complete the transaction. The SAP  
                // adapter will always return a TranactionalRfcOperationIdentifier, whether   
                // one was supplied in the call or not.  
                sapTrfcClient.RfcConfirmTransID(request.TransactionalRfcOperationIdentifier);  
  
                Console.WriteLine("SAP Transaction {0} has been committed", sapTxId);  
  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
                throw;  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw;  
            }  
            finally  
            {  
                // Close the client  
                if (sapTrfcClient != null)  
                {  
                    if (sapTrfcClient.State == CommunicationState.Opened)  
                        sapTrfcClient.Close();  
                    else  
                        sapTrfcClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5890d-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5890d-153">See Also</span></span>  
<span data-ttu-id="5890d-154">[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="5890d-154">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="5890d-155">Opérations sur tRFCs dans SAP</span><span class="sxs-lookup"><span data-stu-id="5890d-155">Operations on tRFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)