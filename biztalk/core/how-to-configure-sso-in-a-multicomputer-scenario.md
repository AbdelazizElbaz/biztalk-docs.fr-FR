---
title: "Comment configurer l’authentification unique dans un scénario multiserveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, SSO
- SSO database, clustering
- clustering, Master Secret server
- SSO, configuring
- configuring, Master Secret server
- Master Secret server, clustering
- clustering, SSO database
- Master Secret server, configuring
- SSO, multiple computers
ms.assetid: 4511a03d-96f2-45f0-9891-e8b3e253499c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45bfa58c1fc11a76109f56938b8e1b43790935f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-sso-in-a-multicomputer-scenario"></a>Comment configurer l’authentification unique dans un scénario multiserveur
Cette section contient des instructions pour la configuration de l'authentification unique (SSO) de l'entreprise dans un scénario incluant trois ordinateurs.  
  
 Dans le scénario suivant, l'ordinateur A est le serveur de secret principal, l'ordinateur B est le serveur d'authentification unique et l'ordinateur C héberge la base de données SSO. L'ordinateur B peut agir comme serveur d'exécution, serveur d'administration (les sous-services d'administration de l'authentification unique utilisent ce serveur pour gérer la base de données SSO) ou serveur de mappage (les sous-services d'administration et de client de l'authentification unique utilisent ce serveur pour gérer les mappages).  
  
 Si vous souhaitez ajouter d'autres serveurs d'authentification unique à votre environnement, suivez les étapes de configuration de l'ordinateur B. Les nouveaux serveurs pointeront vers la base de données SSO existante et ne peuvent correspondre au serveur de secret principal.  
  
> [!NOTE]
>  Il est recommandé de configurer le serveur de secret principal sur un ordinateur distinct du serveur d'authentification unique et de celui hébergeant la base de données SSO.  
  
### <a name="to-configure-the-master-secret-server-and-create-the-sso-database-on-computer-a"></a>Pour configurer le serveur de secret principal et créer la base de données SSO sur l'ordinateur A  
  
1.  Effectuez une installation personnalisée de BizTalk Server et installez uniquement le composant Serveur de secret principal du système d'authentification unique de l'entreprise.  
  
2.  Exécutez l'Assistant Configuration pour configurer l'authentification unique sur le serveur de secret principal. Sur le **Questions de Configuration** page, sélectionnez l’option à **créer un nouveau système SSO**.  
  
3.  Sur le **comptes Windows** , spécifiez les informations d’identification du compte de service pour le service d’authentification unique. Vous devez être membre du groupe Administrateurs de l'authentification unique.  
  
4.  Sur le **les Configurations de base de données** , spécifiez l’emplacement de SQL Server (ordinateur C) et le nom de la base de données SSO (SSODB).  
  
5.  Indiquez les options de sauvegarde du secret principal.  
  
6.  Terminez la configuration.  
  
### <a name="to-configure-the-sso-server-on-computer-b"></a>Pour configurer le serveur d'authentification unique sur l'ordinateur B  
  
1.  Installez le service d'authentification unique de l'entreprise sur l'ordinateur B.  
  
    > [!NOTE]
    >  Il peut s'agir d'un ordinateur BizTalk Server ou Host Integration Server, d'un serveur Web ou d'un simple serveur d'authentification unique (composants d'exécution SSO).  
  
2.  Exécutez l'Assistant Configuration pour configurer l'authentification unique. Sur le **Questions de Configuration** page, sélectionnez l’option à **joindre un système SSO existant**.  
  
3.  Sur le **comptes Windows** , spécifiez les informations d’identification du compte de service pour le service d’authentification unique. Vous devez être membre du groupe Administrateurs de l'authentification unique.  
  
4.  Sur le **les Configurations de base de données** page, pointez sur l’emplacement de SQL Server (ordinateur C) et le nom de la base de données SSO (SSODB).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md)   
 [L’installation de l’authentification unique](../core/installing-sso.md)