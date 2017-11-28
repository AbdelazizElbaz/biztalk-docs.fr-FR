---
title: "Phase 5 : L’exécution de l’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d40fc64-b6cb-448b-8ea1-a6ad7302ab8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fba6d49d8d69276af4282ad0a941ee1fc4d8068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-5-executing-the-assessment"></a><span data-ttu-id="54338-102">Phase 5 : L’exécution de l’évaluation</span><span class="sxs-lookup"><span data-stu-id="54338-102">Phase 5: Executing the Assessment</span></span>
<span data-ttu-id="54338-103">La phase d’exécution est où les données de performances sont générées via le test de charge automatique et où les goulots d’étranglement de performances sont détectées et traitées.</span><span class="sxs-lookup"><span data-stu-id="54338-103">The Execute phase is where the performance data is generated through automated load testing and where performance bottlenecks are discovered and addressed.</span></span> <span data-ttu-id="54338-104">Cette phase est un processus itératif, par laquelle les goulots d’étranglement de performances sont réduites ou éliminées par un test, l’évaluation des performances, l’optimisation et la tester à nouveau.</span><span class="sxs-lookup"><span data-stu-id="54338-104">This phase has an iterative process whereby performance bottlenecks are reduced or eliminated by testing, evaluating performance, optimizing, and testing again.</span></span>  
  
 <span data-ttu-id="54338-105">Cette rubrique décrit les étapes généralement suivies lors de la phase d’exécution d’une évaluation de performances de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="54338-105">This topic describes the steps that are typically followed during the Execute phase of a BizTalk Server performance assessment:</span></span>  
  
## <a name="step-1-run-automated-tests"></a><span data-ttu-id="54338-106">Étape 1 : Exécuter des tests automatisés</span><span class="sxs-lookup"><span data-stu-id="54338-106">Step 1: Run automated tests</span></span>  
 <span data-ttu-id="54338-107">Commencer la phase d’exécution en exécutant des tests automatisés.</span><span class="sxs-lookup"><span data-stu-id="54338-107">Begin the Execute phase by running automated tests.</span></span> <span data-ttu-id="54338-108">En général, une évaluation des performances BizTalk Server se concentre sur le débit ou la latence de test mais peut inclure les tests fonctionnels et vérification de build.</span><span class="sxs-lookup"><span data-stu-id="54338-108">A BizTalk Server performance assessment typically focuses on throughput and/or latency testing but may include build verification and functional tests.</span></span> <span data-ttu-id="54338-109">Pour obtenir des informations complètes sur l’exécution de tests automatisés, consultez [mise en œuvre des tests automatisés](../technical-guides/implementing-automated-testing.md).</span><span class="sxs-lookup"><span data-stu-id="54338-109">For comprehensive information about running automated testing, see [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md).</span></span>  
  
## <a name="step-2-document-and-evaluate-test-results"></a><span data-ttu-id="54338-110">Étape 2 : Document et évaluer les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="54338-110">Step 2: Document and evaluate test results</span></span>  
 <span data-ttu-id="54338-111">À la fin de chaque test, soigneusement documenter les résultats de test et d’évaluer si les objectifs de performance mentionnées ont été remplies.</span><span class="sxs-lookup"><span data-stu-id="54338-111">At the conclusion of each test, thoroughly document the test results and evaluate whether the stated performance goals have been met.</span></span>  
  
## <a name="step-3-modify-the-configuration-of-biztalk-server-third-party-systems-or-solution-artifacts-to-tune-for-performance-based-on-the-test-results"></a><span data-ttu-id="54338-112">Étape 3 : Modifier la configuration de BizTalk Server, les systèmes tiers ou des artefacts de solution pour régler les performances selon les résultats des tests</span><span class="sxs-lookup"><span data-stu-id="54338-112">Step 3: Modify the configuration of BizTalk Server, third-party systems, or solution artifacts to tune for performance based on the test results</span></span>  
 <span data-ttu-id="54338-113">Les résultats des tests permet de prendre des décisions sur l’optimisation de l’environnement d’atteindre les objectifs de débit et de latence.</span><span class="sxs-lookup"><span data-stu-id="54338-113">Use the test results to make decisions about how to optimize the environment to reach stated throughput or latency goals.</span></span>  
  
