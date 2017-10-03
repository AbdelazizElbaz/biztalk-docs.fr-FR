---
title: Exemple de calcul de la mise en attente | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4da41d0d-10ee-4f64-97d1-3cfa9da153f7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ff231b630a5848494c45cd8d4d05f89e764eb41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-dehydration-calculation"></a><span data-ttu-id="52810-102">Exemple de calcul de mise en attente</span><span class="sxs-lookup"><span data-stu-id="52810-102">Sample Dehydration Calculation</span></span>
<span data-ttu-id="52810-103">Voici un exemple de calcul, basé sur des octets privés, permettant de déterminer la mise en attente ou non de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="52810-103">Here is an example of a sample calculation, using private bytes, to determine if BizTalk will dehydrate or not.</span></span> <span data-ttu-id="52810-104">Il utilise les valeurs configurées par défaut et quelques exemples de valeurs d'exécution.</span><span class="sxs-lookup"><span data-stu-id="52810-104">It uses the default configured values, and some example run-time values.</span></span>  
  
 <span data-ttu-id="52810-105">Attribuons les valeurs suivantes aux propriétés de mise en attente :</span><span class="sxs-lookup"><span data-stu-id="52810-105">Assume the following values for the dehydration properties:</span></span>  
  
-   <span data-ttu-id="52810-106">**TimeBlocked** = 60 (heure de l’exemple bloqué en secondes)</span><span class="sxs-lookup"><span data-stu-id="52810-106">**TimeBlocked** = 60 (example time blocked in seconds)</span></span>  
  
-   <span data-ttu-id="52810-107">**WaitingHistory** = 90 (exemple d’historique en attente en secondes)</span><span class="sxs-lookup"><span data-stu-id="52810-107">**WaitingHistory** = 90 (example waiting history in seconds)</span></span>  
  
-   <span data-ttu-id="52810-108">**ActualPrivateBytes** = 250 (exemple de valeur pour les octets privés)</span><span class="sxs-lookup"><span data-stu-id="52810-108">**ActualPrivateBytes** = 250 (example value for private bytes)</span></span>  
  
-   <span data-ttu-id="52810-109">**OptimalUsage** = 50 (valeur de configuration par défaut)</span><span class="sxs-lookup"><span data-stu-id="52810-109">**OptimalUsage** = 50 (default configuration value)</span></span>  
  
-   <span data-ttu-id="52810-110">**MaximalUsage** = 350 (valeur de configuration par défaut)</span><span class="sxs-lookup"><span data-stu-id="52810-110">**MaximalUsage** = 350 (default configuration value)</span></span>  
  
 <span data-ttu-id="52810-111">Étant donné que la **ActualPrivateBytes** sont comprises entre **OptimalUsage** et **MaximalUsage**, alpha est calculé comme suit :</span><span class="sxs-lookup"><span data-stu-id="52810-111">Since the **ActualPrivateBytes** are between **OptimalUsage** and **MaximalUsage**, alpha is calculated as:</span></span>  
  
```  
alpha(private) = (350 – 250) / 350 – 50)  
alpha(private) = 100 / 300  
alpha(private) = 0.33  
```  
  
 <span data-ttu-id="52810-112">Ensuite vous calculez le **TestThreshold** comme suit :</span><span class="sxs-lookup"><span data-stu-id="52810-112">Then you calculate the **TestThreshold** as follows:</span></span>  
  
```  
TestThreshold = 1 + (0.33 * (1800 – 1))  
TestThreshold = 1 + 599.66  
TestThreshold = 600.66  
```  
  
 <span data-ttu-id="52810-113">Puis, vous prenez la décision ou non de mettre en attente :</span><span class="sxs-lookup"><span data-stu-id="52810-113">And finally, make the decision to dehydrate or not:</span></span>  
  
```  
Dehydrate = (90 == -1 OR 90 > 600 OR 60 > (2 * 600))  
Dehydrate = false  
```  
  
 <span data-ttu-id="52810-114">Dans cet exemple, vous pouvez voir que l'orchestration ne sera pas mise en attente.</span><span class="sxs-lookup"><span data-stu-id="52810-114">Using this example, you can determine that the orchestration will not be dehydrated at this time.</span></span>