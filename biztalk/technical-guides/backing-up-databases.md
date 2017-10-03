---
title: "Sauvegarde des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0524a8f0-15a3-4731-a7bd-c0c935fff6c8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6a4b40be0a9a7d4846dd965a4d9f934e69690e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-databases"></a>Sauvegarde de bases de données
Étant donné que[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise des transactions distribuées entre plusieurs bases de données, le travail de sauvegarde de BizTalk Server crée des sauvegardes synchronisées de toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Cela est accompli à l’aide de transactions avec le mode de récupération « Complet » de la base de données marquées. Cela est nécessaire pour les sauvegardes être cohérente entre les bases de données. Pour plus d’informations, consultez [« Transactions marquées, sauvegardes complètes et sauvegardes de journaux »](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565) dans la documentation de BizTalk Server.  
  
## <a name="advantages-of-the-backup-biztalk-server-job"></a>Avantages du travail de sauvegarde de BizTalk Server  
 Le travail de sauvegarde de BizTalk Server est la seule méthode prise en charge pour sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux pour sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données dans un environnement de production n’est pas pris en charge.  
  
 Si la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail n’est pas exécuté, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] unbounded augmentera de journaux de transaction de base de données. Le travail de sauvegarde tronque les journaux des transactions, ce qui les empêcher de croissance illimitée. Si la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction de base de données continuent d’augmenter, ils impossible à un moment donné remplir le disque, elles sont hébergées sur.  
  
> [!NOTE]  
>  À l’aide de la sauvegarde de ces deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail et envoi de journaux est actuellement le seul entièrement documenté et méthode de prise en charge pour l’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sauvegarde de base de données et de restauration.  
  
## <a name="guidelines-for-the-backup-biztalk-server-job"></a>Recommandations pour le travail de sauvegarde de BizTalk Server  
 Vous devez restaurer l’intégralité de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement régulièrement. Cela inclut non seulement l’ou les serveurs SQL et le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, mais également sur les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez documenter et pratique de ces procédures avant une défaillance se produit réellement.  
  
> [!NOTE]  
>  La sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail ne supprime pas les anciens fichiers de sauvegarde. Vous devez définir et placer des processus en place pour archiver les anciens fichiers de sauvegarde et de les déplacer à partir du répertoire de sauvegarde qui utilise de la tâche de sauvegarde.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Consultez les rubriques suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation :  
  
-   Pour plus d’informations spécifiques [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de sauvegarde et restauration des tâches, consultez [« Liste de vérification : sauvegarde et restauration »](http://go.microsoft.com/fwlink/?LinkId=154070) (http://go.microsoft.com/fwlink/?LinkId=154070).  
  
-   Pour une vue d’ensemble de la sauvegarde et restauration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [« Sauvegarde et restauration de BizTalk serveur »](http://go.microsoft.com/fwlink/?LinkId=154071) (http://go.microsoft.com/fwlink/?LinkId=154071).  
  
-   Pour plus d’informations sur la configuration de la tâche de sauvegarde de BizTalk Server, consultez [« Comment pour configurer la sauvegarde de travail de BizTalk Server »](http://go.microsoft.com/fwlink/?LinkId=154072) (http://go.microsoft.com/fwlink/?LinkId=154072).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des journaux de BizTalk Server pour la récupération d’urgence](../technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)