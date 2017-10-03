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
# <a name="partial-backup-sets"></a><span data-ttu-id="0675a-102">Jeux de sauvegarde partielles</span><span class="sxs-lookup"><span data-stu-id="0675a-102">Partial Backup Sets</span></span>
<span data-ttu-id="0675a-103">Lorsque vous sauvegardez les bases de données sur le système source, des problèmes peuvent se produire ce résultat dans un jeu de sauvegarde partiels.</span><span class="sxs-lookup"><span data-stu-id="0675a-103">When backing up the databases on the source system, problems may occur that result in a partial backup set.</span></span> <span data-ttu-id="0675a-104">Lorsque cela se produit, la table Master.dbo.bts_LogShippingHistory contient un 0 dans le **SetComplete** colonne pour tous les enregistrements dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="0675a-104">When this occurs, the Master.dbo.bts_LogShippingHistory table will contain a 0 in the **SetComplete** column for all records in the set.</span></span>  
  
 <span data-ttu-id="0675a-105">Ces jeux ne peut pas être restauré.</span><span class="sxs-lookup"><span data-stu-id="0675a-105">These sets cannot be restored.</span></span> <span data-ttu-id="0675a-106">Par conséquent, la chaîne de jeu de sauvegarde du journal est rompue.</span><span class="sxs-lookup"><span data-stu-id="0675a-106">As a result the log backup set chain is broken.</span></span> <span data-ttu-id="0675a-107">L’ensemble doit être ignoré, comme le journal ainsi que tous les jeux de sauvegarde, jusqu'à l’ensemble suivant de sauvegarde complète.</span><span class="sxs-lookup"><span data-stu-id="0675a-107">The set must be ignored, as well as all log backup sets after it, up to the next full backup set.</span></span> <span data-ttu-id="0675a-108">Le jeu de sauvegarde complète valide suivant recherche automatiquement le travail de restauration.</span><span class="sxs-lookup"><span data-stu-id="0675a-108">The restore job will automatically look for the next valid full backup set.</span></span> <span data-ttu-id="0675a-109">Si elle ne trouve pas, elle échoue et restaure définies afin de réparer l’environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="0675a-109">If it does not find one, it fails and restores that set in order to repair the destination environment.</span></span>  
  
 <span data-ttu-id="0675a-110">Dans la plupart des cas le système source détecte qu’un jeu de sauvegarde partiels s’est produite et génère automatiquement un jeu de sauvegarde complète la prochaine fois qu’il s’exécute si elle est configurée pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="0675a-110">In most cases the source system will detect that a partial backup set has occurred and will automatically produce a full backup set the next time it runs if it is configured to do so.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0675a-111">La cause la plus courante de ce problème est un espace disque insuffisant pour les groupes de fichiers sur le système de destination.</span><span class="sxs-lookup"><span data-stu-id="0675a-111">The most common cause of this problem is insufficient disk space for the file groups on the destination system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0675a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0675a-112">See Also</span></span>  
 [<span data-ttu-id="0675a-113">Résolution des problèmes d’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="0675a-113">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)