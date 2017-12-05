---
title: "Interrogation de relations d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, activity relationships
- queries [BAM], relationships
ms.assetid: e3d42b7c-cc11-4707-9095-cfc518902b26
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70c94644e505409f863e5104168740232d57c664
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="querying-activity-relationships"></a>Interrogation des relations d'activité
Les informations de relation d'activité sont disponibles dans une vue SQL créée dynamiquement pour chaque activité. Le nom de cette vue est  
  
 **bam_\<**  *activité*  **\>_AllRelationships**  
  
 Où \< *activité* \> est l’attribut de nom de l’élément d’activité dans la définition BAM XML, qui est le même que le nom d’activité entré à l’aide de la macro complémentaire d’analyse BAM pour Excel.  
  
 Les événements de relation se produisent dans le contexte d'une activité spécifique. Par exemple, si la relation entre Purchase Order et Shipment intervient dans le contexte de l’activité de bon de commande, l’enregistrement de relation s’afficheront dans **bam_PurchaseOrder_AllRelationships**, mais pas dans **bam _Shipment_AllRelationships**. Pour plus d’informations, consultez [relations d’activité](../core/activity-relationships.md).  
  
 Pour rechercher toutes les activités associées à un bon de commande vous devez interroger la vue **bam_PurchaseOrder_AllRelationships** , ainsi que toutes les vues **bam_\<***OtherActivity*   **\>_AllRelationships**, où \< *OtherActivity* \> est l’activité dans la même vue BAM.  
  
 Les enregistrements de relation font partie de l’instance d’activité, et elles sont conservées dans la synchronisation avec les données d’instance, comme décrit dans [stockage des données d’activité](../core/activity-data-storage.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation des données BAM](../core/querying-bam-data.md)