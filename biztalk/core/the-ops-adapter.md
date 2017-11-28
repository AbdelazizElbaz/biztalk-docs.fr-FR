---
title: "L’adaptateur Ops | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Ops adapters
- Ops adapters, about Ops adapters
- Ops adapters
- process management solution tutorial, Ops adapters
- process management solution tutorial, errors
ms.assetid: 7f747a5f-14af-4e4c-bc29-f083f8f00bd0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67463adf4e1e960ab6608e67595a679804aa223e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-ops-adapter"></a><span data-ttu-id="d3423-102">L’adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="d3423-102">The Ops Adapter</span></span>
<span data-ttu-id="d3423-103">La conception de la solution permet, dans la mesure du possible, de transmettre aux systèmes d'opérations les messages et les erreurs posant problème afin que ceux-ci prennent une décision concernant la résolution de l'erreur ou l'arrêt de la commande.</span><span class="sxs-lookup"><span data-stu-id="d3423-103">The design of the solution is to pass, where possible, problematic messages and errors to operations systems that make a decision about fixing the error or terminating the order.</span></span> <span data-ttu-id="d3423-104">L'adaptateur Ops, combiné à la nouvelle fonctionnalité de rapports d'erreurs, traite la plupart de ces cas.</span><span class="sxs-lookup"><span data-stu-id="d3423-104">The Ops adapter, combined with the new error reporting feature, handles many of these cases.</span></span>  
  
 <span data-ttu-id="d3423-105">La solution fait appel à l'adaptateur sur un port configuré de manière à utiliser la fonctionnalité de rapports d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="d3423-105">The solution uses the adapter on a port configured to use the new error reporting feature.</span></span> <span data-ttu-id="d3423-106">Lorsqu’il reçoit une erreur, l’adaptateur appelle deux méthodes, **initialiser** et **Execute**, d’une classe dans un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3423-106">When it receives an error, the adapter calls two methods, **Initialize** and **Execute**, on a class in a specified assembly.</span></span> <span data-ttu-id="d3423-107">Dans la solution, ces méthodes envoient l'erreur au groupe d'opérations approprié.</span><span class="sxs-lookup"><span data-stu-id="d3423-107">In the solution, these methods send the error to the correct operations group.</span></span>  
  
 <span data-ttu-id="d3423-108">La solution inclut un exemple de gestionnaire, bien que vous puissiez facilement écrire le vôtre et l'utiliser dans d'autres solutions.</span><span class="sxs-lookup"><span data-stu-id="d3423-108">The solution includes a sample handler, although you can easily write your own and use the adapter in other solutions.</span></span> <span data-ttu-id="d3423-109">Pour obtenir des informations générales sur la nouvelle fonctionnalité de création de rapports d’erreurs, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).</span><span class="sxs-lookup"><span data-stu-id="d3423-109">For general information about the new error reporting feature, see [Using Failed Message Routing](../core/using-failed-message-routing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3423-110">L’adaptateur Ops est générée à l’aide de l’infrastructure d’adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="d3423-110">The Ops adapter is built using the Adapter Framework.</span></span> <span data-ttu-id="d3423-111">Pour plus d’informations sur la création de cartes avec l’infrastructure, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="d3423-111">For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
 <span data-ttu-id="d3423-112">Cette section présente le fonctionnement ainsi que la configuration de l'adaptateur et fournit des détails sur les assemblys du gestionnaire d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="d3423-112">This section describes how the adapter works and how to configure it, and provides details about the error handler assemblies.</span></span> <span data-ttu-id="d3423-113">En conclusion, vous trouverez des détails sur l'implémentation qui peuvent s'avérer utiles aux utilisateurs souhaitant modifier l'adaptateur ou l'utiliser dans d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="d3423-113">The section concludes with implementation details that would be helpful to users who wish to modify the adapter or use it in other applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3423-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d3423-114">In This Section</span></span>  
  
-   [<span data-ttu-id="d3423-115">À l’aide de l’adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="d3423-115">Using the Ops Adapter</span></span>](../core/using-the-ops-adapter.md)  
  
-   [<span data-ttu-id="d3423-116">Le Gestionnaire d’erreurs Operations exemple</span><span class="sxs-lookup"><span data-stu-id="d3423-116">The Sample Operations Error Handler</span></span>](../core/the-sample-operations-error-handler.md)  
  
-   [<span data-ttu-id="d3423-117">Détails d’implémentation adaptateur OPS</span><span class="sxs-lookup"><span data-stu-id="d3423-117">Ops Adapter Implementation Details</span></span>](../core/ops-adapter-implementation-details.md)