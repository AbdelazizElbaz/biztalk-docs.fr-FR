---
title: Large Distributed Architecture with Information Worker Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- architecture, large distributions
ms.assetid: 92f2d55c-3f51-42ca-99ef-60b23464691e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6b9b1729411e089566988714b83778abac80eb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="large-distributed-architecture-with-information-worker-services"></a>Architecture distribuée étendue avec des services destinés aux travailleurs de l'information
Pour plus d’informations sur la conception de l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 L'analyse BAM (Business Activity Monitoring) assure aux travailleurs de l'information une visibilité des processus d'entreprise et une communication directe avec les partenaires. Ceci implique un ensemble d'impératifs différents pour la sécurisation de ces services. Les travailleurs de l'information ont généralement des comptes dans le domaine d'entreprise (et non dans le domaine de données) et doivent accéder au domaine des interfaces de service pour consulter certaines données générées par BizTalk Server.  
  
 La figure suivante illustre une architecture BizTalk Server distribuée qui inclut l'analyse BAM.  
  
 ![Architecture distribuée](../core/media/5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2.gif "5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2")  
Architecture BizTalk Server distribuée avec des services destinés aux travailleurs de l'information  
  
 Par rapport à l’architecture illustrée dans [Architecture distribuée](../core/large-distributed-architecture.md), l’architecture distribuée pour les services destinés aux travailleurs contient un autres services tels que le portail BAM. Le conteneur des services destinés aux travailleurs de l'information inclut les serveurs et services suivants :  
  
-   Serveur du portail BAM : les utilisateurs finaux utilisent le portail BAM pour accéder aux bases de données BAM et surveiller les indicateurs clés de performance (KPI, Key Performance Indicators) qui mesurent la progression vers un objectif professionnel et d'autres informations sur leur processus d'entreprise. Ce serveur dispose également du service Web de requêtes BAM et du service Web de gestion BAM.  
  
-   Un serveur SQL Server pour l’analyse BAM : la base de données d’importation principale BAM, base de données des archives BAM, schémas en étoile BAM et de la base de données analyse BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture distribuée](../core/large-distributed-architecture.md)   
 [Architecture réduite avec des Services destinés aux travailleurs](../core/scaled-down-architecture-with-information-worker-services.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)