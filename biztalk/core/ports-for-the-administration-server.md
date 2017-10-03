---
title: "Ports pour le serveur d’Administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, administration server
- administration server
ms.assetid: dc0094b2-5ba2-4b8f-84aa-b6232be358ee
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd44158d721f8b6d247b51073e9f9e77ea7f6deb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-administration-server"></a>Ports pour le serveur d’administration
Pour plus d’informations sur la sécurisation de votre déploiement BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 Le tableau suivant répertorie les ports que vous devez configurer pour que le serveur d'administration puisse accéder aux services dont il a besoin. Le pare-feu pour lequel vous devez ouvrir les ports dépend de l'emplacement du serveur de destination au sein de votre architecture. 
  
|Serveur de destination|Service de destination|Port|Protocole|Reason|  
|---|---|---|---|---|  
|Base de données de gestion BizTalk|SQL Server|1433|TCP|Pour créer, configurer et accéder aux informations de la base de données de gestion BizTalk|  
|Base de données de gestion BizTalk|DTC|135|TCP|Connexion traitée à SQL Server à des fins mise à jour de la base de données|  
|Base de données de gestion BizTalk|DTC|50000-50200|TCP|Ports RPC secondaires **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Base de données d'importation principale BAM|SQL Server|1433|TCP|Pour vérifier l'existence de la base de données d'importation principale BAM à l'aide de la console Administration de BizTalk (ou WMI)|  
|Base de données de gestion BizTalk|SQL Server|1433|TCP|Pour afficher les données de configuration et installer les instances d'hôte à l'aide de la console Administration de BizTalk (ou WMI)|  
|Base de données de gestion BizTalk|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création et de mise à jour de l'hôte à l'aide de la console Administration de BizTalk (ou WMI)|  
|Base de données de gestion BizTalk|DTC|50000-50200|TCP|Ports RPC secondaires pour créer un hôte à l’aide de la console Administration de BizTalk (ou WMI) **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Base de données MessageBox|SQL Server|1433|TCP|Pour créer un hôte à l'aide de la console Administration de BizTalk (ou WMI)|  
|Base de données MessageBox|DTC|135|TCP|Connexion traitée à SQL Server à des fins de création et de mise à jour de l'hôte à l'aide de la console Administration de BizTalk (ou WMI)|  
|Base de données MessageBox|DTC|50000-50200|TCP|Ports RPC secondaires pour créer un hôte à l’aide de la console Administration de BizTalk (ou WMI) **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Serveur de traitement|WMI/RPC|135|TCP|Connexion traitée à SQL Server pour ajouter un nouveau serveur au groupe à l'aide de la console Administration de BizTalk (ou WMI)|  
|Serveur de traitement|WMI/RPC|50000-50200|TCP|Ports RPC secondaires pour ajouter un nouveau serveur au groupe à l’aide de la console Administration de BizTalk (ou WMI) **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Serveur de traitement|SMB (Server Message Block)|445|TCP|Permet d’accéder aux partages de fichiers. Peut également être nécessaire pour installer une instance d’hôte à l’aide de la console Administration de BizTalk (ou WMI).|  
|Base de données du moteur des règles d'entreprise|SQL Server|1433|TCP|Pour déployer des règles d'entreprise à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise|  
|Base de données du moteur des règles d'entreprise|DTC|135|TCP|Connexion traitée à SQL Server à des fins de déploiement de règles d'entreprise à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise|  
|Base de données du moteur des règles d'entreprise|DTC|50000-50200|TCP|Ports RPC secondaires pour déployer des règles d'entreprise à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise **Remarque :** vous devrez peut-être ouvrir davantage de ports RPC secondaires en fonction de la charge du serveur.|  
|Base de données de gestion BizTalk|SQL Server|1433|TCP|Pour déployer un assembly|  
|Base de données des suivis|SQL Server|1433|TCP|Pour déployer un assembly|  
|Serveur IIS|IIS|1164|TCP|Pour activer le déploiement d’application BizTalk à pack HTTP ou des Ports de Service Web hébergé sur le serveur IIS dans un fichier MSI.|  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de serveur](../core/server-naming-conventions.md)   
 [Recommandations de sécurité de déploiement application](../core/application-deployment-security-recommendations.md)   
 [Considérations sur la sécurité des messages et le suivi des instances de données](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md)