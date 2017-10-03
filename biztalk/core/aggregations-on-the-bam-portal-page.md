---
title: "Les agrégations sur le portail BAM Page | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], alerts
- aggregations [BAM], viewing results
- alerts, aggregations
- Aggregations page [BAM portal]
- BAM portal, aggregations
ms.assetid: 6bc1a6f2-9e9a-4db6-aaa1-188ed2f2641f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a61df22bf5d07bd1b4d955f2baf884459de52998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-on-the-bam-portal-page"></a>Agrégations dans la page du portail BAM
Les utilisateurs finaux des activités, les développeurs et les analystes d'entreprise utilisent la page du portail BAM lorsqu'ils ont besoin de présenter des données agrégées, c'est-à-dire, des résumés précalculés d'un ensemble de données communiquant les caractéristiques représentatives de cet ensemble de données. La page d'agrégations du portail BAM vous permet d'afficher des données agrégées sous la forme d'un graphique accompagné d'un rapport de tableau croisé dynamique.  
  
## <a name="the-aggregations-page"></a>Page Agrégations  
 La page Agrégations affiche les résultats d'une activité regroupant des informations sur le fonctionnement du processus ou sur le fonctionnement général. Par exemple, un utilisateur peut afficher un graphique à secteurs simple, présentant le détail de 1 000 factures reçues en fonction de leur phase de traitement (400 factures toujours en évaluation, 400 rejetées, 100 payées et 100 toujours en attente).  
  
### <a name="creating-alerts-for-aggregations"></a>Création d'alertes pour les agrégations  
 Vous pouvez utiliser des agrégations comme base de création d'une alerte telle que « Avertissez-moi lorsque le nombre de factures en évaluation est supérieur à 500 ». Pour ce faire, cliquez sur n’importe quelle cellule de tableau croisé dynamique, sélectionnez **définir l’alerte**, ou cliquez sur une cellule et cliquez sur le **définir l’alerte** situé à droite du rapport de tableau croisé dynamique. Pour plus d’informations sur la création d’une alerte, consultez [comment définir une alerte](../core/how-to-set-an-alert.md).  
  
### <a name="viewing-individual-results-of-aggregations"></a>Affichage des résultats spécifiques à une agrégation  
 Vous pouvez sélectionner n'importe quelle quantité agrégée (ex. : 400 factures en évaluation) et afficher les résultats de l'agrégation de façon individuelle. Pour accéder à des résultats individuels en cliquant n’importe quelle cellule de tableau croisé dynamique et en sélectionnant **afficher les résultats**. Cette opération vous dirige vers la page Recherche d'activité où la recherche est automatiquement définie et les résultats affichés (dans l'exemple mentionné plus haut, un enregistrement par facture, soit 400 enregistrements).  
  
> [!NOTE]
>  Certains affichages de l'analyse BAM n'ont pas d'agrégation qui leur soit associée. Par conséquent, selon la façon dont la vue a été créée, il se peut qu'aucune information ne soit accessible.  
  
## <a name="see-also"></a>Voir aussi  
 [Portail BAM](../core/bam-portal.md)   
 [Recherche d’activité sur le portail BAM Page](../core/activity-search-on-the-bam-portal-page.md)   
 [Alert Manager sur le portail BAM Page](../core/alert-manager-on-the-bam-portal-page.md)