---
title: GetWorkflowProperty | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9d3029e-3267-46bc-ba2e-1c6fa1f2e931
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505fc41ce544cdf16e3826116514ba1991ba012e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowproperty"></a><span data-ttu-id="16691-102">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="16691-102">GetWorkflowProperty</span></span>
<span data-ttu-id="16691-103">Transmet la propriété extraite de l'activité racine du workflow sur la pile.</span><span class="sxs-lookup"><span data-stu-id="16691-103">Pushes the extracted property from the root activity of the workflow onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16691-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16691-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16691-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16691-105">Parameters</span></span>  
 <span data-ttu-id="16691-106">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="16691-106">Name of the property.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="16691-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="16691-107">Pushed Value</span></span>  
 <span data-ttu-id="16691-108">Chaîne contenant la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="16691-108">String containing the value of the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16691-109">Notes</span><span class="sxs-lookup"><span data-stu-id="16691-109">Remarks</span></span>  
 <span data-ttu-id="16691-110">L'opération est uniquement valide dans les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="16691-110">This operation is only valid in Updates.</span></span>  
  
 <span data-ttu-id="16691-111">Vous pouvez utiliser la notation ponctuée pour qualifier le nom de propriété que vous souhaitez extraire.</span><span class="sxs-lookup"><span data-stu-id="16691-111">You can use dotted-notation for qualifying the property name you want to retrieve.</span></span> <span data-ttu-id="16691-112">Vous aurez ainsi accès aux objets situés dans d'autres objets exposés via les propriétés.</span><span class="sxs-lookup"><span data-stu-id="16691-112">This will provide you access to objects inside of other objects exposed through properties.</span></span> <span data-ttu-id="16691-113">Par exemple, pour accéder à la propriété City d'une instance Address d'un bon de commande, utilisez « purchaseOrder.Address.City ».</span><span class="sxs-lookup"><span data-stu-id="16691-113">For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".</span></span>  
  
 <span data-ttu-id="16691-114">Les noms de propriété respectent d'abord la casse, puis ne la respectent pas.</span><span class="sxs-lookup"><span data-stu-id="16691-114">Property names are case-sensitive first, and then case-insensitive.</span></span> <span data-ttu-id="16691-115">Ce point est important lorsque plusieurs propriétés d'activité de votre application WF varient uniquement au niveau de la casse.</span><span class="sxs-lookup"><span data-stu-id="16691-115">This is important when you have two or more activity properties that vary only by case in your WF application.</span></span> <span data-ttu-id="16691-116">Par exemple, si votre application de flux de travail possède les propriétés « myWorkflow » et « MyWorkflow » et que vous recherchez « MyWorkflow », vous obtiendrez comme résultat la deuxième propriété car la casse correspond.</span><span class="sxs-lookup"><span data-stu-id="16691-116">For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match.</span></span> <span data-ttu-id="16691-117">Si vous spécifiez « MYWORKFLOW », vous obtiendrez comme résultat la propriété « myWorkflow », qui respecte la casse étant donné que la tentative de non-respect de la casse a échoué.</span><span class="sxs-lookup"><span data-stu-id="16691-117">If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-sensitive match after a case-insensitive match attempt fails.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16691-118">Les valeurs de propriété NULL génèreront le renvoi d'une exception NullReferenceException dans l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="16691-118">NULL property values will result in a NullReferenceException being thrown back to the workflow instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16691-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="16691-119">Example</span></span>  
 <span data-ttu-id="16691-120">Dans l'exemple suivant, une expression de mise à jour permet de rendre la propriété de workflow « City » persistante dans un bon de commande à l'aide de `GetWorkflowProperty`.</span><span class="sxs-lookup"><span data-stu-id="16691-120">In the following sample, an update expression is used to persist the workflow property "City" from a purchase order by using `GetWorkflowProperty`.</span></span>  
  
```  
<ic:Update DataItemName="City" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>po.Info.City</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```