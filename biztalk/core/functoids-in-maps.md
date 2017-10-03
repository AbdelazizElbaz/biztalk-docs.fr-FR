---
title: Fonctoids dans les mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids
- functoids, about functoids
- functoid types, Record Count
- functoid types, Looping
- Looping functoids
- functoids, categories
- functoid types, Addition
- Record Count functoids
ms.assetid: 10ee8b62-cb20-4d26-9d86-b6564f30c297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976af2faed27e6cae8a57d9c7c83308d0519d81d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="functoids-in-maps"></a>Fonctoids figurant dans les mappages
Le Mappeur BizTalk prend en charge les transformations structurelles complexes d'enregistrements et de champs du schéma source en des enregistrements et champs du schéma de destination. Les fonctoids effectuent des calculs en utilisant des formules prédéfinies et des valeurs spécifiques, appelées arguments. Ces calculs sont effectués conformément à l'ordre désigné des enregistrements et champs.  
  
 En sélectionnant un fonctoid à partir de la boîte à outils, en le déplaçant vers la page de grille et en le liant à des nœuds des schémas source et de destination, des données peuvent être ajoutées ensemble, des informations de date et d'heure peuvent être modifiées, des données peuvent être concaténées, etc. Par exemple, le **ajout** fonctoid ajoute les valeurs et les **nombre d’enregistrements** fonctoid retourne le nombre total d’un enregistrement de boucle dans un message d’instance. Catégories de fonctoids que vous pouvez trouver dans la boîte à outils : avancé, Conversion, cumulé, base de données, Date / heure, logique, mathématique, scientifique et chaîne.  
  
> [!NOTE]
>  Tous les fonctoids sont écrits en code inline C# sauf les fonctoids Base de données.  
  
> [!NOTE]
>  Les nœuds de schéma de destination n'acceptent qu’une seule entrée d’un fonctoid à l’exception de la **bouclage** fonctoid.  
  
 Les rubriques de cette section décrivent comment migrer des fonctoids des versions précédentes de BizTalk Server, ce que sont les fonctoids, ce qu’ils font et comment les utiliser.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Catégories de fonctoids](../core/functoid-categories.md)  
  
-   [Paramètres d’entrée de fonctoid](../core/functoid-input-parameters.md)  
  
-   [Fonctoids de base](../core/basic-functoids.md)  
  
-   [Fonctoids avancés](../core/advanced-functoids.md)  
  
-   [Fonctoids en cascade](../core/cascading-functoids.md)  
  
-   [Propriétés des fonctoids](../core/functoid-properties.md)  
  
-   [Migration des fonctoids](../core/migrating-functoids.md)