---
title: "Résultats des tests : Indicateurs de Performance clés de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 902cdfc1-21ab-4f56-b97b-2f8979514b11
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1205b0ca8a3fa502df1616900bd112546c5b5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-results-biztalk-server-key-performance-indicators"></a>Résultats des tests : Indicateurs de Performance clés de BizTalk Server
Cette rubrique résume BizTalk Server Performance indicateurs clés (KPI) observé sur les scénarios de test. Plus précisément, ces tests évaluée débit mesuré par la «**BizTalk : messagerie/Documents traités par seconde**« compteur Analyseur de performances et la latence, telle que mesurée par le temps de réponse du client Visual studio.  
  
## <a name="summary-of-biztalk-server-key-performance-indicators"></a>Résumé des indicateurs de Performance clés de BizTalk Server  
 Pour chaque scénario, les machines physiques étaient limités afin que le nombre de processeurs logiques et les processeurs virtuels était équivalent. Cela a été effectuée à l’aide des commutateurs /maxmem et/NUMPROC du fichier boot.ini. Pour plus d’informations sur l’utilisation de ces commutateurs, consultez « Démarrage INI Options référence » à [http://go.microsoft.com/fwlink/?LinkId=122139](http://go.microsoft.com/fwlink/?LinkId=122139).  
  
 **Comparaison des indicateurs de Performance clé BizTalk Server –** en cours d’exécution [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur Hyper-V virtual machine fourni environ 95 % des performances de débit et la latence [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur du matériel physique pour ce scénario de test. En raison de la nature sans état de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]supplémentaires [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] machines virtuelles peuvent être facilement ajoutés à l’environnement comme requis pour fournir la montée en puissance parallèle et améliorer les performances générales du système. Création et ajout de supplémentaires [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’environnement peut être effectuée à l’aide de l’utilitaire sysprep pour générer de nouvelles images à partir d’une image de base.  
  
> [!NOTE]  
>  Un fichier de réponses sysprep et les scripts sont fournies avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] pour s’adapter à l’aide de sysprep pour créer des images supplémentaires à partir d’une image existante d’un ordinateur qui a [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installé. Ces exemples de scripts sont conçus pour une utilisation avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installé sur 32 bits et 64 bits uniquement les versions de Windows Server 2008. Pour plus d’informations, consultez le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation en ligne.  
  
 Mise en service, la consolidation et la gestion des ordinateurs virtuels peuvent être considérablement accélérés via l’utilisation de System Center Virtual Machine Manager (VMM). Pour plus d’informations sur System Center Virtual Machine Manager, consultez [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303)  
  
 Les résultats obtenus dans ce laboratoire de performances montrent une amélioration marquée à partir des performances obtenue lors de l’exécution [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] sur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] dans un ordinateur virtuel Hyper-V. En cours d’exécution [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] sur Hyper-V virtual machine fourni environ 75 % des performances de débit et la latence [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] sur du matériel physique et l’environ 95 % performances observées lors de l’exécution [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] sur les ordinateurs virtuels Hyper-V. Ces performances accrues est en grande partie imputable à l’amélioration des performances de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] lors de l’exécution en tant que système d’exploitation invité sur Hyper-V. La comparaison des performances connexes à partir de la [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] guide Hyper-V est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=147144](http://go.microsoft.com/fwlink/?LinkId=147144).  
  
 Le graphique ci-dessous illustre les performances de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur les différentes plateformes de test :  
  
 ![Les indicateurs de Performance clés BizTalk](../technical-guides/media/biztalkkpi.gif "BizTAlkKPI")  
  
 Le tableau ci-dessous illustre les performances relatives de l’indicateur collectées pour chaque configuration. Chaque jeu de résultats est calculée en pourcentage de la configuration de base indicateur de performance clé.  
  
|Indicateur de performance clé|Virtuel BizTalk/physiques SQL|Virtuel BizTalk/virtuel SQL sur des hôtes distincts|Virtuel SQL BizTalk/virtuel dans l’environnement de consolidé|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\BizTalk:Messaging\Documents traitées par seconde|94.3%|79.8%|67%|  
|Latence telle que mesurée par le client Visual Studio|94.3%|79.7%|66.9%|  
  
 Pour plus d’informations sur la façon d’optimiser les performances d’une solution BizTalk Server, consultez le Guide des optimisations BizTalk Server performances disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=122477](http://go.microsoft.com/fwlink/?LinkId=122477).  
  
## <a name="performance-comparison-results-summary"></a>Résumé de résultats de comparaison de performances  
 Le débit de 94.3 % et la latence de 94.3 % obtenue lors de l’exécution uniquement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur Hyper-V suggère que la virtualisation de ce niveau de votre solution à l’aide de Hyper-V procure d’excellentes performances avec la mise en service, consolidation, flexibilité et facilité de gestion qui sont possibles lors du déploiement de solutions dans un environnement Hyper-V.  
  
### <a name="throughput-comparison-sample-results"></a>Exemples de comparaison de débit résultats  
 Lorsque le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs utilisés dans l’environnement BizTalk Server ont été exécutées sur des machines virtuelles de Hyper-V, débit de la solution BizTalk Server, telle que mesurée par le «**BizTalk : messagerie/Documents traités par seconde**» compteur du moniteur de performances comprise 67 % % 94.3 du débit réalisable lorsque tous les ordinateurs utilisés dans l’environnement BizTalk Server ont été installés sur du matériel physique.  
  
### <a name="latency-comparison-sample-results"></a>Exemples de comparaison de latence résultats  
 Lorsque le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs utilisés dans l’environnement BizTalk Server ont été exécutées sur des machines virtuelles de Hyper-V, la latence de la solution BizTalk Server, telle que mesurée par la réponse du client Visual Studio temps comprise 66.9 % et % 94.3 de la latence atteignables lorsque toutes les les ordinateurs utilisés dans l’environnement BizTalk Server ont été installés sur du matériel physique.