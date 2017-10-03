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
# <a name="sample-dehydration-calculation"></a>Exemple de calcul de mise en attente
Voici un exemple de calcul, basé sur des octets privés, permettant de déterminer la mise en attente ou non de BizTalk. Il utilise les valeurs configurées par défaut et quelques exemples de valeurs d'exécution.  
  
 Attribuons les valeurs suivantes aux propriétés de mise en attente :  
  
-   **TimeBlocked** = 60 (heure de l’exemple bloqué en secondes)  
  
-   **WaitingHistory** = 90 (exemple d’historique en attente en secondes)  
  
-   **ActualPrivateBytes** = 250 (exemple de valeur pour les octets privés)  
  
-   **OptimalUsage** = 50 (valeur de configuration par défaut)  
  
-   **MaximalUsage** = 350 (valeur de configuration par défaut)  
  
 Étant donné que la **ActualPrivateBytes** sont comprises entre **OptimalUsage** et **MaximalUsage**, alpha est calculé comme suit :  
  
```  
alpha(private) = (350 – 250) / 350 – 50)  
alpha(private) = 100 / 300  
alpha(private) = 0.33  
```  
  
 Ensuite vous calculez le **TestThreshold** comme suit :  
  
```  
TestThreshold = 1 + (0.33 * (1800 – 1))  
TestThreshold = 1 + 599.66  
TestThreshold = 600.66  
```  
  
 Puis, vous prenez la décision ou non de mettre en attente :  
  
```  
Dehydrate = (90 == -1 OR 90 > 600 OR 60 > (2 * 600))  
Dehydrate = false  
```  
  
 Dans cet exemple, vous pouvez voir que l'orchestration ne sera pas mise en attente.