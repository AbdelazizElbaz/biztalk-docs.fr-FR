---
title: "Affichage de l’historique de restauration des sauvegardes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring, history
- backing up, history
ms.assetid: 8852befa-b8e7-469d-b014-75c881907442
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa5a7fbe2b0e731920880570b0555402ba162c7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-the-history-of-restored-backups"></a><span data-ttu-id="786a6-102">Affichage de l'historique des sauvegardes restaurées</span><span class="sxs-lookup"><span data-stu-id="786a6-102">Viewing the History of Restored Backups</span></span>
<span data-ttu-id="786a6-103">Pour déterminer le dernier jeu de sauvegarde restauré avec succès, passez en revue le contenu de la table Master.dbo.bts_LogShippingHistory.</span><span class="sxs-lookup"><span data-stu-id="786a6-103">To determine the last successful backup set restored, review the contents of the Master.dbo.bts_LogShippingHistory table.</span></span> <span data-ttu-id="786a6-104">Celle-ci est renseignée par le travail Obtenir l'historique des sauvegardes et mise à jour par le travail Restaurer les bases de données.</span><span class="sxs-lookup"><span data-stu-id="786a6-104">This table is populated by the Get Backup History job and updated by the Restore Databases job.</span></span> <span data-ttu-id="786a6-105">Lorsqu'une sauvegarde a été correctement restaurée, la colonne Restored est définie sur 1 et la colonne RestoredDateTime est définie sur la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="786a6-105">When a backup is successfully restored, the Restored column is set to 1 and the RestoredDateTime is set to the current date and time.</span></span>  
  
 <span data-ttu-id="786a6-106">Lorsque toutes les bases de données restaurées sur un serveur à partir d'une sauvegarde spécifique ont été correctement restaurées, l'ID de ce jeu de sauvegarde est écrit dans la table LogShippingLastRestoreSet.</span><span class="sxs-lookup"><span data-stu-id="786a6-106">When all of the databases being restored to the server from a particular backup set have been successfully restored, that backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table.</span></span>  
  
## <a name="gaps-in-the-restore-process"></a><span data-ttu-id="786a6-107">Emplacements vides dans le processus de restauration</span><span class="sxs-lookup"><span data-stu-id="786a6-107">Gaps in the restore process</span></span>  
 <span data-ttu-id="786a6-108">Lors de la consultation d'enregistrements dans la table Master.dbo.bts_LogShippingHistory, il est possible que vous rencontriez des emplacements vides dans les jeux restaurés.</span><span class="sxs-lookup"><span data-stu-id="786a6-108">When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may find gaps in the sets restored.</span></span> <span data-ttu-id="786a6-109">Cela peut se produire pour plusieurs raisons.</span><span class="sxs-lookup"><span data-stu-id="786a6-109">This can occur for several reasons.</span></span> <span data-ttu-id="786a6-110">Toutefois, vous pouvez quand même rétablir la stabilité de votre système de destination (c'est-à-dire vos ordinateurs de sauvegarde), et ce même si des emplacements vides sont présents.</span><span class="sxs-lookup"><span data-stu-id="786a6-110">However, you can still recover the stability of your destination system (which are your backup computers), even when gaps have occurred.</span></span> <span data-ttu-id="786a6-111">La découverte d'un emplacement vide doit donner lieu à la restauration d'une sauvegarde complète afin de réparer le système de destination.</span><span class="sxs-lookup"><span data-stu-id="786a6-111">A gap must be followed by a restore of a full backup set to repair the destination system.</span></span> <span data-ttu-id="786a6-112">Si vous n'agissez pas de la sorte, l'environnement de destination sera instable.</span><span class="sxs-lookup"><span data-stu-id="786a6-112">If a gap is not followed by a full backup set restore, the destination environment is not stable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="786a6-113">Les sauvegardes complètes sont uniquement restaurées pour créer initialement la base de données et pour réparer les problèmes dans la chaîne de sauvegarde de l'historique du journal.</span><span class="sxs-lookup"><span data-stu-id="786a6-113">Full backups are only restored to initially create the database and to repair problems in the log history backup chain.</span></span> <span data-ttu-id="786a6-114">Dans la plupart des cas, les jeux de sauvegarde complète ne sont pas restaurés étant donné qu'ils ne font pas partie de la chaîne de sauvegarde du journal.</span><span class="sxs-lookup"><span data-stu-id="786a6-114">In most cases full backup sets are not restored, as they are not part of the log backup chain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786a6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="786a6-115">See Also</span></span>  
 [<span data-ttu-id="786a6-116">Informations avancées sur la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="786a6-116">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)