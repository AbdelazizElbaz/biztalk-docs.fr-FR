---
title: Dimension de la progression | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], progress dimensions
- Progress dimension [BAM]
ms.assetid: 472fcbf6-502f-4c81-bf48-f7eec98e391b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2e4764071beb2aa94aac738e8f1cec2377dd1d8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="progress-dimension"></a>Dimension de la progression
Utilisez une dimension de progression afin de regrouper des activités BAM en fonction des étapes majeures qu'elles ont atteintes. Un exemple permet de mieux comprendre le concept.  
  
 Prenons en compte l'orchestration du didacticiel 1 qui traite des requêtes pour des éléments. (Consultez [didacticiel 1 : intégration](../core/tutorial-1-enterprise-application-integration.md) pour plus d’informations sur cette orchestration.) L'orchestration comporte une forme Décision, laquelle comprend deux branches. Dans [4 du didacticiel : analyse BAM](http://msdn.microsoft.com/library/81d5e768-f8a6-4eb0-8e6c-64db47455476) vous mappez l’étape majeure de commerciale refusé à une forme de la branche qui représente la demande refusée, et vous mappez l’étape majeure de commerciale Approved à une forme dans la branche représentant la demande en cours d’approbation. Vous créez ensuite une dimension de progression incluant les étapes majeures commerciales Approved (Approuvé) et Denied (Refusé). Lorsque vous utilisez la dimension de progression dans un tableau croisé dynamique, vous pouvez afficher les activités BAM regroupées en fonction de leur état Approved (Approuvé) ou Denied (Refusé). Cela est illustré dans le schéma suivant.  
  
 ![Tableau croisé dynamique avec des colonnes pour approuvé et refusé](../core/media/bts-view-with-approved-denieds.gif "bts_view-avec-approuvé-refus")  
  
 Vous pouvez définir des sous-étapes majeures dans l'étape majeure Denied (Refusé), et ce même si cela n'est pas présenté dans les didacticiels. Par exemple, si l'orchestration a identifié des motifs ayant entraîné un refus, vous pouvez créer des sous-étapes majeures nommées Poor credit (Crédit insuffisant) et Out-of-stock (Rupture de stock) dans l'étape majeure Denied (Refusé). Si vous avez utilisé la dimension de progression dans un tableau croisé dynamique, vous pouvez parcourir l'étape majeure Denied (Refusé) afin de visualiser les activités BAM ayant atteint l'étape majeure Poor-credit (Crédit insuffisant),ainsi que les activités BAM ayant atteint l'étape majeure Out-of-stock (Rupture de stock).  
  
 Dimensions de la progression de l’analyse BAM se composent de *étapes majeures de progression* et *étapes de progression*. Une étape majeure de progression correspond à une classification, une manière de regrouper des activités BAM. Il s'agit par exemple des étapes majeures de progression Approved (Approuvé) et Denied (Refusé), qui vous permettent de classer les activités Request comme étant approuvées ou refusées.  
  
> [!NOTE]
>  Il ne convient pas d'utiliser le mot « étape majeure » pour faire référence aux deux concepts. A *étape majeure commerciale* est un élément d’activité dans une activité BAM ; il représente la date et l’heure à laquelle un événement de l’application s’est produite. A *étape majeure de progression* est une méthode de regroupement des instances d’activité. Chaque étape majeure de progression correspond à une étape majeure commerciale. Afin d'éviter tout risque de confusion, envisagez d'utiliser un nom identique pour l'étape majeure de progression et l'étape majeure commerciale correspondante.  
  
 Un niveau de progression désigne un groupe d'étapes majeures paires. Notre exemple de sous-étapes majeures inclut deux niveaux de progression. Le premier niveau de progression comprend les étapes majeures de progression Approved (Approuvé) et Denied (Refusé). Le second niveau de progression comprend les étapes majeures de progression Poor-credit (Crédit insuffisant) et Out-of-stock (Rupture de stock).  
  
 Une dimension de progression est constituée à la base d'une étape majeure de progression. Cette étape majeure de progression représente généralement le message d'origine reçu. Chaque étape majeure de progression peut comprendre un niveau de progression, ainsi qu'un nombre indéterminé d'étapes majeures de progression. Toutes les étapes majeures de progression d'un niveau de progression doivent s'exclure mutuellement. Dans l'illustration suivante, Disposition et Reason (Motif) correspondent à des niveaux de progression, tandis que Received (Reçu), Approved (Approuvé), Denied (Refusé), Poor credit (Crédit insuffisant) et Out of stock (Rupture de stock) sont des étapes majeures de progression.  
  
 ![Définition des deux &#45; du niveau de dimension de progression](../core/media/bts-progress-dimension-two-levelss.gif "bts_progress-dimension-2-levelss")  
  
## <a name="how-to-create-progress-dimensions"></a>Création des dimensions de la progression  
 Vous devez concevoir la dimension de progression avant d'utiliser l'Assistant Vue BAM en vue de la créer. Le tableau ci-dessous identifie le processus de conception d'une dimension de progression et inclut également un exemple de chaque étape.  
  
|Traiter|Exemple|  
|-------------|-------------|  
|Établissez la hiérarchie des catégories et sous-catégories pour lesquelles créer des rapports.<br /><br /> Ces niveaux seront considérés comme des étapes majeures de progression.|Reçu :<br /><br /> -Approuvé<br /><br /> -Refusé<br /><br /> -Crédit faible<br /><br /> -Out Of Stock|  
|Pour chaque ensemble de catégories figurant au même niveau, choisissez un nom représentatif de ces catégories.<br /><br /> Ces noms définis seront considérés comme des niveaux de progression.|Le niveau incluant les valeurs Approved (Approuvé) et Denied (Refusé) est nommé « disposition ».<br /><br /> Le niveau incluant les valeurs Poor Credit (Crédit insuffisant) et Out Of Stock (Rupture de stock) est nommé « reason » (Motif).|  
|Identifiez les étapes majeures commerciales représentant chaque étape majeure de progression.<br /><br /> **Remarque :** l’activité BAM doit inclure un élément d’activité pour chacune de ces étapes majeures commerciales.|Reçu : reçu<br /><br /> Approuvé : approuvé<br /><br /> Refusée : refusé<br /><br /> Crédit faible :-Crédit de médiocre refusé<br /><br /> En rupture de Stock : Refusé-de rupture|  
  
 Les étapes majeures de progression, les niveaux et les étapes majeures commerciales sont utilisées lorsque vous créez la dimension de progression.  
  
> [!NOTE]
>  La procédure suivante débute au moment de la création d'une dimension. Vous avez déjà créé des activités BAM et avez déjà commencé à créer une vue BAM.  
  
#### <a name="to-create-a-progress-dimension"></a>Pour créer une dimension de progression  
  
1.  Cliquez sur le **compléments** onglet, puis sélectionnez **vue BAM** à partir de la **BAM** liste déroulante dans le **commandes de Menu** groupe.  
  
2.  Dans l’Assistant Vue BAM, cliquez sur **suivant** jusqu'à ce que vous voyiez la **nouvelle vue BAM : Dimensions et l’agrégation des mesures** page.  
  
3.  Cliquez sur **nouvelle Dimension**.  
  
4.  Dans le **nouvelle Dimension** boîte de dialogue, tapez un nom pour la dimension dans le **nom de la Dimension** zone, puis sélectionnez **Dimension de progression** à partir de la **Dimension type** liste déroulante.  
  
5.  Cliquez sur **nouvelle étape majeure**.  
  
6.  Dans le **étape majeure de progression** zone de la **nouvelle étape majeure de progression** boîte de dialogue, tapez le nom de l’étape majeure de progression au niveau supérieur de la hiérarchie que vous avez créée. Pour l’exemple en cours d’exécution, vous devez taper `Received`.  
  
7.  Sélectionnez l’étape majeure commerciale qui correspond à l’étape majeure de progression, puis cliquez sur **OK**. Pour l’exemple en cours d’exécution, vous sélectionneriez **reçus (\<nom de l’activité\>)**.  
  
8.  Dans le **nouvelle Dimension** boîte de dialogue, cliquez sur **nouvelle étape**.  
  
9. Dans le **progression étape** zone de la **nouveau niveau de progression** boîte de dialogue, tapez le nom du niveau plus élevé, puis cliquez sur **OK**.  Pour l’exemple en cours d’exécution, vous devez taper **disposition**.  
  
10. Dans le **nouvelle Dimension** boîte de dialogue, cliquez sur **nouvelle étape majeure**.  
  
11. Dans le **étape majeure de progression** zone de la **nouvelle étape majeure de progression** boîte de dialogue, tapez le nom de l’une des étapes majeures de premier niveau. Pour l’exemple que nous utilisons, vous devez taper `Approved`.  
  
12. Dans le **étape majeure commerciale** zone de liste déroulante, sélectionnez l’étape majeure commerciale qui correspond à l’étape majeure de progression, puis cliquez sur **OK**. Pour l’exemple en cours d’exécution, vous sélectionneriez **Approved (\<nom de l’activité\>)**.  
  
13. Répétez les trois étapes précédentes pour ajouter d'autres étapes majeures figurant dans le même niveau de progression.  
  
14. Si une étape majeure commerciale inclut des sous-étapes majeures, sélectionnez l’étape majeure de parent dans la **nouvelle Dimension** boîte de dialogue, cliquez sur **nouvelle étape**, puis répétez les cinq étapes précédentes pour définir la sous-étape et ses étapes majeures.  
  
     L’illustration suivante montre le **nouvelle Dimension** boîte de dialogue après avoir créé la dimension de progression de l’exemple.  
  
     ![Définition des deux &#45; du niveau de dimension de progression](../core/media/bts-progress-dimension-two-levelss.gif "bts_progress-dimension-2-levelss")  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md)   
 [Dimension données](../core/data-dimension.md)   
 [Dimension de temps](../core/time-dimension.md)   
 [Dimension de plage numérique](../core/numeric-range-dimension.md)   
 [Définition des dimensions](../core/defining-dimensions.md)