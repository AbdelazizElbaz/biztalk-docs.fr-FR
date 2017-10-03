---
title: "Compteurs de Performance de l’intercepteur BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9b64ae1-4d94-4c3c-add1-fa020713be5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 989316edff34463905c7547db815b3daaf4d4a46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-interceptor-performance-counters"></a>Compteurs de performance de l'intercepteur BAM
Les compteurs de performance vous permettent d'analyser des aspects spécifiques du travail effectué par les intercepteurs BAM. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Le tableau suivant répertorie les compteurs de performance disponibles pour les intercepteurs BAM. La catégorie des compteurs de performance est « Intercepteur BAM ».  
  
|Compteur| Description|  
|-------------|-----------------|  
|Nombre moyen Moyenne de vidage/des événements BAM ayant échoué|Nombre moyen d'événements BAM ayant échoué pendant une opération de vidage de données dans la base de données d'importation principale.|  
|Réussites événements BAM/vidage|Nombre moyen d'événements BAM ayant réussi pendant une opération de vidage de données dans la base de données d'importation principale. Si la transaction est annulée, ces événements ne seront pas conservés dans la base de données.|  
|Nombre moyen Extraction s/BAM événement|Durée moyenne d'extraction des événements BAM.|  
|Nombre moyen Vider s/BAM événement|Durée moyenne de vidage des événements BAM.|  
|Total échecs événements BAM pendant vidage|Nombre total d'événements BAM ayant échoué au cours de l'opération de vidage de données|  
|Total réussite événements BAM pendant vidage|Nombre total d'événements BAM ayant réussi pendant l'opération de vidage dans la base de données d'importation principale. Si la transaction est annulée, ces événements ne seront pas conservés dans la base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Compteurs de Performance BAM](../core/bam-performance-counters.md)