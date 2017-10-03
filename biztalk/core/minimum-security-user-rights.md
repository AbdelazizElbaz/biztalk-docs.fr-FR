---
title: "Droits d’utilisateur de sécurité minimales | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- permissions, user accounts
- permissions, roles
- administrator accounts, permissions
- roles, permissions
- permissions, administrator accounts
- user accounts, permissions
- user accounts, access control
- security, permissions
ms.assetid: 44b6e7da-8e6c-40c0-a250-52ab422c0adf
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ad405afd1f69b4499b8c4650586411957a2ca3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="minimum-security-user-rights"></a>Droits d’utilisateur de sécurité minimales
Les groupes et les comptes utilisés par BizTalk Server possèdent les droits d'utilisateur minimaux dont ils ont besoin pour effectuer la plupart des tâches. Aussi, certaines tâches peuvent nécessiter d'autres droits d'utilisateur en plus de ceux accordés automatiquement à votre groupe par BizTalk Server. Dans cette rubrique :  
  
 [Groupe et l’appartenance au rôle](../core/minimum-security-user-rights.md#BKMK_GroupRole)  
  
 [Droits d’utilisateur pour effectuer des tâches d’administration](../core/minimum-security-user-rights.md#BKMK_UserRights)  
  
 [Ajout de la Communauté – liste des tâches](../core/minimum-security-user-rights.md#BKMK_Community)  
  
##  <a name="BKMK_GroupRole"></a>Groupe et l’appartenance au rôle  
 Le tableau suivant décrit les autorisations de sécurité minimales dont vous avez besoin pour effectuer des tâches dans BizTalk Server :  
  
|Tâche|Groupes ou rôles|  
|----------|---------------------|  
|**Programme d’installation**||  
|Installation|-Administrateurs local|  
|Configuration|Les administrateurs BizTalk Server<br />-Administrateurs local<br />-sysadmin rôle SQL Server<br />-Les administrateurs SSO<br />-Administrateur OLAP|  
|Ajout à un groupe BizTalk Server|-Administrateurs local<br />Les administrateurs BizTalk Server|  
|**Administration de BizTalk**||  
|Création d'une base de données MessageBox|Les administrateurs BizTalk Server<br />-sysadmin rôle SQL Server|  
|Création et suppression d'un hôte BizTalk|Les administrateurs BizTalk Server<br />-rôle de base de données SQL Server db_ddladmin sur les bases de données MessageBox de BizTalk|  
|Modification de la propriété de suivi de l'hôte pour un hôte|Les administrateurs BizTalk Server<br />-rôle de base de données SQL Server db_securityadmin sur la base de données d’importation principale BAM, les bases de données BizTalk MessageBox et la base de données des suivis BizTalk|  
|Création (installation), suppression et modification des informations d'identification d'une instance d'hôte|<ul><li>Administrateurs BizTalk Server</li><li>Administrateurs locaux</li><li>Rôle SQL Server securityadmin sur le ou les serveurs sur lesquels sont situées les bases de données suivantes :<br /><br /> <ul><li>bases de données MessageBox BizTalk, base de données de gestion BizTalk, base de données du moteur de règles, base de données des suivis BizTalk, base de données d'importation principale BAM</li></ul></li><li>Rôle de base de données SQL Server db_securityadmin dans les bases de données suivantes :<br /><br /> <ul><li>bases de données MessageBox BizTalk, base de données de gestion BizTalk, base de données du moteur de règles, base de données des suivis BizTalk, base de données d'importation principale BAM</li></ul></li></ul>|  
|Démarrage et arrêt d'une instance d'hôte|Les administrateurs BizTalk Server|  
|Ajout et suppression d'un serveur|Les administrateurs BizTalk Server<br />-Les administrateurs sur l’ordinateur que vous ajoutez ou supprimez locales.|  
|Ajout et suppression d'un gestionnaire de réception|Les administrateurs BizTalk Server<br />-Administrateurs d’applications associées à SSO|  
|Arrêt et démarrage des applications, orchestrations, ports d'envoi et groupes de ports d'envoi|Les opérateurs BizTalk Server|  
|Activation et désactivation des emplacements de réception|Les opérateurs BizTalk Server|  
|Recherche d'artefacts|Les opérateurs BizTalk Server|  
|Ajout d'un adaptateur|Les administrateurs BizTalk Server<br />-Administrateurs d’applications associées à SSO|  
|Bases de données de sauvegarde|-Rôle BTS_BACKUP_USERS pour les bases de données<br />-rôle de SQL Server sysadmin sur le serveur SQL Server hébergeant la base de données de gestion BizTalk. **Remarque :** vous devez configurer le service de l’Agent SQL Server pour exécuter sous un compte de domaine ou un compte local avec un utilisateur mappé sur chaque instance de SQL Server.|  
|Configuration de groupes BizTalk à l'aide d'un certificat|Les administrateurs BizTalk Server|  
|Toutes les autres tâches (WMI inclus)|Les administrateurs BizTalk Server|  
|**Opérations et des messages et des instances de Service de suivi**||  
|Affichage de la page Hub du groupe, exécution de requêtes, enregistrement et chargement de requêtes|Les opérateurs BizTalk Server|  
|Affichage des résultats d'une requête|Les opérateurs BizTalk Server|  
|Configuration générale et configuration du suivi|-Administrateurs de BizTalk Server (lecture et écriture)<br />Opérateurs de serveur BizTalk (lecture)|  
|Consultation d'un cube d'analyse du fonctionnement|Les administrateurs BizTalk Server|  
|Affichage des propriétés de message|Les administrateurs BizTalk Server|  
|Enregistrement de corps de message|Les administrateurs BizTalk Server|  
|Utilisez **rechercher le Message** requête|Les administrateurs BizTalk Server|  
|Utilisez **requête de Build**|Les administrateurs BizTalk Server|  
|Utilisation du débogueur de l'orchestration|Les administrateurs BizTalk Server|  
|Affichage du flux de messages et des événements de message dans la page Hub du groupe à l'aide de la console Administration de BizTalk Server.|Les opérateurs BizTalk Server|  
|Interruption, arrêt et reprise des instances de service|Les opérateurs BizTalk Server|  
|Archivage et purge de messages à partir de la base de données des suivis|-rôle db_owner sur la base de données des suivis BizTalk|  
|Toutes les autres tâches|Les administrateurs BizTalk Server|  
|**Éditeur de modèle de suivi**||  
|Lecture et écriture dans la base de données de gestion BizTalk|Les administrateurs BizTalk Server|  
|**Bus d’événements BAM MMC**||  
|Toutes les tâches|Les administrateurs BizTalk Server|  
|**Assistant Publication de services WCF BizTalk**||  
|Toutes les tâches|-Administrateurs local|  
|**Assistant Publication de Services Web BizTalk**||  
|Toutes les tâches|-Administrateurs local|  
|**Analyse BAM**||  
|Exécution de BM.exe|-rôle de base de données SQL Server db_owner dans les bases de données d’importation principale BAM, schémas en étoile BAM et archives BAM|  
|Exécution de BM.exe, s'il y a une base de données Analysis Services|-rôle de base de données SQL Server db_owner dans les bases de données d’importation principale BAM, schémas en étoile BAM et archives BAM<br />-Administrateurs OLAP dans la base de données BAM Analysis Services|  
|Création d'un compte pour la vue BAM|-rôle de base de données SQL Server db_owner dans la base de données d’importation principale BAM<br />-Administrateurs OLAP dans la base de données BAM Analysis Services|  
|**Moteur de règles (règles de publication)**||  
|Déploiement/annulation du déploiement de stratégies, manipulation d'artefacts liés à la sécurité|-Rôle de base de données RE_ADMIN_USERS SQL Server dans la base de données du moteur de règles|  
  
##  <a name="BKMK_UserRights"></a>Droits d’utilisateur pour effectuer des tâches d’administration  
 Le compte utilisé pour exécuter des tâches d'administration à l'aide de la console Administration de BizTalk Server ou de Windows Management Instrumentation (WMI) requiert différents niveaux de droits d'utilisateur selon la tâche à effectuer.  
  
 Le tableau suivant décrit les droits d'utilisateur dont le compte à besoin pour effectuer les tâches, des plus faibles (niveau 1) aux plus élevés (niveau 4).  
  
|Niveau des droits d'utilisateur|Droits d'utilisateur octroyés|Tâches|  
|--------------------------|-------------------------|-----------|  
|0|Les opérateurs BizTalk Server|-De base d’administration et surveillance des tâches. Pas de modification possible des paramètres de configuration. Pas d'accès aux propriétés ou au contenu des messages.|  
|1|Les administrateurs BizTalk Server|-Toutes les tâches d’administration, à l’exception de ceux qui requièrent de niveau 2 à 4 des droits d’utilisateur|  
|2|-Droits d’utilisateurs octroyés au niveau 1<br />-le rôle de SQL Server securityadmin sur tous les serveurs SQL<br />-les rôles de base de données SQL Server db_securityadmin et db_accessadmin dans les bases de données des suivis BizTalk, du moteur de règles, administration de BizTalk, importation principale BAM et BizTalk MessageBox<br />-rôle de base de données SQL Server db_ddladmin sur toutes les bases de données MessageBox de BizTalk<br />-Administrateurs d’applications associées à SSO|-Permet de créer et supprimer des hôtes BizTalk<br />-Propriété de suivi de l’hôte modifier<br />-Permet d’ajouter et supprimer des serveurs<br />-Permet d’ajouter et supprimer des gestionnaires de réception<br />-Ajouter des cartes|  
|3|-Utilisateur aux droits accordés au niveau 2<br />-Locales administrateurs sur tous les ordinateurs d’exécution BizTalk Server|-Permet de créer et supprimer des instances d’hôte|  
|4|-Utilisateur aux droits accordés au niveau 3<br />-le rôle sysadmin SQL Server sur tous les serveurs SQL qui ont des bases de données MessageBox de BizTalk|-Créer des bases de données MessageBox|  
  
##  <a name="BKMK_Community"></a>Ajout de la Communauté – liste des tâches  
 [Droits de sécurité minimales pour BizTalk Server 2013 R2](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx) (http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2013-r2.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md)   
 [Conception des Architectures système pour BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Bases de données BizTalk Server](../core/databases-in-biztalk-server.md)   
 [Groupes et comptes d’utilisateur Windows dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)