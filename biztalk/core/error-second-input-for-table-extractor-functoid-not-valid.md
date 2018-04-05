---
title: 'Erreur : la deuxième entrée de fonctoid Extracteur de Table non valide | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.secondInputForTableExtractorNotValid
ms.assetid: 099f7374-8625-40af-a74b-24c4de941a7b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e674ad6777ebff53fefe053e1b6af46ebc54ef3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---second-input-for-table-extractor-functoid-not-valid"></a>Erreur : la deuxième entrée de fonctoid Extracteur de Table non valide
**Code d’erreur**  
  
 btm1073  
  
 **Explication**  
  
 La deuxième entrée de paramètre au **extracteur de Table** fonctoid n’est pas valide. Ce paramètre doit être une constante entière positive qui indique une colonne valide dans la grille de bouclage de table le **bouclage de Table** fonctoid qui est indiqué par le premier paramètre d’entrée.  
  
 **Action de l’utilisateur**  
  
 Vérifiez que les paramètres d’entrée au **extracteur de Table** fonctoid, accessibles via son **paramètres d’entrée** propriété et la **configurer \<fonctoid\> Fonctoid** boîte de dialogue, sont comme indiqué dans le tableau suivant.  
  
|Numéro du paramètre d'entrée du fonctoid Extracteur de table| Description|  
|-----------------------------------------------------|-----------------|  
|1|Lien à partir de la **bouclage de Table** fonctoid à partir duquel le **extracteur de Table** fonctoid extraira les données de la colonne tel qu’indiqué par son deuxième paramètre.|  
|2|Le nombre d’une colonne valide dans la table de données configurée par le biais du **grille Bouclage de Table** propriété de la **bouclage de Table** fonctoid spécifié par le premier paramètre d’entrée.|