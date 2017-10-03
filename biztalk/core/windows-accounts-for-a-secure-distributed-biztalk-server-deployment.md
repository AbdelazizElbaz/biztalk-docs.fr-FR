---
title: "Comptes Windows pour un déploiement de BizTalk Server distribuée sécurisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, Windows groups
- user accounts, naming conventions
- user accounts
- access control, Windows groups
- security, access control
- architecture, security
- security, Windows accounts
- administrator accounts
- user accounts, administrators
- architecture, large distributions
ms.assetid: 2a0893ef-8bfb-481b-b024-7f7d6e2a6f09
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 678977b23f377425718e483d87725ba191bbda86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-accounts-for-a-secure-distributed-biztalk-server-deployment"></a>Comptes Windows pour un déploiement sécurisé de BizTalk Server
Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Cette section fournit de recommandations concernant la création de groupes et de comptes Windows dans un environnement BizTalk Server distribué. Les noms de groupe et de compte sont des suggestions basées sur les fonctions des groupes et des comptes. Vous pouvez choisir les noms de ces groupes et comptes. Pour plus d’informations sur les architectures BizTalk Server distribuées, consultez [Architecture distribuée](../core/large-distributed-architecture.md).  
  
## <a name="windows-groups-for-a-secure-distributed-biztalk-server-deployment"></a>Groupes Windows pour un déploiement sécurisé de BizTalk Server  
 La liste suivante décrit les groupes Windows recommandés à l'administrateur de domaine pour créer le contrôleur de domaine dans la couche Données.  
  
-   Administrateurs SSO  
  
-   Administrateurs d'applications associées à authentification unique  
  
-   Administrateurs BizTalk Server  
  
-   Opérateurs BizTalk Server  
  
 Pour plus d’informations sur les groupes Windows qui utilise de BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
 Outre les groupes de domaines précédents, le tableau suivant répertorie des groupes supplémentaires spécifiques du déploiement sécurisé, destinés à l'administrateur de domaine pour créer le contrôleur de domaine dans la couche Données.  
  
|Nom de groupe (suggéré)|Fonction|  
|------------------------------|-------------|  
|Utilisateurs d'hôtes de traitement BizTalk 1|Groupe pour les instances d'un hôte in-process spécifique que vous utilisez pour traiter des messages. Créez un groupe pour chaque hôte in-process que vous utilisez pour traiter des messages dans votre environnement BizTalk Server.|  
|Utilisateurs d'hôte d'envoi BizTalk 1|Groupe pour l'instance d'un hôte in-process spécifique que vous utilisez pour envoyer des messages. Créez un groupe pour chaque hôte in-process que vous utilisez pour envoyer des messages dans votre environnement BizTalk Server.|  
|Utilisateurs d’hôtes 1 de réception BizTalk|Groupe pour l'instance d'un hôte in-process spécifique que vous utilisez pour recevoir des messages. Créez un groupe pour chaque hôte in-process que vous utilisez pour recevoir des messages dans votre environnement BizTalk Server.|  
|Utilisateurs d'hôte de suivi BizTalk|Groupe pour l'hôte BizTalk que vous dédiez au suivi.|  
|Utilisateurs SOAP BizTalk|Groupe pour les instances de l'hôte isolé que vous utilisez pour l'adaptateur SOAP.|  
|Utilisateurs HTTP BizTalk|Groupe pour les instances des hôtes isolés que vous utilisez pour l'adaptateur HTTP.|  
  
 L'administrateur de domaine doit créer les groupes suivants dans le contrôleur de domaine du domaine des interfaces de service :  
  
-   Utilisateurs du portail BAM BizTalk  
  
## <a name="windows-user-or-service-accounts-for-a-secure-distributed-biztalk-server-deployment"></a>Comptes d'utilisateur ou de service Windows pour un déploiement distribué sécurisé de BizTalk Server  
 Le tableau suivant répertorie les comptes recommandés à l'administrateur de domaine pour créer le contrôleur de domaine dans le domaine des données. L'administrateur de domaine doit s'assurer que les comptes sont membres des groupes indiqués.  
  
 Pour obtenir des informations complètes sur les comptes d’utilisateur par BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
|Nom de compte (exemple)|Type|Membre du groupe|  
|------------------------------|----------|---------------------|  
|Administrateur de l'authentification unique|Utilisateur|Administrateurs SSO|  
|Service de l'authentification unique|Service|Administrateurs SSO|  
|Secret principal de l'authentification unique|Service|Administrateurs SSO|  
|Administrateur BizTalk|Utilisateur|Administrateurs BizTalk<br /><br /> Administrateurs d'applications associées à authentification unique|  
|Opérateur BizTalk|Utilisateur|Opérateurs BizTalk|  
|Traitement BizTalk 1|Service|Utilisateurs d'hôtes de traitement BizTalk 1|  
|2 de traitement BizTalk **Remarque :** vous pouvez créer plusieurs comptes pour chaque hôte de traitement dans votre environnement.|Service|Utilisateurs d'hôtes de traitement BizTalk 1|  
|Suivi BizTalk|Service|Utilisateurs d'hôte de suivi BizTalk|  
|adaptateur SOAP|Service|Utilisateurs SOAP BizTalk|  
|adaptateur HTTP|Service|Utilisateurs HTTP BizTalk|  
|Service de mise à jour du moteur des règles|Service||  
|Installation|Utilisateur|Administrateurs de l'authentification unique (uniquement pour la configuration du serveur de secret principal)<br /><br /> Administrateurs locaux<br /><br /> Rôle SQL Server sysadmin<br /><br /> Administrateur OLAP|  
|Pool d’applications BAM|Service|IIS_WPG|  
|Gestion de l'analyse BAM|Service|IIS_WPG|  
|Notification BAM|Service|SQLServer2005NotificationServicesUser$\<**Nom_Ordinateur**>|  
  
 Le tableau suivant répertorie les comptes recommandés à l'administrateur de domaine pour créer le contrôleur de domaine dans le domaine d'entreprise.  
  
|Nom du compte|Type|  
|------------------|----------|  
|Administrateur SharePoint|Utilisateur|  
|Informations d'identification de site SharePoint|Utilisateur|  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture distribuée](../core/large-distributed-architecture.md)   
 [Autorisations de sécurité minimales](../core/minimum-security-user-rights.md)   
 [Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)