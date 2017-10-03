---
title: Constante | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0af49bf5-e7de-41da-ac27-70301b8ee4d4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674307acea439bc260399cc01da4165eedaa2da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constant"></a><span data-ttu-id="a07b9-102">Constante</span><span class="sxs-lookup"><span data-stu-id="a07b9-102">Constant</span></span>
<span data-ttu-id="a07b9-103">Transmet une seule valeur constante sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a07b9-103">Pushes a single constant value onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a07b9-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Constant">  
  <ic:Argument>val</ic:Argument>  
</ic:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a07b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a07b9-105">Parameters</span></span>  
 <span data-ttu-id="a07b9-106">Valeur constante.</span><span class="sxs-lookup"><span data-stu-id="a07b9-106">Constant value.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="a07b9-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="a07b9-107">Pushed Value</span></span>  
 <span data-ttu-id="a07b9-108">Chaîne contenant la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="a07b9-108">String containing the constant value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a07b9-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a07b9-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07b9-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="a07b9-110">Example</span></span>  
 <span data-ttu-id="a07b9-111">L’exemple d’expression de filtre suivant utilise le **constante** opération pour transmettre une valeur qui sera ensuite utilisée dans une **est égal à** opération pour vous assurer que le nom de l’activité actuelle est « FoodAndDrinksPolicy ».</span><span class="sxs-lookup"><span data-stu-id="a07b9-111">The following sample filter expression uses the **Constant** operation to push a value that will then be used in an **Equals** operation to ensure that the current activity name is "FoodAndDrinksPolicy".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="a07b9-112">Il s’agit d’un modèle d’utilisation commun pour le **constante** opération.</span><span class="sxs-lookup"><span data-stu-id="a07b9-112">This is a common usage pattern for the **Constant** operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07b9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a07b9-113">See Also</span></span>  
 [<span data-ttu-id="a07b9-114">Opérations de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="a07b9-114">Interceptor Operations</span></span>](../core/interceptor-operations.md)