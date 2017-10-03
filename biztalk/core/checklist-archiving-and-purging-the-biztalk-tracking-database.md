---
title: "Liste de vérification : Archivage et la purge de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], checklist
- checklists, purging [Tracking database]
- purging, checklist
- checklists, archiving [Tracking database]
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22e97ac12e6b6b304318f57f309767ec7c63815f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-archiving-and-purging-the-biztalk-tracking-database"></a>Liste de vérification : Archivage et la purge de la base de données de suivi de BizTalk
|Étape|Référence|  
|----------|---------------|  
|Lisez la présentation relative à l'archivage et à la purge afin de vous familiariser avec l'archivage et la purge des données de suivi.|[Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|Bien qu'il vous soit possible d'exécuter le travail de purge et d'archivage DTA en recourant aux informations d'identification que vous avez utilisées pour vous connecter, il est préférable, pour une meilleure sécurité, que vous configuriez le rôle BTS_BACKUP_USERS à l'aide des informations d'identification SQL Server nécessaires. Ainsi, il est inutile d'étendre les privilèges.|[Comment configurer le rôle BTS_BACKUP_USERS pour l’archivage et la purge des données de la base de données de suivi de BizTalk](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|Configurez le travail de purge et d'archivage DTA.|[Configuration du travail de purge et d’archivage DTA](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|Exécutez le travail de purge et d'archivage DTA en vue d'archiver les données dans la base de données des suivis BizTalk (BizTalkDTADb) et de purger les données anciennes.|[Purge des données de la base de données de suivi de BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|Si vous le souhaitez, purgez manuellement les données de la base de données des suivis BizTalk (BizTalkDTADb).|[Purge manuelle des données à partir de la base de données de suivi BizTalk](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|Activez la validation automatique des données archivées de la base de données des suivis BizTalk (BizTalkDTADb).|[Comment activer la Validation de l’archivage automatique](../core/how-to-enable-automatic-archive-validation.md)|  
|Copiez les messages de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Cette opération est obligatoire pour pouvoir purger les données avec le travail DTA Purge and Archive.|[Comment copier des Messages suivis dans la base de données de suivi de BizTalk](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)