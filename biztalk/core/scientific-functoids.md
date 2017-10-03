---
title: Fonctoids scientifiques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0311b7dc-1955-45af-b858-681faccc939b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b23f65ecede9082ec93041ddab45fa92029851a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scientific-functoids"></a>Fonctoids scientifiques

## <a name="overview"></a>Vue d'ensemble
**Scientifique** fonctoids sont utilisés pour effectuer des calculs exponentiels, logarithmiques et trigonométriques standard diverses.  
  
 À l’exception de la **fonctoid Logarithme** et **X ^ Y** fonctoids, qui exigent deux paramètres d’entrée, la **scientifique** fonctoids tous les acceptent un seul paramètre.  
  
 Les quatre fonctions trigonométriques **scientifique** fonctoids (**Arc tangente**, **cosinus**, **sinus**, et **tangente**) tous les utiliseront radians au lieu de degrés comme unité pour leur entrée pertinente ou les paramètres de sortie. Un radian est une unité de mesure des angles, de sorte qu’il existe 2π radians dans un cercle. Il en résulte que :  
  
-   2π radians équivalent à 360 degrés  
  
-   1 radian = 180/π degrés  
  
-   1 degré = π/180 radians  
  
 Si vos messages d’instance d’entrée ou de sortie utilisent des degrés comme unité de mesure des angles, vous devez utiliser un **mathématique** fonctoid en conjonction avec un trigonométrique **scientifique** fonctoid obtenir un résultat correct.  

## <a name="available-functoids"></a>Fonctoids disponibles  
 Le **scientifique** fonctoids sont : 

* 10^n
* Arc tangente
* Logarithme spécifié à partir de la base
* Logarithme commun
* Cosinus
* Fonction exponentielle naturelle
* Logarithme naturel
* Sinus
* Tangente
* X^Y
  
## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **Référence des fonctoids scientifiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]