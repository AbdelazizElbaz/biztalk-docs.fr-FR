---
title: "Ports pour l’entreprise unique de serveurs d’authentification | Documents Microsoft"
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, SSO
- SSO
ms.assetid: 30eb99f9-02cb-43c9-b038-d7bd898e3a7a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0335a6a09cb8d323261c2d8357cc3d5b929b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-enterprise-single-sign-on-servers"></a>Ports des serveurs d'authentification unique de l'entreprise
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports dont un serveur d'authentification unique de l'entreprise dans le domaine de traitement a besoin pour accéder au serveur de secret principal et à la base de données SSO. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Utilisateur connecté|Base de données SSO|SQL Server|1433|TCP|Créer et établir la connexion à la base de données SSO|  
|Compte du service SSO|Serveur de secret principal|Service d'authentification unique|135|TCP|Connexion traitée à SQL Server permettant au service d'authentification unique de récupérer la clé du secret principal auprès du serveur de secret principal|  
|Compte du service SSO|Serveur de secret principal|Service d'authentification unique|50000-50200|TCP|Ports RPC secondaires utilisés pour récupérer la clé du secret auprès du serveur de secret principal **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour permettre au serveur de secret principal SSO d'accéder aux services dont il a besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. Vous devez ouvrir ces ports aux trafics entrant et sortant.  
  
|Contexte du service ou de l'application|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Utilisateur connecté|Base de données SSO|SQL Server|1433|TCP|Créer et établir la connexion à la base de données SSO|  
|Compte du service SSO|Serveur(s) de traitement|Service d'authentification unique|135|TCP|Connexion traitée à SQL Server permettant au service d'authentification unique de récupérer la clé du secret principal auprès du serveur de secret principal|  
|Compte du service SSO|Serveur(s) de traitement|Service d'authentification unique|50000-50200|TCP|Ports RPC secondaires utilisés pour récupérer la clé du secret auprès du serveur de secret principal **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de serveur](../core/server-naming-conventions.md)   
 [Recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)