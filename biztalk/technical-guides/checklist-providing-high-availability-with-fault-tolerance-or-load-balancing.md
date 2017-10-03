---
title: "Liste de vérification : Offrant une haute disponibilité avec l’équilibrage de la tolérance de panne ou de la charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c93cfc3-05b2-43ad-b0a9-b7f0d2596113
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72976dba4ed30ad6747d2d6175702110fe9730a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-providing-high-availability-with-fault-tolerance-or-load-balancing"></a>Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge
Cette rubrique répertorie les étapes que vous devez exécuter pour configurer la tolérance de panne et/ou d’équilibrage de charge pour les composants d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement offre une haute disponibilité. Configuration de la tolérance de panne de ces composants permet au système de continuer à fonctionner si un composant échoue.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Créer plusieurs instances d’hôte BizTalk et implémenter la prise en charge pour les adaptateurs qui en ont besoin de clustering de l’hôte.|[Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|Configurer les hôtes de suivi pour la haute disponibilité.|[Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|Configurer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sur un cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance sur un cluster Windows server.|[Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)|  
|Configurer les hôtes de suivi pour la haute disponibilité. Vérifiez qu’il n’y a au moins N + 1 héberger les instances avec le suivi activé où N est le nombre de bases de données MessageBox du groupe BizTalk.|Pour activer le suivi pour un ordinateur hôte, sélectionnez l’option pour **autoriser le suivi de hôte** sur la **propriétés de l’hôte** boîte de dialogue disponible à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour plus d’informations sur la définition des propriétés de hôte, consultez la rubrique [comment modifier les propriétés de l’hôte](http://go.microsoft.com/fwlink/?LinkId=154359) (http://go.microsoft.com/fwlink/?LinkId=154359).|  
|Entraîner le basculement de base de données régulièrement pour assurer la fonctionnalité de basculement.|Cette responsabilité doit être directement attribuée pour vous assurer que cette opération s’effectue de manière cohérente.|  
|Vérifier a suffisamment de puissance de traitement et de mémoire sur les nœuds de cluster passif pour activer plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances de s’exécuter simultanément dans les scénarios de basculement.|Si deux instances SQL régulièrement consomment plus 50 pour cent des ressources sur les nœuds de cluster individuels, puis lorsque les deux instances de basculent vers un nœud unique, chaque instance entraînera dégradation des performances. Par conséquent, le test doit être effectué pour vous assurer qu’un seul nœud du cluster seront en mesure de gérer la charge jusqu'à ce que le nœud défaillant est remis en ligne. Si un seul nœud ne peut pas gérer la charge des deux instances SQL songez à ajouter des nœuds de cluster supplémentaires pour implémenter une topologie de cluster actif/actif/passif.|  
|Implémenter un réseau de stockage (SAN) pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. **Remarque :** si possible, configurez les disques SAN à l’aide de RAID topologie 1 + 0 (il s’agit d’une bande de miroir) pour optimiser les performances et haute disponibilité.|Dans le [« Optimisation de base de données BizTalk Server livre blanc »](http://go.microsoft.com/fwlink/?linkid=104427) (http://go.microsoft.com/fwlink/?linkid=104427), consultez la section « Disque Infrastructure » sous « Réglage des performances ».|  
|Utiliser le Clustering Windows pour le serveur de secret principal Enterprise Single Sign-On (SSO) de cluster.|[Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md) **Remarque :** cluster pas le service d’authentification unique sur un ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] , sauf si vous mettez en cluster l’authentification unique et un hôte BizTalk du même groupe de clusters. Pour plus d’informations sur le clustering avec le service d’authentification unique et un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôte dans le même groupe de clusters voir [comment l’authentification unique de Cluster et un hôte BizTalk du même groupe de clusters](http://go.microsoft.com/fwlink/?LinkId=154367) (http://go.microsoft.com/fwlink/?LinkId=154367).|  
|Sauvegardez le Secret Enterprise Single Sign-On (SSO).|Consultez [comment sauvegarder le Secret principal](http://go.microsoft.com/fwlink/?LinkID=151395) (http://go.microsoft.com/fwlink/?LinkID=151395).|  
|Configurer le serveur Web des Internet Information Services (IIS) pour les instances de l’hôte isolé et de la page Web du portail BAM soit hautement disponible à l’aide de l’équilibrage de charge réseau (NLB) ou d’autres périphériques d’équilibrage de charge.|**Pour Windows Server 2008**: consultez [Guide de déploiement de l’équilibrage de charge réseau](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139).|  
  
## <a name="see-also"></a>Voir aussi  
 [Haute disponibilité](../technical-guides/providing-high-availability.md)