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
# <a name="cleaning-the-destination-environment"></a><span data-ttu-id="e2b2c-102">Nettoyage de l’environnement de Destination</span><span class="sxs-lookup"><span data-stu-id="e2b2c-102">Cleaning the Destination Environment</span></span>
<span data-ttu-id="e2b2c-103">Si le travail de restauration rencontre des conditions d’erreur qui ne peut pas être résolues, nettoyez l’environnement de destination pour qu’il puisse commencer à partir d’un environnement vide.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-103">If the restore job encounters error conditions that cannot be resolved, clean the destination environment so that it can start from an empty environment.</span></span> <span data-ttu-id="e2b2c-104">Exécution de la procédure stockée **sp_LogShippingClean** situé dans la base de données master sur la destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance sera « nettoyer » l’environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-104">Running the stored procedure **sp_LogShippingClean** located in the master database on the destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance will “clean” the destination environment.</span></span> <span data-ttu-id="e2b2c-105">Cette procédure supprime toutes les bases de données et supprime le dernier jeu de données restauré pour la source spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-105">This procedure drops all databases and deletes the last restored data set for the specified source.</span></span>  
  
 <span data-ttu-id="e2b2c-106">Avant d’exécuter cette procédure, vous devez désactiver le **envoi de journaux - restaurer les bases de données** tâche (le travail de l’historique de sauvegarde get peut continuer à s’exécuter).</span><span class="sxs-lookup"><span data-stu-id="e2b2c-106">Before running this procedure, disable the **BTS Log Shipping - Restore Databases** job (the get backup history job may continue running).</span></span> <span data-ttu-id="e2b2c-107">Pour plus d’informations sur la désactivation de la **envoi de journaux - restaurer les bases de données** travail voir [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span><span class="sxs-lookup"><span data-stu-id="e2b2c-107">For more information about disabling the **BTS Log Shipping - Restore Databases** job see [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span></span> <span data-ttu-id="e2b2c-108">Après le **sp_LogShippingClean** procédure est exécutée, la prochaine exécution du travail de restauration qu’elle recherche la plus récente sauvegarde complète avec un jeu de sauvegarde valide de journaux suivantes.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-108">After the **sp_LogShippingClean** procedure is run, the next time the restore job runs it will find the most recent full backup set with a valid subsequent log backup set.</span></span> <span data-ttu-id="e2b2c-109">Si ce jeu a déjà été restauré, le travail de restauration efface le **Restored** colonne pour définir et toutes les définit et se poursuit avec la restauration de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-109">If this set has already been restored, the restore job clears the **Restored** column for the set and all subsequent sets and then proceeds with restoring the set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2b2c-110">Étant donné que le travail de recherche pour la sauvegarde complète la plus récente définie une fois que l’environnement a été nettoyé, force une sauvegarde complète sur le système source après l’exécution de cette procédure, mais avant d’exécuter le travail de restauration.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-110">Because the job looks for the most recent full backup set after the environment has been cleaned, force a full backup on the source system after running this procedure but before running the restore job.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2b2c-111">Le **sp_LogShippingClean** procédure doit être répétée sur tous les serveurs qui sont de restauration des bases de données pour un système source donné afin de conserver les différents serveurs synchronisées avec d’autres les jeux ont été appliquées.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-111">The **sp_LogShippingClean** procedure must be repeated on all servers that are restoring databases for a given source system in order to keep the different servers in synch with each other in terms of which sets have been applied.</span></span>  
  
 <span data-ttu-id="e2b2c-112">Pour exécuter le **sp_LogShippingClean** procédure, vous connecter à la base de données master sur tous les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances qui font partie de la récupération d’urgence de site et exécutez la commande suivante dans le **nouvelle requête** option disponible dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio pour chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance :</span><span class="sxs-lookup"><span data-stu-id="e2b2c-112">To run the **sp_LogShippingClean** procedure, connect to the master database on all [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances that are part of the disaster recovery site and execute the following command in the **New Query** option available in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio for each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance:</span></span>  
  
```  
sp_LogShippingClean 'SourceID'  
```  
  
 <span data-ttu-id="e2b2c-113">où **SourceID** correspond à l’identificateur configuré sur la production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances.</span><span class="sxs-lookup"><span data-stu-id="e2b2c-113">where **SourceID** corresponds to the identifier configured on the production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b2c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2b2c-114">See Also</span></span>  
 [<span data-ttu-id="e2b2c-115">Résolution des problèmes d’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="e2b2c-115">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)