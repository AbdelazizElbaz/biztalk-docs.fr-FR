---
title: Fonctoid Bouclage de table | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Looping functoids, about Table Looping functoids
ms.assetid: 6189a789-afe7-4e72-a778-2b0374db8f69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c5e5f2967fb48bfe896c26246db1630266812f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-functoid"></a>Fonctoid Bouclage de table
Le **bouclage de Table** fonctoid vous permet de créer une table de valeurs de sortie à utiliser pour créer le message d’instance de sortie. Les données de la table peuvent être composées de liens et de constantes. Le premier paramètre d’entrée de la **bouclage de Table** fonctoid configure l’étendue, ou combien de fois les enregistrements de boucle. La deuxième entrée de paramètre pour le **bouclage de Table** fonctoid détermine le nombre de colonnes dans la table, et les autres entrées définissent les valeurs de cellule possibles pour la table, dans aucun ordre particulier. Pour plus d’informations sur l’utilisation de ces propriétés, consultez [Configuration de bouclage Table-Driven](../core/table-driven-looping-configuration.md). Consultez également [exemple de bouclage Table-Driven](../core/table-driven-looping-example.md).  
  
> [!NOTE]
>  Le **bouclage de Table** fonctoid est répétée pour qu’il est connecté à l’enregistrement de bouclage. À chaque itération, il effectue une boucle par ligne de la grille de bouclage de table, produisant des boucles de sortie multiples.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid Extracteur de table](../core/table-extractor-functoid.md)   
 [L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)