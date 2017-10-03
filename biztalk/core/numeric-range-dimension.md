---
title: "Dimension de plage numérique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], Numeric Range dimension
- Numeric Range dimension [BAM]
ms.assetid: a874ce44-b034-498f-ba58-114028dbef2c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fb6d4c21e0a207cfeec3e592569ca0f48f3badf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="numeric-range-dimension"></a>Dimension de la plage numérique
La dimension de plage numérique permet de classer les agrégations par catégories en fonction de noms conviviaux de plages données. Par exemple, un analyste d'entreprise peut définir une dimension de plage numérique intitulée Taille du bon de commande, dotée des plages suivantes : Peu élevé pour les bons de commande d'un montant compris entre 0 et 100 €, Moyen pour ceux dont le montant est compris entre 100 et 1 000 € et Important pour ceux d'un montant supérieur à 1 000 €.  
  
> [!NOTE]
>  Si un montant de bon de commande n’est pas dans les plages définies, par exemple, un montant de bon de commande est inférieur à 0, et ensuite une ligne « hors limites » sera automatiquement créée par l’analyse BAM pour contenir les données d’out-of-range.  
  
> [!NOTE]
>  Vous ne pouvez pas créer deux dimensions de plage numérique faisant référence au même alias de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md)   
 [Dimension de progression](../core/progress-dimension.md)   
 [Dimension données](../core/data-dimension.md)   
 [Dimension de temps](../core/time-dimension.md)   
 [Définition des Dimensions](../core/defining-dimensions.md)