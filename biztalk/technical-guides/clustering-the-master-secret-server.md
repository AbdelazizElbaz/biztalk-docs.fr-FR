---
title: Clustering du serveur de secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f37997582cbd94d8bbb5eaee829eead0af85ad2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="clustering-the-master-secret-server"></a>Clustering du serveur de secret principal
Le service d’application BizTalk Server conserve une dépendance codée en dur sur le service Enterprise Single Sign-On (SSO) qui est installé avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le service d’authentification unique doit être en mesure de communiquer avec le serveur de secret principal à démarrer. Nous vous recommandons de mettre en cluster le service d’authentification unique sur le serveur de secret principal à tolérance de pannes pour le serveur de secret principal. Pour plus d’informations, consultez [Options d’Installation de l’authentification unique de haute disponibilité](http://go.microsoft.com/fwlink/?LinkId=156838) (http://go.microsoft.com/fwlink/?LinkId=156838) dans l’aide de BizTalk Server.  
  
## <a name="preparing-for-clustering-the-master-secret-server"></a>Préparation pour le Clustering du serveur de secret principal  
  
### <a name="deciding-whether-to-use-a-dedicated-cluster-or-the-sql-server-cluster"></a>S’il faut utiliser un Cluster dédié ou le Cluster SQL Server  
 Clustering matériel est coûteux. Pour réduire les ressources matérielles pour une solution hautement disponible, vous pouvez ajouter le serveur de secret principal en tant que ressource de cluster dans votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster de la base de données. Si vous utilisez la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster de la base de données, nous vous recommandons de ne pas mettre le serveur de secret principal sur le même nœud actif en tant que la base de données MessageBox. La base de données MessageBox est généralement plus occupé que les autres bases de données. Même si le serveur de secret principal ne consomme pas beaucoup de ressources de matériel, il est préférable pour le déplacer vers un nœud actif du cluster différent à partir du nœud de base de données MessageBox actif.  
  
### <a name="clustering-the-sso-database"></a>Clustering de la base de données SSO  
 Le serveur de secret principal dépend de la base de données SSO. Pour générer une authentification unique de haute disponibilité, vous devez mettre en cluster la base de données SSO. Pour plus d’informations sur les clusters de bases de données BizTalk, consultez [Clustering le Databases2 serveur BizTalk](../technical-guides/clustering-the-biztalk-server-databases2.md).  
  
### <a name="creating-domain-groups-and-accounts"></a>Création de comptes et groupes de domaine  
 Vous devez configurer les comptes et groupes de domaine suivants avant de mettre le serveur de secret principal :  
  
-   Créez des groupes de domaine avec les noms des administrateurs de l’authentification unique et administrateurs d’applications associées à authentification unique. Pour créer une instance en cluster du service SSO de l’entreprise, vous devez créer les groupes Administrateurs SSO et administrateurs d’applications associées à authentification unique en tant que groupes de domaine.  
  
-   Créez ou désignez un compte de domaine qui est membre du groupe Administrateurs de domaine. Le service SSO sur chaque nœud sera configuré pour ouvrir une session en tant que ce compte de domaine. Ce compte doit disposer du droit « Session en tant que service » sur chaque nœud du cluster. Ce compte doit également être reçu l’accès contrôle total au cluster.  
  
## <a name="clustering-the-master-secret-server"></a>Clustering du serveur de secret principal  
 Voici les étapes de base pour le serveur de secret principal de clustering :  
  
1.  Installer et configurer l’authentification unique de l’entreprise sur les nœuds de cluster.  
  
2.  Créer la ressource de l’authentification unique de l’entreprise en cluster et les ressources dépendantes.  
  
3.  Restaurez le secret principal sur le deuxième nœud du cluster. Si vous déplacez le serveur de secret principal sur le cluster, vous devez restaurer le secret principal sur le premier nœud de cluster ainsi.  
  
4.  Mettez le groupe de clusters contenant le service d’authentification unique, en ligne.  
  
5.  Mettre à jour le nom de secret principal dans la base de données de gestion.  
  
 Pour obtenir des instructions détaillées sur le serveur de secret principal de clustering, consultez [mise en Cluster du serveur de secret principal](http://go.microsoft.com/fwlink/?LinkId=156839) (http://go.microsoft.com/fwlink/?LinkId=156839) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Désignation manuelle d’un nouveau serveur de secret principal](../technical-guides/designating-a-new-master-secret-server-manually.md)