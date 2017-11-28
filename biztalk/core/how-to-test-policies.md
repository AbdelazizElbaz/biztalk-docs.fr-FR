---
title: "Comment tester les stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- Business Rule Composer, testing
- Business Rule Composer, policies
- testing, Business Rule Composer
- policies, testing
ms.assetid: 122dee26-d1f1-49a6-a6d5-a9d3d861a66b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7a0f8c0d63d14d5a529039a6e1c8af5b363cc9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-policies"></a><span data-ttu-id="67a86-102">Comment les stratégies de Test</span><span class="sxs-lookup"><span data-stu-id="67a86-102">How to Test Policies</span></span>
<span data-ttu-id="67a86-103">Pour tester une stratégie, vous avez besoin de faits sur lesquels les règles peuvent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="67a86-103">To test a policy, you need facts on which the rules can be executed.</span></span> <span data-ttu-id="67a86-104">Vous pouvez ajouter des faits en spécifiant des valeurs dans les documents XML ou dans les tables de bases de données vers lesquels vous pointerez dans le testeur de stratégie, ou vous pouvez utiliser un créateur de faits qui fournira au moteur un ensemble d'objets .NET en guise de faits.</span><span class="sxs-lookup"><span data-stu-id="67a86-104">You can add facts by specifying values in XML documents or database tables that you will point to in the policy tester, or you can use a fact creator to supply to the engine an array of .NET objects as facts.</span></span> <span data-ttu-id="67a86-105">Pour plus d’informations, consultez [création d’un créateur de faits](../core/how-to-create-a-fact-creator.md).</span><span class="sxs-lookup"><span data-stu-id="67a86-105">For more information, see [Creating a Fact Creator](../core/how-to-create-a-fact-creator.md).</span></span>  
  
### <a name="to-test-a-policy-in-the-business-rule-composer"></a><span data-ttu-id="67a86-106">Pour tester une stratégie dans l’Éditeur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67a86-106">To test a policy in the Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="67a86-107">Dans la fenêtre Explorateur de stratégies, cliquez sur la version de stratégie que vous voulez tester.</span><span class="sxs-lookup"><span data-stu-id="67a86-107">In the Policy Explorer window, click the policy version that you want to test.</span></span>  
  
2.  <span data-ttu-id="67a86-108">Cliquez sur le **tester la stratégie** bouton (flèche verte) dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="67a86-108">Click the **Test Policy** button (green arrow) on the menu bar.</span></span>  
  
     <span data-ttu-id="67a86-109">Le volet du haut affiche les types de faits référencés par les règles de stratégie.</span><span class="sxs-lookup"><span data-stu-id="67a86-109">The top pane displays the fact types that the policy rules reference.</span></span>  
  
3.  <span data-ttu-id="67a86-110">Pour ajouter une instance de fait, cliquez sur une **Document XML** ou **Table de base de données** type de fait, puis cliquez sur **ajouter une Instance**.</span><span class="sxs-lookup"><span data-stu-id="67a86-110">To add a fact instance, click an **XML Document** or **Database Table** fact type, and then click **Add Instance**.</span></span>  
  
4.  <span data-ttu-id="67a86-111">Si vous souhaitez supprimer une instance de fait, cliquez sur le type de fait correspondant, puis cliquez sur **supprimer une Instance**.</span><span class="sxs-lookup"><span data-stu-id="67a86-111">If you want to remove a fact instance, click the corresponding fact type, and then click **Remove Instance**.</span></span>  
  
5.  <span data-ttu-id="67a86-112">Si vous souhaitez ajouter un créateur de faits que vous avez écrit, cliquez sur **ajouter** dans le volet du créateur de faits.</span><span class="sxs-lookup"><span data-stu-id="67a86-112">If you want to add a fact creator that you have written, click **Add** in the fact creator pane.</span></span>  
  
6.  <span data-ttu-id="67a86-113">Cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="67a86-113">Click **Test**.</span></span>  
  
     <span data-ttu-id="67a86-114">Le résultat du suivi du test de la stratégie s’affiche dans la fenêtre de sortie de test.</span><span class="sxs-lookup"><span data-stu-id="67a86-114">The policy test trace output appears in the test output window.</span></span>  
  
7.  <span data-ttu-id="67a86-115">Cliquez avec le bouton droit dans la fenêtre de sortie pour enregistrer, effacer, sélectionner ou copier le texte de sortie.</span><span class="sxs-lookup"><span data-stu-id="67a86-115">Right-click in the output window to save, clear, select, or copy the output text.</span></span>  
  
     ![](../core/media/ebiz-testpolicy.gif "ebiz_testpolicy")  
<span data-ttu-id="67a86-116">Sélection de faits pour le test d’une stratégie</span><span class="sxs-lookup"><span data-stu-id="67a86-116">Selecting fact to test a policy</span></span>