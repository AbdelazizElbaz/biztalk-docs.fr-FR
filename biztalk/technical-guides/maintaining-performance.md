---
title: Maintien des performances | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae7e63ed-4e28-45b1-ab00-be9f9488a2e6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da10987a6532987ff7a2ed925e717a0a713cac6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-performance"></a>Maintien des performances
Cette section fournit des informations destinées à vous aider à résoudre les problèmes de performances découverts au cours de vos contrôles de maintenance de routine. Vous pouvez également utiliser les outils et les techniques présentées ici de manière proactive, pour identifier les problèmes potentiels avant qu’ils deviennent des problèmes critiques.  
  
 En règle générale, vous devrez établir un référentiel de performances standard servant à évaluer les performances du système en cours.  
  
 Outre les rubriques de cette section, les autres rubriques de ce document résoudre les problèmes de performances. Ces rubriques sont répertoriées dans les rubriques connexes ci-dessous.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Meilleures pratiques pour la gestion des performances](../technical-guides/best-practices-for-maintaining-performance.md)  
  
-   [Configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md)  
  
-   [Comment régler l’intervalle d’actualisation du Cache Configuration](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)  
  
-   [Comment désactiver le suivi de](../technical-guides/how-to-disable-tracking.md)  
  
-   [Résolution des problèmes de performances Issues3](../technical-guides/troubleshooting-performance-issues3.md)  
  
## <a name="related-sections"></a>Sections connexes  
  
-   Pour plus d’informations sur les performances des problèmes en général, consultez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Guide d’optimisation des performances à [http://go.microsoft.com/fwlink/?LinkID=150492](http://go.microsoft.com/fwlink/?LinkID=150492).  
  
-   Pour plus d’informations sur l’analyse des journaux de moniteur de performances hebdomadaire par rapport à la ligne de base et les seuils, consultez [à l’aide de l’outil performances analyse des journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md), « Recherche et éliminer les goulots d’étranglement » dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances Guide d’optimisation à [http://go.microsoft.com/fwlink/?LinkId=154675](http://go.microsoft.com/fwlink/?LinkId=154675), et [résolution des problèmes de performances Issues3](../technical-guides/troubleshooting-performance-issues3.md).  
  
-   Pour plus d’informations à propos de s’assurer que le système ne connaît pas la croissance automatique fréquente de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [définition des paramètres de croissance automatique pour les bases de données](../technical-guides/defining-auto-growth-settings-for-databases.md), « Suivi des instructions de dimensionnement de base de données » dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677)et « Identification des goulots d’étranglement au niveau de la base de données » dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678).  
  
-   Pour plus d’informations sur la maintenance de SQL Server, [effectuer les procédures de Maintenance SQL Server](~/technical-guides/checklist-configuring-sql-server.md).  
  
-   Pour plus d’informations sur l’exécution de SQL Server Profiler pendant une charge élevée pour vérifier les délais de réponse longs et utilisation importante des ressources, consultez « À l’aide de SQL Server Profiler » dans l’aide de SQL Server à [http://go.microsoft.com/fwlink/?LinkID=106720](http://go.microsoft.com/fwlink/?LinkID=106720).  
  
-   Pour plus d’informations à propos de s’assurer que le traitement par lot des messages pour tous les adaptateurs est approprié pour la consommation des ressources ou la latence, consultez [configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md).  
  
-   Pour plus d’informations sur l’augmentation de l’intervalle d’actualisation du cache BizTalk Server, consultez [comment régler l’intervalle d’actualisation du Cache Configuration](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md).  
  
-   Pour plus d’informations sur la limitation de l’hôte entrant et sortant, consultez « What limitation d’hôte » ? dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154694](http://go.microsoft.com/fwlink/?LinkId=154694). Pour plus d’informations sur les déclencheurs, les actions et les stratégies de prévention de limitation du trafic entrant et sortant, consultez « déclencheurs de condition de limitation, les actions et stratégies d’atténuation » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/? LinkId = 154695](http://go.microsoft.com/fwlink/?LinkId=154695).  
  
-   Pour utiliser un pipeline d’envoi PassThrough plutôt que le pipeline d’envoi XML par défaut, consultez « Gestion envoyer des Ports à l’aide de l’Explorateur BizTalk » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkID=154696](http://go.microsoft.com/fwlink/?LinkID=154696).  
  
-   Pour plus d’informations sur le dimensionnement de la base de données de suivi, consultez « Instructions dimensionnement de base de données de suivi » dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677).  
  
-   Pour plus d’informations sur les bases de données MessageBox, BizTalkDTADb et BAMPrimaryImport de dimensionnement, consultez « Identification de des goulots d’étranglement dans la couche de base de données » dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678).  
  
-   Pour plus d’informations sur la prévention des conflits dans la base de données MessageBox, consultez [comment éviter la Contention de disque](http://go.microsoft.com/fwlink/?LinkId=158809) ([http://go.microsoft.com/fwlink/?LinkId=158809](http://go.microsoft.com/fwlink/?LinkId=158809)) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Guide d’optimisation des performances.