---
title: "Comment identifier les goulots d’étranglement dans la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b72e726-6225-47a0-8e1d-0f5a9cf745d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16cd05b6c399d250d8a411f41f56406f19afc9e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-tracking-database"></a>Comment identifier les goulots d’étranglement dans la base de données de suivi
Pour identifier les goulots d’étranglement dans la base de données des suivis BizTalk (BizTalkDTADb), procédez comme suit :  
  
1.  Vérifiez que le service de l'Agent SQL est exécuté.  
  
2.  Vérifiez que le travail d'archivage et de purge est en cours d'exécution et s'effectue correctement.  
  
3.  Assurez-vous que le travail TrackedMessages_Copy_BizTalkMsgBoxDB est en cours d’exécution et l’exécution.  
  
4.  Vérifiez qu'il existe suffisamment d'espace disque disponible pour les archives DTADb et l'augmentation de la base de données.  
  
5.  Utiliser un hôte dédié pour le suivi et de mesurer le compteur de performances de longueur de file d’attente hôte sous charge.  
  
6.  Vérifiez le compteur de performances de taille de Table du spouleur pour une tendance haussière au fil du temps.  
  
7.  Vérification de la durée de l’exécution du travail Archive et de Purge de longs temps d’exécution.  
  
8.  Vérifier la réactivité du disque (disque secondes par le compteur de performances en lecture/écriture) sur le disque qui héberge la base de données des suivis BizTalk.  
  
 Nous vous recommandons fortement de paramétrage vers le bas de la valeur des paramètres suivants du dtasp_BackupAndPurgeTrackingDatabase ou dtasp_PurgeTrackingDatabase appelée par la Purge et d’archivage :  
  
-   @nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Valeur par défaut est 0 heure.  
  
-   @nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Le délai par défaut est de 1 jour.  
  
-   @nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé. L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active. Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé. Valeur par défaut est 30 jours.  
  
 Ces paramètres doivent être définies conformément aux stratégies de rétention des données dans un environnement de production, alors que dans les tests de laboratoire de performances nous recommandons que vous utilisez des valeurs comme suit :  
  
 déclarer @dtLastBackup date/heure ensemble @dtLastBackup = GetUTCDate()  
 EXEC dtasp_PurgeTrackingDatabase 1, 0, 1,@dtLastBackup  
  
## <a name="see-also"></a>Voir aussi  
 [Goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md)