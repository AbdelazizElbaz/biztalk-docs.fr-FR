---
title: "Qu'est-ce qu'une agrégation ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP cubes, BAM
- BAM, aggregations
- BAM, OLAP cubes
- aggregations [BAM], OLAP cubes
- aggregations [BAM], about aggregations
- aggregations [BAM]
ms.assetid: 77d40602-ef56-4a5b-a18f-56ccbff573a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df24dced4d7075e85b8b002bf90b821ce745f91e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-aggregation"></a>Qu'est-ce qu'une agrégation ?
Dans Excel, les agrégations sont des résumés précalculés de données qui améliorent le temps de réponse de requête, les réponses étant prêtes avant que les questions ne soient posées. Par exemple, lorsqu'une table de faits d'un entrepôt de données contient des centaines de milliers de lignes, la réponse à une requête demandant les calendriers d'expédition de deux produits particuliers peut s'avérer être longue si le calcul de la réponse nécessite l'analyse de la table de faits. En revanche, la réponse peut être presque immédiate si les données récapitulatives fournies en réponse à cette requête ont été précalculées.  
  
 L'illustration suivante montre un exemple de données d'agrégation précalculées.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
Cube OLAP BAM  
  
 La figure ci-dessous récapitule les quantités de chaque produit livrées à des emplacements spécifiques sur une période de deux mois. Excel définit généralement ces données comme une mesure. Les données utilisées pour le filtrage et la catégorisation sont définies dans Excel comme une dimension.  
  
 Pour plus d'informations sur l'exploration des données multidimensionnelles, consultez la rubrique de l'aide d'Excel consacrée aux tableaux croisés dynamiques.  
  
 Vous pouvez créer des agrégations d'activités multidimensionnelles basées sur les données disponibles dans une vue spécifique. Ces agrégations contiennent des mesures (données à agréger, telles que des montants en euros) et des dimensions (utilisées pour filtrer ou regrouper, telles que État ou Ville).  
  
 Vous pouvez créer des agrégations sous la forme de cubes de traitement analytique en ligne (OLAP), qui représentent un instantané de l'entreprise à un moment précis, ou sous la forme d'agrégations RTA, déterminées par le scénario d'entreprise et que vous visualisez à l'aide de la structure multidimensionnelle en temps réel.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Agrégations planifiées](../core/scheduled-aggregations.md)  
  
-   [Agrégations en temps réel](../core/real-time-aggregations.md)