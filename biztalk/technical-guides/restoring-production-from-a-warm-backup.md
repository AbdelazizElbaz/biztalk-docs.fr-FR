---
title: "Restauration de Production à partir d’une sauvegarde à chaud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bda14b8-b3cc-4a5e-a353-fca5885fd594
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e590b4eccb6ee946a915ff1f3a0265bbfe977e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-production-from-a-warm-backup"></a>Restauration de Production à partir d’une sauvegarde à chaud
Si le système source devient non fiable, il est possible de restaurer les bases de données à partir de la destination à la source. Effectuez la procédure suivante pour restaurer des bases de données à partir de la destination à la source.  
  
### <a name="to-restore-the-databases-from-the-destination-to-the-source-follow-these-steps"></a>Pour restaurer les bases de données à partir de la destination à la source, procédez comme suit  
  
1.  Désactiver tous les travaux de sauvegarde sur la source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
2.  Attendre que tous les travaux sur la récupération d’urgence (DR) destination de restauration [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
3.  Désactiver tous les travaux de restauration sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
4.  Restaurer toutes les bases de données avec STOPATMARK sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
5.  Arrêtez tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services sur tous les serveurs BizTalk.  
  
6.  Supprimer tous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-bases de données sur la source (production) associées [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
7.  Sauvegardez toutes les bases de données (complète) sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
8.  Restaurer (installation complète), toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sauvegardées à l’étape 7 pour la source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
9. Redémarrez tous les serveurs BizTalk, y compris le serveur de secret principal.  
  
10. Supprimer tous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-bases de données sur la destination (DR) associées [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
11. Activer les travaux de sauvegarde de la source de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
12. Activer les travaux de restauration sur la destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations avancées sur la sauvegarde et Restore2](../technical-guides/advanced-information-about-backup-and-restore2.md)