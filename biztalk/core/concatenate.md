---
title: "Concaténer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21a773d-a9cc-4a6f-b548-46badcd92aab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4766f65fb0cbe26c8f3c545c38235d83abb283a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="concatenate"></a><span data-ttu-id="33b94-102">Concaténation</span><span class="sxs-lookup"><span data-stu-id="33b94-102">Concatenate</span></span>
<span data-ttu-id="33b94-103">Supprime les deux premiers éléments de la pile, les concatène, puis transmet les résultats sur la pile.</span><span class="sxs-lookup"><span data-stu-id="33b94-103">Removes the top two items from the stack, concatenates them, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33b94-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Concatenate" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33b94-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33b94-105">Parameters</span></span>  
 <span data-ttu-id="33b94-106">Deux premiers éléments de la pile.</span><span class="sxs-lookup"><span data-stu-id="33b94-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="33b94-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="33b94-107">Pushed Value</span></span>  
 <span data-ttu-id="33b94-108">Chaîne de résultat de l'opération de concaténation.</span><span class="sxs-lookup"><span data-stu-id="33b94-108">String result of the concatenation operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33b94-109">Notes</span><span class="sxs-lookup"><span data-stu-id="33b94-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="33b94-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="33b94-110">Example</span></span>  
 <span data-ttu-id="33b94-111">Dans l’exemple suivant mettre à jour d’expression, la chaîne constante « démarrer : » est concaténée avec la valeur de la propriété de contexte « EventTime » et conservé dans la colonne de base de données NewOrderCreateTime.</span><span class="sxs-lookup"><span data-stu-id="33b94-111">In the following example update expression, the constant string "Start:" is concatenated with the value of the "EventTime" context property and persisted to the database column NewOrderCreateTime.</span></span>  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33b94-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33b94-112">See Also</span></span>  
 [<span data-ttu-id="33b94-113">Opérations de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="33b94-113">Interceptor Operations</span></span>](../core/interceptor-operations.md)