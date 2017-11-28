---
title: "Dans SAP à l’aide du modèle de Service WCF de réception entrant tRFC appels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving inbound using the WCF service model
- WCF service model, receiving inbound tRFC calls
ms.assetid: 02dc282b-b659-466a-8bd1-f400a05f71ec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fb2091d0701831985a1975aa33bd5ecb667b443
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="3d472-102">Réception entrant tRFC appelle dans SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="3d472-102">Receive Inbound tRFC Calls in SAP using the WCF Service Model</span></span>
<span data-ttu-id="3d472-103">Vous pouvez utiliser la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] comme serveur RFC (tRFC) transactionnels pour recevoir les appels entrants tRFC à partir de SAP.</span><span class="sxs-lookup"><span data-stu-id="3d472-103">You can use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a transactional RFC (tRFC) server to receive inbound tRFC calls from SAP.</span></span> <span data-ttu-id="3d472-104">Pour le trafic entrant tRFCs, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge plusieurs tRFCs dans la même unité logique de SAP de travail (LUW).</span><span class="sxs-lookup"><span data-stu-id="3d472-104">For inbound tRFCs, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports multiple tRFCs in the same SAP logical unit of work (LUW).</span></span>  
  
 <span data-ttu-id="3d472-105">Les sections de cette rubrique fournissent des informations sur l’utilisation de la carte en tant que tRFC serveur dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="3d472-105">The sections in this topic provide information about how to use the adapter as a tRFC server in the WCF service model.</span></span>  
  
 <span data-ttu-id="3d472-106">Vous trouverez plus d’informations sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme serveur tRFC dans les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3d472-106">You can find more information about using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a tRFC server in the following topics:</span></span>  
  
-   <span data-ttu-id="3d472-107">Pour une vue d’ensemble de la prise en charge pour tRFCs sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="3d472-107">For an overview of support for tRFCs on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span> <span data-ttu-id="3d472-108">Vous devez lire cette rubrique avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3d472-108">You should read this topic before continuing.</span></span>  
  
-   <span data-ttu-id="3d472-109">Pour plus d’informations sur les schémas de message pour les opérations de serveur tRFC, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="3d472-109">For more information about the message schemas for tRFC server operations, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
## <a name="the-wcf-service-contract-for-a-trfc"></a><span data-ttu-id="3d472-110">Le contrat de Service WCF pour un tRFC</span><span class="sxs-lookup"><span data-stu-id="3d472-110">The WCF Service Contract for a tRFC</span></span>  
 <span data-ttu-id="3d472-111">Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un contrat de service WCF pour le tRFCs que vous souhaitez recevoir à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="3d472-111">You use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF service contract for the tRFCs that you want to receive from the SAP system.</span></span> <span data-ttu-id="3d472-112">Le contrat généré pour un tRFC entrant est similaire à celui généré par une commande RFC entrante, sauf que :</span><span class="sxs-lookup"><span data-stu-id="3d472-112">The contract generated for an inbound tRFC is similar to that generated for an inbound RFC except that:</span></span>  
  
-   <span data-ttu-id="3d472-113">les opérations tRFC sont signalées sous le nœud TRFC.</span><span class="sxs-lookup"><span data-stu-id="3d472-113">tRFC operations are surfaced under the TRFC node.</span></span>  
  
-   <span data-ttu-id="3d472-114">Le contrat de service WCF (interface) généré pour tRFCs entrant est nommé « Trfc ».</span><span class="sxs-lookup"><span data-stu-id="3d472-114">The WCF service contract (interface) generated for incoming tRFCs is named "Trfc".</span></span> <span data-ttu-id="3d472-115">Vous devez spécifier cette interface lorsque vous ajoutez le point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3d472-115">You must specify this interface when you add the service endpoint to the service host.</span></span> <span data-ttu-id="3d472-116">C’est également l’interface que votre service WCF doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="3d472-116">This is also the interface that your WCF service must implement.</span></span>  
  
    ```  
    public interface Trfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Trfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD/response")]  
        Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
    }  
    ```  
  
