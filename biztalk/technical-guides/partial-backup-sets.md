---
title: Les jeux de sauvegarde partielles | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b9f15c0-4d31-4322-ac0a-8efdeed6f71e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9740cb0f45d6bb46c13a95e50e4717ef142b164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="partial-backup-sets"></a>Jeux de sauvegarde partielles
Lorsque vous sauvegardez les bases de données sur le système source, des problèmes peuvent se produire ce résultat dans un jeu de sauvegarde partiels. Lorsque cela se produit, la table Master.dbo.bts_LogShippingHistory contient un 0 dans le **SetComplete** colonne pour tous les enregistrements dans le jeu.  
  
 Ces jeux ne peut pas être restauré. Par conséquent, la chaîne de jeu de sauvegarde du journal est rompue. L’ensemble doit être ignoré, comme le journal ainsi que tous les jeux de sauvegarde, jusqu'à l’ensemble suivant de sauvegarde complète. Le jeu de sauvegarde complète valide suivant recherche automatiquement le travail de restauration. Si elle ne trouve pas, elle échoue et restaure définies afin de réparer l’environnement de destination.  
  
 Dans la plupart des cas le système source détecte qu’un jeu de sauvegarde partiels s’est produite et génère automatiquement un jeu de sauvegarde complète la prochaine fois qu’il s’exécute si elle est configurée pour ce faire.  
  
> [!NOTE]  
>  La cause la plus courante de ce problème est un espace disque insuffisant pour les groupes de fichiers sur le système de destination.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)