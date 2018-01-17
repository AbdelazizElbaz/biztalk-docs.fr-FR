---
title: "Nœuds Élément de champ et Nœuds d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1fffbca-8886-42c0-9214-cd0c5314850c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d90f622e20bbdbace6804b2418cb68fd2ad60da
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="field-element-nodes-vs-field-attribute-nodes"></a>Nœuds Élément de champ et Nœuds Attribut de champ

## <a name="overview"></a>Vue d'ensemble
Des schémas de fichier plat sont utilisés par le désassembleur de fichier plat afin de contrôler la manière dont les messages d'instance de fichier plat entrants sont convertis dans leur format XML équivalent et utilisés par l'assembleur de fichier plat pour contrôler comment les messages XML sortants sont convertis dans leurs messages d'instance de fichier plat équivalents. Lors de la construction de ces schémas, vous utilisez soit un **élément de champ** nœud ou un **attribut de champ** nœud à certains endroits du schéma pour contrôler si un champ particulier dans l’instance de fichier plat message correspond à un élément XML ou à un attribut XML dans le format XML équivalent du message.  

## <a name="example"></a>Exemple  
 Par exemple, la valeur de champ alignée à gauche, et remplie d’astérisques «`red*****`» dans un fichier plat, message d’instance peut être convertie dans sa représentation XML équivalente de deux manières différentes, selon si ce champ dans le schéma est un **champ Élément** nœud ou un **attribut de champ** nœud. Lorsque ce champ est représenté dans le schéma par un **élément de champ** nœud avec ses **nom de nœud** « couleur » et le contenant la valeur de propriété **enregistrement** nœud a son **Nom du nœud** propriété définie sur « shirt », l’équivalent XML du champ de fichier plat est (indiqué en gras).  
  
```  
<shirt>  
    <color>red</color>  
</shirt>  
```  
  
 Lorsque ce même champ de fichier plat est représenté dans le schéma par un **attribut de champ** nœud avec ses **nom de nœud** de couleur et de l’objet contenant la valeur de propriété **enregistrement** nœud possède son **Nom de nœud** propriété shirt, l’équivalent XML du champ de fichier plat est (indiqué en gras) :  
  
```  
<color shirt="red"/>  
```  
  
> [!NOTE]
>  Schémas de fichier plat ont une restriction supplémentaire qui, au sein d’une donnée **enregistrement** nœud subordonné **attribut de champ** nœuds subordonnés doivent précéder **enregistrement** nœuds ou  **Élément de champ** nœuds.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations relatives aux champs](../core/field-considerations.md)
-  **Nom du nœud** propriété[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]