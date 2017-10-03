---
title: Comment supprimer des profils de suivi orphelins | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, orphans
- tracking profiles, activities
- tracking profiles, deleting
- activities, tracking profiles
ms.assetid: e8923dab-5d02-41a3-840b-104b20624e6c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33ddea8751a017db21306c06cdcca5929de641ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-orphaned-tracking-profiles"></a>Suppression de modèles de suivi orphelins
Les modèles de suivi sont associés à une activité. Lorsque le déploiement d'une activité est annulé, les modèles de suivi associés peuvent devenir orphelins, c'est-à-dire qu'ils ne sont plus associés à une activité. Vous pouvez utiliser la procédure suivante pour supprimer les modèles de suivi.  
  
### <a name="to-remove-an-orphaned-tracking-profile"></a>Pour supprimer un modèle de suivi orphelin  
  
1.  Redéployez la définition BAM. Pour plus d’informations sur le déploiement de définitions BAM, consultez [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).  
  
2.  Utilisez l'Éditeur de modèle de suivi pour supprimer le modèle de suivi. Pour plus d’informations sur la suppression des profils de suivi, consultez [comment appliquer et supprimer un profil de suivi](../core/how-to-apply-and-remove-a-tracking-profile.md).  
  
3.  Annulez le déploiement de la définition BAM. Pour plus d’informations sur la suppression de définitions BAM, consultez [comment supprimer des définitions BAM](../core/how-to-remove-bam-definitions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)