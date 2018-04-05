---
title: Les opérations sont prises en charge par l’adaptateur Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, performing by using the adapter
ms.assetid: 800cf44b-357f-4850-8878-f49ceb549adf
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40bfb247ff0f3af2abeec584c5fd079f392cd18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-siebel-adapter"></a><span data-ttu-id="6554e-102">Les opérations sont prises en charge par l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="6554e-102">What operations are supported by the Siebel adapter</span></span>
<span data-ttu-id="6554e-103">Les clients de carte peuvent effectuer des opérations sur le système Siebel par soit :</span><span class="sxs-lookup"><span data-stu-id="6554e-103">Adapter clients can perform operations on the Siebel system by either:</span></span>  
  
-   <span data-ttu-id="6554e-104">Création de projets BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6554e-104">Creating BizTalk projects.</span></span>  
  
-   <span data-ttu-id="6554e-105">À l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="6554e-105">Using the WCF channel model.</span></span>  
  
-   <span data-ttu-id="6554e-106">À l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="6554e-106">Using the WCF service model.</span></span>  
  
 <span data-ttu-id="6554e-107">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="6554e-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="6554e-108">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="6554e-108">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="6554e-109">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="6554e-109">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="6554e-110">Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span><span class="sxs-lookup"><span data-stu-id="6554e-110">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span></span>  
  
 <span data-ttu-id="6554e-111">Cette section fournit des informations sur les opérations prises en charge sur le système Siebel en utilisant le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6554e-111">This section provides information about the operations supported on the Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6554e-112">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge la réception des appels entrants à partir d’un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="6554e-112">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support receiving inbound calls from a Siebel system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6554e-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6554e-113">In This Section</span></span>  
  
-   [<span data-ttu-id="6554e-114">Opérations sur les composants d’entreprise Siebel</span><span class="sxs-lookup"><span data-stu-id="6554e-114">Operations on Business Components in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)  
  
-   [<span data-ttu-id="6554e-115">Opérations sur les Services métier de Siebel</span><span class="sxs-lookup"><span data-stu-id="6554e-115">Operations on Business Services in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)  
  
## <a name="see-also"></a><span data-ttu-id="6554e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6554e-116">See Also</span></span>  
 [<span data-ttu-id="6554e-117">Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="6554e-117">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)