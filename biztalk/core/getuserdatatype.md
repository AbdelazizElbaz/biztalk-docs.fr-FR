---
title: GetUserDataType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0605919-a733-4a9d-a725-109346db11a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5525dba034571acd91d1f3dd99f2b56069f81fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getuserdatatype"></a><span data-ttu-id="efb11-102">GetUserDataType</span><span class="sxs-lookup"><span data-stu-id="efb11-102">GetUserDataType</span></span>
<span data-ttu-id="efb11-103">Transmet le nom du type de données utilisateur actuel sur la pile.</span><span class="sxs-lookup"><span data-stu-id="efb11-103">Pushes the name of the current user data type onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efb11-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserDataType" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efb11-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efb11-105">Parameters</span></span>  
 <span data-ttu-id="efb11-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="efb11-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="efb11-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="efb11-107">Pushed Value</span></span>  
 <span data-ttu-id="efb11-108">Chaîne contenant le type de données utilisateur actuel au format qualifié pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="efb11-108">String containing the current user data type in assembly-qualified format.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efb11-109">Notes</span><span class="sxs-lookup"><span data-stu-id="efb11-109">Remarks</span></span>  
 <span data-ttu-id="efb11-110">Contrairement aux **GetActivityType**, cette opération n’utilise pas le format du nom de classe qualifié d’assembly ; au lieu de cela, il transmet uniquement le nom du type :</span><span class="sxs-lookup"><span data-stu-id="efb11-110">Unlike **GetActivityType**, this operation does not use the assembly-qualified class name format; instead, it pushes only the type name:</span></span>  
  
```  
MyLibrary.MyObject  
```  
  
> [!NOTE]
>  <span data-ttu-id="efb11-111">Si vous utilisez le format de nom de classe qualifié pour les assemblys comme une constante lors de la comparaison de valeurs, le résultat donnera toujours `false`.</span><span class="sxs-lookup"><span data-stu-id="efb11-111">If you use the assembly-qualified class name format as a constant when comparing values it will always evaluate to `false`.</span></span>  
  
## <a name="special-filter-behavior"></a><span data-ttu-id="efb11-112">Comportement de filtre spécial</span><span class="sxs-lookup"><span data-stu-id="efb11-112">Special Filter Behavior</span></span>  
 <span data-ttu-id="efb11-113">Lorsque cette opération est effectuée dans un filtre, les types de données utilisateur dérivés sont également mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="efb11-113">When this operation is performed inside of a filter, derived user data types are always matched as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efb11-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="efb11-114">Example</span></span>  
 <span data-ttu-id="efb11-115">L'exemple suivant contient une expression de filtre d'événements qui donne le résultat `true` pour les instances `MyLibrary.MyObject` et pour toutes les instances de classes qui dérivent de `MyLibrary.MyObject`.</span><span class="sxs-lookup"><span data-stu-id="efb11-115">The following sample contains an event filter expression that will evaluate to `true` for `MyLibrary.MyObject` instances and for any instances from classes that derive from `MyLibrary.MyObject`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyLibrary.MyObject</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```