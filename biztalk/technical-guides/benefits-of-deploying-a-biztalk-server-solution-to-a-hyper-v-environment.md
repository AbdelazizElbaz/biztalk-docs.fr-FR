---
title: "Les avantages potentiels de déploiement d’une Solution BizTalk Server sur un Hyper-V virtualisé environnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 588c70f0-68f0-4e58-8f3d-aa6834397bd4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9602a48b0deb4eeddc6f10b2d529d68d94cc781a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="potential-benefits-of-deploying-a-biztalk-server-solution-to-a-hyper-v-virtualized-environment"></a>Environnement de virtualiser les avantages potentiels de déploiement d’une Solution BizTalk Server sur un Hyper-V
Cette rubrique décrit certains des avantages du déploiement de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution vers un environnement virtualisé Hyper-V.  
  
## <a name="benefits-of-running-a-biztalk-server-solution-on-a-hyper-v-virtualized-environment"></a>Avantages de l’exécution d’une Solution BizTalk Server sur un Hyper-V virtualisé environnement  
 Le déploiement de votre solution BizTalk Server s’exécute sur un environnement virtualisé Hyper-V offre la souplesse et les fonctionnalités suivantes :  
  
-   **Possibilité de définir plusieurs limites de sécurité logique distinct sur un seul ordinateur physique -** Hyper-V prend en charge la création de limites de sécurité logique distinct ou partitions au sein d’une ressource de matériel physique unique. Une partition est une unité logique d’isolation, pris en charge par l’hyperviseur, dans laquelle s’exécutent les systèmes d’exploitation. Par exemple, vous pouvez créer plusieurs groupes BizTalk Server pour s’exécuter sur un seul ordinateur hôte de Hyper-V, alors que vous ne serez pas en mesure de faire cela lors de l’installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le système d’exploitation d’un seul ordinateur hôte.  
  
-   **Facilité de déploiement et de gestion –** la Consolidation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs en moins de serveurs physiques simplifie le déploiement. [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]utilise une méthode simplifiée pour les déploiements d’ordinateurs physiques et virtuels à l’aide de fichiers .vhd. En outre, une solution complète de gestion Hyper-V est disponible avec System Center Virtual Machine Manager. Pour plus d’informations sur System Center Virtual Machine Manager, consultez [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).  
  
-   **Erreur de prise en charge de la tolérance de panne via le clustering Hyper-V -** , car Hyper-V est une application prenant en charge les clusters, Windows Server 2008 fournit hôte natif clustering prise en charge des ordinateurs virtuels créés dans un environnement virtualisé Hyper-V.  
  
-   **Facilité de montée en puissance parallèle -** puissance de traitement supplémentaire, la bande passante réseau et la capacité de stockage pouvant être utilisés pour votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution rapidement et facilement à répartir des ressources supplémentaires disponibles à partir de l’ordinateur hôte à l’invité ordinateurs virtuels. Cette opération peut nécessiter que l’ordinateur hôte est mis à niveau ou que les ordinateurs virtuels invités sont déplacés vers un ordinateur hôte plus performante. La fonctionnalité de migration dynamique de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] vous permet de déplacer des machines virtuelles s’exécutant à l’ordinateur physique meilleures performances, la mise à l’échelle ou la consolidation optimale sans impacter les utilisateurs.  
  
-   **Consolidation des ressources matérielles -** plusieurs serveurs physiques peuvent être facilement consolidées dans relativement moins de serveurs par l’implémentation de la virtualisation avec Hyper-V. Consolidation prend en charge pleinement parti des ressources matérielles déployé.  
  
 Pour plus d’informations détaillées fournissent des informations sur les fonctionnalités et avantages Hyper-V, consultez [virtualisation avec Hyper-V](http://go.microsoft.com/fwlink/?LinkID=202438).