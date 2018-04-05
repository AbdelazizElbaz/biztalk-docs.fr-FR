---
title: Opérations spéciales | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, special operations surfaced by the SAP adapter
ms.assetid: 8725fe63-6ff4-49c8-b386-d4c67e2be440
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe2472d905e9e726b827d44da79bdfe840233354
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="special-operations"></a><span data-ttu-id="18f71-102">Opérations spéciales</span><span class="sxs-lookup"><span data-stu-id="18f71-102">Special Operations</span></span>
<span data-ttu-id="18f71-103">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose plusieurs opérations spéciales.</span><span class="sxs-lookup"><span data-stu-id="18f71-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces several special operations.</span></span> <span data-ttu-id="18f71-104">Ces opérations ne sont pas basées sur les artefacts du système SAP.</span><span class="sxs-lookup"><span data-stu-id="18f71-104">These operations are not based on SAP system artifacts.</span></span> <span data-ttu-id="18f71-105">Elles sont signalées pour fournir des fonctionnalités pour les applications clientes de carte.</span><span class="sxs-lookup"><span data-stu-id="18f71-105">They are surfaced to provide functionality for adapter client applications.</span></span> <span data-ttu-id="18f71-106">Les opérations spéciales sont :</span><span class="sxs-lookup"><span data-stu-id="18f71-106">The special operations are:</span></span>  
  
-   <span data-ttu-id="18f71-107">**RfcGetAttributes**.</span><span class="sxs-lookup"><span data-stu-id="18f71-107">**RfcGetAttributes**.</span></span> <span data-ttu-id="18f71-108">Cette opération est exposée en surface sous le nœud RFC et expose les fonctionnalités du SDK RFC.</span><span class="sxs-lookup"><span data-stu-id="18f71-108">This operation is surfaced under the RFC node and exposes functionality of the RFC SDK.</span></span> <span data-ttu-id="18f71-109">Il fournit les informations suivantes sur la connexion RFC :</span><span class="sxs-lookup"><span data-stu-id="18f71-109">It provides the following information about the RFC connection:</span></span>  
  
    -   <span data-ttu-id="18f71-110">L’ID du système</span><span class="sxs-lookup"><span data-stu-id="18f71-110">The system ID</span></span>  
  
    -   <span data-ttu-id="18f71-111">La page de codes du partenaire</span><span class="sxs-lookup"><span data-stu-id="18f71-111">The partner code page</span></span>  
  
    -   <span data-ttu-id="18f71-112">La langue</span><span class="sxs-lookup"><span data-stu-id="18f71-112">The language</span></span>  
  
     <span data-ttu-id="18f71-113">Pour plus d’informations sur l’opération RfcGetAttributes y compris son schéma de message, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="18f71-113">For more information about the RfcGetAttributes operation including its message schema, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
-   <span data-ttu-id="18f71-114">**RfcConfirmTransID**.</span><span class="sxs-lookup"><span data-stu-id="18f71-114">**RfcConfirmTransID**.</span></span> <span data-ttu-id="18f71-115">Cette opération est exposée en surface sous le nœud TRFC et expose les fonctionnalités du SDK RFC.</span><span class="sxs-lookup"><span data-stu-id="18f71-115">This operation is surfaced under the TRFC node and exposes RFC SDK functionality.</span></span> <span data-ttu-id="18f71-116">Cette opération vous permet de confirmer l’ID de transaction de SAP sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="18f71-116">You use this operation to confirm SAP transaction IDs on the SAP system.</span></span>  
  
     <span data-ttu-id="18f71-117">Pour plus d’informations sur la façon d’utiliser l’opération RfcConfirmTransID et son schéma de message, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="18f71-117">For more information about how to use the RfcConfirmTransID operation and about its message schema, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
-   <span data-ttu-id="18f71-118">**chaîne SapAdapterUtilities.ConvertGuidToTid(Guid)**.</span><span class="sxs-lookup"><span data-stu-id="18f71-118">**string SapAdapterUtilities.ConvertGuidToTid(Guid)**.</span></span> <span data-ttu-id="18f71-119">Il s’agit d’une méthode publique exposée par l’assembly d’adaptateur SAP.</span><span class="sxs-lookup"><span data-stu-id="18f71-119">This is a public method exposed by the SAP adapter assembly.</span></span> <span data-ttu-id="18f71-120">(Il n’est pas une opération par l’adaptateur.) Il retourne la transaction SAP ID (TID) mappé sur le GUID spécifié.</span><span class="sxs-lookup"><span data-stu-id="18f71-120">(It is not an operation surfaced by the adapter.) It returns the SAP transaction ID (TID) mapped to the specified GUID.</span></span>  
  
     <span data-ttu-id="18f71-121">En interne, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] mappe la transaction SAP ID (TID) qui identifie une unité logique de travail (LUW) sur le système SAP sur un GUID.</span><span class="sxs-lookup"><span data-stu-id="18f71-121">Internally, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] maps the SAP transaction ID (TID) that identifies a logical unit of work (LUW) on the SAP system to a GUID.</span></span> <span data-ttu-id="18f71-122">Ce GUID est exposé aux clients de la carte, afin qu’ils peuvent s’engager un tRFC (LUW) en appelant l’opération RfcConfirmTransID pour confirmer son TID sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="18f71-122">This GUID is exposed to adapter clients, so that they can commit a tRFC (LUW) by invoking the RfcConfirmTransID operation to confirm its TID on the SAP system.</span></span>  
  
     <span data-ttu-id="18f71-123">Toutefois, pour certains scénarios, vous devrez peut-être le TID est associé à un tRFC.</span><span class="sxs-lookup"><span data-stu-id="18f71-123">However, for some scenarios, you may need the TID that is associated with a tRFC.</span></span> <span data-ttu-id="18f71-124">Par exemple, vous souhaiterez identifier le LUW sur le système SAP pour résoudre un problème.</span><span class="sxs-lookup"><span data-stu-id="18f71-124">For example, you may want to identify the LUW on the SAP system to troubleshoot an issue.</span></span> <span data-ttu-id="18f71-125">Pour ces scénarios, vous pouvez appeler **ConvertGuidToTid**.</span><span class="sxs-lookup"><span data-stu-id="18f71-125">For these scenarios you can call **ConvertGuidToTid**.</span></span> <span data-ttu-id="18f71-126">Pour utiliser **ConvertGuidToTid** dans votre code, vous devez ajouter une référence à l’assembly d’adaptateur SAP à votre projet.</span><span class="sxs-lookup"><span data-stu-id="18f71-126">To use **ConvertGuidToTid** in your code, you must add a reference to the SAP adapter assembly to your project.</span></span>  
  
     <span data-ttu-id="18f71-127">Pour plus d’informations sur l’appel de tRFCs, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="18f71-127">For more information about invoking tRFCs, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span> <span data-ttu-id="18f71-128">L’exemple suivant montre comment appeler **ConvertGuidToTid**.</span><span class="sxs-lookup"><span data-stu-id="18f71-128">The following example shows how to invoke **ConvertGuidToTid**.</span></span>  
  
    ```  
    // messageGuid is the GUID associated with a tRFC or IDOC  
  
    string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="18f71-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18f71-129">See Also</span></span>  
 [<span data-ttu-id="18f71-130">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="18f71-130">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)