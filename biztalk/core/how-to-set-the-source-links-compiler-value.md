---
title: "Comment définir la Source de liens du compilateur valeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61a7adf74d0b186f338220a383da6b6831013312
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-source-links-compiler-value"></a>Définition de la valeur du compilateur de liaisons sources
Vous pouvez utiliser la **liaisons sources** propriété d’un lien pour spécifier comment une valeur est récupérée à partir du nœud source et appliquée au nœud de destination. Cette rubrique explique les choix disponibles et comment choisir parmi ces derniers.  
  
### <a name="to-set-the-source-links-link-property"></a>Pour définir la propriété de lien Liaisons sources  
  
1.  Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.  
  
     Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.  
  
2.  Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, définissez la **liaisons sources** propriété à une des options suivantes :  
  
    -   **Nom de la copie.** le nom du nœud dans le schéma source est utilisé comme valeur pour le nœud lié dans le schéma de destination.  
  
    -   **Copier la valeur texte.** la valeur correspondant au nœud dans le schéma source (données d’élément ou valeur d’attribut) est utilisée comme valeur du nœud lié dans le schéma de destination. Il s’agit du choix par défaut. Par exemple, `<Node>Hello<Name>Chris</Name>Barry</Node>` donne « Hello ».  
  
    -   **Copier le texte et sous-contenu : valeur.** la valeur correspondant au nœud d’enregistrement et la valeur de tous ses nœuds enfants, ainsi que leurs nœuds enfants, dans le schéma source (données d’élément et valeurs d’attribut) sont associées pour donner la valeur du nœud lié dans le schéma de destination. Par exemple, `<Node>Hello<Name>Chris</Name>Barry</Node>` se traduit par « Hello Chris Barry ».  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)   
 [Liens et des Directives de compilateur](../core/compiler-directives-and-links.md)