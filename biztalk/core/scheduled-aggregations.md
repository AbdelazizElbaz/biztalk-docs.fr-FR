---
title: "Agrégations planifiées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- scheduling, aggregations [BAM]
- aggregations [BAM], scheduling
ms.assetid: 4e2da2eb-b1fc-4b27-98d6-564e6df719e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf2558b046d53deb6036553c5206beebd4d80ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduled-aggregations"></a>Agrégations planifiées
Dans le composant BAM, les agrégations planifiées reposent sur des cubes OLAP générés de façon dynamique et sur des lots DTS (Data Transformation Services). Les données des agrégations planifiées constituent une capture instantanée de vos activités d'entreprise lorsque vous démarrez le lot DTS. Pour ce faire, la première étape du lot DTS pour l’analyse est un appel à la procédure stockée **bam_Metadata_BeginAnalysis** capable d’extraire un instantané consistant en :  
  
-   une capture instantanée de toutes les instances d'activité en cours ;  
  
-   une fenêtre incrémentielle des instances d'activité terminées entre le moment où vous avez lancé l'exécution du lot DTS pour la dernière fois et le moment de la capture instantanée.  
  
 Pour obtenir ce résultat, le composant BAM applique un verrou exclusif sur le stockage d'activité pendant un cours instant afin d'empêcher l'écriture des données dans ce même temps. Une fois la capture instantanée extraite par le composant BAM, le lot DTS peut mettre du temps à s'exécuter mais durant ce processus, le composant BAM ignore toute nouvelle donnée. Le schéma ci-dessous illustre cette activité :  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig9.gif "ebiz_prog_bam_data_maint_fig9")  
Agrégations planifiées BAM  
  
 Dans ce schéma, le composant BAM déplace des données entre les instances d'activité terminées et le cube OLAP des instances terminées et traite le cube de façon incrémentielle.  
  
 Dans le même temps, il déplace les données entre les activités en cours et le cube des instances actives, traité dans son intégralité par le lot DTS. Cela est possible dans la mesure ou le composant BAM considère que pour un instant donné, seul un nombre réduit d'activités est en cours de processus.  
  
 Les données destinées aux agrégations planifiées sont disponibles dans un cube virtuel permettant d'effacer la différence entre les activités terminées et les activités en cours. Pour plus d’informations, consultez [interrogation des données agrégées planifiées](../core/querying-scheduled-aggregated-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Qu’est une agrégation ?](../core/what-is-an-aggregation.md)