---
title: "Mise à l’échelle d’un environnement BizTalk Server de Production | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a972b983-5ec5-4a2a-934f-b2788ccd424e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6dfd90864f6698c54558c65aa3a87b96c0459c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-a-production-biztalk-server-environment"></a><span data-ttu-id="32cb2-102">Mise à l’échelle d’un environnement BizTalk Server de Production</span><span class="sxs-lookup"><span data-stu-id="32cb2-102">Scaling a Production BizTalk Server Environment</span></span>
<span data-ttu-id="32cb2-103">Cette section fournit une vue d’ensemble de l’environnement lab qui a été utilisé pour effectuer le test de charge d’une solution BizTalk Server, un résumé des résultats de test de charge et observations générales et recommandations en fonction des résultats dans le laboratoire.</span><span class="sxs-lookup"><span data-stu-id="32cb2-103">This section provides an overview of the lab environment that was used to perform load testing of a BizTalk Server solution, a summary of the load test results, and general observations and recommendations based upon the findings in the lab.</span></span>  
  
 <span data-ttu-id="32cb2-104">Les informations fournies dans ces rubriques peut et doit être utilisées comme un guide pour la mise à l’échelle votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="32cb2-104">The information provided in these topics can and should be used as a guide for scaling your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="32cb2-105">En plus de ce guide, nous vous recommandons d’effectuer régulièrement test de charge tout au long du cycle de développement de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="32cb2-105">In addition to this guidance we recommend that you complete periodic load testing throughout the development cycle of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32cb2-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="32cb2-106">In This Section</span></span>  
  
-   [<span data-ttu-id="32cb2-107">Vue d’ensemble du scénario</span><span class="sxs-lookup"><span data-stu-id="32cb2-107">Scenario Overview</span></span>](../technical-guides/scenario-overview.md)  
  
-   [<span data-ttu-id="32cb2-108">Indicateurs de Performance clés</span><span class="sxs-lookup"><span data-stu-id="32cb2-108">Key Performance Indicators</span></span>](../technical-guides/key-performance-indicators.md)  
  
-   [<span data-ttu-id="32cb2-109">Observations et recommandations</span><span class="sxs-lookup"><span data-stu-id="32cb2-109">Observations and Recommendations</span></span>](../technical-guides/observations-and-recommendations.md)