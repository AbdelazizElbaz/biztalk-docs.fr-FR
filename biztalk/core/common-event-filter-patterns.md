---
title: "Modèles de filtre des événements courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc80168b-25bd-4228-b84c-d38bf4e2fe4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef90a4533b8b12929488d3a323dae47976eace0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="common-event-filter-patterns"></a>Modèles de filtre des événements communs
Lorsque vous travaillez avec l'intercepteur BAM de Windows Workflow Foundation (WF), il est probable que vous notiez une utilisation fréquente d'un ensemble de modèles de filtre communs dans vos fichiers de configuration de l'intercepteur. Tandis que certains de ces modèles de filtre sont spécifiques à vos applications et environnements, de nombreux modèles peuvent être utilisés sur des applications et environnements divers.  
  
 Cette rubrique rassemble de nombreux modèles de filtre communs utilisés par les fichiers de configuration de l'intercepteur et écrits pour des applications WF. Les modèles sont regroupés par événement de suivi Windows Workflow Foundation :  
  
-   Événements d'état d'activité  
  
-   Événements d'état de workflow  
  
-   Événements utilisateur  
  
 Chaque modèle peut être copié dans votre fichier de configuration de l'intercepteur et adapté à votre application.  
  
## <a name="activity-status-event-filter-patterns"></a>Modèles de filtre des événements d'état d'activité  
 Les activités sont les blocs de construction fondamentaux des workflows. Un workflow est un ensemble d'activités qui sont organisées hiérarchiquement dans une structure arborescente. Une activité représente une action dans un workflow. Il peut s'agir d'une action simple, telle qu'un délai, ou d'une activité composite comprenant plusieurs activités enfants.  
  
 Les filtres de cette section filtrent les activités et utilisent une ou plusieurs opérations personnalisées suivantes pour l'intercepteur WF BAM :  
  
-   GetActivityName  
  
-   GetActivityEvent  
  
-   GetActivityType  
  
-   GetActivityProperty  
  
-   GetWorkflowProperty  
  
-   GetContextProperty  
  
> [!NOTE]
>  Si vous n'utilisez pas l'opération GetActivityEvent dans votre filtre, celui-ci recherche uniquement les événements d'activité fermée.  
  
