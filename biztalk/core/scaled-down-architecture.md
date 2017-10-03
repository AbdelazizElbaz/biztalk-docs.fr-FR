---
title: "Architecture réduite | Documents Microsoft"
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
ms.assetid: e25798aa-4a1e-418c-9e0c-db964e8b5a80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a112f3f737a1a5aec0cfac16b7689d3dada1e8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-down-architecture"></a>Architecture réduite
Pour plus d’informations sur l’architecture système pour[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 La figure suivante fournit un exemple d'architecture [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui combine certains domaines et serveurs BizTalk pour réduire le nombre de serveurs et de pare-feu nécessaires. Bien que cette architecture ne soit pas la plus distribuée, elle différencie toujours les serveurs BizTalk Server selon leur fonction.  
  
 ![Architecture réduite](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")  
  
        Scaled Down Architecture  
  
 Dans la figure précédente, les serveurs des interfaces de service et du domaine des services correspondent aux hôtes BizTalk, et non aux serveurs physiques. Même s'il est recommandé de conserver le serveur de secret principal et les outils d'administration dans des ordinateurs isolés, vous pouvez avoir des instances d'hôte pour le suivi, le traitement, l'envoi et la réception des hôtes exécutés sur plusieurs ordinateurs. De même, les serveurs du réseau de périmètre correspondent aux emplacements logiques.  
  
 Les serveurs du réseau de périmètre pour SMTP, Message Queuing, FILE, et SQL correspondent respectivement aux serveurs de messagerie, à la file d'attente, au répertoire et aux serveurs SQL Server à partir desquels les hôtes BizTalk envoient et reçoivent des messages dans le domaine des services.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture réduite avec des Services destinés aux travailleurs](../core/scaled-down-architecture-with-information-worker-services.md)   
 [Architecture distribuée](../core/large-distributed-architecture.md)   
 [Conception d’une Architecture sécurisée](../core/designing-a-secure-architecture.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)