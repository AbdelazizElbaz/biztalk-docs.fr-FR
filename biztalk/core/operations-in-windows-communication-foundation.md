---
title: "Opérations dans Windows Communication Foundation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1728d2f-ac74-446e-a36f-4b645a6e042a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6b5344b8fb2c5a5ba7a68b112adb50133198c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-in-windows-communication-foundation"></a><span data-ttu-id="886bc-102">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="886bc-102">Operations in Windows Communication Foundation</span></span>
<span data-ttu-id="886bc-103">Cette section contient les opérations personnalisées prises en charge par l'intercepteur WCF BAM.</span><span class="sxs-lookup"><span data-stu-id="886bc-103">This section contains the custom operations supported by the BAM WCF interceptor.</span></span>  
  
 <span data-ttu-id="886bc-104">Notez que, si un élément de nom d'opération contient un attribut Action :</span><span class="sxs-lookup"><span data-stu-id="886bc-104">Note that if an operation name element contains an Action attribute:</span></span>  
  
1.  <span data-ttu-id="886bc-105">le nom d'opération est celui identifié par l'attribut de nom pour le client et le serveur ;</span><span class="sxs-lookup"><span data-stu-id="886bc-105">The operation name is the one identified by the name attribute for both the client and the server,</span></span>  
  
2.  <span data-ttu-id="886bc-106">pour les chemins de réponse (réponse de rappel), réponse de client et réponse de service, le nom d'opération est identifié par l'attribut de nom.</span><span class="sxs-lookup"><span data-stu-id="886bc-106">For reply paths (callback reply), client reply and service rely, the operation name is identified by the name attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="886bc-107">Les messages de réponse auront un nœud nommé par l'ajout du mot « Result » au nom spécifié par l'attribut de nom.</span><span class="sxs-lookup"><span data-stu-id="886bc-107">Reply messages will have a node that is named by appending the word "Result" to the name specified by the name attribute.</span></span> <span data-ttu-id="886bc-108">Vous devez vous assurer que les expressions XPath reflètent cette convention d'affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="886bc-108">You must ensure that the XPaths reflect this naming convention.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="886bc-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="886bc-109">In This Section</span></span>  
  
-   [<span data-ttu-id="886bc-110">AutoGenerateCorrelationToken</span><span class="sxs-lookup"><span data-stu-id="886bc-110">AutoGenerateCorrelationToken</span></span>](../core/autogeneratecorrelationtoken.md)  
  
-   [<span data-ttu-id="886bc-111">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="886bc-111">GetContextProperty</span></span>](../core/getcontextproperty1.md)  
  
-   [<span data-ttu-id="886bc-112">GetEndpointName</span><span class="sxs-lookup"><span data-stu-id="886bc-112">GetEndpointName</span></span>](../core/getendpointname.md)  
  
-   [<span data-ttu-id="886bc-113">GetOperationName</span><span class="sxs-lookup"><span data-stu-id="886bc-113">GetOperationName</span></span>](../core/getoperationname.md)  
  
-   [<span data-ttu-id="886bc-114">GetServiceContractCallPoint</span><span class="sxs-lookup"><span data-stu-id="886bc-114">GetServiceContractCallPoint</span></span>](../core/getservicecontractcallpoint.md)  
  
-   [<span data-ttu-id="886bc-115">XPath</span><span class="sxs-lookup"><span data-stu-id="886bc-115">XPath</span></span>](../core/xpath.md)