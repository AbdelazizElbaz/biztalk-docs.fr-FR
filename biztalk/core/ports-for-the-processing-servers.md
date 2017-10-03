---
title: Ports pour les serveurs de traitement | Documents Microsoft
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, processing
- ports, processing servers
ms.assetid: 0207b68f-8769-4674-aadc-b3a67b6f210b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4539a17ae95f02c17c754ddcf44882911d805b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-processing-servers"></a>Ports pour les serveurs de traitement
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour que les serveurs de traitement puissent accéder aux services dont ils ont besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Utilisateur connecté|Base de données de gestion BizTalk|SQL Server|1433|TCP|Création et configuration de la base de données de gestion BizTalk|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création, de configuration et de mise à jour de la base de données|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données MessageBox|SQL Server|1433|TCP|Création et configuration de la base de données MessageBox|  
|Utilisateur connecté|Base de données MessageBox|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création de l'hôte|  
|Utilisateur connecté|Base de données MessageBox|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Compte de service SSO|Base de données SSO|SQL Server|1433|TCP|Connexion du service d'authentification unique de l'entreprise à la base de données SSO|  
|Utilisateur connecté|Base de données SSO|DTC|135|TCP|Connexion traitée à SQL Server à des fins de connexion à la base de données SSO|  
|Utilisateur connecté|Base de données SSO|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données des suivis|SQL Server|1433|TCP|Création et configuration de la base de données des suivis|  
|Utilisateur connecté|Base de données des suivis|DTC|135|TCP|Connexion traitée à SQL Server|  
|Utilisateur connecté|Base de données des suivis|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|SQL Server|1433|TCP|Création et configuration de la base de données du moteur des règles d'entreprise|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création, de configuration et de mise à jour de la base de données|  
|Utilisateur connecté|Base de données du moteur des règles d'entreprise|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2393|TCP|Mise à jour et récupération d'informations de la base de données Analyse BAM|  
|Utilisateur connecté|Base de données d'analyse BAM|Système de fichiers du serveur OLAP|445|TCP|Pour créer le fichier de données OLAP (.mdb) sur l’ordinateur distant|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2725|TCP|Pour récupérer des données pour l’analyse (rapports de tableau croisé dynamique)|  
|Utilisateur connecté|Base de données Analyse BizTalk|OLAP|2393|TCP|Pour créer et configurer la base de données analyse BizTalk **Remarque :** les serveurs de traitement doivent se connecter à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration BizTalk.|  
|Utilisateur connecté|Base de données Analyse BizTalk|Système de fichiers du serveur OLAP|445|TCP|Pour créer le fichier de données OLAP (.mdb) sur l’ordinateur distant **Remarque :** les serveurs de traitement doivent se connecter à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration BizTalk.|  
|Utilisateur connecté|Base de données Analyse BizTalk|OLAP|2725|TCP|Création et configuration de la base de données, et récupération des données pour analyse (rapports de tableau croisé dynamique)|  
|Compte du service SSO|Serveur de secret principal|RPC|135|TCP|Connexion traitée à SQL Server pour que le service SSO puisse se connecter au serveur de secret principal|  
|Compte du service SSO|Serveur de secret principal|RPC secondaire|50000-50200|TCP|Ports RPC secondaires pour que le service SSO puisse se connecter au serveur de secret principal. **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Compte de service pour une instance de l'hôte BizTalk|Base de données MessageBox|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Compte de service pour une instance de l'hôte BizTalk|Base de données de gestion BizTalk|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Compte de service pour une instance de l'hôte BizTalk|Base de données SSO|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
|Compte de service pour une instance de l'hôte BizTalk|Base de données des suivis|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données lors d'opérations d'exécution|  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de serveur](../core/server-naming-conventions.md)   
 [Recommandations de sécurité d’exécution BizTalk Server](../core/biztalk-server-runtime-security-recommendations.md)   
 [Recommandations de sécurité de moteur de règle métier](../core/business-rule-engine-security-recommendations.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)