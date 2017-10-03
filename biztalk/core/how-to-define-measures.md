---
title: "Comment définir des mesures | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating measures
- aggregations [BAM], measures
- BAM views, measures
ms.assetid: fd3dfe6b-cc63-4306-8aad-a9d2a9af01e8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56fea736baaec3f259fc8831a7256e28eaabc9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-measures"></a>Définition des mesures
Une mesure définit la manière dont une activité est calculée. Lorsque vous créez une vue BAM, vous pouvez définir une mesure pour l'activité figurant dans la vue. Par exemple, pour une activité de bon de commande, vous pouvez calculer le montant total des bons de commande, le nombre de bons de commande, le montant moyen des bons de commande, etc.  
  
 Les mesures prises en charge par l'analyse BAM sont notamment les suivantes :  
  
-   Sum  
  
-   Compter  
  
-   Moyenne  
  
-   Minimum  
  
-   Maximum  
  
> [!NOTE]
>  Actuellement, le composant RTA (Real-time Aggregation, agrégation en temps réel) de l'analyse BAM ne prend pas en charge les mesures Minimum et Maximum. Vous pouvez utiliser ces mesures, mais lorsque vous marquez le tableau croisé dynamique Excel comme une agrégation RTA, les mesures Minimum et Maximum sont ignorées.  
  
### <a name="to-add-new-measures"></a>Pour ajouter de nouvelles mesures  
  
1.  Dans l’Assistant Vue BAM, cliquez sur **suivant** jusqu'à ce que vous voyiez la **nouvelle vue BAM : Dimensions et l’agrégation des mesures** page. Cliquez sur **de nouvelles mesures**.  
  
2.  Entrez le nom de la mesure.  
  
3.  Dans la liste déroulante, sélectionnez le **élément de Base de données**.  
  
4.  Cliquez sur le **type d’agrégation** vous souhaitez utiliser. Les choix possibles sont les suivants :  
  
    -   Sum  
  
    -   Compter  
  
    -   Moyenne  
  
    -   Minimum (non pris en charge pour les RTA).  
  
    -   Maximum (non pris en charge pour les RTA)  
  
5.  Cliquez sur **OK**. Lorsque vous avez terminé l’ajout de dimensions et mesures, cliquez sur **suivant**.  
  
6.  Sur le **nouvelle vue BAM : résumé** page, passez en revue les informations relatives à votre nouvelle vue, puis cliquez sur **suivant**.  
  
7.  Cliquez sur **Terminer** pour terminer le **Assistant Vue BAM**.  
  
 Si vous avez ajouté des mesures et des dimensions à la vue BAM, vous pouvez ajouter ces éléments dans le tableau croisé dynamique du classeur Excel. Pour plus d’informations sur la création d’un tableau croisé dynamique, consultez [comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Dimensions](../core/defining-dimensions.md)