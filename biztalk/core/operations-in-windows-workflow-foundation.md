---
title: "Opérations de Windows Workflow Foundation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a048dfc0-26b2-4f20-9d2f-c52f1ab19ac3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62cb1ba3cb82a21bb573145d00057112784c89a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-in-windows-workflow-foundation"></a>Opérations dans Windows Workflow Foundation
Cette section contient les opérations personnalisées prises en charge par l'intercepteur WF BAM.  
  
## <a name="determining-where-operations-are-allowed"></a>Détermination de l'emplacement où les opérations sont autorisées  
 Les opérations personnalisées fournies par l'intercepteur WF BAM peuvent être classées par catégories en fonction du type de trackpoint Windows Workflow Foundation associé :  
  
-   Activité  
  
-   Flux de travail  
  
-   Utilisateur  
  
 L’intercepteur WF BAM utilise les catégories pour affecter un type de TrackPoint à chaque **OnEvent**. Il base cette affectation sur les types d’opérations qu’il voit dans le **OnEvent** filtre et les sections d’extraction et de manipulation de données. Par exemple, si le **OnEvent** contient un **mise à jour** élément qui utilise le **GetUserData** opération, il est un utilisateur type de TrackPoint, étant donné que les événements d’activité et de flux de travail prend pas en charge cette opération. Pour plus d’informations sur les points de suivi, consultez la rubrique System.Workflow.Runtime.Tracking à [http://go.microsoft.com/fwlink/?LinkId=80242](http://go.microsoft.com/fwlink/?LinkId=80242).  
  
> [!NOTE]
>  Les trackpoints de workflow ne peuvent pas extraire de données du workflow.  
  
 Les opérations doivent doivent être compatibles tant à l'intérieur d'une expression de filtre qu'entre les sections d'extraction et de manipulation des données de l'expression de filtre à l'intérieur d'un élément `OnEvent`. Le tableau suivant présente les opérations qui peuvent être utilisées dans une expression de filtre pour chaque type de trackpoint.  
  
|Opération d'expression de filtre|Valide pour le trackpoint d'activité ?|Valide pour le trackpoint de workflow ?|Valide pour le trackpoint d'utilisateur ?|  
|---------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|Égal à|Oui|Oui|Oui|  
|And|Oui|Oui|Oui|  
|Concaténation|Non|Non|Non|  
|Constante|Oui|Oui|Oui|  
|GetActivityEvent|Oui|Non|Non|  
|GetActivityName|Oui|Non|Oui|  
|GetActivityProperty|Oui|Non|Oui|  
|GetActivityType|Oui|Non|Oui|  
|GetContextProperty|Non|Non|Non|  
|GetUserData|Non|Non|Non|  
|GetUserDataType|Non|Non|Oui|  
|GetUserKey|Non|Non|Oui|  
|GetWorkflowEvent|Non|Oui|Non|  
|GetWorkflowProperty|Non|Non|Non|  
  
 Si vous mélangez des opérations non compatibles, vous obtenez une erreur lors du déploiement de votre fichier de configuration d'intercepteur. Par exemple, si vous utilisez à la fois le `GetActivityEvent` et `GetWorkflowEvent` dans un filtre, ou à un événement d’extraction ou de manipulation de données et filtrer (comme **CorrelationID**), vous recevez une erreur.  
  
 Le table suivant résume les opérations que chaque type d'activité prend en charge dans l'extraction ou la manipulation de données.  
  
|Opération d'extraction ou de manipulation de données|Valide pour le trackpoint d'activité ?|Valide pour le trackpoint de workflow ?|Valide pour le trackpoint d'utilisateur ?|  
|-----------------------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|Égal à|Oui|Oui|Oui|  
|And|Oui|Oui|Oui|  
|Concaténation|Oui|Oui|Oui|  
|Constante|Oui|Oui|Oui|  
|GetActivityEvent|Oui|Non|Non|  
|GetActivityName|Oui|Non|Oui|  
|GetActivityProperty|Oui|Non|Oui|  
|GetActivityType|Oui|Non|Oui|  
|GetContextProperty|Oui|Oui|Oui|  
|GetUserData|Non|Non|Oui|  
|GetUserDataType|Non|Non|Oui|  
|GetUserKey|Non|Non|Oui|  
|GetWorkflowEvent|Non|Oui|Non|  
|GetWorkflowProperty|Oui|Non|Oui|  
  
> [!NOTE]
>  Il existe un mappage entre un seul **OnEvent** et un point de suivi unique.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [GetActivityEvent](../core/getactivityevent.md)  
  
-   [GetActivityName](../core/getactivityname.md)  
  
-   [GetActivityProperty](../core/getactivityproperty.md)  
  
-   [GetActivityType](../core/getactivitytype.md)  
  
-   [GetContextProperty](../core/getcontextproperty2.md)  
  
-   [GetUserData](../core/getuserdata.md)  
  
-   [GetUserDataType](../core/getuserdatatype.md)  
  
-   [GetUserKey](../core/getuserkey.md)  
  
-   [GetWorkflowEvent](../core/getworkflowevent.md)  
  
-   [GetWorkflowProperty](../core/getworkflowproperty.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Intercepteur WF BAM](../core/bam-wf-interceptor.md)