---
title: "Le contrôle de version du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, service solutions
- service solution tutorial, versioning
ms.assetid: 0e09720f-53f2-4b38-aae3-a79ddfd35be5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af1c5d1475fc37322be9a8483963bbfd1432fbb4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="versioning-the-service-oriented-solution"></a><span data-ttu-id="2d27f-102">Solution orientée services de contrôle de version du Service</span><span class="sxs-lookup"><span data-stu-id="2d27f-102">Versioning the Service Oriented Solution</span></span>
<span data-ttu-id="2d27f-103">Les deux orchestrations qui agissent comme frontaux à la solution, **CustomerServiceReceiveSend** et **CustomerServiceNativeRequestResponse**, appelez le centre, l’orchestration de travail,  **CustomerService**.</span><span class="sxs-lookup"><span data-stu-id="2d27f-103">The two orchestrations that act as front ends to the solution, **CustomerServiceReceiveSend** and **CustomerServiceNativeRequestResponse**, call the central, working orchestration, **CustomerService**.</span></span> <span data-ttu-id="2d27f-104">Les appels de l'orchestration dépendent du numéro de version de l'assembly contenant l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="2d27f-104">Orchestration calls depend on the version number of the assembly containing the orchestration.</span></span> <span data-ttu-id="2d27f-105">Comme les trois orchestrations sont situées dans le même assembly, il n'existe aucun problème de contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="2d27f-105">Because all three orchestrations are in the same assembly, there are no versioning issues.</span></span>  
  
 <span data-ttu-id="2d27f-106">En outre, le processus d'entreprise implémenté par les orchestrations est un processus de requête-réponse de très courte durée, qui se termine rapidement.</span><span class="sxs-lookup"><span data-stu-id="2d27f-106">In addition, the business process implemented by the orchestrations is a very short-lived request-response process that completes quickly.</span></span> <span data-ttu-id="2d27f-107">C'est pourquoi, la question du contrôle de version du processus d'entreprise ne se pose pas dans cette solution : en effet, les orchestrations sont associées à un assembly unique et une version unique.</span><span class="sxs-lookup"><span data-stu-id="2d27f-107">Thus, the question of versioning the business process does not arise in this solution—there are no different orchestrations in different assemblies with different versions.</span></span>  
  
 <span data-ttu-id="2d27f-108">Cependant, les orchestrations utilisent bien les schémas de l'assembly de schéma.</span><span class="sxs-lookup"><span data-stu-id="2d27f-108">However, the orchestrations do use the schemas in the schema assembly.</span></span> <span data-ttu-id="2d27f-109">Si les schémas sont révisés et compilés dans une autre version, vous devez recompiler les orchestrations avec la dernière version de l'assembly de schéma.</span><span class="sxs-lookup"><span data-stu-id="2d27f-109">If the schemas are revised and compiled into a different version, you must recompile the orchestrations with the newer version of the schema assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d27f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d27f-110">See Also</span></span>  
 [<span data-ttu-id="2d27f-111">Développement d’un Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="2d27f-111">Developing a Service Oriented Solution</span></span>](../core/developing-a-service-oriented-solution.md)