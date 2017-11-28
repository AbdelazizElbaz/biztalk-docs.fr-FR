---
title: GetActivityProperty | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2321f1ec-d98d-478f-bb1d-a11a98e60fa5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55f0d24da85088fb8f13693c8c71d32bee1bef7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityproperty"></a><span data-ttu-id="b9140-102">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="b9140-102">GetActivityProperty</span></span>
<span data-ttu-id="b9140-103">Transmet la propriété extraite de l'activité associée à l'événement de suivi dans la pile.</span><span class="sxs-lookup"><span data-stu-id="b9140-103">Pushes the extracted property from the activity related to the tracking event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9140-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9140-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9140-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9140-105">Parameters</span></span>  
 <span data-ttu-id="b9140-106">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b9140-106">Name of the property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9140-107">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b9140-107">Return Value</span></span>  
 <span data-ttu-id="b9140-108">Chaîne contenant la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b9140-108">String containing the value of the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9140-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b9140-109">Remarks</span></span>  
 <span data-ttu-id="b9140-110">Vous pouvez utiliser la notation ponctuée pour qualifier le nom de propriété que vous souhaitez extraire.</span><span class="sxs-lookup"><span data-stu-id="b9140-110">You can use dotted-notation for qualifying the property name you want to retrieve.</span></span> <span data-ttu-id="b9140-111">Vous aurez ainsi accès aux objets situés dans d'autres objets exposés via les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b9140-111">This will provide you access to objects inside of other objects exposed through properties.</span></span> <span data-ttu-id="b9140-112">Par exemple, pour accéder à la propriété City d'une instance Address d'un bon de commande, utilisez « purchaseOrder.Address.City ».</span><span class="sxs-lookup"><span data-stu-id="b9140-112">For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".</span></span>  
  
 <span data-ttu-id="b9140-113">Les noms de propriété respectent d'abord la casse, puis ne la respectent pas.</span><span class="sxs-lookup"><span data-stu-id="b9140-113">Property names are case-sensitive first, and then case-insensitive.</span></span> <span data-ttu-id="b9140-114">Ce point est important lorsque plusieurs propriétés d'activité de votre application WF varient uniquement au niveau de la casse.</span><span class="sxs-lookup"><span data-stu-id="b9140-114">This is important when you have two or more activity properties that vary only by case in your WF application.</span></span> <span data-ttu-id="b9140-115">Par exemple, si votre application de flux de travail possède les propriétés « myWorkflow » et « MyWorkflow » et que vous recherchez « MyWorkflow », vous obtiendrez comme résultat la deuxième propriété car la casse correspond.</span><span class="sxs-lookup"><span data-stu-id="b9140-115">For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match.</span></span> <span data-ttu-id="b9140-116">Si vous recherchez « MYWORKFLOW », la recherche avec distinction de casse ne donnera aucun résultat, mais si vous relancez la recherche sans distinction de casse, le résultat « myWorkflow » s'affichera.</span><span class="sxs-lookup"><span data-stu-id="b9140-116">If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-insensitive match after a case-sensitive match attempt fails.</span></span>  
  
 <span data-ttu-id="b9140-117">Par exemple, si vous avez deux propriétés de l’activité qui varient uniquement par la casse : « myProperty » et « MyProperty ».</span><span class="sxs-lookup"><span data-stu-id="b9140-117">For example, if you have two activity properties that vary only by case: "myProperty" and "MyProperty".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9140-118">Les valeurs de propriété NULL génèreront le renvoi d'une exception NullReferenceException dans l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="b9140-118">NULL property values will result in a NullReferenceException being thrown back to the workflow instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9140-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9140-119">Example</span></span>  
 <span data-ttu-id="b9140-120">Dans l'exemple suivant, une expression de mise à jour permet de rendre la propriété d'activité « MyProperty » persistante à l'aide de `GetActivityProperty`.</span><span class="sxs-lookup"><span data-stu-id="b9140-120">In the following sample, an update expression is used to persist the activity property "MyProperty" by using `GetActivityProperty`.</span></span>  
  
```  
<ic:Update DataItemName="TextData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetActivityProperty">  
      <wf:Argument>MyProperty</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```