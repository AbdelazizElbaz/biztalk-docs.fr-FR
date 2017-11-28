---
title: "Appeler les BAPI dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAPIs, invoking by using the WCF service model
- WCF service model, invoking BAPIs
ms.assetid: be3c48d6-2213-4ae5-97f4-634fbc423022
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 437c88516cfb771e0e5ae10807391235d602eb37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-bapis-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="af67f-102">Appeler les BAPI dans SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="af67f-102">Invoke BAPIs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="af67f-103">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des interfaces BAPI en tant que :</span><span class="sxs-lookup"><span data-stu-id="af67f-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs as:</span></span>  
  
-   <span data-ttu-id="af67f-104">**Opérations RFC**.</span><span class="sxs-lookup"><span data-stu-id="af67f-104">**RFC operations**.</span></span> <span data-ttu-id="af67f-105">Interfaces BAPI comme n’importe quel autre RFC sont signalées sous le nœud RFC dans la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af67f-105">BAPIs like any other RFC are surfaced under the RFC node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="af67f-106">**Méthodes des objets métiers SAP**.</span><span class="sxs-lookup"><span data-stu-id="af67f-106">**Methods of SAP business objects**.</span></span> <span data-ttu-id="af67f-107">En tant que méthodes d’objets métier, les interfaces BAPI sont signalées par un objet métier sous le nœud BAPI dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af67f-107">As methods of business objects, BAPIs are surfaced by business object under the BAPI node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
 <span data-ttu-id="af67f-108">Si vous appelez un BAPI sous la forme d’une opération de RFC ou une méthode d’objet métier, chaque BAPI fait toujours partie d’un LUW sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-108">Whether you invoke a BAPI as an RFC operation or as a business object method, each BAPI is always part of an LUW on the SAP system.</span></span>  
  
 <span data-ttu-id="af67f-109">Pour une vue d’ensemble de la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="af67f-109">For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
 <span data-ttu-id="af67f-110">Lorsque vous utilisez le modèle de service WCF pour appeler des interfaces BAPI en tant que méthodes d’objet métier, chaque objet de métier SAP est représenté par une classe de client WCF et les interfaces BAPI de cet objet sont représentés en tant que méthodes sur le client.</span><span class="sxs-lookup"><span data-stu-id="af67f-110">When you use the WCF service model to invoke BAPIs as business object methods, each SAP business object is represented by a WCF client class and the BAPIs of that business object are represented as methods on the client.</span></span> <span data-ttu-id="af67f-111">Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF pour les objets métier spécifique qui contient des méthodes pour chaque BAPI que vous souhaitez appeler dans votre code.</span><span class="sxs-lookup"><span data-stu-id="af67f-111">You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class for specific business objects that contains methods for each BAPI that you want to invoke in your code.</span></span> <span data-ttu-id="af67f-112">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également des types .NET pour encapsuler les paramètres et types de données qui sont utilisés par chaque BAPI.</span><span class="sxs-lookup"><span data-stu-id="af67f-112">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates .NET types to encapsulate the parameters and data types that are used by each BAPI.</span></span> <span data-ttu-id="af67f-113">Vous pouvez ensuite créer une instance de cette classe de client WCF et appeler ses méthodes pour appeler la cible de BAPI.</span><span class="sxs-lookup"><span data-stu-id="af67f-113">You can then create an instance of this WCF client class and call its methods to invoke the target BAPIs.</span></span>  
  
 <span data-ttu-id="af67f-114">Les sections suivantes vous montrent comment appeler des interfaces BAPI en tant que méthodes d’objets métier et expliquent comment les transactions BAPI sont prises en charge dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-114">The following sections show you how to invoke BAPIs as methods of business objects and discuss how BAPI transactions are supported in the WCF service model.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="af67f-115">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="af67f-115">The WCF Client Class</span></span>  
 <span data-ttu-id="af67f-116">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence un autre contrat de service, pour chaque objet de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="af67f-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a different service contract, for each business object.</span></span> <span data-ttu-id="af67f-117">Cela signifie que, pour chaque objet métier WCF unique classe de client est créée.</span><span class="sxs-lookup"><span data-stu-id="af67f-117">This means that for each business object a unique WCF client class is created.</span></span> <span data-ttu-id="af67f-118">Le nom de cette classe est basé sur le type d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="af67f-118">The name of this class is based on the business object type.</span></span> <span data-ttu-id="af67f-119">Par exemple pour l’objet métier Sales Order (type d’objet métier BUS2032), la classe de client WCF est **BapiBUS2032Client**.</span><span class="sxs-lookup"><span data-stu-id="af67f-119">For example for the Sales Order business object (business object type BUS2032), the WCF client class is **BapiBUS2032Client**.</span></span> <span data-ttu-id="af67f-120">Chaque cible BAPI dans l’objet métier est représentée comme une méthode dans la classe de client WCF générée.</span><span class="sxs-lookup"><span data-stu-id="af67f-120">Each target BAPI in the business object is represented as a method in the generated WCF client class.</span></span> <span data-ttu-id="af67f-121">Dans chaque méthode :</span><span class="sxs-lookup"><span data-stu-id="af67f-121">In each method:</span></span>  
  