-   <span data-ttu-id="3d472-117">Le contrat de message de demande pour les opérations TRFC a un paramètre GUID.</span><span class="sxs-lookup"><span data-stu-id="3d472-117">The request message contract for TRFC operations has a GUID parameter.</span></span> <span data-ttu-id="3d472-118">Il s’agit de GUID qui mappe vers le TID SAP pour le tRFC.</span><span class="sxs-lookup"><span data-stu-id="3d472-118">This is the GUID that maps to the SAP TID for the tRFC.</span></span> <span data-ttu-id="3d472-119">Dans les opérations de serveur tRFC, l’adaptateur gère tous les appels à la validation, la restauration et confirmer le TID par le système SAP, donc il est inutile d’utiliser explicitement de ce GUID.</span><span class="sxs-lookup"><span data-stu-id="3d472-119">In tRFC server operations, the adapter manages all calls to commit, rollback, and confirm the TID by the SAP system so there is no reason for you to explicitly use this GUID.</span></span> <span data-ttu-id="3d472-120">Toutefois, vous pouvez l’utiliser pour récupérer le TID SAP à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en appelant **SapAdapterUtilities.ConvertGuidToTid**.</span><span class="sxs-lookup"><span data-stu-id="3d472-120">However, you can use it to retrieve the SAP TID from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by calling **SapAdapterUtilities.ConvertGuidToTid**.</span></span> <span data-ttu-id="3d472-121">Cela peut être utile pour vous aider à résoudre les problèmes sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="3d472-121">This can be useful to help you troubleshoot issues on the SAP system.</span></span>  
  
    ```  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Trfc/", IsWrapped=true)]  
    public partial class Z_RFC_MKD_ADDRequest {  
  
        ...  
  
        public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y, System.Guid TransactionalRfcOperationIdentifier) {  
            this.DEST = DEST;  
            this.X = X;  
            this.Y = Y;  
            this.TransactionalRfcOperationIdentifier = TransactionalRfcOperationIdentifier;  
        }  
    }  
  
    ```  
  
## <a name="how-do-i-enable-the-adapter-to-act-as-a-trfc-server"></a><span data-ttu-id="3d472-122">Comment activer l’adaptateur pour agir comme un serveur tRFC ?</span><span class="sxs-lookup"><span data-stu-id="3d472-122">How do I Enable the Adapter to Act as a tRFC Server?</span></span>  
 <span data-ttu-id="3d472-123">Pour activer l’adaptateur d’agir en tant que tRFC serveur, vous devez définir le **TidDatabaseConnectionString** liaison de propriété à la chaîne de connexion pour la base de données TID.</span><span class="sxs-lookup"><span data-stu-id="3d472-123">To enable the adapter to act as a tRFC server, you must set the **TidDatabaseConnectionString** binding property to the connection string for the TID database.</span></span> <span data-ttu-id="3d472-124">Vous devez le faire avant d’ouvrir l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="3d472-124">You should do this before you open the service host.</span></span> <span data-ttu-id="3d472-125">Il s’agit de la base de données dans laquelle l’adaptateur stocke la transaction SAP ID (TID) pour chaque tRFC.</span><span class="sxs-lookup"><span data-stu-id="3d472-125">This is the database in which the adapter stores the SAP transaction ID (TID) for each tRFC.</span></span> <span data-ttu-id="3d472-126">Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3d472-126">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
## <a name="how-do-i-enlist-in-the-transaction-for-inbound-trfcs"></a><span data-ttu-id="3d472-127">Comment inscrire la transaction de tRFCs entrant ?</span><span class="sxs-lookup"><span data-stu-id="3d472-127">How do I Enlist in the Transaction for Inbound tRFCs?</span></span>  
 <span data-ttu-id="3d472-128">Une SAP logique unité de travail (LUW) peut contenir plusieurs tRFCs.</span><span class="sxs-lookup"><span data-stu-id="3d472-128">An SAP Logical Unit of Work (LUW) can contain multiple tRFCs.</span></span> <span data-ttu-id="3d472-129">Sur le système SAP, un LUW est identifié par un ID de Transaction unique (TID).</span><span class="sxs-lookup"><span data-stu-id="3d472-129">On the SAP system a LUW is identified by a unique Transaction ID (TID).</span></span> <span data-ttu-id="3d472-130">L’adaptateur crée une transaction validable pour chacun du TID par le système SAP lorsqu’il appelle tRFC des appels sur la carte.</span><span class="sxs-lookup"><span data-stu-id="3d472-130">The adapter creates a committable transaction for each of the TIDs that the SAP system uses when it invokes tRFC calls on the adapter.</span></span> <span data-ttu-id="3d472-131">Lorsque le système SAP appelle un tRFC sur la carte ; l’adaptateur transmet la transaction associée le TID SAP à votre service.</span><span class="sxs-lookup"><span data-stu-id="3d472-131">When the SAP system invokes a tRFC on the adapter; the adapter flows the transaction associated with the SAP TID to your service.</span></span> <span data-ttu-id="3d472-132">Vous pouvez accéder à cette transaction en tant que la transaction ambiante d’à l’intérieur de votre méthode d’opération.</span><span class="sxs-lookup"><span data-stu-id="3d472-132">You can access this transaction as the ambient transaction from inside your operation method.</span></span> <span data-ttu-id="3d472-133">En inscrivant dans cette transaction ambiante, les actions effectuées dans l’opération peuvent participer à la LUW SAP.</span><span class="sxs-lookup"><span data-stu-id="3d472-133">By enlisting in this ambient transaction, the actions performed in the operation can participate in the SAP LUW.</span></span>  
  
 <span data-ttu-id="3d472-134">Pour inscrire dans la transaction ambiante dans une méthode d’opération, vous devez :</span><span class="sxs-lookup"><span data-stu-id="3d472-134">To enlist in the ambient transaction in an operation method, you must:</span></span>  
  
