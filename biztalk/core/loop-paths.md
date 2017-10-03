---
title: Chemins de bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Looping functoids, paths
- maps, conditional looping
ms.assetid: 4612dc2d-2c39-427d-88ac-65f9e85873c7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69e7d1c092ee5ca34b8c2ef3f309eff6c44b271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loop-paths"></a>Chemins de bouclage
Un élément dans un schéma en boucle si la propriété Max Occurs est supérieure à 1. Un chemin de bouclage se produit lorsque vous dessinez un lien entre un élément de bouclage du schéma source et un élément de bouclage du schéma de destination.  
  
## <a name="configuring-a-loop-path"></a>Configuration d'un chemin de bouclage  
 Le Mappeur BizTalk gère automatiquement les enregistrements de boucle lorsque vous créez un chemin de bouclage.  
  
 Vous pouvez configurer un chemin de bouclage dans un mappage en liant un champ d’un enregistrement de boucle du schéma source à un champ se trouvant dans un enregistrement de boucle du schéma de destination. L'illustration ci-dessous représente un mappage qui copie uniquement des enregistrements d'une enquête sur l'alimentation dans une liste d'adresses principale.  
  
 ![Mappage illustrant l’utilisation d’un chemin de bouclage. ] (../core/media/correct-loop-path-map.gif "correct_loop_path_map")  
Mappage de chemin de bouclage  
  
## <a name="multiple-loop-paths"></a>Plusieurs chemins de bouclage  
 Plusieurs chemins de bouclage se produisent dans un mappage lorsque vous liez des champs contenus par au moins deux enregistrements de boucle à des champs contenus par un seul enregistrement de boucle. L’illustration suivante présente une tentative pour combiner les adresses collectées à partir de deux enquêtes différentes en une seule liste d'adresses principale.  
  
 ![La carte avec plusieurs chemins de bouclage](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")  
Mappage avec plusieurs chemins de bouclage (incorrect)  
  
 Ce mappage ne produira pas les résultats attendus. Lorsque le Mappeur rencontre plusieurs chemins de bouclage au cours de la compilation, il émet un avertissement et sélectionne par défaut le premier chemin de bouclage. Pour combiner les deux adresses différentes dans une liste d’adresses principale unique, utiliser un **bouclage** fonctoid comme indiqué dans le mappage ci-dessous.  
  
 ![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingfunctoid.gif "loopingfunctoid")  
Mappage du fonctoid Bouclage (correct)  
  
 Le **bouclage** fonctoid doit être utilisé au lieu de plusieurs chemins de bouclage dans les scénarios suivants :  
  
1.  lorsque le Mappeur ne produit pas le résultat souhaité dans un scénario avec plusieurs chemins de bouclage ;  
  
2.  pour combiner plusieurs structures répétées dans un message d'instance d'entrée en une structure répétée unique dans le message d'instance de sortie ;  
  
3.  pour convertir un schéma plat en un schéma hiérarchique en mappant un enregistrement unique vers plusieurs enregistrements. Il s'agit d'une opération courante lors de la conversion de schémas plats vers des catalogues Microsoft Commerce Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)