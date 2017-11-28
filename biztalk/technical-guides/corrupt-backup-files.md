---
title: Endommager les fichiers de sauvegarde | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc48197c-944a-4f0a-ba01-8e1d91c88ad3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda5acae756fd2c4d0afc0263bc723af3ba77e15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="corrupt-backup-files"></a><span data-ttu-id="06933-102">Fichiers de sauvegarde endommagés</span><span class="sxs-lookup"><span data-stu-id="06933-102">Corrupt Backup Files</span></span>
<span data-ttu-id="06933-103">Un fichier de sauvegarde peut devenir endommagé, manquant ou endommagé.</span><span class="sxs-lookup"><span data-stu-id="06933-103">A backup file may become corrupt, damaged, or missing.</span></span> <span data-ttu-id="06933-104">Si cela se produit, au moins un fichier ne peut pas être restauré.</span><span class="sxs-lookup"><span data-stu-id="06933-104">If this occurs, at least one file cannot be restored.</span></span> <span data-ttu-id="06933-105">Le travail de restauration sur le système qui ont subi l’échec de recherche pour le jeu de sauvegarde complète valid suivant.</span><span class="sxs-lookup"><span data-stu-id="06933-105">The restore job on the system that suffered the failure searches for the next valid full backup set.</span></span> <span data-ttu-id="06933-106">Dans la plupart des cas, il sera nécessaire forcer une sauvegarde complète sur le système source.</span><span class="sxs-lookup"><span data-stu-id="06933-106">In most cases it will be necessary to force a full backup on the source system.</span></span> <span data-ttu-id="06933-107">Si aucun jeu de ce type n’existe, le travail de restauration échoue, et chaque exécution ultérieure échoue également jusqu'à l’arrivée d’un jeu de sauvegarde complet valid.</span><span class="sxs-lookup"><span data-stu-id="06933-107">If no such set exists, the restore job fails and each subsequent run also fails until a valid full backup set arrives.</span></span> <span data-ttu-id="06933-108">Si un jeu n’existe pas, il est utilisé pour réparer l’environnement.</span><span class="sxs-lookup"><span data-stu-id="06933-108">If a set does exist, it is used to repair the environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06933-109">En raison de la manière dont [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] écrit des données de sauvegarde dans un fichier, il est possible que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] signalera la réussite même si la sauvegarde a échoué lors de l’écriture réelle des données.</span><span class="sxs-lookup"><span data-stu-id="06933-109">Due to the manner in which [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] writes backup data to a file, it is possible that [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] will report successful completion even if the backup failed during the actual writing of the data.</span></span> <span data-ttu-id="06933-110">Ce scénario se produit principalement lorsque le disque en cours d’écriture n’est pas local à l’ordinateur et d’une défaillance du réseau ou l’interruption se produit.</span><span class="sxs-lookup"><span data-stu-id="06933-110">This scenario primarily occurs when the disk being written to is not local to the computer and a network failure or interruption occurs.</span></span> <span data-ttu-id="06933-111">Pour des raisons de général, si une panne réseau se produit pendant l’exécution de la tâche de sauvegarde, force une sauvegarde complète une fois le problème de connectivité réseau est résolu.</span><span class="sxs-lookup"><span data-stu-id="06933-111">As a general precaution, if a network failure occurs while the backup job is running, force a full backup after the network connectivity problem is resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06933-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06933-112">See Also</span></span>  
 [<span data-ttu-id="06933-113">Résolution des problèmes d’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="06933-113">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)