---
title: Comment supprimer un Index | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes [BAM], deleting
- Get-Index command [BAM]
- aggregations [BAM], indexes
ms.assetid: 5f9c7989-3357-451f-8565-1d4b01c1d16a
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ab00dc2640bbede95881280b73962c33442e46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-an-index"></a>Comment supprimer un Index
Les administrateurs utilisent la **delete-index** commande pour supprimer un index sur l’activité spécifiée aux points de contrôle spécifiés.  
  
### <a name="to-delete-an-index-on-an-activity"></a>Pour supprimer un index sur une activité  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité. Appuyez sur **Entrée**.  
  
3.  Type **bm delete-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment supprimer un Index](../core/how-to-delete-an-index.md)   
 [Comment obtenir la liste des index sur une agrégation](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)