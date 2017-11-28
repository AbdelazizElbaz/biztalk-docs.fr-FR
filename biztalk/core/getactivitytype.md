---
title: GetActivityType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a5aae3-9688-4c49-a78e-1d9c1cc85fea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67e6f31331907e20e810c11e82002fb08b89abe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivitytype"></a><span data-ttu-id="ead58-102">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="ead58-102">GetActivityType</span></span>
<span data-ttu-id="ead58-103">Transmet le nom du type d'activité en cours sur la pile.</span><span class="sxs-lookup"><span data-stu-id="ead58-103">Pushes the name of the current activity type onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ead58-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityType" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ead58-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ead58-105">Parameters</span></span>  
 <span data-ttu-id="ead58-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ead58-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="ead58-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="ead58-107">Pushed Value</span></span>  
 <span data-ttu-id="ead58-108">Chaîne contenant le type d'activité en cours dans le format de nom de classe qualifié d'assembly.</span><span class="sxs-lookup"><span data-stu-id="ead58-108">String containing the current activity type in assembly-qualified class name format.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ead58-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ead58-109">Remarks</span></span>  
 <span data-ttu-id="ead58-110">L'opération `GetActivityType` récupère le type d'activité en cours et le place sur la pile au format de nom de classe qualifié d'assembly :</span><span class="sxs-lookup"><span data-stu-id="ead58-110">The `GetActivityType` operation retrieves the current activity type and places it on the stack in assembly-qualified class name format:</span></span>  
  
```  
TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08, processorArchitecture=MSIL  
```  
  
 <span data-ttu-id="ead58-111">Lors de la comparaison, vous pouvez spécifier le type autant que nécessaire pour satisfaire vos besoins de recherche spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ead58-111">When comparing, you can specify as much of the type as necessary to satisfy your specific search needs.</span></span> <span data-ttu-id="ead58-112">Par exemple, vous pouvez comparer le résultat de GetActivityType avec la constante :</span><span class="sxs-lookup"><span data-stu-id="ead58-112">For example, you might compare the result of GetActivityType with the constant:</span></span>  
  
 <span data-ttu-id="ead58-113">TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0</span><span class="sxs-lookup"><span data-stu-id="ead58-113">TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0</span></span>  
  
 <span data-ttu-id="ead58-114">Ceci est moins restrictif que le format de nom de classe qualifié d'assembly.</span><span class="sxs-lookup"><span data-stu-id="ead58-114">This is less restrictive than the assembly-qualified class name format.</span></span>  
  
## <a name="special-filter-behavior"></a><span data-ttu-id="ead58-115">Comportement de filtre spécial</span><span class="sxs-lookup"><span data-stu-id="ead58-115">Special Filter Behavior</span></span>  
 <span data-ttu-id="ead58-116">Lorsque cette opération est effectuée dans un filtre, les activités dérivées sont également mises en correspondance.</span><span class="sxs-lookup"><span data-stu-id="ead58-116">When this operation is performed inside of a filter, derived activities are always matched as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead58-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ead58-117">Example</span></span>  
 <span data-ttu-id="ead58-118">L'exemple suivant contient une expression de filtre d'événement qui donne le résultat `true` pour les instances `System.Workflow.ComponentModel.Activity` et les instances des classes dérivées de `System.Workflow.ComponentModel.Activity`.</span><span class="sxs-lookup"><span data-stu-id="ead58-118">The following sample contains an event filter expression that will evaluate to `true` for `System.Workflow.ComponentModel.Activity` instances and any instances from classes that derive from `System.Workflow.ComponentModel.Activity`.</span></span>  
  
```  
<ic:Expression>  
  <wf:Operation Name="GetActivityType" />  
  <ic:Operation Name="Constant">  
    <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
  </ic:Operation>  
  <ic:Operation Name="Equals" />  
</ic:Expression>  
```