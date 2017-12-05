---
title: "Les journaux de comptes d’utilisateurs et rôles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2056ea90-5e9f-4501-95d6-18c905db4023
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7dbec7cfa23c8a1e07e32cdf0c3ce7b044651ec
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="log-shipping-user-accounts-and-roles"></a>Journaux de rôles et les comptes d’utilisateur
Envoi de journaux est pilotée par un travail de l’Agent SQL Server pour automatiser le processus de restauration des sauvegardes et des journaux de BizTalk Server. Des autorisations incorrectes peuvent entraîner des opérations de restauration effectuées par envoi de journaux de BizTalk Server pour faire échouer. Le compte d’utilisateur configuré pour restaurer les bases de données doit avoir accès à l’instance de base de données de production qui héberge la base de données de gestion BizTalk. Dans la plupart des cas cela signifie que le compte de service pour le travail de l’Agent SQL Server gèrent le journaux de BizTalk Server sur la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance requiert une connexion et des autorisations sur l’instance de base de données de production qui héberge le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]base de données de gestion. Cela suppose que le compte de service SQL Server Agent est configuré en tant que le propriétaire du travail.  
  
 BizTalk Server inclut un rôle SQL Server nommé BTS_BACKUP_USERS afin que le compte d’utilisateur configuré pour restaurer les bases de données ne nécessite pas d’autorisation des administrateurs système SQL Server.  
  
 Lorsque vous configurez le compte d’utilisateur qui effectue les opérations de restauration de base de données dans le cadre de la copie des journaux de BizTalk Server, vérifiez que les éléments suivants :  
  
-   Configurer le service de l’Agent SQL Server pour une exécution sous un compte de domaine avec un utilisateur mappé configuré dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio (dans **sécurité**, **connexions**) sur chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance hôtes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données restaurées par les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journal des travaux de copie.  
  
-   Configurer un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] connexion de compte pour cet utilisateur et affectez cet utilisateur au rôle BizTalk BTS_BACKUP_USERS SQL sur chaque serveur.  
  
-   Affectez cet utilisateur à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] rôle des administrateurs système sur l’ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui héberge le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de gestion.  
  
-   Le compte qui effectue la sauvegarde et de restauration doivent disposer les opérations de lecture et d’accès en écriture pour le chemin UNC partagent où sont créés les fichiers de sauvegarde.