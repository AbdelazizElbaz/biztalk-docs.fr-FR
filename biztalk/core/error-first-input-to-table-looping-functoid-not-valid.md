---
title: Erreur - première entrée non valide du fonctoid Bouclage de Table | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.firstInputForTableLoopingNotValid
ms.assetid: 3ece2c0c-bcac-42d5-9536-34f073937879
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9ebecbd92b43dd25e6ff3dde04d942b936f40d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---first-input-to-table-looping-functoid-not-valid"></a>Erreur - première entrée non valide du fonctoid Bouclage de Table
**Code d’erreur**  
  
 btm1071  
  
 **Explication**  
  
 Le premier paramètre d’entrée au **bouclage de Table** fonctoid n’est pas valide. Ce paramètre doit être un lien à partir d’un nœud dans le schéma source, le nombre d’occurrences de l’élément correspondant dans un message d’instance d’entrée va contrôler le nombre de fois où des associés **extracteur de Table** fonctoids est appelé au moment de l’exécution.  
  
 **Action de l’utilisateur**  
  
 Vérifiez que les paramètres d’entrée pour le **bouclage de Table** fonctoid, accessibles via le **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.  
  
|Nombre de paramètres d'entrée du fonctoid Création de table| Description|  
|---------------------------------------------------|-----------------|  
|1|Lien à partir d’un enregistrement ou champ du schéma source, le nombre d’occurrences de laquelle un message d’instance d’entrée contrôle le nombre de fois associés de **extracteur de Table** fonctoids sont exécutés.|  
|2|Le nombre de colonnes dans la table de données configuré par le biais du **grille Bouclage de Table** propriété du **bouclage de Table** fonctoid.|  
|3 – 100|Constantes et liens (depuis le schéma source ou la sortie d'autres fonctoids) pouvant devenir des sources possibles de données dans la grille de création de table.|