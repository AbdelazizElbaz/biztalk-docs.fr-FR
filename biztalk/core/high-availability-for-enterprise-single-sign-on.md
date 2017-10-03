---
title: "Haute disponibilité pour Enterprise Single Sign-On | Documents Microsoft"
ms.custom: 
ms.date: 2016-02-29
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, availability
- high availability, SSO
- Master Secret server, high availability
- SSO, high availability
ms.assetid: 6c631b5c-7147-4cc0-b58a-6749e83df9d3
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 023eaa82b11353347040dea13fc126f6044db3bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-enterprise-single-sign-on"></a>Haute disponibilité appliquée à l'authentification unique de l'entreprise
Même si vous n'utilisez pas la fonctionnalité d'authentification unique de l'entreprise pour mapper les informations d'identification et l'authentification unique, cette fonctionnalité constitue un élément essentiel de l'infrastructure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] puisque BizTalk Server s'en sert pour sécuriser les informations présentes sur les emplacements de réception.  
  
 Vous devez configurer le premier ordinateur où vous installez le service d'authentification unique en tant que serveur de secret principal. Le serveur de secret principal est le serveur d'authentification unique qui stocke le secret principal (clé de chiffrement). Celui-ci correspond à la clé de chiffrement utilisée par le système d'authentification unique pour chiffrer et déchiffrer les données stockées dans la base de données de l'authentification unique.  
  
 Si un serveur d'authentification unique s'arrête et que vous disposez d'autres ordinateurs serveurs BizTalk Server exécutant la même instance d'hôte, donc d'autres serveurs d'authentification unique, ces serveurs supplémentaires continuent de fonctionner normalement. Par conséquent, le serveur de secret principal continue de remplir ses fonctions et les processus BizTalk Server ne sont pas interrompus.  
  
 Si le serveur de secret principal s'arrête, toutes les opérations en cours d'exécution au moment de la panne, y compris le déchiffrement des informations d'identification, continuent de s'exécuter correctement. Cependant, vous ne pouvez pas chiffrer les nouvelles informations d'identification. L'environnement BizTalk Server est donc dépendant de la disponibilité du serveur de secret principal, comme l'indique le schéma suivant :  
  
 ![Points de défaillance](../core/media/tdi-highava-pointsfailure-mss.gif "TDI_HighAva_PointsFailure_MSS")  
  
> [!NOTE]
>  Lorsque le serveur de secret principal devient indisponible, les instances d'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent encore effectuer des opérations d'exécution à l'aide de la copie du secret principal mise en mémoire cache jusqu'à ce que :  
>   
>  -   les instances d'hôte soient redémarrées ;  
> -   le service de l'authentification unique se trouvant sur l'ordinateur qui exécute les instances d'hôte BizTalk soit redémarré ;  
> -   le secret principal de l'authentification unique soit modifié.  
>   
>  Si le service de l'authentification unique est redémarré sur les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou si le secret principal de l'authentification unique est modifié, la copie du secret principal mise en mémoire cache est libérée et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit alors être en mesure de contacter le serveur de secret principal dans le but de récupérer une autre copie du secret principal. Si le serveur de secret principal n'est pas disponible, toute opération administrative qui nécessite l'accès à ce serveur à des fins de chiffrement échoue.  
  
## <a name="making-the-master-secret-server-available"></a>Obtention d'un serveur de secret principal disponible  
 Pour obtenir la disponibilité d'un système d'authentification unique, donc d'un environnement BizTalk Server, il est indispensable de sauvegarder le secret principal dès qu'il a été généré. Sinon, vous perdez les données que le système d'authentification unique a chiffrées à l'aide de ce secret principal. Pour plus d’informations sur la sauvegarde du secret, consultez [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
 Vous pouvez rendre le secret principal disponible de deux manières :  
  
-   **Disponible, mais pas hautement disponible.** dans cette configuration, le secret principal est mis en mémoire cache pour tous les serveurs d'authentification unique et les opérations d'exécution fonctionnent normalement, même en cas de défaillance du serveur de secret principal. Cependant, vous ne pouvez plus modifier la configuration des ports ou de l'authentification unique. L'exécution de BizTalk Server ne rencontre pas de problèmes, mais aucune modification de la conception n'est possible.  
  
     Bien que cette configuration ne permette pas une disponibilité élevée, elle est suffisante dans la plupart des scénarios et compatible avec la mise à l'échelle des hôtes de réception, d'envoi et de traitement.  
  
-   **Hautement disponible.** Pour disposer d'un serveur de secret principal redondant, utilisez le clustering Windows sur un cluster de serveur de secret principal distinct ou configurez le serveur de secret principal sur un cluster de bases de données existant. Lorsqu'ils sont installés sur un cluster de base de données, les services fournis par le serveur de secret principal n'utilisent pas beaucoup de ressources et n'ont généralement pas d'impact sur la fonctionnalité de base de données ou sur les performances. Le schéma suivant illustre la façon dont vous pouvez rendre le serveur de secret principal hautement disponible.  
  
     ![Serveur de secret principal hautement disponible](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")  
  
     Bien que cette configuration permette une disponibilité élevée, elle exige de disposer de ressources matérielles supplémentaires. Pour plus d’informations sur les options d’installation de haute disponibilité pour l’authentification unique, consultez [Options d’Installation de l’authentification unique de haute disponibilité](../core/high-availability-sso-installation-options.md). Cette section fournit des informations détaillées sur la configuration du serveur de secret principal de l'authentification unique en tant que ressource de cluster à haute disponibilité sur un cluster de serveurs Windows Server.  
  
    > [!NOTE]
    >  Afin de réduire les ressources matérielles nécessaires à une solution hautement disponible, vous pouvez ajouter le serveur de secret principal en tant que ressource de cluster sur le cluster SQL Server. Vous n’avez pas besoin d’acheter des licences supplémentaires pour installer le service d’authentification unique sur un autre ordinateur BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)   
 [Création d’un environnement hautement disponible BizTalk Server](../core/creating-a-highly-available-biztalk-server-environment.md)   
 [Mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md)