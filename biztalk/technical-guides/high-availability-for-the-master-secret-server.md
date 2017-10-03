---
title: "Haute disponibilité pour le serveur de secret principal | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b99cb04-61a5-41cc-a409-35897c17b789
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4c8c18f394b800ffeee9994294b2d2dbf0cb3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-for-the-master-secret-server"></a>Haute disponibilité pour le serveur de secret principal
Même si vous n’utilisez pas la fonctionnalité Enterprise Single Sign-On (SSO) pour le mappage des informations d’identification et l’authentification unique, l’authentification unique est un élément essentiel de la Microsoft global [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] infrastructure, car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l’authentification unique pour protéger les informations de port configuration. Les données de configuration de port sont chiffrées et stockées dans la base de données SSO. Chaque serveur BizTalk server est un service d’authentification unique (ENTSSO.exe) qui est utilisé pour chiffrer et déchiffrer les données de configuration du port.  
  
 Démarre un service d’authentification unique, il récupère la clé de chiffrement à partir du serveur de secret principal. Cette clé de chiffrement est appelée le secret principal. Le serveur de secret principal est un autre service d’authentification unique qui a un sous-service supplémentaire qui gère et distribue le secret principal. Après la récupération d’un secret, le service SSO met en cache. Toutes les 60 secondes, le service SSO synchronise le secret principal avec le serveur de secret principal.  
  
 Si le serveur de secret principal échoue et que le service SSO détecte la défaillance de l’une de ses intervalles d’actualisation, le service d’authentification unique et toutes les opérations d’exécution en cours d’exécution avant que le serveur a échoué, y compris le déchiffrement des informations d’identification, se poursuivent normalement. Toutefois, vous ne peut pas chiffrer les données de configuration de port ou de nouvelles informations d’identification. Par conséquent, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement comporte une dépendance sur la disponibilité du serveur de secret principal.  
  
## <a name="making-the-master-secret-server-available"></a>Obtention d'un serveur de secret principal disponible  
 Pour la disponibilité du système SSO et donc du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, il est essentiel de sauvegarder le secret principal dès qu’il est généré. Sinon, vous perdez les données que le système d'authentification unique a chiffrées à l'aide de ce secret principal. Pour plus d’informations sur la sauvegarde du secret, consultez [comment revenir Up the Master Secret](http://go.microsoft.com/fwlink/?LinkID=151934) (http://go.microsoft.com/fwlink/?LinkID=151934) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Vous pouvez rendre le secret principal disponible de deux manières :  
  
-   **Disponibles, mais pas très**. Vous pouvez créer un événement de Microsoft System Center Operations Manager pour vous avertir lorsque le serveur de secret principal devient indisponible et vous pouvez promouvoir manuellement un autre serveur d’authentification unique pour le serveur de secret principal et restaurer le secret sur ce serveur.  
  
     Bien que cette configuration n’est pas hautement disponible, elle est suffisante pour la plupart des scénarios et il est cohérent avec la mise à l’échelle des hôtes de réception, envoi et de traitement.  
  
-   **Haute disponibilité**. Pour disposer d'un serveur de secret principal redondant, utilisez le clustering Windows sur un cluster de serveur de secret principal distinct ou configurez le serveur de secret principal sur un cluster de bases de données existant. Lorsqu'ils sont installés sur un cluster de base de données, les services fournis par le serveur de secret principal n'utilisent pas beaucoup de ressources et n'ont généralement pas d'impact sur la fonctionnalité de base de données ou sur les performances. Le schéma suivant illustre la façon dont vous pouvez rendre le serveur de secret principal hautement disponible.  
  
     ![Serveur de secret principal hautement disponible](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")  
  
     Bien que cette configuration permette une disponibilité élevée, elle exige de disposer de ressources matérielles supplémentaires. Pour plus d’informations sur les options d’installation de haute disponibilité pour l’authentification unique, consultez [Options d’Installation de l’authentification unique de haute disponibilité](http://go.microsoft.com/fwlink/?LinkId=156838) (http://go.microsoft.com/fwlink/?LinkId=156838) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
     Cette section comprend des informations détaillées sur la configuration du serveur de secret principal SSO en tant que ressource de cluster à haute disponibilité sur un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster.  
  
    > [!NOTE]  
    >  Pour réduire les ressources matérielles pour une solution hautement disponible, vous pouvez ajouter le serveur de secret principal en tant que ressource de cluster dans votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster. Notez que vous ne souhaitez pas acheter supplémentaires [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] licences pour l’installation de l’authentification unique de service sur l’ordinateur exécutant SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Clustering du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md)  
  
-   [Désignation d’un nouveau serveur de secret principal manuellement](../technical-guides/designating-a-new-master-secret-server-manually.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Planification pour une haute disponibilité2](../technical-guides/planning-for-high-availability2.md)   
 [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)