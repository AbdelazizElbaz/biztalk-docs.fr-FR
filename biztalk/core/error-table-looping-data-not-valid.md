---
title: 'Erreur : données non valides de bouclage de Table | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tableLoopingDataNotValid
ms.assetid: 19c38e79-bab0-4899-ae24-e1485327e891
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9478026980ecaf3e2049773737250c56d18262c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---table-looping-data-not-valid"></a>Erreur : données non valides de bouclage de Table
**Code d’erreur**  
  
 btm1065  
  
 **Explication**  
  
 La table de données associées **bouclage de Table** fonctoid n’est pas valide, probablement en raison d’un deuxième paramètre d’entrée configuré de façon incorrecte pour le fonctoid, ou une grille Bouclage de table mal configurée.  
  
 **Action de l’utilisateur**  
  
 Vérifiez que les paramètres d’entrée pour le **bouclage de Table** fonctoid, accessibles via le **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.  
  
|Nombre de paramètres d'entrée du fonctoid Création de table| Description|  
|---------------------------------------------------|-----------------|  
|1|Lien à partir d’un enregistrement ou champ du schéma source, le nombre d’occurrences de laquelle un message d’instance d’entrée contrôle le nombre de fois associés de **extracteur de Table** fonctoids sont exécutés.|  
|2|Le nombre de colonnes dans la table de données configuré par le biais du **grille Bouclage de Table** propriété du **bouclage de Table** fonctoid.|  
|3 – 100|Constantes et liens (depuis le schéma source ou la sortie d'autres fonctoids) pouvant devenir des sources possibles de données dans la grille de création de table.|  
  
 En outre, assurez-vous de configurer correctement la grille de bouclage de table accessibles via la **grille Bouclage de Table** propriété et la **Configuration de bouclage de Table** boîte de dialogue. Une valeur constante ou un lien doit être choisie pour chaque cellule qui sera accessible par associé à un **extracteur de Table** fonctoid.