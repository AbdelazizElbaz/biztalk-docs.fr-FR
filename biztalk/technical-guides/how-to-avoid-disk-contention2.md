---
title: "Comment éviter de disque Contention2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37bdf6bd-cb34-4540-819e-908d83a22d40
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7be7a38ac3f3f6cc1d7d266c664cbb85f731c22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-disk-contention"></a>Élimination des risques de conflit au niveau des disques
BizTalk Server est conçu comme un système persistant. Pour les scénarios de débit élevé, les bases de données MessageBox et des suivis BizTalk peuvent rencontrer des conflits sévères. Ces conflits peuvent être aggravés par des disques lents. Si les disques sont lentes (supérieur à 15 ms en moyenne pour AVG. Disque s/lecture ou AVG. Disque s/écriture), le risque de SQL Server pour maintenir les verrous plus de temps (temps d’attente de verrou élevé et les délais d’attente de verrou haute). Cela, à son tour, peut entraîner les tables MessageBox (files d’attente de l’Application et Spool) de croître, provoquant l’encombrement de la base de données et de limitation. Cette situation a pour résultat faible débit global.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’identification si un serveur possède un goulot d’étranglement du disque, consultez [Analyseur de performances Windows](http://go.microsoft.com/fwlink/?LinkID=204007) (http://go.microsoft.com/fwlink/?LinkID=204007). Analyseur de performances Windows est un composant logiciel enfichable Microsoft Management Console (MMC) qui fournit des outils d’analyse des performances du système.  
  
 Pour éviter la contention de disque, procédez comme suit :  
  
|Étapes|Référence|  
|-----------|---------------|  
|Utilisez Raid10 / 0 + configurations de 1 disque.|[Pratiques recommandées pour éviter les goulots d’étranglement](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|Si possible, déployez les bases de données sur un réseau SAN à grande vitesse. Si plusieurs bases de données partagent les mêmes disques, nous vous recommandons de les configurer sur séparé **dédié** disques. En outre, nous vous recommandons de séparer les fichiers MDF et LDF pour la base de données MessageBox sur des disques différents.|[Optimisation des groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)|  
|Envisagez l’allocation de plusieurs fichiers pour la base de données TEMPDB, car cela sera considérablement réduire la contention de disque et répartir la charge sur plusieurs fichiers de données.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Envisagez de séparer la base de données MessageBox sur un serveur dédié qui est distinct des bases de données des suivis BizTalk.|[À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Affecter le répertoire du fichier journal MSDTC vers un autre lecteur dédié.|[Optimisation des performances du système d’exploitation](../technical-guides/optimizing-operating-system-performance.md)|  
|En cas de conflit dû au journal PageFile ou MSDTC, essayez de le déplacer vers un autre lecteur.|[Pratiques recommandées pour éviter les goulots d’étranglement](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|Optimiser la base de données de suivi pour les opérations d’écriture.|[Comment identifier les goulots d’étranglement dans la base de données de suivi](../technical-guides/how-to-identify-bottlenecks-in-the-tracking-database.md)|  
|Optimiser la base de données MessageBox pour la lecture et les opérations d’écriture.|[Comment identifier les goulots d’étranglement dans la MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)|  
|Si une instance d’hôte BizTalk est saturer l’UC, envisagez de les répartir l’envoi, réception, traitement et le suivi des fonctionnalités dans plusieurs hôtes. Cela configure le système afin que la fonctionnalité d’orchestration s’exécute sur un serveur dédié distinct afin d’améliorer le débit global du système.|[Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)|  
|Si plusieurs orchestrations sont déployées, envisagez de leur inscription dans les hôtes d’orchestration dédié différent. Cela isole les différentes orchestrations et empêche la contention des ressources partagées dans le même espace d’adressage physique ou sur le même serveur.|[Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)|  
|Envisagez d’utiliser d’analyseur de performances Windows pour diagnostiquer les problèmes de contention de disque...|[Analyseur de performances Windows](http://go.microsoft.com/fwlink/?LinkID=204007)|  
  
 Pour plus d’informations sur l’analyse des performances de disque, consultez les ressources suivantes :  
  
-   [Sans les problèmes liés aux disques](http://go.microsoft.com/fwlink/?LinkId=120947) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=120947 » \t « _blank » http://go.microsoft.com/fwlink/?LinkId=120947).  
  
-   [SQL Server avant d’e/s meilleures pratiques](http://go.microsoft.com/fwlink/?LinkId=120948) (http://go.microsoft.com/fwlink/?LinkId=120948).  
  
-   Section « Les goulots d’étranglement d’e/s » de [résolution des problèmes de performances dans SQL Server 2008](http://go.microsoft.com/fwlink/?LinkID=153586) (http://go.microsoft.com/fwlink/?LinkID=153586).  
  
## <a name="see-also"></a>Voir aussi  
 [Goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md)