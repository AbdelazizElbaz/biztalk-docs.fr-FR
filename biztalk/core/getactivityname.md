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
# <a name="getactivityname"></a>GetActivityName
Transmet le nom de l'activité en cours sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetActivityName"/>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le nom de l'activité en cours.  
  
## <a name="remarks"></a>Notes  
 Windows Workflow Foundation exécute ses tâches au moyen d'une série d'activités configurée par le développeur. Un nom unique est assigné à chacune de ces activités au sein du flux de travail. Vous pouvez intercepter des données concernant une activité spécifique en filtrant sur le nom unique.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient une expression de filtre d’événement configurée pour rechercher une activité spécifique, FoodAndDrinksPolicy — dans un flux de travail fermé. à l'aide d'une combinaison d'opérations comprenant `GetActivityName`, `GetActivityEvent` ainsi que des opérations logiques.  
  
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