---
title: "Comment créer des schémas utilisant d’autres schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff0bcd9a-6c66-4c3b-bd41-64047a7c8392
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f427e5cd8e3f82e57dc8926c6e00889e1c97afe9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-schemas-that-use-other-schemas"></a>Comment créer des schémas utilisant d’autres schémas
Le langage XSD (XML Schema Definition) fournit trois mécanismes différents mais liés entre eux qui permettent d'utiliser un schéma dans un autre schéma. Ces mécanismes sont ceux qui consistent à importer un schéma, à inclure un schéma et à redéfinir un schéma. Pour une brève description de ces mécanismes et leurs différences, consultez [schémas utilisant d’autres schémas](../core/schemas-that-use-other-schemas.md). Pour plus d’informations, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md) pour des liens vers les spécifications et le manuel de XSD.  
  
 Cette rubrique décrit les étapes nécessaires à l'importation, l'inclusion et la redéfinition d'autres schémas dans un schéma en cours de développement.  
  
### <a name="to-import-include-or-redefine-one-schema-within-another-schema"></a>Pour importer, inclure ou redéfinir un schéma dans un autre schéma  
  
1.  Dans l'Éditeur BizTalk, ouvrez le schéma dans lequel vous souhaitez importer, inclure ou redéfinir un autre schéma. Vous pouvez ouvrir un schéma en double-cliquant dessus dans l'Explorateur de solutions.  
  
2.  Sélectionnez le **schéma** nœud en haut de l’arborescence du schéma.  
  
3.  Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
4.  Dans la fenêtre Propriétés, dans le **avancé** catégorie, dans la partie valeur de la **importations** propriété, cliquez sur le bouton de sélection (**...** ) bouton.  
  
5.  Dans le **importations** boîte de dialogue le **importer le nouveau schéma en tant que** liste, sélectionnez **XSD : importer**, **XSD : inclure**, ou **XSD Redéfinir**, le cas échéant, puis cliquez sur **ajouter**.  
  
6.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schéma** nœud dans l’arborescence du projet, sélectionnez le schéma que vous souhaitez importer, inclure, ou redéfinir, puis cliquez sur **OK**.  
  
7.  Dans le **importations** boîte de dialogue, cliquez sur **OK**.  
  
     Les directives XSD appropriées pour implémenter l’importation, inclure ou redéfinir l’opération sont ajoutés à la **schéma** élément dans la vue XSD, y compris un nouveau **importer**, **incluent**, ou **redéfinir** élément, comme il convient.  
  
> [!IMPORTANT]
>  Assurez-vous d'avoir bien compris les différentes finalités de ces trois mécanismes et en quoi ils diffèrent en termes d'exigences d'espace de noms. Vous pouvez toujours supprimer un schéma précédemment importé, inclus ou redéfini et utiliser ensuite l'un des deux autres mécanismes. Toutefois, si vous avez abondamment référencé ce schéma, vous devrez éventuellement le retravailler.  
  
> [!IMPORTANT]
>  Le mécanisme XSD d'importation, d'inclusion et de redéfinition d'un schéma dans un autre schéma fonctionne par référence au schéma importé, inclus ou redéfini. Cela signifie que si vous apportez une modification au schéma importé, inclus ou redéfini, elle sera répercutée dans le schéma contenant la référence d'importation, d'inclusion ou de redéfinition.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)   
 [Comment créer des références à un autre nœud ou Type](../core/how-to-create-references-to-another-node-or-type.md)