-   <span data-ttu-id="af67f-122">Paramètres d’exportation SAP sont exposés en tant que **hors** paramètres</span><span class="sxs-lookup"><span data-stu-id="af67f-122">SAP export parameters are surfaced as **out** parameters</span></span>  
  
-   <span data-ttu-id="af67f-123">Paramètres d’appel SAP sont exposés en tant que **ref** paramètres.</span><span class="sxs-lookup"><span data-stu-id="af67f-123">SAP calling parameters are surfaced as **ref** parameters.</span></span>  
  
-   <span data-ttu-id="af67f-124">Les types SAP complexes telles que les structures sont signalées en tant que classes .NET avec des propriétés qui correspondent aux champs de type SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-124">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="af67f-125">Ces classes sont définies dans l’espace de noms suivant : microsoft.lobservices.sap._2007._03.Types.Rfc.</span><span class="sxs-lookup"><span data-stu-id="af67f-125">These classes are defined in the following namespace: microsoft.lobservices.sap._2007._03.Types.Rfc.</span></span>  
  
 <span data-ttu-id="af67f-126">BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK sont signalées pour chaque objet de l’entreprise et vous devez toujours inclure ces éléments dans votre client WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-126">BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK are surfaced for each business object and you should always include these in your WCF client.</span></span>  
  
 <span data-ttu-id="af67f-127">Le code suivant montre une partie d’une classe de client WCF générée pour l’objet d’entreprise de vente.</span><span class="sxs-lookup"><span data-stu-id="af67f-127">The following code shows part of a WCF client class generated for the Sales Order business object.</span></span> <span data-ttu-id="af67f-128">Ce client contient des méthodes pour appeler CREATEFROMDAT2, BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK.</span><span class="sxs-lookup"><span data-stu-id="af67f-128">This client contains methods to invoke CREATEFROMDAT2, BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK.</span></span> <span data-ttu-id="af67f-129">Les constructeurs et tout autre code a été omis par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="af67f-129">For clarity the constructors and other code has been omitted.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class BapiBUS2032Client : System.ServiceModel.ClientBase<BapiBUS2032>, BapiBUS2032 {  
  
    // Code has been removed for clarity  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="SALESDOCUMENT">Number of Generated Document</param>  
    /// <param name="BEHAVE_WHEN_ERROR">Error Handling</param>  
    /// …  
    /// <param name="ORDER_TEXT">Texts</param>  
    /// <param name="PARTNERADDRESSES">BAPI Reference Structure for Addresses (Org./Company)</param>  
    /// <param name="RETURN">Return Messages</param>  
    /// <returns></returns>  
    public string CREATEFROMDAT2(  
                string BEHAVE_WHEN_ERROR,   
                string BINARY_RELATIONSHIPTYPE,   
                string CONVERT,   
                string INT_NUMBER_ASSIGNMENT,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDLS LOGIC_SWITCH,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1 ORDER_HEADER_IN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1X ORDER_HEADER_INX,   
                string SALESDOCUMENTIN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPI_SENDER SENDER,   
                string TESTRUN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPAREX[] EXTENSIONIN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICCARD[] ORDER_CCARD,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUBLB[] ORDER_CFGS_BLOB,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUINS[] ORDER_CFGS_INST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUPRT[] ORDER_CFGS_PART_OF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUCFG[] ORDER_CFGS_REF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUREF[] ORDER_CFGS_REFINST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVAL[] ORDER_CFGS_VALUE,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVK[] ORDER_CFGS_VK,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICOND[] ORDER_CONDITIONS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICONDX[] ORDER_CONDITIONS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITM[] ORDER_ITEMS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITMX[] ORDER_ITEMS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDKEY[] ORDER_KEYS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPARNR[] ORDER_PARTNERS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDL[] ORDER_SCHEDULES_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDLX[] ORDER_SCHEDULES_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDTEXT[] ORDER_TEXT,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIADDR1[] PARTNERADDRESSES,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2[] RETURN) { ...}  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <param name="WAIT">Using the command `COMMIT AND WAIT`</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_COMMIT(string WAIT) { ... }  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_ROLLBACK() { ... }  
}  
```  
  
## <a name="bapi-transactions-in-the-wcf-service-model"></a><span data-ttu-id="af67f-130">Transactions BAPI dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="af67f-130">BAPI Transactions in the WCF Service Model</span></span>  
 <span data-ttu-id="af67f-131">Chaque BAPI, si elle est appelée en tant qu’une demande de changement ou une méthode d’objet métier, fait partie d’une transaction (LUW) sur le système SAP. et chaque BAPI reçu sur la même connexion SAP fait partie de la même transaction BAPI sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-131">Every BAPI, whether it is invoked as an RFC or as a business object method, is part of a transaction (LUW) on the SAP system; and every BAPI received over the same SAP connection is part of the same BAPI transaction on the SAP system.</span></span> <span data-ttu-id="af67f-132">SAP valide ou annule la transaction BAPI lorsqu’il reçoit un BAPI_TRANSACTION_COMMIT ou un BAPI_TRANSACTION_ROLLBACK sur la connexion.</span><span class="sxs-lookup"><span data-stu-id="af67f-132">SAP commits or rolls back the BAPI transaction when it receives a BAPI_TRANSACTION_COMMIT or a BAPI_TRANSACTION_ROLLBACK on the connection.</span></span> <span data-ttu-id="af67f-133">Après qu’une validation ou restauration a été effectuée, BAPI suivant reçu sur la connexion commence une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-133">After a commit or rollback has been performed, the next BAPI received over the connection begins a new transaction.</span></span>  
  
 <span data-ttu-id="af67f-134">Pour la carte chaque canal WCF dispose d’une connexion SAP dédiée.</span><span class="sxs-lookup"><span data-stu-id="af67f-134">For the adapter each WCF channel has a dedicated SAP connection.</span></span> <span data-ttu-id="af67f-135">Dans le modèle de service WCF, chaque client WCF a un canal interne qui est utilisé d’envoyer des messages au système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-135">In the WCF service model, each WCF client has an inner channel that is used send messages to the SAP system.</span></span> <span data-ttu-id="af67f-136">Cela signifie que les interfaces BAPI qui sont appelées à l’aide d’un client WCF spécifique font partie d’une transaction BAPI unique sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-136">This means that the BAPIs that are invoked using a specific WCF client are part of a unique BAPI transaction on the SAP system.</span></span> <span data-ttu-id="af67f-137">Cela constitue une limitation importante lorsque vous utilisez le modèle de service WCF pour appeler des interfaces BAPI en tant que méthodes d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="af67f-137">This imposes a significant limitation when you use the WCF service model to invoke BAPIs as business object methods.</span></span> <span data-ttu-id="af67f-138">Étant donné que chaque objet de métier SAP est représenté par une classe de client WCF dédiée, vous ne pouvez pas appeler BAPI à partir de deux objets différents dans le cadre de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-138">Because each SAP business object is represented by a dedicated WCF client class, you cannot invoke BAPIs from two different business objects as part of the same transaction.</span></span> <span data-ttu-id="af67f-139">La contourner ce problème consiste à appeler les interfaces BAPI en tant qu’opérations de RFC.</span><span class="sxs-lookup"><span data-stu-id="af67f-139">The way around this is to invoke the BAPIs as RFC operations.</span></span> <span data-ttu-id="af67f-140">C’est parce que le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère un seul client WCF pour les opérations de RFC, et, par conséquent, toutes les opérations sont appelées à l’aide de ce client sont envoyées via le même canal WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-140">This is because the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates a single WCF client for RFC operations, and, therefore, all operations invoked using that client are sent over the same WCF channel.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af67f-141">Si vous souhaitez inclure des interfaces BAPI issues d’objets SAP différentes dans la même transaction BAPI, vous devez les appeler en tant qu’opérations RFC (à l’aide de ce même client WCF).</span><span class="sxs-lookup"><span data-stu-id="af67f-141">If you want to include BAPIs from different SAP business objects in the same BAPI transaction, you must invoke them as RFC operations (using the same WCF client).</span></span> <span data-ttu-id="af67f-142">Vous ne pouvez pas les appeler en tant que méthodes d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="af67f-142">You cannot invoke them as business object methods.</span></span>  
  
 <span data-ttu-id="af67f-143">Vous appelez BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK pour valider ou restaurer la transaction BAPI sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-143">You call BAPI_TRANSACTION_COMMIT or BAPI_TRANSACTION_ROLLBACK to commit or roll back the BAPI transaction on the SAP system.</span></span> <span data-ttu-id="af67f-144">L’adaptateur met en évidence ces interfaces deux BAPI :</span><span class="sxs-lookup"><span data-stu-id="af67f-144">The adapter surfaces these two BAPIs:</span></span>  
  
-   <span data-ttu-id="af67f-145">Sous le nœud de base en tant qu’opérations de RFC.</span><span class="sxs-lookup"><span data-stu-id="af67f-145">Under the Basis node as RFC operations.</span></span>  
  
-   <span data-ttu-id="af67f-146">Sous chaque objet de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="af67f-146">Under each business object.</span></span>  
  
 <span data-ttu-id="af67f-147">Pour plus d’informations sur la façon dont l’adaptateur prend en charge les transactions BAPI sur SAP, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="af67f-147">For more information about how the adapter supports BAPI transactions on SAP, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="how-to-create-an-application-that-invokes-bapis-as-methods-of-business-objects"></a><span data-ttu-id="af67f-148">Comment créer une Application qui appelle des interfaces BAPI en tant que méthodes d’objets métier</span><span class="sxs-lookup"><span data-stu-id="af67f-148">How to Create an Application that Invokes BAPIs as Methods of Business Objects</span></span>  
 <span data-ttu-id="af67f-149">Cette section fournit des informations sur l’appel des interfaces BAPI en tant que méthodes d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="af67f-149">This section provides information about how to invoke BAPIs as methods of business objects.</span></span> <span data-ttu-id="af67f-150">La même procédure doit être suivie pour appeler des interfaces BAPI en tant qu’opérations de RFC, à ceci près que vous créez un client WCF qui cible les BAPI en tant qu’opérations RFC et l’utiliser pour appeler chaque BAPI.</span><span class="sxs-lookup"><span data-stu-id="af67f-150">The same basic procedure should be followed to invoke BAPIs as RFC operations, except that you create a WCF client that targets the BAPIs as RFC operations and use it to invoke each BAPI.</span></span>  
  
 <span data-ttu-id="af67f-151">Pour créer une application cliente BAPI, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="af67f-151">To create a BAPI client application, perform the following steps.</span></span>  
  
#### <a name="to-create-an-bapi-client-application"></a><span data-ttu-id="af67f-152">Pour créer une application cliente BAPI</span><span class="sxs-lookup"><span data-stu-id="af67f-152">To create an BAPI client application</span></span>  
  
1.  <span data-ttu-id="af67f-153">Générer une classe de client WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-153">Generate a WCF client class.</span></span> <span data-ttu-id="af67f-154">Utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou ServiceModel Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF (ou classes) qui cible les objets et interfaces BAPI avec lequel vous souhaitez travailler.</span><span class="sxs-lookup"><span data-stu-id="af67f-154">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class (or classes) that targets the business objects and BAPIs with which you want to work.</span></span> <span data-ttu-id="af67f-155">Veillez à inclure le BAPI_TRANSACTION_COMMIT et les méthodes BAPI_TRANSACTION_ROLLBACK (BAPI) exposées pour chaque objet d’entreprise cible.</span><span class="sxs-lookup"><span data-stu-id="af67f-155">Be sure to include the BAPI_TRANSACTION_COMMIT and the BAPI_TRANSACTION_ROLLBACK methods (BAPIs) exposed for each target business object.</span></span> <span data-ttu-id="af67f-156">Pour plus d’informations sur la façon de générer un client WCF, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="af67f-156">For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="af67f-157">Créez une instance de la classe de client WCF générée à l’étape 1 et créer et configurer un client WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-157">Create an instance of the WCF client class generated in step 1, and create and configure a WCF client.</span></span> <span data-ttu-id="af67f-158">Configuration du client WCF implique la spécification de la liaison et l’adresse de point de terminaison que le client utilisera.</span><span class="sxs-lookup"><span data-stu-id="af67f-158">Configuring the WCF client involves specifying the binding and endpoint address that the client will use.</span></span> <span data-ttu-id="af67f-159">Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="af67f-159">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="af67f-160">Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="af67f-160">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="af67f-161">Le code suivant initialise le client WCF pour l’objet métier SAP de vente (BUS2032) à partir de la configuration et définit les informations d’identification pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-161">The following code initializes the WCF client for the Sales Order (BUS2032) SAP business object from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    BapiBUS2032Client bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
    bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
    bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="af67f-162">Ouvrez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-162">Open the WCF client.</span></span>  
  
    ```  
    bapiClient.Open();  
    ```  
  
4.  <span data-ttu-id="af67f-163">Appeler des méthodes sur le client WCF créé à l’étape 2 pour appeler les interfaces BAPI appropriés sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-163">Invoke methods on the WCF client created in step 2 to invoke the appropriate BAPIs on the SAP system.</span></span> <span data-ttu-id="af67f-164">Vous pouvez appeler plusieurs interfaces BAPI sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="af67f-164">You can invoke multiple BAPIs on the SAP system.</span></span>  
  
5.  <span data-ttu-id="af67f-165">Terminer la transaction par :</span><span class="sxs-lookup"><span data-stu-id="af67f-165">End the transaction by:</span></span>  
  
    1.  <span data-ttu-id="af67f-166">Appeler la méthode BAPI_TRANSACTION_COMMIT pour valider la transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-166">Invoking the BAPI_TRANSACTION_COMMIT method to commit the transaction.</span></span>  
  
        ```  
        bapiClient.BAPI_TRANSACTION_COMMIT("X");  
        ```  
  
    2.  <span data-ttu-id="af67f-167">Appeler la méthode BAPI_TRANSACTION_ROLLBACK pour restaurer la transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-167">Invoking the BAPI_TRANSACTION_ROLLBACK method to roll back the transaction.</span></span>  
  
        ```  
        bapiClient.BAPI_TRANSACTION_ROLLBACK();  
        ```  
  
6.  <span data-ttu-id="af67f-168">Fermez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="af67f-168">Close the WCF client.</span></span>  
  
    ```  
    bapiClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="af67f-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="af67f-169">Example</span></span>  
 <span data-ttu-id="af67f-170">L’exemple suivant appelle BAPI CREATEFROMDAT2 sur l’objet métier Sales Order.</span><span class="sxs-lookup"><span data-stu-id="af67f-170">The following example invokes the CREATEFROMDAT2 BAPI on the Sales Order business object.</span></span> <span data-ttu-id="af67f-171">Il appelle BAPI plusieurs fois et appelle ensuite BAPI_TRANSACTION_COMMIT pour valider la transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-171">It invokes the BAPI several times and then invokes BAPI_TRANSACTION_COMMIT to commit the transaction.</span></span> <span data-ttu-id="af67f-172">Si une erreur se produit lors de l’appel BAPI, BAPI_TRANSACTION_ROLLBACK est appelé dans le Gestionnaire d’exceptions pour annuler la transaction.</span><span class="sxs-lookup"><span data-stu-id="af67f-172">If an error occurs when invoking the BAPI, BAPI_TRANSACTION_ROLLBACK is invoked in the exception handler to roll back the transaction.</span></span>  
  
 <span data-ttu-id="af67f-173">La méthode CREATEFROMDAT2 prend de paramètres ; ils sont omis dans l’exemple par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="af67f-173">The CREATEFROMDAT2 method takes many parameters; these are omitted in the example for the sake of brevity.</span></span> <span data-ttu-id="af67f-174">Vous trouverez un exemple qui montre comment les transactions BAPI dans les exemples fournis avec Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af67f-174">You can find a sample that demonstrates BAPI transactions in the samples shipped with the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="af67f-175">Pour plus d’informations, consultez [exemples pour l’adaptateur SAP ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="af67f-175">For more information, see [Samples for the SAP Adapter ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using microsoft.lobservices.sap._2007._03.Types.Rfc;  
  
