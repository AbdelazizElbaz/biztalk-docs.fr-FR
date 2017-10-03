---
title: Comment utiliser la forme Expression | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Expression shapes
- Expression shape [Orchestration Designer]
- Expression shape [Orchestration Designer], configuring
- Expression shape [Orchestration Designer], about Expression shape
ms.assetid: 2d702aa9-b824-4f47-a416-70707ce8ef29
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e263454db9674d5bc86b6b7dae1649003f3d129c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expression-shape"></a><span data-ttu-id="c1711-102">Utilisation de la forme Expression</span><span class="sxs-lookup"><span data-stu-id="c1711-102">How to Use Expression Shape</span></span>
<span data-ttu-id="c1711-103">Le **Expression** forme vous permet d’entrer une expression XLANG/s choisie dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c1711-103">The **Expression** shape enables you to enter any XLANG/s expression you choose in your orchestration.</span></span> <span data-ttu-id="c1711-104">Par exemple, vous pouvez effectuer un appel de type .NET pour exécuter un programme externe ou simplement modifier la valeur des variables de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="c1711-104">For example, you can make a .NET call to run an external program, or simply manipulate the values of your orchestration variables.</span></span>  
  
 <span data-ttu-id="c1711-105">Alors que le **Expression** forme est très souple, il n’est pas recommandé d’utiliser pour exécuter la logique d’orchestration de niveau supérieur, ce qui serait préférable visible dans l’orchestration de dessin elle-même.</span><span class="sxs-lookup"><span data-stu-id="c1711-105">While the **Expression** shape is quite flexible, it is not good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself.</span></span> <span data-ttu-id="c1711-106">En général, il est plus facile à comprendre et à gérer vos orchestrations si votre **Expression** formes contiennent des expressions simples et modulables.</span><span class="sxs-lookup"><span data-stu-id="c1711-106">In general, it is easier to understand and maintain your orchestrations if your **Expression** shapes contain simple and modular expressions.</span></span>  
  
### <a name="to-configure-an-expression-shape"></a><span data-ttu-id="c1711-107">Pour configurer une forme Expression</span><span class="sxs-lookup"><span data-stu-id="c1711-107">To configure an Expression shape</span></span>  
  
1.  <span data-ttu-id="c1711-108">Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur le **Expression** mettre en forme et cliquez sur **modifier l’Expression** ou, dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) bouton pour le **Expression** propriété.</span><span class="sxs-lookup"><span data-stu-id="c1711-108">If BizTalk Expression Editor is not visible, right-click the **Expression** shape and click **Edit Expression** or, in the Properties window, click the Ellipsis (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="c1711-109">Dans l'Éditeur d'expression BizTalk, créez une expression pour affecter des valeurs.</span><span class="sxs-lookup"><span data-stu-id="c1711-109">In BizTalk Expression Editor, create an expression to assign values.</span></span> <span data-ttu-id="c1711-110">Pour plus d’informations, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c1711-110">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1711-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1711-111">See Also</span></span>  
 [<span data-ttu-id="c1711-112">Langage XLANG-s</span><span class="sxs-lookup"><span data-stu-id="c1711-112">XLANG-s Language</span></span>](../core/xlang-s-language.md)