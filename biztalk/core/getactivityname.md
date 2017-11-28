---
title: GetActivityName | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 479552fa-1535-4f3d-90ff-4615f14c88b1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55e8f35746f5f4ed1bbbe10a4d45300895340869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityname"></a><span data-ttu-id="02c7d-102">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="02c7d-102">GetActivityName</span></span>
<span data-ttu-id="02c7d-103">Transmet le nom de l'activité en cours sur la pile.</span><span class="sxs-lookup"><span data-stu-id="02c7d-103">Pushes the name of the current activity onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02c7d-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityName"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02c7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02c7d-105">Parameters</span></span>  
 <span data-ttu-id="02c7d-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="02c7d-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="02c7d-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="02c7d-107">Pushed Value</span></span>  
 <span data-ttu-id="02c7d-108">Chaîne contenant le nom de l'activité en cours.</span><span class="sxs-lookup"><span data-stu-id="02c7d-108">String containing the current activity name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02c7d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="02c7d-109">Remarks</span></span>  
 <span data-ttu-id="02c7d-110">Windows Workflow Foundation exécute ses tâches au moyen d'une série d'activités configurée par le développeur.</span><span class="sxs-lookup"><span data-stu-id="02c7d-110">Windows Workflow Foundation performs its work as a series of activities configured by the developer.</span></span> <span data-ttu-id="02c7d-111">Un nom unique est assigné à chacune de ces activités au sein du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="02c7d-111">Each of these activities is assigned a unique name within the workflow.</span></span> <span data-ttu-id="02c7d-112">Vous pouvez intercepter des données concernant une activité spécifique en filtrant sur le nom unique.</span><span class="sxs-lookup"><span data-stu-id="02c7d-112">You can intercept data for a specific activity by filtering based on its unique name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02c7d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="02c7d-113">Example</span></span>  
 <span data-ttu-id="02c7d-114">L’exemple suivant contient une expression de filtre d’événement configurée pour rechercher une activité spécifique, FoodAndDrinksPolicy — dans un flux de travail fermé.</span><span class="sxs-lookup"><span data-stu-id="02c7d-114">The following sample contains an event filter expression configured to find a specific activity—FoodAndDrinksPolicy—in a Closed workflow.</span></span> <span data-ttu-id="02c7d-115">à l'aide d'une combinaison d'opérations comprenant `GetActivityName`, `GetActivityEvent` ainsi que des opérations logiques.</span><span class="sxs-lookup"><span data-stu-id="02c7d-115">This is done by using a combination of operations including `GetActivityName`, `GetActivityEvent`, and logical operations.</span></span>  
  
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
  
 <span data-ttu-id="02c7d-116">Ce modèle de filtre est commun aux fichiers de configuration de l'intercepteur Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="02c7d-116">This filter pattern is common with Windows Workflow Foundation interceptor configuration files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02c7d-117">Les arguments ne requièrent pas de guillemets, sauf si vous tentez explicitement de rechercher une chaîne contenant des guillemets.</span><span class="sxs-lookup"><span data-stu-id="02c7d-117">Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.</span></span>