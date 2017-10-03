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
# <a name="getactivityevent"></a>GetActivityEvent
Transmet le nom de l'événement d'activité en cours sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetActivityEvent"/>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant l'événement d'activité en cours.  
  
## <a name="remarks"></a>Notes  
 Une activité de workflow peut passer par plusieurs états pendant la durée de vie du workflow. L'intercepteur BAM de Windows Workflow Foundation prend en charge la plupart des valeurs d'état d'exécution définies par l'énumération `System.Workflow.ComponentModel.ActivityExecutionStatus`, comme indiqué dans le tableau suivant :  
  
|État de l'exécution|Description|  
|----------------------|-----------------|  
|Canceling|Représente l'état d'une activité qui est en cours d'annulation.|  
|Closed|Représente l'état d'une activité qui est fermée.|  
|Compensating|Représente l'état d'une activité en cours de compensation.|  
|Executing|Représente l'état d'une activité en cours d'exécution.|  
|Faulting|Représente l'état d'une activité défaillante.|  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser `GetActivityEvent` et `GetWorkflowEvent` dans le même élément OnEvent.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant contient une expression de filtre d'événements configurée pour rechercher une activité spécifique (FoodAndDrinksPolicy) au sein d'un flux de travail fermé à l'aide d'une combinaison d'opérations comprenant `GetActivityEvent`, `GetActivityName` ainsi que des opérations logiques.  
  
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
  
 Ce modèle de filtre est commun aux fichiers de configuration de l'intercepteur Windows Workflow Foundation.  
  
> [!NOTE]
>  Les arguments ne requièrent pas de guillemets, sauf si vous tentez explicitement de rechercher une chaîne contenant des guillemets.  
  
## <a name="see-also"></a>Voir aussi  
 [Énumération System.Workflow.ComponentModel.ActivityExecutionStatus](http://go.microsoft.com/fwlink/?LinkId=119570)