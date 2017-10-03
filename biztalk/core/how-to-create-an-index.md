---
title: "Comment créer un Index | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Create-Index command [BAM]
- indexes [BAM], creating
- indexes [BAM], aggregations
- creating, indexes [BAM]
- aggregations [BAM], indexes
ms.assetid: 456d94e6-2e84-4d12-ad38-49f9eeb103f3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1427e8ee22e2012f759817350b0e3fa8ae49cf6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-an-index"></a>Création d'un index
Les administrateurs utilisent la **index créer** commande pour créer un index sur l’activité spécifiée aux points de contrôle spécifiés.  
  
### <a name="to-create-an-index-on-an-activity"></a>Pour créer un index sur une activité  
  
1.  À partir d’une invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]de suivi.  
  
2.  Type **bm create-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité >-point de contrôle :\<point de contrôle 1 >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
3.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Comment supprimer un Index](../core/how-to-delete-an-index.md)   
 [Comment obtenir la liste des index sur une agrégation](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)