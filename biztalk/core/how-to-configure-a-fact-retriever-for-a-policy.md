---
title: "Comment configurer un extracteur de faits pour une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, policies
- Business Rule Composer, facts
- policies, facts
ms.assetid: a7bcf3e5-3f28-4f0e-b112-8c97dee072a1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18572af1323de817b3c934866af917d2601332f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-fact-retriever-for-a-policy"></a><span data-ttu-id="10cad-102">Comment configurer un extracteur de faits pour une stratégie</span><span class="sxs-lookup"><span data-stu-id="10cad-102">How to Configure a Fact Retriever for a Policy</span></span>
<span data-ttu-id="10cad-103">Vous pouvez stocker les faits qui changent rarement puis, avant le premier cycle d'exécution de votre application hôte, les extraire, les présenter une fois au moteur des règles pour qu'il les mette en mémoire cache et les réutiliser pour d'autres cycles d'exécution.</span><span class="sxs-lookup"><span data-stu-id="10cad-103">You can store facts that do not change frequently, and then before the first execution cycle of your host application, you can retrieve these facts from storage, present them once to the rule engine for caching, and reuse them over multiple execution cycles.</span></span>  
  
 <span data-ttu-id="10cad-104">Vous avez le choix entre deux méthodes pour associer un extracteur de faits à une stratégie :</span><span class="sxs-lookup"><span data-stu-id="10cad-104">There are two ways to associate a fact retriever with a policy.</span></span> <span data-ttu-id="10cad-105">Faire cela à l’aide de l’éditeur des règles d’entreprise ou par programmation à l’aide de la **RuleSetExecutionConfiguration** objet.</span><span class="sxs-lookup"><span data-stu-id="10cad-105">You can do this by using the Business Rule Composer or programmatically by using the **RuleSetExecutionConfiguration** object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10cad-106">Une seule implémentation d'extracteur de faits peut être associée à une version de stratégie.</span><span class="sxs-lookup"><span data-stu-id="10cad-106">Only one fact retriever implementation can be associated with a policy version.</span></span>  
  
### <a name="to-associate-a-fact-retriever-with-a-policy-in-the-business-rule-composer"></a><span data-ttu-id="10cad-107">Pour associer un extracteur de faits à une stratégie dans l'Éditeur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="10cad-107">To associate a fact retriever with a policy in the Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="10cad-108">Dans la fenêtre Explorateur de stratégies, cliquez sur la version de stratégie à laquelle vous voulez associer l'extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="10cad-108">In the Policy Explorer window, click the policy version with which you want to associate the fact retriever.</span></span>  
  
2.  <span data-ttu-id="10cad-109">Dans la fenêtre Propriétés, cliquez sur le **points de suspension** bouton (...) dans le **extracteur de faits** propriété à rechercher dans le global assembly cache pour un objet extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="10cad-109">In the Properties window, click the **ellipsis** button (…) in the **FactRetriever** property to browse in the global assembly cache for a fact retriever object.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="10cad-110">Le **points de suspension** bouton (...) n’apparaît que si vous cliquez sur le **extracteur de faits** ligne dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="10cad-110">The **ellipsis** button (…) does not appear until you click the **FactRetriever** row in the Property Window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10cad-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10cad-111">See Also</span></span>  
 [<span data-ttu-id="10cad-112">Comment créer un extracteur de faits</span><span class="sxs-lookup"><span data-stu-id="10cad-112">How to Create a Fact Retriever</span></span>](../core/how-to-create-a-fact-retriever.md)