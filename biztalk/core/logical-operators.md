---
title: "Opérateurs logiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aaceb64-a5a0-462a-a0eb-8352bed999e5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3b3c187e353babafd86590fdeacdc19fc115b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logical-operators"></a><span data-ttu-id="e7725-102">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="e7725-102">Logical Operators</span></span>
<span data-ttu-id="e7725-103">L'infrastructure des règles d'entreprise prend en charge l'utilisation des opérateurs logiques AND, OR et NOT lors de la création des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7725-103">The Business Rules Framework supports using the logical AND, logical OR, and logical NOT operators in creating business rules.</span></span> <span data-ttu-id="e7725-104">Le tableau suivant décrit ces opérateurs logiques.</span><span class="sxs-lookup"><span data-stu-id="e7725-104">The following table describes the logical operators.</span></span>  
  
|<span data-ttu-id="e7725-105">Opérateur logique</span><span class="sxs-lookup"><span data-stu-id="e7725-105">Logical Operator</span></span>|<span data-ttu-id="e7725-106"> Description</span><span class="sxs-lookup"><span data-stu-id="e7725-106">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e7725-107">**AND**</span><span class="sxs-lookup"><span data-stu-id="e7725-107">**AND**</span></span>|<span data-ttu-id="e7725-108">Retourne **true** si les deux opérandes ont la valeur **true**; sinon, retourne **false**.</span><span class="sxs-lookup"><span data-stu-id="e7725-108">Returns **true** if both the operands evaluate to **true**; otherwise returns **false**.</span></span>|  
|<span data-ttu-id="e7725-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="e7725-109">**OR**</span></span>|<span data-ttu-id="e7725-110">Retourne **true** si l’un des opérandes a la valeur **true**, sinon retourne **false**.</span><span class="sxs-lookup"><span data-stu-id="e7725-110">Returns **true** if one of the operands evaluates to **true**, otherwise returns **false**.</span></span>|  
|<span data-ttu-id="e7725-111">**NOT**</span><span class="sxs-lookup"><span data-stu-id="e7725-111">**NOT**</span></span>|<span data-ttu-id="e7725-112">Retourne **true** si l’opérande a la valeur **false**, sinon retourne **false**.</span><span class="sxs-lookup"><span data-stu-id="e7725-112">Returns **true** if the operand evaluates to **false**, otherwise returns **false**.</span></span>|  
  
 <span data-ttu-id="e7725-113">Lorsque les opérandes sont de type différent, le moteur de règles convertit le type de l'un des paramètres afin qu'il corresponde à celui de l'autre paramètre, ou bien convertit les types des deux paramètres en un type commun avant d'évaluer l'expression.</span><span class="sxs-lookup"><span data-stu-id="e7725-113">When operands are of different types, the rule engine converts type of one of the parameters to match the type of the other parameter or converts types of both the parameters to a common type before evaluating the expression.</span></span>  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a><span data-ttu-id="e7725-114">Pour utiliser un opérateur logique dans une règle d'entreprise</span><span class="sxs-lookup"><span data-stu-id="e7725-114">To use a logical operator in a business rule</span></span>  
 <span data-ttu-id="e7725-115">Procédez comme suit pour utiliser un opérateur logique dans une règle d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7725-115">Use the following procedure to use a logical operator in a business rule.</span></span>  
  
1.  <span data-ttu-id="e7725-116">Dans le **IF** avec le bouton droit du volet de l’éditeur des règles d’entreprise, le **Conditions** nœud et sélectionnez l’opérateur logique que vous souhaitez ajouter à l’expression logique.</span><span class="sxs-lookup"><span data-stu-id="e7725-116">In the **IF** pane of Business Rule Composer, right-click the **Conditions** node, and then select the logical operator that you wish to add to the logical expression.</span></span>  
  
2.  <span data-ttu-id="e7725-117">Cliquez avec le bouton droit sur l'opérateur logique, puis ajoutez les prédicats ou opérateurs logiques imbriqués souhaités.</span><span class="sxs-lookup"><span data-stu-id="e7725-117">Right-click the logical operator, and add the predicates or nested logical operators you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7725-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7725-118">See Also</span></span>  
 [<span data-ttu-id="e7725-119">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="e7725-119">Arithmetic Operators</span></span>](../core/arithmetic-operators.md)