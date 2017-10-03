---
title: "Stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, policies
- policies, about policies
- policies, deploying
- policies, Business Rules Engine
- policies
- business rules, policies
- policies, versioning
- policies, testing
- policies, creating
- policies, updating
ms.assetid: 2e0ae081-938d-4e2a-947e-1c0ecfebb4b8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd05d6cf67d89ee811cac45ac3950697db74f59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policies"></a><span data-ttu-id="3d6a2-102">Stratégies</span><span class="sxs-lookup"><span data-stu-id="3d6a2-102">Policies</span></span>
<span data-ttu-id="3d6a2-103">Une stratégie est un groupe logique de règles.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-103">A policy is a logical grouping of rules.</span></span> <span data-ttu-id="3d6a2-104">Vous créez une version d'une stratégie, vous l'enregistrez, vous la testez en l'appliquant à des faits et lorsque vous êtes satisfait des résultats, vous la publiez et vous la déployez dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-104">You compose a version of a policy, save it, test it by applying it to facts, and, when you are satisfied with the results, publish it and deploy it to a production environment.</span></span>  
  
## <a name="policy-composition"></a><span data-ttu-id="3d6a2-105">Création d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="3d6a2-105">Policy Composition</span></span>  
 <span data-ttu-id="3d6a2-106">Vous pouvez créer des stratégies dans l'Éditeur des règles d'entreprise en établissant des règles à partir de faits et de définitions.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-106">You can compose policies in the Business Rule Composer by constructing rules from facts and definitions.</span></span> <span data-ttu-id="3d6a2-107">Une stratégie peut contenir un ensemble arbitrairement grand de règles, mais, de façon générale, vous créez une stratégie à partir de règles relatives à un domaine d'entreprise spécifique dans le contexte de l'application qui va utiliser cette stratégie.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-107">A policy can contain an arbitrarily large set of rules, but typically you compose a policy from rules that pertain to a specific business domain within the context of the application that will be using the policy.</span></span>  
  
## <a name="policy-testing"></a><span data-ttu-id="3d6a2-108">Test de la stratégie</span><span class="sxs-lookup"><span data-stu-id="3d6a2-108">Policy Testing</span></span>  
 <span data-ttu-id="3d6a2-109">Vous pouvez effectuer un test efficace de votre stratégie avant de la publier et de la déployer dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-109">You can effectively perform a test run of your policy before it is published and deployed in a production environment.</span></span> <span data-ttu-id="3d6a2-110">L'Éditeur des règles d'entreprise vous permet de fournir des instances de faits à une stratégie, d'exécuter celle-ci et d'afficher ses résultats.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-110">The Business Rule Composer allows you to supply instances of facts to a policy, run the policy, and view its output.</span></span> <span data-ttu-id="3d6a2-111">Les résultats indiquent l'activité des faits, l'exécution des règles, l'évaluation de la condition et les mises à jour de l'agenda.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-111">The output includes fact activity, rule execution, condition evaluation, and updates to the agenda.</span></span>  
  
## <a name="policy-versions"></a><span data-ttu-id="3d6a2-112">Versions de stratégie</span><span class="sxs-lookup"><span data-stu-id="3d6a2-112">Policy Versions</span></span>  
 <span data-ttu-id="3d6a2-113">Une fois toutes les règles définies, vous pouvez publier la version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-113">After you have defined all the rules in your policy, you can publish the policy version.</span></span> <span data-ttu-id="3d6a2-114">Ainsi, la stratégie est verrouillée et son comportement bien défini.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-114">In this way the policy is locked down, and its behavior is well-defined.</span></span>  
  
 <span data-ttu-id="3d6a2-115">Vous pouvez utiliser une version de stratégie donnée dans votre environnement d'entreprise dans un ensemble de circonstances donné et la remplacer par une autre version lorsque ces circonstances changent.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-115">A given policy version can be used under a given set of circumstances in your business environment, and replaced by another version when those circumstances change.</span></span> <span data-ttu-id="3d6a2-116">Aussi, différentes applications peuvent utiliser des versions anciennes et nouvelles simultanément.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-116">Also, both new and old versions can be used simultaneously by different applications.</span></span>  
  
## <a name="policy-deployment"></a><span data-ttu-id="3d6a2-117">Déploiement de stratégie</span><span class="sxs-lookup"><span data-stu-id="3d6a2-117">Policy Deployment</span></span>  
 <span data-ttu-id="3d6a2-118">Lorsque vous êtes prêt à exécuter votre stratégie dans un environnement de production, vous pouvez la déployer afin qu'elle soit disponible pour une application hôte.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-118">When your policy is ready to be run in a production environment, you can deploy it to make it available to a hosting application.</span></span>  
  
## <a name="dynamic-policy-updates"></a><span data-ttu-id="3d6a2-119">Mises à jour dynamiques de stratégie</span><span class="sxs-lookup"><span data-stu-id="3d6a2-119">Dynamic Policy Updates</span></span>  
 <span data-ttu-id="3d6a2-120">Les mises à jour dynamiques de stratégie vous permettent de modifier les stratégies indépendamment du processus d'entreprise exécuté.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-120">Dynamic policy updates allow you to modify policies independently of a running business process.</span></span> <span data-ttu-id="3d6a2-121">Vous pouvez créer et déployer une version mise à jour de la stratégie et l'application hôte peut incorporer cette mise à jour quasiment en temps réel.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-121">You can create and deploy an updated version of the policy, and the hosting application can incorporate the update in near real time.</span></span> <span data-ttu-id="3d6a2-122">La mise à jour ne nécessite pas que vous changiez le code, ce qui vous permet d'économiser les frais de redéveloppement et de redéploiement de l'application.</span><span class="sxs-lookup"><span data-stu-id="3d6a2-122">This update does not require you to change any code, and thus you can avoid the overhead of redeveloping and redeploying the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6a2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d6a2-123">See Also</span></span>  
 [<span data-ttu-id="3d6a2-124">Moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="3d6a2-124">Business Rules Engine</span></span>](../core/business-rules-engine.md)