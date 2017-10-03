---
title: Ports pour le serveur de suivi | Documents Microsoft
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking server
- ports, tracking server
ms.assetid: 4b4913a4-7d8d-4fd0-a116-ba868c4ad7da
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975f5e42c800a6d4ae4015108afa2650b2c7f626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-tracking-server"></a>Ports pour le serveur de suivi
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour que le serveur de suivi puisse accéder aux services dont il a besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Utilisateur connecté|Base de données de gestion BizTalk|SQL Server|1433|TCP|Création et configuration de la base de données de gestion BizTalk|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|135|TCP|Connexion traitée à SQL Server à des fins de mise à jour et de récupération d'informations de la base de données|  
|Utilisateur connecté|Base de données de gestion BizTalk|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Utilisateur connecté|Base de données SSO|SQL Server|1433|TCP|Connexion du service d'authentification unique à la base de données SSO|  
|Utilisateur connecté|Base de données d'importation principale BAM|SQL Server|1433|TCP|Validation de la base de données d'importation principale BAM. L'hôte de suivi se connecte à cette base de données au moment de l'exécution.|  
|Utilisateur connecté|Base de données de schémas en étoile BAM|SQL Server|1433||Mise à jour et récupération d'informations de la base de données. **Remarque :** l’hôte de suivi se connecte à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration de BizTalk pour créer un nouveau groupe BizTalk à partir de ce serveur.|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|445|TCP|Création du fichier de données OLAP (.mdb) sur l'ordinateur distant. **Remarque :** l’hôte de suivi se connecte à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration de BizTalk pour créer un nouveau groupe BizTalk à partir de ce serveur.|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2383 (SQL Server 2005 Analysis Services)||Pour créer et configurer la base de données analyse BAM **Remarque :** hôte de suivi le se connecte à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration de BizTalk pour créer un nouveau groupe BizTalk à partir de ce serveur.|  
|Utilisateur connecté|Base de données d'analyse BAM|OLAP|2725|TCP|Pour récupérer des données pour l’analyse (rapports de tableau croisé dynamique) **Remarque :** hôte de suivi le se connecte à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration de BizTalk pour créer un nouveau groupe BizTalk à partir de ce serveur.|  
|Utilisateur connecté|Base de données des suivis|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données|  
|Utilisateur connecté|Base de données MessageBox|SQL|1433|TCP|Mise à jour et récupération d'informations de la base de données|  
|Utilisateur connecté|Base de données MessageBox|DTC|135|TCO|Connexion traitée à SQL Server|  
|Utilisateur connecté|Base de données MessageBox|DTC|50000-50200||Ports RPC secondaires|  
|Utilisateur connecté|Base de données des archives de l'analyse BAM|SQL Server|1433|TCP|Pour mettre à jour et récupérer des informations à partir de la base de données **Remarque :** hôte de suivi le se connecte à cette base de données uniquement lorsque vous exécutez le Gestionnaire de Configuration de BizTalk pour créer un nouveau groupe BizTalk à partir de ce serveur.|  
|Compte de service SSO|Base de données SSO|SQL Server|1433|TCP|Mise à jour et récupération d'informations de la base de données|  
|Compte de service SSO|Serveur de secret principal|Service de secret principal|135|TCP|Connexion traitée à SQL Server pour que le service SSO puisse se connecter au serveur de secret principal|  
|Compte de service SSO|Serveur de secret principal|RPC secondaire|50000-50200|TCP|Ports RPC secondaires pour que le service SSO puisse se connecter au serveur de secret principal|  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de serveur](../core/server-naming-conventions.md)   
 [Considérations sur la sécurité des messages et le suivi des instances de données](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)   
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)