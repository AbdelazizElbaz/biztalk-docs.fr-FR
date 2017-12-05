---
title: "À l’aide de la gestion des exceptions ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6ce411-2d34-4fd8-9644-6fbc9cec266d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4eff5a729b8c8ca191b2185180e312f9e895c02
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-esb-exception-management"></a><span data-ttu-id="3ef49-102">À l’aide de la gestion des exceptions ESB</span><span class="sxs-lookup"><span data-stu-id="3ef49-102">Using ESB Exception Management</span></span>
<span data-ttu-id="3ef49-103">Erreurs et exceptions peuvent se produire dans une plage de contextes et pendant un nombre différent d’étapes de traitement dans une architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="3ef49-103">Errors and exceptions can occur in a range of contexts and during a number of different processing stages in an ESB.</span></span> <span data-ttu-id="3ef49-104">Cette section fournit des informations sur la gestion des exceptions et décrit comment vous pouvez publier des informations via le portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="3ef49-104">This section provides information about handling exceptions and describes how you can publish details through the ESB Management Portal.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3ef49-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="3ef49-105">Overview</span></span>  
 <span data-ttu-id="3ef49-106">Il existe de nombreuses façons de gérer les exceptions dans une solution BizTalk Server, y compris à l’aide d’infrastructures telles que la bibliothèque de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="3ef49-106">There are many ways to handle exceptions in a BizTalk Server solution, including using frameworks such as the Enterprise Library.</span></span> <span data-ttu-id="3ef49-107">Toutefois, lorsque vous développez avec ESB et BizTalk Server, vous travaillez dans un environnement basé sur le message.</span><span class="sxs-lookup"><span data-stu-id="3ef49-107">However, when developing with ESB and BizTalk Server, you are working in a message-based environment.</span></span> <span data-ttu-id="3ef49-108">Tous les éléments dans une solution BizTalk sont orienté messages, et les développeurs BizTalk de réflexion d’une manière orientée message.</span><span class="sxs-lookup"><span data-stu-id="3ef49-108">Everything in a BizTalk solution is message-oriented, and BizTalk developers think in a message-oriented way.</span></span> <span data-ttu-id="3ef49-109">Par conséquent, le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implémente une approche orientée message pour la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="3ef49-109">Therefore, the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a message-oriented approach to exception handling.</span></span>  
  
 <span data-ttu-id="3ef49-110">L’infrastructure de gestion d’Exception ESB suit un modèle de conception qui permet une approche flexible permettant l’analyse des exceptions et réponses d’erreur proviennent en dehors de la solution, peut-être au niveau de la division.</span><span class="sxs-lookup"><span data-stu-id="3ef49-110">The ESB Exception Management Framework follows a design pattern that provides a flexible approach to exception monitoring and enables error responses to originate from outside of the solution—perhaps at business-unit level.</span></span>  
  
 <span data-ttu-id="3ef49-111">Les rubriques suivantes traitent de l’infrastructure de gestion d’Exception ESB plus en détail :</span><span class="sxs-lookup"><span data-stu-id="3ef49-111">The following topics discuss the ESB Exception Management Framework in more detail:</span></span>  
  
-   [<span data-ttu-id="3ef49-112">Conception de l’infrastructure de gestion des exceptions ESB</span><span class="sxs-lookup"><span data-stu-id="3ef49-112">Design of the ESB Exception Management Framework</span></span>](../esb-toolkit/design-of-the-esb-exception-management-framework.md)  
  
-   [<span data-ttu-id="3ef49-113">Les composants de l’infrastructure de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="3ef49-113">The Components of the Exception Management Framework</span></span>](../esb-toolkit/the-components-of-the-exception-management-framework.md)  
  
-   [<span data-ttu-id="3ef49-114">Utilisation de l’infrastructure de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="3ef49-114">Using the Exception Management Framework</span></span>](../esb-toolkit/using-the-exception-management-framework.md)  
  
-   [<span data-ttu-id="3ef49-115">Création de gestionnaires d’exceptions personnalisés</span><span class="sxs-lookup"><span data-stu-id="3ef49-115">Creating Custom Exception Handlers</span></span>](../esb-toolkit/creating-custom-exception-handlers.md)