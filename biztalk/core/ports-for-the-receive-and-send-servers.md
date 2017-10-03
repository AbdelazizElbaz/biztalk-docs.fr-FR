---
title: "Ports pour les serveurs de l’envoi et la réception | Documents Microsoft"
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection strings
- servers, sending
- ports, servers
- servers, receiving
- BizTalk Server, service accounts
- SSO, service accounts
ms.assetid: 19cafe74-6676-4779-8ced-de0841dba19f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04ddda71d04cf784f07cf8e0783775d7ae91e6d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-receive-and-send-servers"></a>Ports pour les serveurs de réception et d'envoi
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour que les serveurs de réception et d'envoi puissent accéder aux services dont ils ont besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Compte de service BizTalk|Partage de fichiers<br /><br /> Partage de base des documents EDI|Serveur de réception/envoi|445|TCP|Récupération et déplacement des fichiers vers l'emplacement de fichier pour l'adaptateur FILE|  
|Compte de service BizTalk|FTP Server|Service FTP|20|TCP|Récupération et déplacement des fichiers vers le serveur FTP pour l'adaptateur FTP|  
|Compte de service BizTalk|FTP Server|Service FTP|21|TCP|Récupération et déplacement des fichiers vers le serveur FTP pour l'adaptateur FTP|  
|Compte de service BizTalk|Serveur POP3|Service POP3|110|TCP|Récupération des messages du serveur POP3 pour l'adaptateur POP3|  
|Compte de service BizTalk|Serveur de traitement|Windows Message Queuing|1801|TCP|Réception des messages et envoi de messages au moteur d'exécution BizTalk pour l'adaptateur Message Queuing de BizTalk|  
|Chaîne de connexion|Cible de l'adaptateur SQL|SQL Server|1433|TCP|Récupération et envoi des messages des bases de données utilisées par l'adaptateur SQL|  
|Chaîne de connexion|Cible de l'adaptateur SQL|DTC|135|TCP|Connexion traitée à SQL Server pour l'adaptateur SQL|  
|Chaîne de connexion|Cible de l'adaptateur SQL|DTC|50000-50200|TCP|Ports RPC secondaires pour l’adaptateur SQL **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Compte de service BizTalk|SMTP/Exchange|SMTP|25|TCP|Connexion au serveur SMTP pour l'adaptateur SMTP|  
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
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|Mise à jour et récupération d'informations de la base de données Analyse BAM|  
|Utilisateur connecté|Base de données d'analyse BAM|Système de fichiers du serveur OLAP|445|TCP|Pour créer le fichier de données OLAP (.mdb) sur l’ordinateur distant|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2725|TCP|À des fins de récupération des données pour analyse (rapports de tableau croisé dynamique)|  
|Utilisateur connecté|Base de données Analyse BizTalk|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|Pour créer et configurer la base de données analyse BizTalk **Remarque :** les serveurs de traitement doivent se connecter à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration BizTalk.|  
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
 [Recommandations de sécurité de l’adaptateur HTTP](../core/http-adapter-security-recommendations.md)   
 [Recommandations de sécurité de l’adaptateur SOAP](../core/soap-adapter-security-recommendations.md)   
 [Recommandations de sécurité de l’adaptateur FTP](http://msdn.microsoft.com/library/ea7c0577-9d72-4d63-94e7-8f649c6e713f)   
 [Recommandations de sécurité de l’adaptateur SMTP](../core/smtp-adapter-security-recommendations.md)   
 [Recommandations de sécurité de l’adaptateur de fichier](http://msdn.microsoft.com/library/fe4d51c0-b697-457b-bf27-f1cf6965d954)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)