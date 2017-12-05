---
title: "Paramètres d’entrée du fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cca24f93-74a8-460c-b9ab-9aa2c767fe2f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a430b96f7a76ad6f99a7b3f9ee151f17c7b55a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="functoid-input-parameters"></a>Paramètres d'entrée de fonctoid
La configuration correcte des paramètres d'entrée des fonctoids est un des aspects stratégiques de l'utilisation des fonctoids dans les mappages. Lors de l’ordre des paramètres d’entrée n’est pas critique pour tous les fonctoids (telles que la **ajout** fonctoid, qui affiche les propriétés associées qu’attend d’une addition), plusieurs fonctoids doivent avoir les paramètres d’entrée spécifié dans l’ordre approprié.  
  
## <a name="create-input-paramaters"></a>Créer des paramètres d’entrée
 Il existe deux méthodes pour créer les paramètres d'entrée d'un fonctoid :  
  
-   créer des liens dans la partie gauche d'un fonctoid dans la page de grille affichée. L'ordre dans lequel vous créez les liens est celui dans lequel les paramètres d'entrée associés sont transmis au fonctoid ;  
  
-   En ouvrant le **configurer \<fonctoid\> fonctoid** boîte de dialogue et ajouter de nouveaux paramètres d’entrée. Cette boîte de dialogue est importante, car elle permet aussi de remettre les paramètres d'entrée d'un fonctoid dans l'ordre approprié. Par exemple, si vous créez des liens avec le fonctoid dans un ordre incorrect, vous pouvez vous servir de cette boîte pour apporter les corrections nécessaires. Pour obtenir des instructions sur la configuration des paramètres d’entrée d’un fonctoid, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).  
  
 Vous devez utiliser le **configurer \<fonctoid\> fonctoid** boîte de dialogue pour créer des paramètres d’entrée qui sont des constantes.  
  
 Lorsque vous fournissez une étiquette pour un lien ou un fonctoid à l’aide de la **étiquette** propriété dans la fenêtre Propriétés lorsque la liaison ou le fonctoid est sélectionné, cette étiquette sera affichée dans le **configurer \<fonctoid\> Fonctoid** boîte de dialogue au lieu du XPath correspondant d’un nœud de schéma, ou le nom d’un fonctoid actuellement utilisé comme paramètre d’entrée. Avec les étiquettes, il sera beaucoup plus facile de différencier les paramètres et de les mettre dans l'ordre qui convient.  
  
 Pour plus d’informations sur l’ordre correct des paramètres d’entrée du fonctoid définitives, consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les paramètres d’entrée de fonctoid](../core/how-to-configure-functoid-input-parameters.md)   
 [Configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md)   
 [Configurer les fonctoids Bouclage de table et Extracteur de table](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)