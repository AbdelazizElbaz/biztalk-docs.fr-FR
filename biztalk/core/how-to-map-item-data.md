---
title: "Comment mapper des données de l’élément | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data extraction
- orchestrations, data extraction
- orchestrations, tracking profiles
- tracking profiles, orchestrations
- tracking profiles, data extraction
ms.assetid: ae8b395e-152a-4e08-af31-3c9276f52711
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efdfd722e1610be02c06dd6e2a9597e13c0f1e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-item-data"></a>Mappage de données d'élément
Vous devez mapper des données d'élément pour définir l'extraction de données à partir d'une orchestration.  
  
> [!NOTE]
>  Il vous faut être sûr de mapper des valeurs de type de données compatibles avec les éléments d'activité lorsque vous créez des modèles de suivi. Si les types de données ne sont pas compatibles, vous recevrez un message d'erreur d'exécution BAM.  
  
> [!NOTE]
>  Quant vous mappez des étapes majeures telles que des horodatages, les données en cours de mappage doivent être conformes à la représentation de chaîne SQL d'un horodatage. Les données de date et d'heure au format de date et d'heure XML JJ-MM-AAAATHH:MM:SS.mmm-HH:MM ne sont pas prises en charge.  
>   
>  La chaîne de date suivante n'est par exemple pas prise en charge : 31-05-1999T13:20:00.000-05:00  
  
## <a name="prerequisites"></a>Conditions préalables  
 Orchestrations et définitions d'activité BAM déployées que vous connecterez.  
  
### <a name="how-to-map-item-data"></a>Comment mapper des données de l’élément  
  
1.  Ouvrez un modèle de suivi existant ou créez-en un. Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).  
  
2.  Dans le scénario, une définition d'activité nommée LoanProcessBamDef est importée. Il contient le **LoanProcess** nœud d’activité, avec un client **SSN** comme ActivityID. Pour plus d’informations, consultez [nœuds Activity et ActivityID](../core/activity-and-activityid-nodes.md).  
  
3.  Assurez-vous que chaque activité dispose d'un ActivityID ou d'un élément de données ContinuationID à suivre tel que le SSN d'un client.  
  
4.  Mappez des actions d'orchestration vers le dossier d'événements d'entreprise approprié afin d'indiquer l'événement à suivre. Par exemple, dans un scénario de traitement de prêt les éléments suivants, entre autres, seraient glissés sous le **LoanProcess** dossier d’activité :  
  
    -   **LoanApplicationReceived**  
  
    -   **CreditHistoryRequest**  
  
    -   **CreditHistoryResponse**  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds d’élément de données](../core/data-item-nodes.md)   
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)