---
title: GetActivityEvent | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fe824c9-4cea-44da-b830-5520d67988e0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fb039c0e9946091214a52fbb605753a212c233c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityevent"></a><span data-ttu-id="3cc63-102">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="3cc63-102">GetActivityEvent</span></span>
<span data-ttu-id="3cc63-103">Transmet le nom de l'événement d'activité en cours sur la pile.</span><span class="sxs-lookup"><span data-stu-id="3cc63-103">Pushes the name of the current activity event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cc63-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityEvent"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cc63-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3cc63-105">Parameters</span></span>  
 <span data-ttu-id="3cc63-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3cc63-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="3cc63-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="3cc63-107">Pushed Value</span></span>  
 <span data-ttu-id="3cc63-108">Chaîne contenant l'événement d'activité en cours.</span><span class="sxs-lookup"><span data-stu-id="3cc63-108">String containing the current activity event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc63-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3cc63-109">Remarks</span></span>  
 <span data-ttu-id="3cc63-110">Une activité de workflow peut passer par plusieurs états pendant la durée de vie du workflow.</span><span class="sxs-lookup"><span data-stu-id="3cc63-110">A workflow activity can pass through several states during the lifetime of the workflow.</span></span> <span data-ttu-id="3cc63-111">L'intercepteur BAM de Windows Workflow Foundation prend en charge la plupart des valeurs d'état d'exécution définies par l'énumération `System.Workflow.ComponentModel.ActivityExecutionStatus`, comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="3cc63-111">The Windows Workflow Foundation BAM interceptor supports most of the execution status values defined by the `System.Workflow.ComponentModel.ActivityExecutionStatus` enumeration, as shown in the following table.</span></span>  
  
|<span data-ttu-id="3cc63-112">État de l'exécution</span><span class="sxs-lookup"><span data-stu-id="3cc63-112">Execution status</span></span>|<span data-ttu-id="3cc63-113">Description</span><span class="sxs-lookup"><span data-stu-id="3cc63-113">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="3cc63-114">Canceling</span><span class="sxs-lookup"><span data-stu-id="3cc63-114">Canceling</span></span>|<span data-ttu-id="3cc63-115">Représente l'état d'une activité qui est en cours d'annulation.</span><span class="sxs-lookup"><span data-stu-id="3cc63-115">Represents the status when an activity is in the process of being canceled.</span></span>|  
|<span data-ttu-id="3cc63-116">Closed</span><span class="sxs-lookup"><span data-stu-id="3cc63-116">Closed</span></span>|<span data-ttu-id="3cc63-117">Représente l'état d'une activité qui est fermée.</span><span class="sxs-lookup"><span data-stu-id="3cc63-117">Represents the status when an activity is closed.</span></span>|  
|<span data-ttu-id="3cc63-118">Compensating</span><span class="sxs-lookup"><span data-stu-id="3cc63-118">Compensating</span></span>|<span data-ttu-id="3cc63-119">Représente l'état d'une activité en cours de compensation.</span><span class="sxs-lookup"><span data-stu-id="3cc63-119">Represents the status when an activity is compensating.</span></span>|  
|<span data-ttu-id="3cc63-120">Executing</span><span class="sxs-lookup"><span data-stu-id="3cc63-120">Executing</span></span>|<span data-ttu-id="3cc63-121">Représente l'état d'une activité en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="3cc63-121">Represents the status when an activity is executing.</span></span>|  
|<span data-ttu-id="3cc63-122">Faulting</span><span class="sxs-lookup"><span data-stu-id="3cc63-122">Faulting</span></span>|<span data-ttu-id="3cc63-123">Représente l'état d'une activité défaillante.</span><span class="sxs-lookup"><span data-stu-id="3cc63-123">Represents the status when an activity is faulting.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3cc63-124">Vous ne pouvez pas utiliser `GetActivityEvent` et `GetWorkflowEvent` dans le même élément OnEvent.</span><span class="sxs-lookup"><span data-stu-id="3cc63-124">You cannot use both `GetActivityEvent` and `GetWorkflowEvent` in the same OnEvent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc63-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3cc63-125">Example</span></span>  
 <span data-ttu-id="3cc63-126">L'exemple suivant contient une expression de filtre d'événements configurée pour rechercher une activité spécifique (FoodAndDrinksPolicy) au sein d'un flux de travail fermé</span><span class="sxs-lookup"><span data-stu-id="3cc63-126">The following sample contains an event filter expression configured to find a specific activity—FoodAndDringPolicy—in a Closed workflow.</span></span> <span data-ttu-id="3cc63-127">à l'aide d'une combinaison d'opérations comprenant `GetActivityEvent`, `GetActivityName` ainsi que des opérations logiques.</span><span class="sxs-lookup"><span data-stu-id="3cc63-127">This is done by using a combination of operations including `GetActivityEvent`, `GetActivityName`, and logical operations.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
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
  
 <span data-ttu-id="3cc63-128">Ce modèle de filtre est commun aux fichiers de configuration de l'intercepteur Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="3cc63-128">This filter pattern is common with Windows Workflow Foundation interceptor configuration files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cc63-129">Les arguments ne requièrent pas de guillemets, sauf si vous tentez explicitement de rechercher une chaîne contenant des guillemets.</span><span class="sxs-lookup"><span data-stu-id="3cc63-129">Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc63-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cc63-130">See Also</span></span>  
 [<span data-ttu-id="3cc63-131">Énumération System.Workflow.ComponentModel.ActivityExecutionStatus</span><span class="sxs-lookup"><span data-stu-id="3cc63-131">System.Workflow.ComponentModel.ActivityExecutionStatus enumeration</span></span>](http://go.microsoft.com/fwlink/?LinkId=119570)