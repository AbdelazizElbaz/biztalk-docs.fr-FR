---
title: GetWorkflowEvent | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2534e0b8-26df-4554-b0df-742014deb64d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dc753bd45452af6ab586a11f216bc65f9539fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowevent"></a>GetWorkflowEvent
Transmet le nom de l'événement de flux de travail en cours sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetWorkflowEvent" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant l'événement de flux de travail en cours.  
  
## <a name="remarks"></a>Notes  
 Une instance de flux de travail peut passer par plusieurs états au cours de son exécution. Par exemple, une instance de flux de travail peut devenir inactive ou être suspendue. Chaque fois que l'instance de flux de travail change d'état, elle transmet un événement d'état de flux de travail à l'infrastructure de suivi d'exécution. L'intercepteur BAM de Windows Workflow Foundation prend en charge la plupart des événements définis par l'énumération `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent`, comme illustré dans le tableau suivant.  
  
|Événement d'activité| Description|  
|--------------------|-----------------|  
|Modifié|Une modification de flux de travail s'est produite sur l'instance de flux de travail.|  
|Terminé|L'instance de flux de travail est terminée.|  
|Créé le|L'instance de flux de travail a été créée.|  
|Exception|Une exception non gérée a été levée.|  
|Idle|L'instance de flux de travail est inactive.|  
|Loaded|L'instance de flux de travail a été chargée en mémoire.|  
|Persisted|L'instance de flux de travail a été rendue persistance.|  
|Resumed|L'exécution d'une instance de flux de travail précédemment suspendue a repris.|  
|Démarré|L'instance de flux de travail a été démarrée.|  
|Suspendu|L'instance de flux de travail a été suspendue.|  
|Arrêté|L'instance de flux de travail a été interrompue.|  
|Unloaded|L'instance de flux de travail a été déchargée de la mémoire.|  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser `GetWorkflowEvent` et `GetActivityEvent` dans le même élément OnEvent.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant contient un filtre configuré pour rechercher une activité spécifique (« FoodAndDrinksPolicy ») dans un flux de travail. Dans l'exemple, un filtre est configuré pour rechercher l'activité nommée « FoodAndDrinksPolicy » dans un flux de travail fermé. Cette opération est effectuée en comparant la valeur retournée par `GetWorkflowEvent` à la constante « Created ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowEvent" />   
      <ic:Operation Name="Constant">  
        <ic:Argument>Created</ic:Argument>   
      </ic:Operation>  
    <ic:Operation Name="Equals" />   
  </ic:Expression>  
</ic:Filter>  
```  
  
 Cette opération est utile pour le suivi de la durée de vie d'un flux de travail et pour la détection d'exceptions ou d'autres problèmes liés au flux de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [Énumération de System.Workflow.Runtime.Tracking.TrackingWorkflowEvent](http://go.microsoft.com/fwlink/?LinkId=119568)