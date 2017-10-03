---
title: "Gestion des bases de données BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], databases
- databases [BAM], managing
- databases, BAM
ms.assetid: ce3c472e-2da1-4d67-816a-befe4ded20d9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dbe8cdb2c7806ab62b67db80c4741d64560fba9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-databases"></a>Gestion des bases de données BAM
Les administrateurs utilisent l'utilitaire de gestion de l'analyse BAM (bm.exe) pour configurer, gérer et mettre à jour les bases de données BAM. Cette section vous indique comment vous servir de l'utilitaire de gestion de l'analyse BAM pour accomplir ces tâches d'administration courantes (voir tableau suivant) pour les bases de données BAM.  
  
 Pour plus d’informations sur la sauvegarde et restauration des bases de données BAM, consultez [sauvegarde et restauration de BAM](../core/backing-up-and-restoring-bam.md).  
  
|Base de données|Nom par défaut de la base de données| Description|  
|--------------|---------------------------|-----------------|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Base de données ou l'analyse BAM collecte les données de suivi brutes.|  
|Base de données de l'application des services de notification BAM|BAMAlertsApplication|Contient des informations d'alerte relatives aux notifications BAM. Par exemple, lorsque vous créez une alerte à partir du portail BAM, des entrées spécifiant les conditions et les événements auxquels l'alerte se rapporte ainsi que des éléments de données relatifs à l'alerte sont insérés dans la base de données.|  
|Base de données de l'instance des services de notification BAM|BAMAlertsNSMain|Contient des informations d'instance précisant la manière dont les services de notification se connectent au système contrôlé par l'analyse BAM.|  
|Base de données de schémas en étoile BAM|BAMStarSchema|Contient le tableau intermédiaire et les tables de mesures et de dimensions.|  
|Base de données d'analyse BAM|BAMAnalysis|Contient les cubes OLAP d'analyse BAM pour les analyses en ligne et hors ligne.|  
|Base de données des archives de l'analyse BAM|BAMArchive|Archive d'anciennes données d'activité d'entreprise. Vous pouvez créer une base de données des archives de l'analyse BAM pour réduire la quantité de données d'activité d'entreprise accumulées dans la base de données d'importation principale BAM.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’archivage des données de base de données d’importation principale](../core/archiving-primary-import-database-data.md)  
  
-   [Création d’une vue partitionnée dans la base de données d’archivage](../core/creating-a-partitioned-view-in-the-archiving-database.md)  
  
-   [Planification de SQL Server Integration Services Packages](../core/scheduling-sql-server-integration-services-packages.md)  
  
-   [Procédure : configurer des bases de données BAM à l’aide de l’utilitaire de gestion BAM](../core/how-to-set-up-the-bam-databases-using-the-bam-management-utility.md)  
  
-   [Comment récupérer le fichier de Configuration BAM à l’aide de l’utilitaire de gestion BAM](../core/how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility.md)  
  
-   [Comment mettre à jour la Configuration BAM à l’aide de l’utilitaire de gestion BAM](../core/how-to-update-the-bam-configuration-using-the-bam-management-utility.md)  
  
-   [Comment référencer des bases de données importation principale BAM supplémentaires](../core/how-to-reference-additional-bam-primary-import-databases.md)  
  
-   [Comment désactiver une référence de base de données d’importation principale BAM](../core/how-to-disable-a-bam-primary-import-database-reference.md)  
  
-   [Comment répertorier toutes les bases de données référencées](../core/how-to-list-all-referenced-databases.md)  
  
-   [Comment supprimer des Instances d’activité incomplètes](../core/how-to-remove-incomplete-activity-instances.md)  
  
-   [Comment mettre à jour la Configuration après une sauvegarde et restauration de l’utilitaire BAM Management](../core/update-the-bam-management-utility-configuration-after-a-backup-and-restore.md)  
  
-   [L’intégration BAM avec SQL Server Reporting Services](../core/how-to-integrate-bam-with-sql-server-reporting-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)