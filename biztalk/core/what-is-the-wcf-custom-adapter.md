---
title: "Qu'est-ce que l'adaptateur WCF-Custom ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-Custom adapters, about WCF-Custom adapters
ms.assetid: 7b2178dd-f737-4784-9bcb-e2b3979bfb0d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e090f82bc43d96dc14295af2fac2807cf1fd137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-custom-adapter"></a><span data-ttu-id="f2edb-103">Qu'est-ce que l'adaptateur WCF-Custom ?</span><span class="sxs-lookup"><span data-stu-id="f2edb-103">What Is the WCF-Custom Adapter?</span></span>
<span data-ttu-id="f2edb-104">L'adaptateur WCF-Custom permet d'activer l'utilisation des composants d'extensibilité WCF dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f2edb-104">The WCF-Custom adapter is used to enable the use of WCF extensibility components in BizTalk Server.</span></span> <span data-ttu-id="f2edb-105">Il optimise la flexibilité de l'infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="f2edb-105">The adapter enables complete flexibility of the WCF framework.</span></span> <span data-ttu-id="f2edb-106">Les utilisateurs peuvent ainsi sélectionner et configurer une liaison WCF pour l'emplacement de réception et le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f2edb-106">It allows users to select and configure a WCF binding for the receive location and send port.</span></span> <span data-ttu-id="f2edb-107">L'adaptateur permet également de définir les comportements de point de terminaison et les paramètres de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f2edb-107">It also allows users to set the endpoint behaviors and security settings.</span></span>  
  
 <span data-ttu-id="f2edb-108">L'adaptateur WCF-Custom est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f2edb-108">The WCF-Custom adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="f2edb-109">**Adaptateur de réception WCF-Custom**</span><span class="sxs-lookup"><span data-stu-id="f2edb-109">**WCF-Custom Receive Adapter**</span></span>  
  
 <span data-ttu-id="f2edb-110">L'adaptateur de réception WCF-Custom permet de recevoir les requêtes de service WCF via les liaisons, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message entrant que vous avez sélectionnés et configurés dans la boîte de dialogue Propriétés du transport de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f2edb-110">You use the WCF-Custom receive adapter to receive WCF service requests through the bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured in the transport properties dialog in the receive location.</span></span> <span data-ttu-id="f2edb-111">Un emplacement de réception qui utilise l'adaptateur de réception WCF-Custom peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="f2edb-111">A receive location that uses the WCF-Custom receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="f2edb-112">**Adaptateur d’envoi WCF-Custom**</span><span class="sxs-lookup"><span data-stu-id="f2edb-112">**WCF-Custom Send Adapter**</span></span>  
  
 <span data-ttu-id="f2edb-113">L'adaptateur d'envoi WCF-Custom permet d'appeler un service WCF à l'aide du contrat sans type avec les liaisons, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message sortant que vous avez sélectionnés et configurés.</span><span class="sxs-lookup"><span data-stu-id="f2edb-113">You use the WCF-Custom send adapter to call a WCF service through the typeless contract with the bindings, service behavior, endpoint behavior, security mechanism, and the source of the outbound message body that you selected and configured.</span></span>  
  
 <span data-ttu-id="f2edb-114">Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="f2edb-114">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2edb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2edb-115">See Also</span></span>  
 <span data-ttu-id="f2edb-116">[Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f2edb-116">[Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md) </span></span>  
 [<span data-ttu-id="f2edb-117">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="f2edb-117">WCF Adapters</span></span>](../core/wcf-adapters.md)