1.  <span data-ttu-id="3d472-135">Annoter la méthode d’opération avec le **TransactionScopeRequired** propriété de la **OperationBehavior** attribut.</span><span class="sxs-lookup"><span data-stu-id="3d472-135">Annotate the operation method with the **TransactionScopeRequired** property of the **OperationBehavior** attribute.</span></span> <span data-ttu-id="3d472-136">Cela indique à WCF que vous souhaitez accéder à la transaction ambiante d’à l’intérieur de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3d472-136">This tells WCF that you want access to the ambient transaction from inside the operation.</span></span>  
  
2.  <span data-ttu-id="3d472-137">Créer une étendue de transaction soit en annotant la méthode d’opération avec le **TransactionAutoComplete** propriété de la **OperationBehavior** attribut ou en utilisant explicitement un  **TransactionScope** à l’intérieur de la méthode d’opération.</span><span class="sxs-lookup"><span data-stu-id="3d472-137">Create a transaction scope either by annotating the operation method with the **TransactionAutoComplete** property of the **OperationBehavior** attribute or by explicitly using a **TransactionScope** inside the operation method.</span></span>  
  
 <span data-ttu-id="3d472-138">L’exemple suivant montre un service qui implémente les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="3d472-138">The following example shows a service that implements two operations.</span></span> <span data-ttu-id="3d472-139">Les deux méthodes d’opération sont annotés avec les **TransactionScopeRequired** propriété pour accéder à la transaction ambiante.</span><span class="sxs-lookup"><span data-stu-id="3d472-139">Both operation methods are annotated with the **TransactionScopeRequired** property to access the ambient transaction.</span></span>  
  
-   <span data-ttu-id="3d472-140">**Z_TRFC_EXAMPLE1** explicitement s’inscrit dans la transaction en utilisant un **TransactionScope** objet.</span><span class="sxs-lookup"><span data-stu-id="3d472-140">**Z_TRFC_EXAMPLE1** explicitly enlists in the transaction by using a **TransactionScope** object.</span></span>  
  
-   <span data-ttu-id="3d472-141">**Z_TRFC_EXAMPLE2** est annoté avec le **TransactionAutoComplete** propriété à inscrire dans la transaction</span><span class="sxs-lookup"><span data-stu-id="3d472-141">**Z_TRFC_EXAMPLE2** is annotated with the **TransactionAutoComplete** property to enlist in the transaction</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, UseSynchronizationContext = false)]  
class Z_Example_ServiceContractClass : Trfc  
{  
  
    // This operation method explicitly creates a TransactionScope to enlist in the ambient transaction  
    // You must explictly call ts.Complete to complete the transaction before you return from the operation  
    // Otherwise the transaction is aborted.  
    // You can throw an exception or return without calling ts.complete to abort the transacation  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public Z_TRFC_EXAMPLE1Response Z_TRFC_EXAMPLE1(Z_TRFC_EXAMPLE1Request request)  
    {  
        using (TransactionScope ts = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Process tRFC  
  
            ...  
  
            Z_TRFC_EXAMPLE1Response response = new Z_TRFC_EXAMPLE1Response();  
            response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
            return response;  
            //since there is no ts.Complete(), this is equivalent to a rollback.  
        }  
    }  
  
    // This operation method sets the TransactionAutoComplete property of the OperationBehavior attribute  
    // to enlist in the transaction. There is no need to explictly create a TransactionScope in the code.  
    // If the method returns with no unhandled exceptions, the transaction completes; otherwise it aborts  
    // You can throw an exception to abort the transaction.  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public Z_TRFC_EXAMPLE2Response Z_TRFC_EXAMPLE2(Z_TRFC_EXAMPLE2Request request)  
    {  
        // Process tRFC  
  
        ...  
  
        Z_TRFC_EXAMPLE2Response response = new Z_TRFC_EXAMPLE2Response();  
        response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
        return response;  
        //if there is no unhandled exception, the transaction completes when the operation returns.  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d472-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d472-142">See Also</span></span>  
[<span data-ttu-id="3d472-143">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="3d472-143">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)