### <a name="filter-by-activity-name-closed-activity"></a>Filtre par nom d'activité (activité fermée)  
 Vous devez fréquemment filtrer les événements d'activité fermée par nom d'activité. Cela est utile lorsque vous devez capturer des données d'une activité spécifique, telle que la réception d'un fichier ou l'écriture de données dans une base de données.  
  
 Le fragment suivant filtre une activité fermée nommée « MyActivity ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-closed-activity-event"></a>Filtre par type d'activité (événement d'activité fermée)  
 Vous pouvez également filtrer une activité par type plutôt que par nom. Par exemple, vous pouvez enregistrer un nom d'activité et un horodatage pour toutes les activités d'un workflow. Pour ce faire, utilisez l'opération `GetActivityType`. `GetActivityType` compare un type fourni avec le type de base et tous les types dérivés pour identifier une correspondance. La comparaison par rapport à `System.Workflow.ComponentModel.Activity` correspond dans la mesure où toutes les activités de workflow doivent en dériver.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-event-any-activity-type"></a>Filtre par événement d'activité (tout type d'activité)  
 Ce filtre utilise l'opération GetActivityEvent pour rechercher les activités fermées. Il permet de capturer des informations sur tous les événements fermés (par rapport à un événement spécifique par nom ou type).  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-type-closed-activity-event"></a>Filtre par nom et type d'activité (événement d'activité fermée)  
 Vous pouvez filtrer les activités par nom d'activité et type d'activité si vous voulez spécifier le type exact d'activité (architecture de processeur incluse) à rechercher. L'exemple suivant recherche « MyActivity » dérivant de `System.Workflow.ComponentModel.Activity`. Vous pouvez le modifier en un type dérivé pour le rendre plus restrictif.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
<ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-event-any-activity-type"></a>Filtre par nom et événement d'activité (tout type d'activité)  
 Cette expression filtre par nom d'activité et événement d'activité. Cela permet de capturer des informations relatives à une activité ou un événement spécifique ou de capturer des données de plusieurs événements d'une activité donnée. Par exemple, vous pouvez rechercher deux éléments OnEvent différents, l'un pour MyActivity lorsqu'il est en cours d'exécution et l'autre lorsqu'il est fermé, comme suit :  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-event"></a>Filtre par type et événement d'activité  
 Ce filtre permet de capturer des informations sur toutes les activités qui dérivent d'un type spécifique au cours d'un événement d'activité unique. Par exemple, vous pouvez suivre un ID de bon de commande et un horodatage d'un bon de commande lorsqu'il transite par un workflow. Pour ce faire, utilisez les opérations `GetActivityEvent` et `GetActivityType`. `GetActivityType` compare un type fourni avec le type de base et tous les types dérivés pour identifier une correspondance. La comparaison par rapport à `System.Workflow.ComponentModel.Activity` correspond dans la mesure où toutes les activités de workflow doivent en dériver.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-type-and-event"></a>Filtre par nom, type et événement d'activité  
 Filtrer une activité par nom, type et événement peut être utile pour mieux qualifier l'activité à suivre. Par exemple, le filtre suivant recherche l'activité fermée « MyActivity » dont le type est égal à ou dérive de `System.Workflow.ComponentModel.Activity`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="workflow-status-event-filter-patterns"></a>Modèles de filtre des événements d'état de workflow  
 Les filtres de cette section filtrent les événements de workflow et utilisent une ou plusieurs opérations personnalisées suivantes pour l'intercepteur WF BAM :  
  
-   GetWorkflowEvent  
  
-   GetContextProperty  
  
### <a name="filter-by-workflow-event"></a>Filtre par événement de workflow  
 Cette expression filtre par événement de workflow.  
  
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
  
## <a name="user-event-filter-patterns"></a>Modèles de filtre des événements utilisateur  
 Si votre application suit les informations personnalisées par le biais de la méthode TrackData, vous pouvez filtrer en fonction des caractéristiques des données à l'aide d'une ou de plusieurs opérations de données utilisateur personnalisées suivantes pour l'intercepteur WF BAM :  
  
-   GetUserDataType  
  
-   GetUserKey  
  
-   GetUserData  
  
 Le filtre peut combiner ces opérations avec les opérations suivantes pour créer une expression plus complexe :  
  
-   GetActivityName  
  
-   GetActivityType  
  
-   GetActivityProperty  
  
-   GetWorkflowProperty  
  
-   GetContextProperty  
  
 Si votre filtre n'inclut pas au moins une opération de données utilisateur, votre filtre n'est pas un filtre d'événements utilisateur et l'OnEvent associé génère une erreur (si une opération utilisateur apparaît dans une expression de mise à jour correspondante) ou est identifié comme un trackpoint d'activité et non d'utilisateur.  
  
### <a name="filter-by-activity-name-and-user-data-type"></a>Filtre par nom d'activité et type de données utilisateur  
 Fréquemment, vous pouvez identifier un événement par le nom d'activité et le type de données utilisateur. L'expression suivante filtre une activité nommée « MyActivity » et un type de données utilisateur qui dérive de `System.Object`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-data-type"></a>Filtre par type d'activité et type de données utilisateur  
 Vous pouvez filtrer par type d'activité et type de données utilisateur. Cela vous permet de filtrer des événements en fonction du type dont ils dérivent car `GetActivityType` et `GetUserDataType` effectuent une comparaison par rapport au type spécifié et à tous les types dérivés.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-data-type"></a>Filtre par nom d'activité, type d'activité et type de données utilisateur  
 Ce filtre limite davantage le modèle de filtre du type d'activité et du type de données utilisateur en incluant le nom d'activité.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-user-key"></a>Filtre par nom d'activité et clé utilisateur  
 Si votre application a une activité qui appelle `TrackData` avec une clé déterminée au moment de l'exécution, vous pouvez filtrer par nom d'activité et clé utilisateur. Cela vous permet de déclencher un `OnEvent` basé sur une valeur de clé spécifique. Par exemple, votre application peut définir plusieurs clés et sélectionner dynamiquement l'une d'elles au sein d'une activité.  
  
 L'expression suivante filtre « MyActivity » contenant une clé utilisateur nommée « ItemKey ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-key"></a>Filtre par type d'activité et clé utilisateur  
 Si votre application contient plusieurs activités qui appellent `TrackData` avec une clé déterminée au moment de l'exécution, vous pouvez filtrer par nom d'activité et clé utilisateur. Cela vous permet de déclencher un `OnEvent` basé sur une valeur de clé spécifique. Par exemple, votre application peut définir plusieurs clés et sélectionner dynamiquement l'une d'elles au sein d'une activité.  
  
 L'expression suivante filtre toute activité dérivant de `System.Workflow.ComponentModel.Activity` contenant une clé utilisateur nommée « ItemKey ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-key"></a>Filtre par nom d'activité, type d'activité et clé utilisateur  
 Ce modèle de filtre affine davantage le modèle de filtre du type d'activité et de la clé utilisateur en incluant le nom d'activité.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-user-data-type-and-user-key"></a>Filtre par nom d'activité, type de données utilisateur et clé utilisateur  
 Ce filtre permet de limiter votre filtre à une activité nommée avec une clé utilisateur spécifique et dérivant d'un type de données spécifique. Par exemple, votre activité peut appeler TrackData à l'aide de la clé « Item » et une valeur de données de chaîne ou d'entier selon le type d'élément.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-user-data-type-and-user-key"></a>Filtre par type d'activité, type de données utilisateur et clé utilisateur  
 Ce filtre permet de limiter votre filtre à un type d'activité avec une clé utilisateur spécifique et dérivant d'un type de données spécifique. Il peut être plus ou moins restrictif que l'utilisation du nom d'activité, du type de données utilisateur et de la clé utilisateur en fonction du type utilisé. Si vous spécifiez le type le plus dérivé, il peut être plus restrictif tandis que si vous spécifiez le type de base racine, il peut être moins restrictif.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-user-data-type-and-user-key"></a>Filtre par nom d'activité, type d'activité, type de données utilisateur et clé utilisateur  
 Ce filtre limite davantage le modèle de filtre du type d'activité, du type de données utilisateur et de la clé utilisateur en incluant le nom d'activité.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>   
```