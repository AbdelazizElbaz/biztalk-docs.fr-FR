---
title: "La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, DTS packages
- backing up [BAM], Tracking Analysis Server database
- backing up [BAM], OLAP cubes
- backing up [BAM], DTS packages
- purging, OLAP cubes
- Analysis database [BAM], backing up
- scheduling, BAM backups
- backing up [BAM], Analysis database
- OLAP cubes, purging
- backing up, BAM
- backing up [BAM], database order
- DTS packages, backing up
- backing up [BAM], Star Schema database
- backing up [BAM], scheduling
- Tracking Analysis Server database [BAM], backing up
- Star Schema database [BAM], backing up
ms.assetid: d39e3491-ab54-44f2-990a-7b8ee86f0501
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e210fbe805e5a942605920e481faa2f1ca7cf2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases"></a>Sauvegarde des bases de données Analyse BAM et Analyse des suivis
La base de données d'analyse BAM (Business Activity Monitoring) et la base de données des suivis du serveur d'analyse stockent le contenu dans des cubes SQL Server Analysis Services. Le travail de sauvegarde de BizTalk Server ne sauvegarde pas ces bases de données. C'est pourquoi, vous devez utiliser le gestionnaire d'analyse SQL Server.  
  
 Une fois ces bases de données sauvegardées, vous pouvez purger les cubes OLAP. Lors de la purge les cubes OLAP, vous devez également effectuer les opérations suivantes :  
  
1.  Dans la base de données BAMStarSchema, tronquez la ou les tables de faits du cube OLAP à purger. La convention d’affectation de noms de table est « bam_*\<CubeName >*_Facts ».  
  
2.  Une fois les cubes OLAP purgés, vous devez traiter entièrement les cubes actifs, terminés et virtuels.  
  
 Pour obtenir des instructions sur la sauvegarde des bases de données d'analyse, consultez la rubrique « Archivage d'une base de données Analysis Services » dans la documentation en ligne de SQL Server.  
  
 **Planification des sauvegardes pour les bases de données BAM**  
  
 Si vous utilisez l'analyse BAM, vérifiez que ni le traitement des cubes BAM ni les lots DTS (Data Transformation Services) de maintenance des données ne sont exécutés lorsque le lot de sauvegarde est programmé pour s'exécuter.  
  
 Pour assurer la cohérence des schémas dans les bases de données BAM, sauvegardez celles-ci, ainsi que les lots DTS, à chaque déploiement ou annulation de déploiement d'une activité BAM.  
  
 Sauvegardez les bases de données d'analyse BAM et BAMStarSchema à chaque déploiement ou annulation de déploiement d'une vue BAM.  
  
 Sauvegardez les bases de données BAM dans l'ordre suivant :  
  
1.  Configurez le travail de sauvegarde de BizTalk Server pour sauvegarder la base de données BAMPrimaryImport et les autres bases de données BizTalk Server.  
  
2.  Exécutez le lot DTS de maintenance des données BAM pour toutes les activités.  
  
     Intégrez ces étapes à un lot DTS et planifiez une exécution régulière du lot. Pour assurer l'intégrité des données, vérifiez qu'aucun autre lot DTS de création de cubes ou de maintenance de données n'est exécuté lorsque ce lot de sauvegarde doit être exécuté.  
  
     Pour vous assurer de récupérer un ensemble complet de données archivées si la base de données BAMArchive échoue, sauvegardez cette dernière après y avoir copié la partition, mais avant de supprimer celle-ci de la base de données BAMPrimaryImport. Pour ce faire, modifiez le lot DTS de maintenance des données pour chaque activité pour insérer une étape pour sauvegarder la base de données BAMArchive avant la dernière étape du lot DTS, « Finalisation de l'archivage ».  
  
3.  Sauvegardez la base de données BAMAnalysis, puis la base de données BAMStarSchema.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md)