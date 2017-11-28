---
title: "Est égal à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac93031a-9d18-443d-9e38-71ef9edd5a30
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b82ac5c779dc6b4d3624b48cebe9df1bc3d1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="equals"></a><span data-ttu-id="b494f-102">Égal à</span><span class="sxs-lookup"><span data-stu-id="b494f-102">Equals</span></span>
<span data-ttu-id="b494f-103">Supprime les deux premiers éléments de la pile, les compare, puis transmet les résultats sur la pile.</span><span class="sxs-lookup"><span data-stu-id="b494f-103">Removes the top two items from the stack, compares the two items, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b494f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b494f-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Equals" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b494f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b494f-105">Parameters</span></span>  
 <span data-ttu-id="b494f-106">Deux premiers éléments de la pile.</span><span class="sxs-lookup"><span data-stu-id="b494f-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="b494f-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="b494f-107">Pushed Value</span></span>  
 <span data-ttu-id="b494f-108">Chaîne de résultat de l'opération de comparaison.</span><span class="sxs-lookup"><span data-stu-id="b494f-108">String result of the comparison operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b494f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b494f-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="b494f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b494f-110">Example</span></span>  
 <span data-ttu-id="b494f-111">L’exemple d’expression de filtre suivant utilise le **est égal à** opération à comparer le nom de l’activité actuelle à la constante « CheckPO ».</span><span class="sxs-lookup"><span data-stu-id="b494f-111">The following example filter expression uses the **Equals** operation to compare the current activity name to the constant "CheckPO".</span></span> <span data-ttu-id="b494f-112">Si les deux valeurs sont égales, l'expression prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="b494f-112">If the two are equal, the expression evaluates to `true`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="b494f-113">Vous pouvez être tenté de définir votre expression comme vous écririez une déclaration en langage C# en vue d'effectuer une comparaison.</span><span class="sxs-lookup"><span data-stu-id="b494f-113">You may be tempted to build your expression exactly as you would write a statement in C# when performing comparisons.</span></span> <span data-ttu-id="b494f-114">Par exemple, vous pouvez comparer trois valeurs en écrivant le code C# suivant :</span><span class="sxs-lookup"><span data-stu-id="b494f-114">For example, you might want to compare three values; in C# you would write something like:</span></span>  
  
```  
bool res = a == b == c;  
```  
  
 <span data-ttu-id="b494f-115">Un tel modèle pour votre expression de filtre reste toutefois insuffisant.</span><span class="sxs-lookup"><span data-stu-id="b494f-115">However, as a model for your expression filter this falls a little short.</span></span> <span data-ttu-id="b494f-116">Envisagez plutôt d'utiliser la déclaration modifiée (mais équivalente) suivante :</span><span class="sxs-lookup"><span data-stu-id="b494f-116">Instead, consider the modified (but equivalent) statement:</span></span>  
  
```  
Bool res = (a == b) && (a == c);  
```  
  
 <span data-ttu-id="b494f-117">Cette déclaration correspond davantage à l'expression de filtre que vous utiliseriez pour effectuer la comparaison.</span><span class="sxs-lookup"><span data-stu-id="b494f-117">This more closely matches the filter expression you would use to perform the comparison.</span></span> <span data-ttu-id="b494f-118">Pour plus d’informations et obtenir un exemple, consultez [et](../core/and.md).</span><span class="sxs-lookup"><span data-stu-id="b494f-118">For more details and an example, see [And](../core/and.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b494f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b494f-119">See Also</span></span>  
 [<span data-ttu-id="b494f-120">Opérations de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="b494f-120">Interceptor Operations</span></span>](../core/interceptor-operations.md)