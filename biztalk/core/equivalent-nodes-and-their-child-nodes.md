---
title: "Nœuds équivalents et leurs nœuds enfants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a85c6a1-6121-4849-b958-7c4bd1c7c552
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05c5603cf1882aa7b262ecc5393a9d91dc93da10
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="equivalent-nodes-and-their-child-nodes"></a>Nœuds équivalents et leurs nœuds enfants

## <a name="overview"></a>Vue d'ensemble
Le  **\<équivalent\>**  nœud et ses enfants sont utilisés dans l’arborescence de schéma pour afficher des occurences de polymorphisme de type de données complexes. Lorsque vous dérivez un type de données complexe d'un autre type de données complexe, le polymorphisme dans XSD permet à ces deux types de données d'apparaître dans des messages d'instance à des endroits pour lesquels le type de données complexe de base a été spécifié. Lors de la validation de schéma, le fait qu’un seul de plusieurs types de données complexes est autorisé à un emplacement particulier est implicitement représenté par le nom de type de données complexe de base associé à la **base** attribut de la **extension** ou **restriction** éléments des types de données complexes dérivés. Pour rendre ce polymorphisme plus évident dans l’arborescence du schéma, le  **\<équivalent\>**  nœud et ses nœuds enfants sont affichés explicitement.  
  
 Le  **\<équivalent\>**  nœud est affiché comme un nœud enfant d’occurrences du type de base de données complexe, indiquant qu’il existe plusieurs types de données complexes qui peuvent se produire à cette position dans une instance Message. Les nœuds enfants de la  **\<équivalent\>**  nœud sont affichés sous forme de la valeur de la **nom** attribut correspondantes **complexType** élément dans la représentation XSD du polymorphisme, affiché entre crochets (\<nom\>).  
  
 Le  **\<équivalent\>**  chaque nœud et ses enfants ont uniquement deux propriétés associées :  
  
-   **\<Équivalent\>**  nœud : **nom de nœud** et **Type de Base**
  
-   Nœuds enfants : **nom de nœud** et **Type de dérivation**

Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="xsd-representation"></a>Représentation XSD  
 Il n’existe aucune représentation XSD directe de la  **\<équivalent\>**  nœud et ses enfants. Ce nœud est utilisé dans l'arborescence pour rendre le polymorphisme de type de données complexe plus visible et évident.  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)