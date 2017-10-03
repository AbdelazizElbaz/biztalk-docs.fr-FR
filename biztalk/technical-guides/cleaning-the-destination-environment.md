---
title: "Nettoyage de l’environnement de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8585853b-e625-48c3-a241-81ebf1be0e1e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4023492bf79223b3ba6b1db5cedebadf88feb9c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cleaning-the-destination-environment"></a>Nettoyage de l’environnement de Destination
Si le travail de restauration rencontre des conditions d’erreur qui ne peut pas être résolues, nettoyez l’environnement de destination pour qu’il puisse commencer à partir d’un environnement vide. Exécution de la procédure stockée **sp_LogShippingClean** situé dans la base de données master sur la destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance sera « nettoyer » l’environnement de destination. Cette procédure supprime toutes les bases de données et supprime le dernier jeu de données restauré pour la source spécifiée.  
  
 Avant d’exécuter cette procédure, vous devez désactiver le **envoi de journaux - restaurer les bases de données** tâche (le travail de l’historique de sauvegarde get peut continuer à s’exécuter). Pour plus d’informations sur la désactivation de la **envoi de journaux - restaurer les bases de données** travail voir [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md). Après le **sp_LogShippingClean** procédure est exécutée, la prochaine exécution du travail de restauration qu’elle recherche la plus récente sauvegarde complète avec un jeu de sauvegarde valide de journaux suivantes. Si ce jeu a déjà été restauré, le travail de restauration efface le **Restored** colonne pour définir et toutes les définit et se poursuit avec la restauration de l’ensemble.  
  
> [!NOTE]  
>  Étant donné que le travail de recherche pour la sauvegarde complète la plus récente définie une fois que l’environnement a été nettoyé, force une sauvegarde complète sur le système source après l’exécution de cette procédure, mais avant d’exécuter le travail de restauration.  
  
> [!NOTE]  
>  Le **sp_LogShippingClean** procédure doit être répétée sur tous les serveurs qui sont de restauration des bases de données pour un système source donné afin de conserver les différents serveurs synchronisées avec d’autres les jeux ont été appliquées.  
  
 Pour exécuter le **sp_LogShippingClean** procédure, vous connecter à la base de données master sur tous les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances qui font partie de la récupération d’urgence de site et exécutez la commande suivante dans le **nouvelle requête** option disponible dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio pour chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance :  
  
```  
sp_LogShippingClean 'SourceID'  
```  
  
 où **SourceID** correspond à l’identificateur configuré sur la production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)