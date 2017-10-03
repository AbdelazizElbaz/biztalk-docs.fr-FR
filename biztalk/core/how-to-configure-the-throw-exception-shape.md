---
title: Comment configurer la forme lever Exception | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Throw Exception shape [Orchestration Designer]
- orchestrations, errors
- Orchestration Designer, errors
ms.assetid: d3190f1b-db5e-4988-bff6-f7a276760ece
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07d156572484ba4fbe71533252ce4fe956136699
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-throw-exception-shape"></a><span data-ttu-id="0607b-102">Configuration de la forme Lever exception</span><span class="sxs-lookup"><span data-stu-id="0607b-102">How to Configure the Throw Exception Shape</span></span>
<span data-ttu-id="0607b-103">Vous pouvez lever explicitement des exceptions dans une orchestration à l’aide de la **lever Exception** forme.</span><span class="sxs-lookup"><span data-stu-id="0607b-103">You can explicitly throw exceptions in an orchestration by using the **Throw Exception** shape.</span></span> <span data-ttu-id="0607b-104">Lorsqu'une exception est levée, le moteur d'exécution recherche le gestionnaire d'exceptions le plus proche, capable de traiter le type d'exception concerné.</span><span class="sxs-lookup"><span data-stu-id="0607b-104">When the throw is performed, the runtime engine will search for the nearest exception handler that can handle the type of exception being thrown.</span></span>  
  
 <span data-ttu-id="0607b-105">En premier lieu, une étendue intégrée est recherchée dans l'orchestration active, puis les gestionnaires d'exception associés à l'étendue sont pris en compte pour la localisation du gestionnaire approprié au type d'exception levée.</span><span class="sxs-lookup"><span data-stu-id="0607b-105">First, the current orchestration is searched for an enclosing scope, and the associated exception handlers of the scope are considered in order to locate the appropriate handler for the type of exception that has been thrown.</span></span>  
  
 <span data-ttu-id="0607b-106">Si aucun gestionnaire d'exceptions n'est trouvé, l'étendue qui comprend le point d'appel de l'orchestration active est recherchée dans l'orchestration qui a appelé l'orchestration active.</span><span class="sxs-lookup"><span data-stu-id="0607b-106">If no appropriate exception handler is found, the orchestration that called the current orchestration is searched for a scope that encloses the point of the call to the current orchestration.</span></span> <span data-ttu-id="0607b-107">Cette recherche se poursuit jusqu'à ce qu'un gestionnaire d'exceptions capable de gérer l'exception soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="0607b-107">This search continues until an exception handler is found that can handle the current exception.</span></span>  
  
 <span data-ttu-id="0607b-108">La correspondance exacte d'une exception est une classe d'exception qui est la même, ou une classe de base, que le type d'exécution de l'exception levée.</span><span class="sxs-lookup"><span data-stu-id="0607b-108">An exact match for the exception is an exception class that is of the same class as, or a base class of, the run-time type of the exception being thrown.</span></span>  
  
 <span data-ttu-id="0607b-109">Une fois le gestionnaire d'exceptions trouvé, le contrôle est transféré à la première instruction de ce gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="0607b-109">After a matching exception handler is found, control is transferred to the first statement of the exception handler.</span></span>  
  
 <span data-ttu-id="0607b-110">Si aucun gestionnaire d'exceptions n'est trouvé, l'orchestration s'arrête.</span><span class="sxs-lookup"><span data-stu-id="0607b-110">If the search for matching exception handlers fails, the orchestration halts.</span></span> <span data-ttu-id="0607b-111">Les transactions peuvent vous aider à limiter l'impact d'un tel événement.</span><span class="sxs-lookup"><span data-stu-id="0607b-111">Transactions can help you minimize the impact of such an occurrence.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="0607b-112">Procédure</span><span class="sxs-lookup"><span data-stu-id="0607b-112">Procedure</span></span>  
  
#### <a name="to-configure-a-throw-exception-shape"></a><span data-ttu-id="0607b-113">Pour configurer une forme Lever exception</span><span class="sxs-lookup"><span data-stu-id="0607b-113">To configure a Throw Exception shape</span></span>  
  
-   <span data-ttu-id="0607b-114">Dans la fenêtre Propriétés, sélectionnez un type d’objet disponible à lever à partir de la **objet Exception** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="0607b-114">In the Properties window, select an available object type to throw from the **Exception Object** drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0607b-115">Sélectionnez Exception générale dans le **lever Exception** uniquement si de forme le **lever Exception** forme se trouve dans un gestionnaire d’exceptions et que vous souhaitez lever l’exception interceptée dans le Gestionnaire d’exceptions en cours à.</span><span class="sxs-lookup"><span data-stu-id="0607b-115">Select General Exception in the **Throw Exception** shape only if the **Throw Exception** shape is within an exception handler and you want to rethrow the exception caught in the current exception handler.</span></span> <span data-ttu-id="0607b-116">Vous recevez une erreur pendant la compilation si vous utilisez une Exception générale pour une **lever Exception** forme dans un autre contexte.</span><span class="sxs-lookup"><span data-stu-id="0607b-116">You will receive an error during the compile if you use General Exception for a **Throw Exception** shape in any other context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0607b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0607b-117">See Also</span></span>  
 [<span data-ttu-id="0607b-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="0607b-118">Exceptions</span></span>](../core/exceptions.md)