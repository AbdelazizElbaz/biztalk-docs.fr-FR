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
# <a name="gaps-in-the-restore-process"></a>Lacunes dans le processus de restauration
Lorsque vous parcourez les enregistrements dans la table Master.dbo.bts_LogShippingHistory, vous pouvez observer des écarts dans les jeux restaurés. Cela peut se produire pour plusieurs raisons. Toutefois, la stabilité du système de destination peut être restaurée même lorsque les intervalles se sont produites. Un espace doit être suivi d’une restauration d’une sauvegarde complète afin de réparer l’environnement de destination. Si un écart n’est pas suivi par une sauvegarde complète de restauration du jeu, l’environnement de destination n’est pas stable et ne peut pas être restauré dans un état cohérent.  
  
> [!NOTE]  
>  Les sauvegardes complètes sont uniquement restaurées pour créer initialement la base de données et pour réparer les problèmes dans la chaîne de sauvegarde de l'historique du journal. Tant que le problème ne se produit pas de restauration, les jeux de sauvegarde complète ne sont pas restaurées, car elles n’interviennent pas dans la chaîne de sauvegarde du journal.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes d’envoi de journaux](../technical-guides/troubleshooting-log-shipping.md)