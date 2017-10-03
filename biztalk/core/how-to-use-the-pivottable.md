---
title: "Comment utiliser le tableau croisé dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM views, pivot tables
- BAM views, previewing data
ms.assetid: af34494b-f577-4d36-9a9e-5d6e9c5fafbe
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed416f7a04392804c4c031a69940c4229eabe99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-pivottable"></a>Utilisation du tableau croisé dynamique
Lorsque vous avez défini une vue BAM incluant des dimensions et des mesures, vous devez mettre à jour un ou plusieurs tableaux croisés dynamiques associés à cette vue.  
  
 Un rapport de tableau croisé dynamique dans Excel est un tableau interactif qui vous permet de combiner et de comparer facilement de grandes quantités de données. Vous pouvez faire pivoter les valeurs figurant dans les lignes et les colonnes pour afficher divers récapitulatifs des données affichées. Un tableau croisé dynamique vous permet d'effectuer des calculs sur les données, tels que des regroupements de nombres ou de moyennes.  
  
 Pour utiliser le tableau croisé dynamique une fois celui-ci créé, effectuez la procédure ci-après. Pour plus d'informations sur l'utilisation des tableaux croisés dynamiques, consultez la documentation Microsoft Excel.  
  
> [!NOTE]
>  Lorsque vous créez un tableau croisé dynamique d'agrégation en temps réel, celui-ci peut comporter jusqu'à 14 niveaux de dimension.  
  
> [!IMPORTANT]
>  Si vous définissez plusieurs tableaux croisés dynamiques dans la feuille de calcul Excel, il est possible que les tableaux résultants grandissent et se chevauchent si l'activité génère un ensemble de données important. Dans cette situation, vous recevez alors un message indiquant qu'un tableau croisé dynamique ne doit pas chevaucher un autre tableau croisé dynamique lorsque vous actualisez les données. Vous pouvez remédier à ce problème en ajoutant des colonnes ou des lignes supplémentaires entre les tableaux croisés dynamiques afin d'éviter leur chevauchement s'ils grandissent.  
  
### <a name="to-use-the-pivottable"></a>Pour utiliser le tableau croisé dynamique  
  
1.  Créez une vue BAM à utiliser avec un tableau croisé dynamique. Pour plus d’informations sur la création d’une vue BAM, consultez [définition d’une vue activité d’entreprise](../core/defining-a-bam-view.md)  
  
2.  À l’aide de la **liste de champs de tableau croisé dynamique**, glisser-déplacer une ou plusieurs dimensions disponibles dans les zones de ligne et de colonne du modèle de tableau croisé dynamique.  
  
3.  À l’aide de la **liste de champs de tableau croisé dynamique**, glisser-déplacer une ou plusieurs mesures dans la zone d’éléments de données du modèle de tableau croisé dynamique.  
  
     Lors de la mise à jour du tableau croisé dynamique, vous remarquerez qu'il est complété par des exemples de données. Ces données vous donnent des indications sur la manière dont le tableau croisé dynamique doit être configuré.  
  
4.  À l’aide de la **tableau croisé dynamique** barre d’outils, associez un graphique du tableau croisé dynamique.  
  
5.  Enregistrez votre classeur Excel.