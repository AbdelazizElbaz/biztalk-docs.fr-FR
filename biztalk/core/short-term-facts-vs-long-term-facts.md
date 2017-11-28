---
title: "Vs de faits à court terme. Faits à long terme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- facts, short-term
- facts, long-term
- short-term facts
- business rules, facts
- long-term facts
ms.assetid: de020b20-1012-498a-969e-4adc4549918c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d5c37926fb1da5499f34e22c35f8a8f32d238bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="short-term-facts-vs-long-term-facts"></a><span data-ttu-id="932a9-102">Vs de faits à court terme. Faits à long terme</span><span class="sxs-lookup"><span data-stu-id="932a9-102">Short-Term Facts vs. Long-Term Facts</span></span>
<span data-ttu-id="932a9-103">Deux types de faits sont déclarés dans la mémoire de travail du moteur de règles, des faits à court terme et des faits à long terme.</span><span class="sxs-lookup"><span data-stu-id="932a9-103">Two types of facts are asserted into the working memory of the rule engine—short-term facts and long-term facts.</span></span>  
  
## <a name="short-term-facts"></a><span data-ttu-id="932a9-104">Faits à court terme</span><span class="sxs-lookup"><span data-stu-id="932a9-104">Short-Term Facts</span></span>  
 <span data-ttu-id="932a9-105">Un fait à court terme est propre à un cycle d'exécution unique du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="932a9-105">A short-term fact is specific to a single execution cycle of the rule engine.</span></span> <span data-ttu-id="932a9-106">Les faits à court terme sont automatiquement retirés de la mémoire de travail du moteur de règles après l'exécution de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="932a9-106">Short-term facts are retracted automatically from the working memory of the rule engine after the policy executes.</span></span> <span data-ttu-id="932a9-107">Si les données d'une stratégie changent entre les cycles d'exécution du moteur de règles, vous soumettez ces données au moteur de règles sous la forme d'un fait à court terme.</span><span class="sxs-lookup"><span data-stu-id="932a9-107">If your data changes between execution cycles of the rule engine for a policy, you submit the data as a short-term fact to the rule engine.</span></span>  
  
 <span data-ttu-id="932a9-108">Exemples de faits à court terme :</span><span class="sxs-lookup"><span data-stu-id="932a9-108">Examples of short-term facts are:</span></span>  
  
-   <span data-ttu-id="932a9-109">Faits soumis en tant que paramètres à la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="932a9-109">The facts you submit as parameters to the **Policy.Execute** method.</span></span>  
  
-   <span data-ttu-id="932a9-110">Faits soumis en tant que paramètres à la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="932a9-110">The facts you submit as parameters to the **Call Rules** shape.</span></span>  
  
-   <span data-ttu-id="932a9-111">Faits soumis à partir d’une action d’une règle utilisant le **Assert** (fonction).</span><span class="sxs-lookup"><span data-stu-id="932a9-111">The facts you submit from an action of a rule using the **Assert** function.</span></span>  
  
## <a name="long-term-facts"></a><span data-ttu-id="932a9-112">Faits à long terme</span><span class="sxs-lookup"><span data-stu-id="932a9-112">Long-Term Facts</span></span>  
 <span data-ttu-id="932a9-113">Les faits à long terme sont chargés dans la mémoire de travail du moteur de règles pour une utilisation sur un nombre arbitraire de cycles d'exécution.</span><span class="sxs-lookup"><span data-stu-id="932a9-113">A long-term fact is loaded into the working memory of the rule engine for use over an arbitrary number of execution cycles.</span></span> <span data-ttu-id="932a9-114">En règle générale, ces faits varient peu et ne changent pas entre les différentes exécutions d'une stratégie.</span><span class="sxs-lookup"><span data-stu-id="932a9-114">Typically, long-term facts are slowly changing facts that do not typically change between executions of a policy.</span></span> <span data-ttu-id="932a9-115">Par exemple, vous pouvez décider de créer une connexion de base de données une seule fois et d'exécuter la stratégie plusieurs fois par le biais de la même connexion.</span><span class="sxs-lookup"><span data-stu-id="932a9-115">For example, you may want to create a database connection only once, and execute the policy several times by using the same database connection.</span></span> <span data-ttu-id="932a9-116">La seule véritable distinction entre les faits à court et long terme réside dans leur implémentation.</span><span class="sxs-lookup"><span data-stu-id="932a9-116">The only real distinction between short-term facts and long-term facts is in implementation.</span></span>  
  
 <span data-ttu-id="932a9-117">Pour soumettre un fait à long terme, procédez de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="932a9-117">To submit a fact as a long-term fact, you need to perform the following steps:</span></span>  
  
1.  <span data-ttu-id="932a9-118">Créez un extracteur de faits qui implémente le **IFactRetriever** interface.</span><span class="sxs-lookup"><span data-stu-id="932a9-118">Create a fact retriever component that implements the **IFactRetriever** interface.</span></span> <span data-ttu-id="932a9-119">Créez et déclarez le fait dans la mémoire de travail de la règle de moteur quand le **UpdateFacts** méthode est appelée pour la première fois et le fait que lorsque cela est nécessaire pour les appels suivants de mise à jour de la **UpdateFacts**(méthode).</span><span class="sxs-lookup"><span data-stu-id="932a9-119">Create and assert the fact into the working memory of the rule engine when the **UpdateFacts** method is invoked for the first time, and update the fact when necessary on subsequent invocations of the **UpdateFacts** method.</span></span>  
  
2.  <span data-ttu-id="932a9-120">Configurer la stratégie pour utiliser l’extracteur de faits à l’aide de l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="932a9-120">Configure the policy to use the fact retriever component by using the Business Rule Composer.</span></span>  
  
 <span data-ttu-id="932a9-121">Pour plus d’informations sur la création d’un extracteur de faits et de l’utiliser dans une stratégie, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).</span><span class="sxs-lookup"><span data-stu-id="932a9-121">For more information about creating a fact retriever and using it in a policy, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="932a9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="932a9-122">See Also</span></span>  
 [<span data-ttu-id="932a9-123">Faits</span><span class="sxs-lookup"><span data-stu-id="932a9-123">Facts</span></span>](../core/facts.md)