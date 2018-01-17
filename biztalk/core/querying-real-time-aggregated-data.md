---
title: "Interrogation en temps réel des données agrégées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], real-time data
- BAM, real-time data
ms.assetid: f60a34a1-ac64-47c7-8f83-1bc301170590
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b71c3adbcbe5aaaea4d9fa4bf25b2aa4191c580
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-real-time-aggregated-data"></a>Interrogation des données agrégées en temps réel
Les données d'agrégation RTA sont disponibles pour d'éventuelles requêtes dans une vue SQL créée dynamiquement dans la base de données d'importation principale BAM.  
  
 Le nom de cette vue est  
  
 **bam_\<** *ViewName* **\>_\<** *RTAName* **\>_RTAView**  
  
 Où  
  
 **\<***ViewName*  **\>**  est l’attribut de nom de l’élément de la vue dans la définition BAM XML, qui est le même que le nom de vue entré dans les Assistants Microsoft Excel associés.  
  
 **\<***RTAName*  **\>**  est l’attribut Name de l’élément RealTimeAggregation dans le XML de définition BAM, analyse BAM génère unique basé sur le nom de la vue.  
  
 Il est essentiel que vous teniez compte des points suivants quand vous interrogez des données agrégées en temps réel :  
  
-   Les agrégations en temps réel doivent être configurées de manière à conserver les agrégations pendant un laps de temps donné (une journée par défaut) et à ne jamais prendre de trop grandes proportions. Les agrégations anciennes doivent être disponibles dans les cubes OLAP.  
  
-   Toute requête effectuée sur les agrégations RTA doit inclure le filtrage d'une dimension de temps située à l'intérieur de la fenêtre en ligne correspondant aux données RTA. Cela est nécessaire du fait que l'analyse BAM réalise la maintenance des données des agrégations RTA sur la base de l'horodatage des données d'analyse BAM et est optimisée pour éliminer les données par blocs. Ainsi, si vous envoyez simplement la commande Transact-SQL « `select *` », les résultats fluctueront de façon imprévisible.  
  
-   Si les données d'activité sont envoyées à l'analyse BAM via la classe DirectEventStream, les données agrégées en temps réel n'ont pas de latence : elles apparaissent instantanément dès qu'est validée la transaction que contient l'application appelante.  
  
-   Si les données d'activité sont envoyées à l'analyse BAM via la classe BufferedEventStream, les données RTA s'afficheront à des fins de requête quelques secondes plus tard, en fonction de la charge du ou des services de bus d'événements BAM et du serveur SQL Server qui héberge la base de données d'importation principale BAM.  
  
-   L'analyse BAM base l'agrégation en temps réel sur une table qu'elle maintient synchronisée, à l'aide de déclencheurs, sur les modifications et les insertions des enregistrements de stockage des données d'activité. Pour plus d’informations, consultez [stockage des données d’activité](../core/activity-data-storage.md). L'agrégation en temps réel peut ainsi avoir un impact significatif sur les performances. Pour plus d’informations, consultez [les agrégations en temps réel](../core/real-time-aggregations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation planifiée des données agrégées](../core/querying-scheduled-aggregated-data.md)   
 [Interrogation des données BAM](../core/querying-bam-data.md)