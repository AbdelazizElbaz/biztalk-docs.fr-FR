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
# <a name="viewing-the-history-of-restored-backups"></a>Affichage de l'historique des sauvegardes restaurées
Pour déterminer le dernier jeu de sauvegarde restauré avec succès, passez en revue le contenu de la table Master.dbo.bts_LogShippingHistory. Celle-ci est renseignée par le travail Obtenir l'historique des sauvegardes et mise à jour par le travail Restaurer les bases de données. Lorsqu'une sauvegarde a été correctement restaurée, la colonne Restored est définie sur 1 et la colonne RestoredDateTime est définie sur la date et l'heure actuelles.  
  
 Lorsque toutes les bases de données restaurées sur un serveur à partir d'une sauvegarde spécifique ont été correctement restaurées, l'ID de ce jeu de sauvegarde est écrit dans la table LogShippingLastRestoreSet.  
  
## <a name="gaps-in-the-restore-process"></a>Emplacements vides dans le processus de restauration  
 Lors de la consultation d'enregistrements dans la table Master.dbo.bts_LogShippingHistory, il est possible que vous rencontriez des emplacements vides dans les jeux restaurés. Cela peut se produire pour plusieurs raisons. Toutefois, vous pouvez quand même rétablir la stabilité de votre système de destination (c'est-à-dire vos ordinateurs de sauvegarde), et ce même si des emplacements vides sont présents. La découverte d'un emplacement vide doit donner lieu à la restauration d'une sauvegarde complète afin de réparer le système de destination. Si vous n'agissez pas de la sorte, l'environnement de destination sera instable.  
  
> [!NOTE]
>  Les sauvegardes complètes sont uniquement restaurées pour créer initialement la base de données et pour réparer les problèmes dans la chaîne de sauvegarde de l'historique du journal. Dans la plupart des cas, les jeux de sauvegarde complète ne sont pas restaurés étant donné qu'ils ne font pas partie de la chaîne de sauvegarde du journal.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)