---
title: Lacunes dans le processus de restauration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 616c4f36-8ed6-4b99-b97a-5635627dfc17
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7d3ccadd950f5a955430b982c1a6f79a262864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="gaps-in-the-restore-process"></a><span data-ttu-id="712f9-102">Lacunes dans le processus de restauration</span><span class="sxs-lookup"><span data-stu-id="712f9-102">Gaps in the Restore Process</span></span>
<span data-ttu-id="712f9-103">Lorsque vous parcourez les enregistrements dans la table Master.dbo.bts_LogShippingHistory, vous pouvez observer des écarts dans les jeux restaurés.</span><span class="sxs-lookup"><span data-stu-id="712f9-103">When reviewing records in the Master.dbo.bts_LogShippingHistory table, you may observe gaps in restored sets.</span></span> <span data-ttu-id="712f9-104">Cela peut se produire pour plusieurs raisons.</span><span class="sxs-lookup"><span data-stu-id="712f9-104">This can occur for several reasons.</span></span> <span data-ttu-id="712f9-105">Toutefois, la stabilité du système de destination peut être restaurée même lorsque les intervalles se sont produites.</span><span class="sxs-lookup"><span data-stu-id="712f9-105">However, the stability of the destination system can be restored even when gaps have occurred.</span></span> <span data-ttu-id="712f9-106">Un espace doit être suivi d’une restauration d’une sauvegarde complète afin de réparer l’environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="712f9-106">A gap must be followed by a restore of a full backup set to repair the destination environment.</span></span> <span data-ttu-id="712f9-107">Si un écart n’est pas suivi par une sauvegarde complète de restauration du jeu, l’environnement de destination n’est pas stable et ne peut pas être restauré dans un état cohérent.</span><span class="sxs-lookup"><span data-stu-id="712f9-107">If a gap is not followed by a full backup set restore, the destination environment is not stable and cannot be restored in a consistent state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="712f9-108">Les sauvegardes complètes sont uniquement restaurées pour créer initialement la base de données et pour réparer les problèmes dans la chaîne de sauvegarde de l'historique du journal.</span><span class="sxs-lookup"><span data-stu-id="712f9-108">Full backups are only restored to initially create the database and to repair problems in the log history backup chain.</span></span> <span data-ttu-id="712f9-109">Tant que le problème ne se produit pas de restauration, les jeux de sauvegarde complète ne sont pas restaurées, car elles n’interviennent pas dans la chaîne de sauvegarde du journal.</span><span class="sxs-lookup"><span data-stu-id="712f9-109">As long as a problem does not occur with a restore, full backup sets are not restored, because they do not participate in the log backup chain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712f9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="712f9-110">See Also</span></span>  
 [<span data-ttu-id="712f9-111">Résolution des problèmes d’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="712f9-111">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)