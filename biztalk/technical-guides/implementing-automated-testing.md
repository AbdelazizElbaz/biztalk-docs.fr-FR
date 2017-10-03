---
title: "Implémentation d’un test automatisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ba540e-789d-49bf-af4b-87e6f37ab96f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee97d5c44ebd32ca5b325af386fb1a8754f5b20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-automated-testing"></a><span data-ttu-id="43f56-102">Implémentation d’un test automatisé</span><span class="sxs-lookup"><span data-stu-id="43f56-102">Implementing Automated Testing</span></span>
<span data-ttu-id="43f56-103">Les solutions BizTalk Server sont souvent déployées dans des scénarios « critique », où la solution BizTalk est un composant principal de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="43f56-103">BizTalk Server solutions are often deployed in “mission-critical” scenarios, whereby the BizTalk solution is a core component of the business.</span></span> <span data-ttu-id="43f56-104">Dans ces scénarios, les performances en continu et la stabilité de BizTalk solution est une spécification de clés de l’entreprise ; Si la solution BizTalk échoue, les coûts de temps d’arrêt associés sont significatifs.</span><span class="sxs-lookup"><span data-stu-id="43f56-104">In these scenarios, the continual performance and stability of the BizTalk solution is a key business requirement; if the BizTalk solution fails, the associated downtime costs are significant.</span></span> <span data-ttu-id="43f56-105">Dans de tels scénarios, il est vital que la solution BizTalk être testées entièrement avant que la solution soit placée en production.</span><span class="sxs-lookup"><span data-stu-id="43f56-105">In such scenarios, it is of paramount importance that the BizTalk solution be thoroughly tested before the solution is placed into production.</span></span> <span data-ttu-id="43f56-106">Les coûts associés aux tests correctement de la solution sont petits par rapport aux coûts de temps d’arrêt résultant ne testant ne pas ou insuffisamment tester la solution.</span><span class="sxs-lookup"><span data-stu-id="43f56-106">The costs associated with properly testing the solution are small compared to the downtime costs resulting from not testing or insufficiently testing the solution.</span></span> <span data-ttu-id="43f56-107">Par conséquent, le test d’une solution BizTalk Server est sans doute la phase la plus importante de tout déploiement d’une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="43f56-107">Therefore, the testing of a BizTalk Server solution is arguably the most important phase of any BizTalk Server solution deployment.</span></span>  
  
 <span data-ttu-id="43f56-108">Cette section décrit la méthode appropriée pour le test d’une solution BizTalk avant d’exécuter la solution dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="43f56-108">This section describes the proper methodology for testing a BizTalk solution before running the solution in a production environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43f56-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="43f56-109">In This Section</span></span>  
  
-   [<span data-ttu-id="43f56-110">Pourquoi il est Important de Test</span><span class="sxs-lookup"><span data-stu-id="43f56-110">Why It Is Important to Test</span></span>](../technical-guides/why-it-is-important-to-test.md)  
  
-   [<span data-ttu-id="43f56-111">Automatiser le processus de génération</span><span class="sxs-lookup"><span data-stu-id="43f56-111">Automating the Build Process</span></span>](../technical-guides/automating-the-build-process.md)  
  
-   [<span data-ttu-id="43f56-112">Pour faciliter les tests automatisés à l’aide de BizUnit</span><span class="sxs-lookup"><span data-stu-id="43f56-112">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)  
  
-   [<span data-ttu-id="43f56-113">À l’aide de Visual Studio pour faciliter le test automatisé</span><span class="sxs-lookup"><span data-stu-id="43f56-113">Using Visual Studio to Facilitate Automated Testing</span></span>](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)