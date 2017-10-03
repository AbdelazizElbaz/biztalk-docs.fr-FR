---
title: "Comment configurer la hiérarchie de nœuds correspondant à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5302e194-cbc7-4d26-b25b-eb4e38abfe23
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d29a794db6f34d7e8251c32bbf428b3a336601fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-node-hierarchy-matching"></a>Configuration d'une correspondance de hiérarchie de nœuds
Lorsque vous créez un lien dans un mappage, le Mappeur BizTalk crée automatiquement des liens de compilateur pour implémenter le lien que vous avez établi. Le **liaisons cibles** propriété d’un lien contrôle la manière dont le Mappeur BizTalk crée les liens de compilateur. Cette rubrique fournit des informations sur la configuration des liaisons cibles.  
  
 Le **liaisons sources** propriété spécifie comment une valeur est récupérée à partir du nœud source et appliquée au nœud de destination. Pour plus d’informations sur la définition des liaisons sources, consultez [comment définir la valeur du compilateur de liens Source](../core/how-to-set-the-source-links-compiler-value.md).  
  
> [!NOTE]
>  Cette opération nécessite l'exécution du Mappeur BizTalk.  
  
### <a name="to-set-the-target-links-property"></a>Pour définir la propriété Liaisons cibles  
  
1.  Dans la page de grille de mappage, cliquez sur un lien pour lequel définir la propriété Liaisons cibles.  
  
2.  Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] **propriétés** , configurez la **liaisons cibles** propriété à une des options suivantes :  
  
    -   **Liaisons aplaties.** la hiérarchie du nœud d'enregistrement source est mise à plat au niveau du nœud d'enregistrement auquel elle est reliée dans le schéma de destination.  
  
        > [!NOTE]
        >  Par défaut, le Mappeur BizTalk définit le **liaisons cibles** propriété **Flatten**.  
  
    -   **Correspondance descendante des liaisons.** la correspondance des nœuds est réalisée niveau par niveau de façon descendante.  
  
    -   **Correspondance ascendante des liaisons.** la correspondance des nœuds est réalisée niveau par niveau de façon ascendante.  
  
## <a name="see-also"></a>Voir aussi  
 [Correspondance au niveau de hiérarchie de nœuds](../core/node-hierarchy-level-matching.md)   
 [Liens et des Directives de compilateur](../core/compiler-directives-and-links.md)   
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)