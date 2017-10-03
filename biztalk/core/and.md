---
title: Et | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bd8f1f-edae-476d-b488-78e6c5ee70bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 676940dfa5cbc23d0c8127923d292e382a4e3cad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="and"></a><span data-ttu-id="9c001-102">And</span><span class="sxs-lookup"><span data-stu-id="9c001-102">And</span></span>
<span data-ttu-id="9c001-103">Supprime les deux premiers éléments de la pile, réalise une opération booléenne **et** de deux éléments et exécute un push du résultat dans la pile.</span><span class="sxs-lookup"><span data-stu-id="9c001-103">Removes the top two items from the stack, performs a Boolean **AND** of the two items, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c001-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c001-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="And" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c001-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c001-105">Parameters</span></span>  
 <span data-ttu-id="9c001-106">Deux premiers éléments de la pile.</span><span class="sxs-lookup"><span data-stu-id="9c001-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="9c001-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="9c001-107">Pushed Value</span></span>  
 <span data-ttu-id="9c001-108">Chaîne de résultat de la valeur booléenne **AND** opération.</span><span class="sxs-lookup"><span data-stu-id="9c001-108">String result of the Boolean **AND** operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c001-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9c001-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c001-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c001-110">Example</span></span>  
 <span data-ttu-id="9c001-111">Le **et** opération est utile lorsque vous avez besoin évaluer plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="9c001-111">The **And** operation is useful when you need to evaluate multiple statements.</span></span> <span data-ttu-id="9c001-112">L’exemple d’expression de filtre suivante vérifie si le nom de l’activité est « CheckPO » et que l’événement d’activité est fermé à l’aide de la **et** opération.</span><span class="sxs-lookup"><span data-stu-id="9c001-112">The following example filter expression checks whether the activity name is "CheckPO" and the activity event is closed by using the **And** operation.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="9c001-113">Dans cet exemple **et** est la dernière opération dans l’expression, car elle s’appuie sur les résultats des comparaisons (et les affiche à partir de la pile pour effectuer la comparaison).</span><span class="sxs-lookup"><span data-stu-id="9c001-113">In this example **And** is the final operation in the expression because it relies on the results of the comparisons (and pops them from the stack to perform the comparison).</span></span> <span data-ttu-id="9c001-114">Vous pouvez étendre cette idée à la réalisation **et** opérations sur plus de deux éléments.</span><span class="sxs-lookup"><span data-stu-id="9c001-114">You can extend this idea to perform **And** operations on more than two items.</span></span> <span data-ttu-id="9c001-115">Par exemple, pour évaluer si une condition A, une condition B et une condition  C se réalisent, vous utilisez une expression similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="9c001-115">For example, to evaluate whether Condition A and Condition B and Condition C are true, you would use an expression like the following:</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityType"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyType</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>   
```  
  
## <a name="see-also"></a><span data-ttu-id="9c001-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c001-116">See Also</span></span>  
 [<span data-ttu-id="9c001-117">Opérations de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="9c001-117">Interceptor Operations</span></span>](../core/interceptor-operations.md)