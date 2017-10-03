---
title: "Comment gérer des liens existants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0db213b9-df84-4ebd-a59f-7691774d5031
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2e61bc8c7fbf015eba28666c63dbeabf57a39e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-existing-links"></a>Gestion des liens existants
Il peut arriver que vous ayez besoin de modifier la source ou la destination d’un lien, de nommer ou de renommer un lien ou encore de supprimer un lien. Cette rubrique contient des instructions détaillées concernant la réalisation de ces types d'opérations.  
  
### <a name="to-change-the-source-or-destination-of-a-link"></a>Pour modifier la source ou la destination d’un lien  
  
1.  Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.  
  
     Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.  
  
2.  Faites glisser un des deux points de terminaison vers le nouveau nœud de schéma ou le fonctoid auquel vous voulez le connecter.  
  
     Tandis que vous faites glisser le point de terminaison, le curseur prend la forme d'une croix. Si vous le pointez sur un nœud de schéma ou un fonctoid (ou tout autre objet) qui ne peut pas accepter le lien, le curseur prend la forme d'un cercle barré.  
  
    > [!IMPORTANT]
    >  Si plusieurs liens d’entrée sont connectés à un fonctoid et que vous redirigiez un ou plusieurs de ces liens d'entrée vers d'autres nœuds du schéma source ou vers d'autres fonctoids, il se peut que l'ordre des paramètres d'entrée dans le fonctoid d'origine ne soit pas conservé. Utilisez le **configurer \<fonctoid > fonctoid** boîte de dialogue pour vérifier l’ordre des paramètres d’entrée et les réorganiser si nécessaire. Pour plus d’informations sur la réorganisation des paramètres d’entrée d’un fonctoid, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md).  
  
### <a name="to-setedit-the-label-of-a-link"></a>Pour définir/modifier l'étiquette d'un lien  
  
1.  Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.  
  
     Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.  
  
2.  Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, fournissez un nom (nouveau) pour la liaison à l’aide de la **étiquette** propriété.  
  
### <a name="to-delete-a-link"></a>Pour supprimer un lien  
  
1.  Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.  
  
     Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.  
  
2.  Sur le **modifier** menu, cliquez sur **supprimer**.  
  
     Vous pouvez également appuyer sur la touche SUPPR ou cliquez sur le lien et cliquez sur **supprimer** dans le menu contextuel.  
  
    > [!NOTE]
    >  Il est possible de sélectionner plusieurs liens et/ou fonctoids afin de les supprimer simultanément. Vous pourrez ensuite annuler et rétablir cette opération. Pour plus d’informations sur Annuler et rétablir des opérations, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)