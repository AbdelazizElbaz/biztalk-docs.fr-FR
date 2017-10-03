---
title: "Comment identifier les goulots d’étranglement dans la base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0372f1f1-d892-4f7d-b6c4-e0f2b5a02f1c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decf27009eea6aff0ff5ed9088ae49ef2014b1cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-primary-import-database"></a>Comment identifier les goulots d’étranglement dans la base de données importation principale BAM
Pour identifier les goulots d’étranglement dans la base de données analyse BAM (Business Activity), procédez comme suit :  
  
1.  Assurez-vous que le nombre d'instances actives n'augmente pas excessivement.  
  
2.  Vérifiez que le service de l'Agent SQL est exécuté.  
  
3.  Si l’analyse OLAP est configurée, vérifiez que le BAM_AN_\<activityname > tâche est exécutée à intervalles réguliers.  
  
4.  Assurez-vous que BAM_DM_\<activityname > (Maintenance des données) est planifiée à intervalles réguliers.  
  
    > [!NOTE]  
    >  Activité de base de données BAM intensive scénarios permettre avoir un impact sur les performances des autres bases de données BizTalk Server, ce qui affecte les performances globales de BizTalk Server. Dans ce cas, envisagez effectuant les opérations suivantes :  
    >   
    >  -   Pensez à réduire la durée de toutes les activités BAM à partir de la valeur par défaut (6 mois) inférieure ou égale à 1 mois. Cela permet de réduire la période pour laquelle les données BAM sont conservées dans la base de données avant l’archivage. Utilisez l’utilitaire de gestion BAM `set-activitywindow` commande pour modifier la durée des activités BAM. Pour plus d’informations sur la gestion des activités de l’utilitaire de gestion BAM commandes consultez [commandes de gestion des activités](http://go.microsoft.com/fwlink/?LinkId=210417) (http://go.microsoft.com/fwlink/?LinkId=210417).  
    > -   Déplacer la base de données des archives BAM vers une instance de SQL Server qui n’héberge pas les bases de données MessageBox de BizTalk. Cela empêche que ces bases de données qui entrent en concurrence pour les ressources et améliorer les performances globales.  
  
5.  Utiliser un hôte dédié pour le suivi et de mesurer le compteur de performances de longueur de file d’attente hôte sous charge.  
  
6.  Vérifiez le compteur de performances de taille de Table du spouleur pour une tendance haussière au fil du temps.  
  
7.  Vérification de la durée de l’exécution du travail Archive et de Purge de longs temps d’exécution.  
  
8.  Vérifier la réactivité du disque (disque secondes par le compteur de performances en lecture/écriture) sur le disque qui héberge la base de données des suivis BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md)