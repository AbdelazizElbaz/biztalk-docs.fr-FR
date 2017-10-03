---
title: "Installation d’ordinateur de développeur pour le Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developer servers
- service solution tutorial, deployment prerequisites
- service solution tutorial, developer servers
ms.assetid: a088696f-c1ee-4578-ac02-af29b6de086b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb3407dbccbc4dccc902892cf04fa71991b8d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developer-machine-setup-for-the-service-oriented-solution"></a>Installation de l'ordinateur de développement pour la solution orientée services
L'architecture orientée services (SOA) est une approche de la génération de systèmes distribués. La solution orientée services montre comment plusieurs systèmes principaux utilisant différents protocoles peuvent être agrégés en un service unique que les clients peuvent consommer. Cette solution intègre les services avec une approche qui garantit les caractéristiques de fourniture et de performance pour l'accord de niveau de service que vous devez respecter.  
  
 La solution orientée services est modélisée selon un scénario d'accord de niveau de service où BizTalk Server et les serveurs d'applications métier (LOB) qui y sont connectés ont trois secondes pour répondre avec une demande de service. L'une de ces trois secondes peut être utilisée par BizTalk Server.  
  
 Il existe trois versions de la solution orientée services : adaptateur, inline et stub. Pour plus d’informations sur les différences entre les trois versions de la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md). En tant que développeur, vous mettez en œuvre le scénario à l'aide de la version stub de ce dernier. Cette version ne nécessite pas de serveurs principaux métier pour l'exécution. Après cela, vous pouvez utiliser la version adaptateur du scénario pour savoir comment les divers adaptateurs et serveurs principaux peuvent être intégrés et configurés pour répondre en utilisant les serveurs BizTalk en tant que service unique. Vous pouvez ensuite mesurer la latence induite par BizTalk Server et ses adaptateurs.  
  
 Si la latence du serveur BizTalk dépasse la configuration requise pour le service, vous contourner ignorer les points de persistance de l'adaptateur métier en installant et en exécutant la version inline de l'architecture orientée services. Cette version contourne les adaptateurs et, par la suite, leurs contributions à la latence en raison du point de persistance MessageBox. Au lieu de cela, la version inline communique directement avec les serveurs principaux au travers de mécanismes RPC (appel de procédure distante), tels que DCOM.  
  
 Pour plus d’informations sur le point de persistance MessageBox, consultez [persistance et le moteur d’Orchestration](../core/persistence-and-the-orchestration-engine.md).  
  
 Ce guide de déploiement décrit comment installer et tester les trois versions de la solution orientée services sur un ordinateur unique.  
  
 Pour plus d’informations sur la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md)  
  
-   [Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)  
  
-   [Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)  
  
-   [Pour exécuter le Service Solution orientée services](../core/how-to-run-the-service-oriented-solution.md)