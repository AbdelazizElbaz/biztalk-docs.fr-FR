---
title: "Opérations sur les documents RFC dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, operations on RFCs
- adapters, operations on IDOCs
- RFC, receiving inbound RFC calls from an SAP system
- RFCs, invoking RFCs on an SAP system
- adapters, operations on BAPIs
- RFC client
- adapters, operations on tRFCs
- RFC server
ms.assetid: ca1b7b00-a9cf-41bc-b87c-2e7ce8cff65c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd4ebbb33e9f9791589a3ef271412c8ae20090f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-rfcs-in-sap"></a><span data-ttu-id="e7283-102">Opérations sur les documents RFC dans SAP</span><span class="sxs-lookup"><span data-stu-id="e7283-102">Operations on RFCs in SAP</span></span>
<span data-ttu-id="e7283-103">Vous pouvez utiliser la[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] à la fois en tant que RFC client et un serveur RFC.</span><span class="sxs-lookup"><span data-stu-id="e7283-103">You can use the[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] both as an RFC client and as an RFC server.</span></span> <span data-ttu-id="e7283-104">Dans les scénarios de client RFC, votre application appelle les RFC sur le système SAP en effectuant des opérations RFC sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7283-104">In RFC client scenarios, your application invokes RFCs on the SAP system by invoking RFC operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e7283-105">Dans des scénarios de serveur RFC SAP système appelle les RFC sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], qui appelle à son tour, le document RFC sous forme d’opération sur votre application.</span><span class="sxs-lookup"><span data-stu-id="e7283-105">In RFC server scenarios the SAP system invokes RFCs on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], which, in turn, invokes the RFC as an operation on your application.</span></span>  
  
