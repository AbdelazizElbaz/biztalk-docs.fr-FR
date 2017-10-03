---
title: "Recommandations de sécurité BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- managing [BAM], security
- BAM, security
ms.assetid: 73613123-c1ed-477a-9f5c-342b2573c975
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f26cd3051dd296cc2849cb9c8ba7f8aa1d7ac6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-security-recommendations"></a>Recommandations de sécurité pour les services BAM
Il est recommandé de respecter les informations suivantes pour la sécurisation et le déploiement de l'analyse BAM dans votre environnement.  
  
-   Si vous utilisez [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], l'ordinateur d'administration doit disposer des logiciels suivants pour déployer l'analyse BAM :  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]  
  
    -   outils clients [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] ;  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]Integration Services  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Analysis Services ;  
  
    -   [!INCLUDE[SQLServer2005_SP3_long](../includes/sqlserver2005-sp3-long-md.md)], si vous allez utiliser les alertes BAM.  
  
        > [!NOTE]
        >  [!INCLUDE[SQLServer2005_SP3_short](../includes/sqlserver2005-sp3-short-md.md)] inclut [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services pour [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)].  
  
    > [!NOTE]
    >  Le contexte utilisateur d'exécution du lot DTS d'analyse doit être un membre du rôle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] db_owner associé aux bases de données d'importation principale BAM et de schémas en étoile BAM. De plus, le compte de service sous lequel Analysis Services est exécuté doit être un administrateur OLAP et avoir un rôle db_owner associé à la base de données de schémas en étoile BAM. Pour plus d’informations, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781).  
  
-   Plusieurs utilisateurs ont besoin d’accéder aux données actives et archivées : commerciaux, les gestionnaires des activités et autres. Ces utilisateurs doivent disposer de comptes dans le domaine des bases de données d'importation principale BAM et d'analyse BAM (domaine d'entreprise) mais leurs comptes n'ont pas besoin d'avoir accès aux ressources BizTalk.  
  
-   Pour les utilisateurs à accéder à des affichages de données BAM, vous devez utiliser l’utilitaire de gestion BAM (BM.exe) pour accorder les autorisations requises pour les vues et les utilisateurs doivent disposer de connexions SQL. Pour plus d’informations sur l’utilitaire de gestion BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md).  
  
-   Pour ajouter des utilisateurs aux rôles qui ont accès aux cubes dans la base de données analyse BAM, vous devez disposer d’un ordinateur d’administration dans le même domaine que les bases de données BAM.  
  
-   La personne qui administre BAM doit avoir un rôle db_owner associé aux bases de données d'importation principale BAM, de schémas en étoile et d'archives BAM. Cette personne doit également être un administrateur OLAP de la base de données analyse BAM.  
  
-   Si vous déployez des classeurs Microsoft Office Excel (fichiers .xls), l'application Excel doit être installée sur l'ordinateur d'administration. Avant de déployer un classeur, ouvrez-le et assurez-vous que le niveau de sécurité des macros est élevé et qu'aucun avertissement ne s'affiche.  
  
-   S'il n'est pas nécessaire de distribuer aux utilisateurs des classeurs Excel BAM associés à des données réelles, il est recommandé de déployer les classeurs à l'aide de fichiers XML. Il n'est ainsi pas nécessaire d'installer Excel sur l'ordinateur d'administration, ni de vérifier le niveau de sécurité des macros.  
  
    > [!IMPORTANT]
    >  Lorsque vous supprimez les autorisations d’un utilisateur sur une vue, vous devez également mettre à supprimer tous les abonnements aux alertes que l’utilisateur a défini. Pour plus d’informations sur la suppression d’abonnés d’une alerte, consultez [comment supprimer les abonnés d’une alerte](../core/how-to-remove-subscribers-from-an-alert.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de sécurité minimales](../core/minimum-security-user-rights.md)   
 [Recommandations de sécurité pour un déploiement BizTalk Server](../core/security-recommendations-for-a-biztalk-server-deployment.md)