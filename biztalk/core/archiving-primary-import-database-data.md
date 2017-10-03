---
title: "L’archivage des données de base de données d’importation principale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Primary Import database [BAM], archiving data
- archived data, BAM
- managing [BAM], archiving data
- data, archiving [BAM]
ms.assetid: 4a014a59-0578-41fa-9441-8b582f54bbe8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0fdfd55681fabd1b6cfc72f68b7e33150a121f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="archiving-primary-import-database-data"></a>Archivage des données dans la base de données d'importation principale
En tant qu'administrateur, vous pouvez indiquer la fenêtre de temps destinée à l'archivage des données d'instance d'activité dans la base de données d'importation principale. Pour cela, utilisez les propriétés OnlineWindowTimeUnit et OnlineWindowTimeLength de la table BAM_Metadata_Activities dans la base de données d'importation principale BAM.  
  
 Si les utilisateurs des activités ont déployé plusieurs activités, vous pouvez attribuer une fenêtre de temps différente à chaque activité. Pour plus d’informations sur le déploiement des activités, consultez « Définition d’une activité d’entreprise » dans *Guide d’utilisation d’informations travailleurs*.  
  
 Le tableau ci-après décrit les valeurs que vous pouvez définir pour les propriétés OnlineWindowTimeUnit et OnlineWindowTimeLength.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|OnlineWindowTimeUnit|Cette propriété peut être : mois, jour, heure ou minute. La valeur par défaut de cette propriété est « mois ».|  
|OnlineWindowTimeLength|Cette propriété doit être définie par un entier. La valeur par défaut de cette propriété est 6.|  
  
 Le composant BAM retire des données de la base de données d'importation principale BAM par partition. Cette opération se produit lorsqu'une partition se trouve en dehors de la fenêtre en ligne spécifiée (heure actuelle - OnlineWindowTimeLength de OnlineWindowTimeUnit). Par exemple, si OnlineWindowTimeLength = 5 et OnlineWindowTimeUnit = jour, les partitions datant de plus de 5 jours sont supprimées.  
  
 Le composant BAM place alors les données d'instance d'activité dans la base de données des archives BAM. Indiquez cette base de données pendant la configuration de l'analyse BAM de BizTalk. Pour plus d’informations sur la configuration BAM de BizTalk, consultez [schéma de Configuration BAM](../core/bam-configuration-schema.md).  
  
 Le composant BAM n'archive pas les données d'instance d'activité si vous n'avez pas exécuté le lot DTS (Data Transformation Services) de mise à jour du cube BAM. Ce dernier traite les données d'instance dans le cube de l'activité.  
  
 Pour plus d’informations sur l’exécution du lot DTS de maintenance de données BAM, consultez [lots DTS BAM](../core/bam-dts-packages.md).  
  
 Avec le temps, la taille de la base de données BAMArchive augmente à mesure que des données d'instance d'activité y sont ajoutées. Bien qu'il n'existe aucune méthode simple pour tronquer une base de données entière, vous pouvez régulièrement tronquer le journal des transactions de la base de données afin de réduire les besoins de stockage, et procéder à la sauvegarde et à l'archivage de la base de données BAMArchive entière. Pour plus d'informations, consultez la rubrique « Troncation du journal des transactions » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de la fenêtre de temps et les propriétés de tranche de temps](../core/defining-the-time-window-and-time-slice-properties.md)   
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)