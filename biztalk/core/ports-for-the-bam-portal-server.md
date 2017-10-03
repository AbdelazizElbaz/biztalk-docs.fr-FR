---
title: Ports pour le serveur du portail BAM | Documents Microsoft
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df67c31c-a7a3-4bff-9374-0d8a0cf0ad21
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adfa47415c1e367941203d20533c5e3ac3f431da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-bam-portal-server"></a>Ports du serveur du portail BAM
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour que le site Web du portail BAM puisse accéder aux services dont il a besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Utilisateur connecté|Base de données de gestion BizTalk|SQL Server|1433|TCP|Création et configuration de la base de données|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création, de configuration et de mise à jour de la base de données|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|50000-50200|TCP|Ports RPC secondaires pour créer et de se connecter à cette base de données **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Pool d'applications|Clients entrants|HTTP(S)|80 ou 443|TCP|Pour le trafic entrant du site Web|  
|Utilisateur connecté|Base de données MessageBox|SQL Server|1433|TCP|Création et configuration de la base de données|  
|Utilisateur connecté|Base de données MessageBox|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création, de configuration et de mise à jour de la base de données|  
|Utilisateur connecté|Base de données MessageBox|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Compte de service SSO|Base de données SSO|SQL Server|1433|TCP|Connexion à la base de données SSO|  
|Utilisateur connecté|Base de données des suivis|SQL Server|1433|TCP|Création et configuration de la base de données|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|SQL Server|1433|TCP|Création et configuration de la base de données|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création, de configuration et de mise à jour de la base de données|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2393|TCP|Création et configuration de la base de données|  
|Utilisateur connecté|Base de données d'analyse BAM|Système de fichiers du serveur OLAP|445|TCP|Création du fichier de données OLAP (.mdb) sur l'ordinateur distant|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2725|TCP|Mise à jour et récupération d'informations de la base de données|  
|Compte de service SSO|Base de données SSO|SQL Server|1433|TCP|Mise à jour et récupération d'informations dans la base de données par le service SSO|  
|Compte de service SSO|Serveur de secret principal|Serveur de secret principal|135|TCP|Connexion traitée à SQL Server pour que le service SSO puisse se connecter au serveur de secret principal|  
|Service SSO|Serveur de secret principal|RPC secondaire|50000-50200|TCP|Ports RPC secondaires pour que le service SSO puisse se connecter au serveur de secret principal. **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Instance de l'hôte BizTalk|Base de données MessageBox|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Instance de l'hôte BizTalk|Base de données de gestion BizTalk|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Instance de l'hôte BizTalk|Base de données SSO|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Instance de l'hôte BizTalk|Base de données des suivis|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Utilisateur du pool d'applications BAM|Services de notification BAM|SQL Server|1433|TCP|Accès à la base de données des services de notification BAM|  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de serveur](../core/server-naming-conventions.md)   
 [Considérations de sécurité pour le portail BAM](../core/security-considerations-for-the-bam-portal.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)