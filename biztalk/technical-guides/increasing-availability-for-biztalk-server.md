---
title: "Augmentation de la disponibilité de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72d9ce5e-d775-4f8e-b1a4-bf3c7c05f571
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa48d7dada00ebadf089834f5025f3fdfdf25070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="increasing-availability-for-biztalk-server"></a>Augmentation de la disponibilité de BizTalk Server
Cette section décrit les manières d’accroître la disponibilité de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  
  
## <a name="strategies-for-increasing-availability"></a>Stratégies permettant d’accroître la disponibilité  
 Les stratégies pour augmenter la disponibilité sont les suivantes :  
  
-   **Haute disponibilité à l’aide du clustering de serveurs Windows Server 2003 ou le clustering de basculement Windows Server 2008**. Un cluster de serveur ou de basculement est un groupe d’ordinateurs indépendants, appelés nœuds, qui fonctionnent ensemble comme un système unique pour garantir que les ressources et applications critiques restent disponibles pour les clients. Si un des nœuds devient indisponible en raison d’exigences de temps mort de défaillance ou de maintenance, un autre nœud commence immédiatement à fournir un service (processus appelé basculement).  
  
    -   Un cluster de serveur ou de basculement est généralement recommandé pour les ordinateurs exécutant SQL Server ce centre le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
    -   Un cluster de serveurs peut-être être nécessaires pour fournir une haute disponibilité pour certains adaptateurs BizTalk.  
  
    -   Un cluster de serveurs est généralement recommandé pour Enterprise Single Sign-On serveur de secret principal.  
  
-   **Haute disponibilité à l’aide d’un formulaire d’équilibrage de charge**.  
  
    -   Équilibrage de charge réseau. Équilibrage de charge réseau offre une disponibilité élevée en redirigeant le trafic réseau entrant à l’utilisation des ordinateurs hôtes du cluster NLB si un hôte échoue ou est hors connexion. Contrairement aux clusters de serveurs, équilibrage de charge réseau ne nécessite pas de matériel spécial.  
  
    -   L’équilibrage de charge hôte BizTalk. L’équilibrage de charge hôte BizTalk est fournie pour les hôtes BizTalk en ajoutant plusieurs serveurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe, puis en configurant plusieurs instances d’un hôte in-process pour s’exécuter sur ces serveurs. Cela répartit l'exécution des services et des artefacts configurés dans cet hôte sur plusieurs instances de l'hôte, ce qui améliore sa disponibilité et son évolutivité.  
  
        > [!NOTE]  
        >  Fonctionnalité d’équilibrage de la charge d’hôte est disponible pour les hôtes in-process uniquement.  
  
    -   L’équilibrage de charge est fournie pour les disques de SQL Server via l’utilisation d’un réseau SAN ou en ajoutant plusieurs bases de données MessageBox.  
  
-   Stratégies permettant de **disponibilité renforcée**. Ces stratégies de fournissent une disponibilité accrue mais généralement nécessite également un administrateur d’effectuer une ou plusieurs actions lors de l’exécution. Par conséquent, ces stratégies sont généralement considérés comme fournissant une disponibilité accrue par opposition à haute disponibilité :  
  
    -   Augmenter la disponibilité à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journal expédition et récupération d’urgence.  
  
    -   Augmentation de la disponibilité via l’implémentation de surveillance approprié et des stratégies de maintenance.  
  
## <a name="difference-between-clustering-and-disaster-recovery"></a>Différence entre la gestion de clusters et la récupération d’urgence  
 Alors que les clusters et la récupération d’urgence augmentent la disponibilité, une différence essentielle entre eux est que les clusters offrent généralement des temps de récupération beaucoup plus rapide que la récupération d’urgence ne. Par conséquent, une solution reposant sur des clusters de serveur ou de basculement ou l’équilibrage de charge est généralement considéré comme offrant une haute disponibilité au lieu de simplement fournir disponibilité.  
  
 Récupération d’urgence vous permet de reprendre le fonctionnement d’un système ayant échoué, mais est généralement un processus manuel et nécessite plus de temps de récupération à une implémentation de la haute disponibilité. Par conséquent, une implémentation de la récupération d’urgence fournit la disponibilité, mais pas une haute disponibilité. Vous devez utiliser à la fois haute disponibilité via des clusters de serveur ou de basculement et équilibrage de charge et disponibilité grâce à la récupération d’urgence, dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Haute disponibilité](../technical-guides/providing-high-availability.md)  
  
-   [Récupération d’urgence](../technical-guides/disaster-recovery.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)   
 [Liste de vérification : Accroître la disponibilité avec la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)