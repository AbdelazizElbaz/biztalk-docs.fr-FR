---
title: "Sauvegarde et restauration des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- backing up, transaction logs
- maintaining, restoring
- restoring, BizTalk Server
- maintaining, backing up
- transaction logs
ms.assetid: 7c08ce19-614c-4728-8dde-c40d4052339e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44bbb9316f1d036551acba5441424bcce65c2549
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-the-biztalk-server-databases"></a>Sauvegarde et restauration des bases de données BizTalk Server
Cette section fournit des informations sur la sauvegarde et la restauration des bases de données de BizTalk Server Vous devez suivre les procédures de cette section pour être certain de pouvoir restaurer un environnement BizTalk Server cohérent en cas de défaillance matérielle. BizTalk Server exécute des transactions distribuées entre les bases de données, de sorte qu'il est essentiel de sauvegarder et restaurer toutes les bases de données.  
  
 BizTalk Server requiert un processus de sauvegarde personnalisé basé sur des sauvegardes de base de données complètes et des sauvegardes de journal avec le marquage de journal transactionnel. Pour plus d’informations sur ce processus, consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journal](../core/marked-transactions-full-backups-and-log-backups.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Liste de vérification : Sauvegarder et restaurer des bases de données BizTalk Server](../core/checklist-back-up-and-restore-biztalk-server-databases.md)  
  
-   [Meilleures pratiques pour la sauvegarde et restauration des bases de données](../core/best-practices-for-backing-up-and-restoring-databases.md)  
  
-   [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)  
  
-   [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)  
  
-   [Résolution de la perte de données](../core/resolving-data-loss.md)  
  
-   [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)