// This Example demonstrates BAPI transactions. Two sales orders are  
// created using the CREATEFROMDAT2 method of a SAP Business Object.   
// After the orders are created, the BAPI transaction is committed.   
// If an exception occurs when sending the BAPIs, the BAPI transaction is   
// rolled back.  
//   
  
namespace SapBapiTxClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the BAPI client from the generated endpoint configuration.  
  
            BapiBUS2032Client bapiClient = null;  
  
            Console.WriteLine("BAPI transaction sample started");  
            Console.WriteLine("\nCreating business object client");  
  
            try  
            {  
                bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
                bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
                bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the BAPI Client  
                bapiClient.Open();  
  
                ...  
  
                // send first BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters ommitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // send second BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters omitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // Commit BAPI Transaction  
                try  
                {  
                    bapiClient.BAPI_TRANSACTION.Commit();  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
            }  
            catch (ConnectionException cex)  
            {  
                // Get here if problem connecting to the SAP system   
  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                // Get here if the SAP system returns an exception  
  
                Console.WriteLine("Exception occurred on the SAP System");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
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
            // Close the client when finished  
                if (bapiClient != null)  
                {  
                    if (bapiClient.State == CommunicationState.Opened)  
                        bapiClient.Close();  
                    else  
                        bapiClient.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="af67f-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af67f-176">See Also</span></span>  
[<span data-ttu-id="af67f-177">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="af67f-177">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)  
 [<span data-ttu-id="af67f-178">Opérations sur les BAPI dans SAP</span><span class="sxs-lookup"><span data-stu-id="af67f-178">Operations on BAPIs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)