## <a name="rfc-operations"></a><span data-ttu-id="e7283-106">Opérations RFC</span><span class="sxs-lookup"><span data-stu-id="e7283-106">RFC Operations</span></span>  
 <span data-ttu-id="e7283-107">RFC sont signalées par un nom en tant qu’opérations sous le nœud de catégorie de métadonnées RFC par la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7283-107">RFCs are surfaced by name as operations under the RFC metadata category node by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e7283-108">(Vous pouvez parcourir ou rechercher les RFC sous le **RFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="e7283-108">(You can browse or search for RFCs under the **RFC** node when you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)</span></span>  
  
 <span data-ttu-id="e7283-109">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peuvent apparaître uniquement ces documents RFC pour lequel il peut récupérer les métadonnées à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-109">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can surface only those RFCs for which it can retrieve metadata from the SAP system.</span></span> <span data-ttu-id="e7283-110">L’adaptateur utilise le SDK RFC pour récupérer ces métadonnées, afin qu’il ne peut pas surface RFC qui contiennent des paramètres avec des types de données qui ne sont pas pris en charge par le SDK RFC.</span><span class="sxs-lookup"><span data-stu-id="e7283-110">The adapter uses the RFC SDK to retrieve this metadata, so it cannot surface RFCs that contain parameters with data types that are not supported by the RFC SDK.</span></span> <span data-ttu-id="e7283-111">Par exemple, l’adaptateur ne peut pas surface RFC qui contiennent des structures de type ITAB II ou tables.</span><span class="sxs-lookup"><span data-stu-id="e7283-111">For example, the adapter cannot surface RFCs that contain ITAB II type structures or tables.</span></span>  
  
 <span data-ttu-id="e7283-112">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les éléments suivants sur les normes RFC :</span><span class="sxs-lookup"><span data-stu-id="e7283-112">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following on RFCs:</span></span>  
  
-   <span data-ttu-id="e7283-113">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="e7283-113">IMPORT parameters</span></span>  
  
-   <span data-ttu-id="e7283-114">Paramètres d’exportation</span><span class="sxs-lookup"><span data-stu-id="e7283-114">EXPORT parameters</span></span>  
  
-   <span data-ttu-id="e7283-115">MODIFICATION des paramètres</span><span class="sxs-lookup"><span data-stu-id="e7283-115">CHANGING parameters</span></span>  
  
 <span data-ttu-id="e7283-116">Pour plus d’informations sur les structures de message et les actions de SOAP utilisées pour les RFC par l’adaptateur, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-116">For more information about the message structures and SOAP actions used for RFCs by the adapter, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
## <a name="invoking-rfcs-on-an-sap-system"></a><span data-ttu-id="e7283-117">Appel de RFC sur un système SAP</span><span class="sxs-lookup"><span data-stu-id="e7283-117">Invoking RFCs on an SAP System</span></span>  
 <span data-ttu-id="e7283-118">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence les RFC en tant qu’opérations individuelles qui prennent le nom de la RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-118">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces RFCs as individual operations that take the name of the RFC on the SAP system.</span></span> <span data-ttu-id="e7283-119">Pour appeler une commande RFC sur le système SAP, vous appelez l’opération RFC nommée de façon appropriée sur la carte.</span><span class="sxs-lookup"><span data-stu-id="e7283-119">To invoke an RFC on the SAP system, you invoke the appropriately named RFC operation on the adapter.</span></span>  
  
 <span data-ttu-id="e7283-120">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="e7283-120">For more information about:</span></span>  
  
-   <span data-ttu-id="e7283-121">Appel d’une commande RFC à l’aide de BizTalk Server, consultez [RFC de code non managé à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-121">Invoking an RFC using BizTalk Server, see [Invoke RFCs by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="e7283-122">Appel d’une demande de changement en utilisant le modèle de service WCF, consultez [appeler les RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-122">Invoking an RFC using the WCF service model, see [Invoke RFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="e7283-123">Appel d’une commande RFC à l’aide du modèle de canal WCF, consultez [appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-123">Invoking an RFC using the WCF channel model, see [Invoke Operations on the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="receiving-inbound-rfc-calls-from-an-sap-system"></a><span data-ttu-id="e7283-124">Appels entrants RFC réception à partir d’un système SAP</span><span class="sxs-lookup"><span data-stu-id="e7283-124">Receiving Inbound RFC Calls from an SAP System</span></span>  
 <span data-ttu-id="e7283-125">Il est possible pour SAP agir comme un client et appeler des modules de fonction sur un serveur RFC externe.</span><span class="sxs-lookup"><span data-stu-id="e7283-125">It is possible for SAP to act as a client and invoke function modules on an external RFC server.</span></span> <span data-ttu-id="e7283-126">Cette fonctionnalité permet de :</span><span class="sxs-lookup"><span data-stu-id="e7283-126">This functionality enables:</span></span>  
  
-   <span data-ttu-id="e7283-127">SAP pour des notifications push vers des systèmes externes sans les systèmes externes devoir interroger continuellement SAP pour les notifications en appelant les RFC.</span><span class="sxs-lookup"><span data-stu-id="e7283-127">SAP to push notifications to external systems without the external systems having to continuously poll SAP for notifications by calling RFCs.</span></span>  
  
-   <span data-ttu-id="e7283-128">L’implémentation de la logique métier en dehors du système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-128">The implementation of business logic outside the SAP system.</span></span> <span data-ttu-id="e7283-129">Le système SAP peut ensuite appeler le programme externe sur le serveur RFC.</span><span class="sxs-lookup"><span data-stu-id="e7283-129">The SAP system can then call the external program on the RFC server.</span></span>  
  
 <span data-ttu-id="e7283-130">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut agir comme un serveur RFC pour recevoir ces RFC les appels entrants à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-130">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can act as an RFC server to receive such inbound RFC calls from the SAP system.</span></span> <span data-ttu-id="e7283-131">Lorsque l’adaptateur reçoit un appel RFC à partir de SAP, il appelle cette opération RFC sur votre application.</span><span class="sxs-lookup"><span data-stu-id="e7283-131">When the adapter receives an RFC call from SAP, it invokes that RFC operation on your application.</span></span>  
  
 <span data-ttu-id="e7283-132">Pour l’adaptateur comme un serveur RFC :</span><span class="sxs-lookup"><span data-stu-id="e7283-132">For the adapter to perform as an RFC server:</span></span>  
  
-   <span data-ttu-id="e7283-133">Le document RFC doit être déclaré dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-133">The RFC must be declared on the SAP system.</span></span> <span data-ttu-id="e7283-134">Il s’agit donc de l’adaptateur peut récupérer les métadonnées qui décrivent la RFC à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-134">This is so the adapter can retrieve metadata that describes the RFC from the SAP system.</span></span> <span data-ttu-id="e7283-135">Le document RFC est réellement implémenté dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e7283-135">The RFC is actually implemented in your application.</span></span>  
  
-   <span data-ttu-id="e7283-136">L’adaptateur doit inscrire avec une destination RFC sur la passerelle SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-136">The adapter must register with an RFC destination on an SAP gateway.</span></span> <span data-ttu-id="e7283-137">L’inscription est basée sur un nom logique est appelé un ID de programme.</span><span class="sxs-lookup"><span data-stu-id="e7283-137">The registration is based on a logical name called a program ID.</span></span> <span data-ttu-id="e7283-138">Vous fournissez des paramètres dans l’URI pour spécifier l’ID de programme, passerelle SAP et de SAP de serveur pour cet enregistrement de connexion.</span><span class="sxs-lookup"><span data-stu-id="e7283-138">You supply parameters in the connection URI to specify the PROGRAM ID, SAP gateway, and SAP server for this registration.</span></span>  
  
 <span data-ttu-id="e7283-139">L’exemple suivant montre le code ABAP requis pour appeler une commande RFC via l’ID de programme, MYDEST.</span><span class="sxs-lookup"><span data-stu-id="e7283-139">The following example shows the ABAP code required to invoke an RFC through the PROGRAM ID, MYDEST.</span></span>  
  
```  
CALL FUNCTION ‘ABC’ DESTINATION ‘MYDEST’  
```  
  
 <span data-ttu-id="e7283-140">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="e7283-140">For more information about:</span></span>  
  
-   <span data-ttu-id="e7283-141">Réception d’un appel de serveur RFC à l’aide de BizTalk Server, consultez [recevoir des appels RFC entrant par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-141">Receiving an RFC server call using BizTalk Server, see [Receive Inbound RFC Calls by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="e7283-142">Réception d’un appel de serveur RFC à l’aide du modèle de service WCF, consultez [recevoir des appels RFC entrant dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-142">Receiving an RFC server call using the WCF service model, see [Receive  Inbound RFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="e7283-143">Réception d’un appel de serveur RFC à l’aide du modèle de canal WCF, consultez [de réception des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-143">Receiving an RFC server call using the WCF channel model, see [Receive Inbound Operations from the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="special-rfc-operations"></a><span data-ttu-id="e7283-144">Opérations RFC spéciaux</span><span class="sxs-lookup"><span data-stu-id="e7283-144">Special RFC Operations</span></span>  
 <span data-ttu-id="e7283-145">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut également effectuer certaines opérations RFC spéciale sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="e7283-145">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can also perform certain special RFC operations on the SAP system.</span></span> <span data-ttu-id="e7283-146">Une telle opération est RfcGetAttributes.</span><span class="sxs-lookup"><span data-stu-id="e7283-146">One such operation is RfcGetAttributes.</span></span>  
  
-   <span data-ttu-id="e7283-147">**RfcGetAttributes**.</span><span class="sxs-lookup"><span data-stu-id="e7283-147">**RfcGetAttributes**.</span></span> <span data-ttu-id="e7283-148">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise cette opération pour obtenir des informations sur les paramètres de connexion RFC comme ID système, page de codes de partenaire et language.</span><span class="sxs-lookup"><span data-stu-id="e7283-148">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses this operation to get information about the RFC connection parameters such as system ID, partner code page, and language.</span></span> <span data-ttu-id="e7283-149">Cette opération n’est disponible sous la **RFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7283-149">This operation is available under the **RFC** node when using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span>  
  
 <span data-ttu-id="e7283-150">Pour plus d’informations sur la structure de message et l’action SOAP pour l’appel d’une opération RfcGetAttributes sur le système SAP, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e7283-150">For more information about message structure and SOAP action for invoking an RfcGetAttributes operation on the SAP system, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7283-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7283-151">See Also</span></span>  
 <span data-ttu-id="e7283-152">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="e7283-152">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>