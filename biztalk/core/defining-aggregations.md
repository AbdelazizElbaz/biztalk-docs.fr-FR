---
title: "Définition des agrégations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], creating
- Excel add-in [BAM], creating aggregations
- aggregations [BAM], Excel add-in
- aggregations [BAM], about aggregations
ms.assetid: d5bf22d5-f491-4b08-a604-c7158e6e282f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3412615d03fc9a9776d86fddfb062ab343c5aaeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-aggregations"></a>Définition des agrégations
Excel définit **agrégations** des résumés précalculés de données qui améliorent les temps de réponse de requête les réponses étant prêtes avant que les questions soient posées. Par exemple, lorsqu'une table de faits d'un entrepôt de données contient des centaines de milliers de lignes, la réponse à une requête demandant les calendriers d'expédition de deux produits particuliers peut s'avérer être longue si le calcul de la réponse nécessite l'analyse de la table de faits. En revanche, la réponse peut être presque immédiate si les données récapitulatives fournies en réponse à cette requête ont été précalculées.  
  
 L'illustration suivante montre un exemple de données d'agrégation précalculées.  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
Données d'agrégation précalculées  
  
 La figure ci-dessous récapitule les quantités de chaque produit livrées à des emplacements spécifiques sur une période de deux mois. Excel définit généralement ces données en tant que **mesure**. Les données utilisées pour le filtrage et la catégorisation, Excel définit comme **dimension**.  
  
> [!NOTE]
>  L'analyse BAM ne prend pas en charge les instances nommées de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services.  
  
 L'expérience utilisateur de recherche de données multidimensionnelles figure à la rubrique de l'aide d'Excel consacrée aux tableaux croisés dynamiques.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment définir des mesures](../core/how-to-define-measures.md)  
  
-   [Définition des Dimensions](../core/defining-dimensions.md)  
  
-   [Comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md)  
  
-   [Définition des agrégations en temps réel](../core/defining-real-time-aggregations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’une vue BAM](../core/defining-a-bam-view.md)