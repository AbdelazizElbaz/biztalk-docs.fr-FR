---
title: "Architecture réduite avec des Services destinés aux travailleurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
ms.assetid: ce1217bf-84a5-4888-89ba-dce85dc38340
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d02558e5904bf740c09ea0db614b2189555ac75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-down-architecture-with-information-worker-services"></a>Architecture réduite avec des services destinés aux travailleurs de l'information
Pour plus d’informations sur l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 La figure suivante fournit un exemple d'architecture BizTalk Server incluant les services destinés aux travailleurs de l'information et qui combine certains domaines et serveurs BizTalk Server pour réduire le nombre de serveurs et de pare-feu nécessaires. Bien que cette architecture ne soit pas la plus distribuée, elle différencie toujours les serveurs BizTalk Server selon leur fonction.  
  
 ![Topologie de réduction](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")  
  
        Scaled Down Architecture with Information Worker Services  
  
 Dans la figure précédente, les serveurs des interfaces de service et du domaine des services correspondent aux hôtes BizTalk, et non aux serveurs physiques. Même s'il est recommandé de conserver le serveur de secret principal et les outils d'administration dans des ordinateurs isolés, vous pouvez avoir des instances d'hôte pour le suivi, le traitement, l'envoi et la réception des hôtes exécutés sur plusieurs ordinateurs. De même, les serveurs du réseau de périmètre correspondent aux emplacements logiques.  
  
 Les serveurs du réseau de périmètre pour SMTP, Windows Message Queuing (également nommé MSMQ), File et SQL correspondent respectivement aux serveurs de messagerie, à la file d'attente, au répertoire et aux serveurs SQL Server à partir desquels les hôtes de BizTalk reçoivent et envoient des messages dans le domaine des interfaces de service.  
  
 Les bases de données BAM du domaine de données sont les bases de données d'importation principale BAM, d'analyse BAM, de schémas en étoile BAM et des archives BAM. BizTalk Server utilise les bases de données d'analyse et des suivis du domaine de données pour le stockage des informations de suivi.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture réduite](../core/scaled-down-architecture.md)   
 [Architecture distribuée avec des Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)