## <a name="step-4-record-all-changes-made-to-the-environment"></a><span data-ttu-id="54338-114">Étape 4 : Enregistrement de toutes les modifications apportées à l’environnement</span><span class="sxs-lookup"><span data-stu-id="54338-114">Step 4: Record all changes made to the environment</span></span>  
 <span data-ttu-id="54338-115">Assurez-vous que toutes les modifications apportées à l’environnement sont soigneusement documentées.</span><span class="sxs-lookup"><span data-stu-id="54338-115">Ensure that any changes made to the environment are thoroughly documented.</span></span> <span data-ttu-id="54338-116">Un enregistrement des modifications vous permet de facilement appliquer les modifications dans l’environnement de production et prend en charge l’annulation des modifications si besoin.</span><span class="sxs-lookup"><span data-stu-id="54338-116">A record of the changes will allow you to easily apply the changes in the production environment and will accommodate the undoing of changes if need be.</span></span>  
  
## <a name="step-5-repeat-this-cycle-until-goals-are-achieved"></a><span data-ttu-id="54338-117">Étape 5 : Répétez le ce cycle jusqu'à ce que les objectifs sont atteints.</span><span class="sxs-lookup"><span data-stu-id="54338-117">Step 5: Repeat this cycle until goals are achieved</span></span>  
 <span data-ttu-id="54338-118">Continuer le cycle de test, l’évaluation et documenter les résultats, optimisation de l’environnement et documenter les modifications de l’environnement jusqu'à ce que les objectifs de performance souhaités sont atteints.</span><span class="sxs-lookup"><span data-stu-id="54338-118">Continue the cycle of testing, evaluating and documenting results, optimizing the environment, and documenting changes to the environment until the desired performance goals are reached.</span></span>  
  
## <a name="step-6-summarize-test-results-at-the-end-of-each-day"></a><span data-ttu-id="54338-119">Étape 6 : Résumer les résultats des tests à la fin de chaque jour</span><span class="sxs-lookup"><span data-stu-id="54338-119">Step 6: Summarize test results at the end of each day</span></span>  
 <span data-ttu-id="54338-120">Effectuez un « rapport de synthèse » des résultats de test et des progrès réalisés à la fin de chaque jour.</span><span class="sxs-lookup"><span data-stu-id="54338-120">Complete an “executive summary” of the test results and progress made at the end of each day.</span></span> <span data-ttu-id="54338-121">Un message électronique qui contient le résumé de la compilation et à envoyer à toutes les parties prenantes dans l’évaluation des performances pour conserver tout le monde informé de la progression est effectuée.</span><span class="sxs-lookup"><span data-stu-id="54338-121">Compile an e-mail that contains the summary, and send to all stakeholders in the performance assessment to keep everyone informed of progress that is being made.</span></span>  
  
## <a name="step-7-update-the-project-plan-as-timeline-goals-are-met"></a><span data-ttu-id="54338-122">Étape 7 : Mettre à jour le plan de projet en tant que les objectifs de chronologie</span><span class="sxs-lookup"><span data-stu-id="54338-122">Step 7: Update the project plan as timeline goals are met</span></span>  
 <span data-ttu-id="54338-123">La chronologie développée dans la phase de planification est une bonne référence pour la progression globale de l’évaluation des performances.</span><span class="sxs-lookup"><span data-stu-id="54338-123">The timeline developed in the Plan phase is a good reference for the overall progress of the performance assessment.</span></span> <span data-ttu-id="54338-124">Mettre à jour cette chronologie que nécessaire pour communiquer l’état d’avancement à toutes les parties prenantes.</span><span class="sxs-lookup"><span data-stu-id="54338-124">Update this timeline as necessary to communicate the progress to all stakeholders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54338-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54338-125">See Also</span></span>  
 [<span data-ttu-id="54338-126">Phases d’une évaluation des performances</span><span class="sxs-lookup"><span data-stu-id="54338-126">Phases of a Performance Assessment</span></span>](../technical-guides/phases-of-a-performance-assessment.md)