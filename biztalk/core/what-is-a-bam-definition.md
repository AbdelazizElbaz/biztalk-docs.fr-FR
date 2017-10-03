---
title: "Qu'est-ce qu'une définition BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], observation models
- definitions [BAM], about BAM definitions
- definitions [BAM]
ms.assetid: 1ba1f45e-85fe-492f-8a2e-98bf3570c633
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cbc600f66be7167aabb4cf0273cb1c0bda78973
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-bam-definition"></a>Qu'est-ce qu'une définition BAM ?
Une définition BAM est une représentation XML d'un modèle d'observation de l'analyse BAM, c'est-à-dire une définition de niveau élevé pour un processus d'entreprise que vous souhaitez analyser. Un modèle d'observation -et, par conséquent, une définition BAM- est constitué des trois éléments principaux suivants : les étapes majeures et les événements de données (l'activité BAM), une description des agrégations de données et la façon dont les informations sont présentées à l'utilisateur (la vue BAM).  
  
> [!NOTE]
>  Vous avez également la possibilité de créer un fichier XML manuellement en fonction du schéma BAM. Cependant, nous vous déconseillons de créer une définition BAM de cette manière car la définition générée n'est pas validée.  
  
 Les définitions BAM peuvent contenir les éléments suivants :  
  
-   Activités d'entreprise : une définition BAM est valide si elle contient une activité d'entreprise (ou activité BAM). Tous les autres éléments de la définition sont facultatifs. Pour plus d’informations sur l’ajout d’une activité d’entreprise à une définition, consultez [la définition d’une activité d’entreprise](../core/how-to-define-a-business-activity.md).  
  
-   Vues : elles définissent l'ensemble des utilisateurs ayant accès aux données définies par l'activité d'entreprise. Elles permettent d'afficher des données filtrées ainsi que des agrégations de ces données et de présenter ces données filtrées de différentes manières (dans un graphique croisé dynamique, par exemple). L'analyse BAM prend en charge la définition d'une ou de plusieurs vues par activité.  
  
     Dans une vue, il est possible de définir les processus d'entreprise suivants :  
  
    -   Attribution d'alias aux données d'entreprise : elle permet d'attribuer des noms conviviaux aux éléments de données. Par exemple, le développeur peut définir un élément de données appelé « PNom ». De votre côté, vous pouvez créer un alias de sorte que « PNom » s'affiche sous la forme « Prénom » lorsque vous consultez les données actives BAM.  Pour plus d’informations sur les alias, consultez [comment afficher les éléments de renommer](../core/how-to-rename-view-items.md).  
  
    -   Durée : période de temps au cours de laquelle l'activité est analysée.  
  
    -   Groupes d'étapes majeures : ensembles d'étapes majeures commerciales. Vous pouvez utiliser un groupe en tant qu'étape majeure commerciale de début ou de fin de la période d'analyse.  
  
    -   Agrégations : il peut s'agir d'agrégations RTA (real-time aggregations) ou d'agrégations planifiées (également appelées « traitement analytique en ligne » ou OLAP), constituées des éléments suivants :  
  
-   Mesures : ensemble de valeurs numériques dans un cube Analysis Services (OLAP) reposant sur une colonne de la table de faits du cube.  
  
-   Dimension de la progression : représente la création d'agrégations en fonction de la progression des activités toujours en cours.  
  
-   Dimension Données : permet de classer une agrégation selon sa catégorie. Les dimensions de données sont fonction de la valeur des éléments de données existant sous forme de chaîne mise en forme dans l'activité BAM.  
  
-   Dimension de temps : permet de créer des agrégations pour les segments de temps indiqués.  
  
-   Dimension de la plage numérique : permet de classer les agrégations par catégories en fonction du nom convivial des plages numériques données.  
  
 Les définitions BAM peuvent contenir des alertes ayant été paramétrées dans les vues BAM. Elles peuvent également comprendre des données présentées sous forme de tableaux croisés dynamiques. Une fois la définition BAM déployée, les rapports de tableau croisé dynamique contiennent les données d'entreprise actives pouvant être visualisées à l'aide du classeur Excel des données actives ou du portail BAM.  
  
> [!NOTE]
>  Les définitions BAM créées à l’aide de la macro complémentaire d’analyse BAM pour Excel ne peut pas contenir d’alertes.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md)   
 [Portail BAM](../core/bam-portal.md)   
 [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md)