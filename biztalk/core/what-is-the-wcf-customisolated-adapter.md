---
title: Qu'est-ce que l'adaptateur WCF-CustomIsolated ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-CustomIsolated adapters, about WCF-CustomIsolated adapters
ms.assetid: 872fe97a-8a96-4b2a-8cc1-2db9b315c44f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fdf5a646f586030df6c9492fc6fb2999e49527a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-customisolated-adapter"></a><span data-ttu-id="633a4-103">Qu'est-ce que l'adaptateur WCF-CustomIsolated ?</span><span class="sxs-lookup"><span data-stu-id="633a4-103">What Is the WCF-CustomIsolated Adapter?</span></span>
<span data-ttu-id="633a4-104">L'adaptateur WCF-CustomIsolated permet d'activer l'utilisation des composants d'extensibilité WCF dans BizTalk Server avec un hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="633a4-104">The WCF-CustomIsolated adapter is used to enable the use of WCF extensibility components in BizTalk Server with an isolated host.</span></span> <span data-ttu-id="633a4-105">Il optimise la flexibilité de l'infrastructure WCF.</span><span class="sxs-lookup"><span data-stu-id="633a4-105">The adapter enables complete flexibility of the WCF framework.</span></span> <span data-ttu-id="633a4-106">Il permet également aux utilisateurs de sélectionner et configurer une liaison WCF pour l'emplacement de réception, et de spécifier les comportements de point de terminaison et les paramètres de sécurité.</span><span class="sxs-lookup"><span data-stu-id="633a4-106">It allows users to select and configure a WCF binding for the receive location, and to specify the endpoint behaviors and security settings.</span></span> <span data-ttu-id="633a4-107">Cet adaptateur peut uniquement être utilisé par les transports hébergés dans IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="633a4-107">This adapter can only be used by transports that are hosted in Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="633a4-108">L'adaptateur WCF-CustomIsolated est constitué d'un adaptateur de réception uniquement</span><span class="sxs-lookup"><span data-stu-id="633a4-108">The WCF-CustomIsolated adapter consists of a receive adapter only.</span></span> <span data-ttu-id="633a4-109">L'adaptateur de réception WCF-CustomIsolated permet de recevoir les requêtes de service WCF via les liaisons WCF, le comportement de service, le comportement de point de terminaison, le mécanisme de sécurité et la source du corps de message entrant que vous avez sélectionnés et configurés pour l'emplacement de réception exécuté dans un hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="633a4-109">You use the WCF-CustomIsolated receive adapter to receive WCF service requests through WCF bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured for the receive location running in an isolated host.</span></span> <span data-ttu-id="633a4-110">Un emplacement de réception qui utilise l'adaptateur de réception WCF-CustomIsolated peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="633a4-110">A receive location that uses the WCF-CustomIsolated receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="633a4-111">Pour plus d’informations sur WCF des adaptateurs de réception, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="633a4-111">For more information about WCF receive adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633a4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="633a4-112">See Also</span></span>  
 <span data-ttu-id="633a4-113">[Configuration de l’adaptateur WCF-CustomIsolated](../core/configuring-the-wcf-customisolated-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="633a4-113">[Configuring the WCF-CustomIsolated Adapter](../core/configuring-the-wcf-customisolated-adapter.md) </span></span>  
 [<span data-ttu-id="633a4-114">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="633a4-114">WCF Adapters</span></span>](../core/wcf-adapters.md)