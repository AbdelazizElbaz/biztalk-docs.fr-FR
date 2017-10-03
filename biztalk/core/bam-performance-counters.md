---
title: Compteurs de Performance BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], performance counters
- performance, counters [BAM]
ms.assetid: e23f7038-36a5-4957-bc73-47011763d109
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4307f72f149405fbc04e4e6cc51efe87229c2bff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-performance-counters"></a>Compteurs de performances BAM
Les compteurs de performance vous permettent d'analyser des aspects spécifiques du travail effectué par le service Bus d'événements BAM. Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.  
  
 Le tableau suivant répertorie les compteurs de performance disponibles dans l'analyse BAM.  
  
|Compteur| Description|  
|-------------|-----------------|  
|Événements traités|Nombre d'événements que le service Bus d'événements BAM est en train de traiter.|  
|Lots traités|Nombre de lots que le service Bus d'événements BAM est en train de traiter.|  
|Événements validés|Nombre d'événements que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.|  
|Enregistrements validés|Nombre d'enregistrements que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.|  
|Lots validés|Nombre de lots que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.|  
|Nombre total d'événements|Nombre d'événements que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.|  
|Nombre total d'enregistrements|Nombre d'enregistrements que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.|  
|Nombre total de lots|Nombre de lots que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.|  
|Nombre total échec de lots|Nombre de lots que le service Bus d'événements BAM n'a pas correctement traités depuis que vous l'avez lancé.|  
|Nombre total échec d'événements|Nombre d'événements que le service Bus d'événements BAM n'a pas correctement traités depuis que vous l'avez lancé.|  
  
 Les compteurs de performance sont situés dans l'Analyseur de performances (perfmon), sous l'objet de performance BizTalk:TDDS. Le nom d'instance des compteurs de performance est une combinaison du nom de serveur source et du nom de la base de données source. Si deux des services Bus d'événements BAM sont exécutés sur le même ordinateur pour deux bases de données source différentes, vous aurez deux instances des compteurs du service Bus d'événements BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [La gestion BAM](../core/managing-bam.md)