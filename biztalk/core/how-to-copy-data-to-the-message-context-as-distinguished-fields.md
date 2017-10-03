---
title: "Comment copier des données dans le contexte du Message en tant que les champs distinctifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 004a13ca-a162-4a5e-9f72-8a5c55bbb7a6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ea68bc0b83c5a8f886416107e1dc98ea8ad8d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-distinguished-fields"></a>Comment copier des données dans le contexte du Message en tant que champs distinctifs
Cette rubrique fournit des instructions pas à pas pour promouvoir une propriété comme un **champ distinctif**.  
  
 Vous pouvez choisir **champ distinctif** plutôt que la promotion **champ de propriété** promotion pour les raisons suivantes :  
  
-   **Champ de propriété** valeurs sont limitées à 255 caractères.  
  
-   **Champ de propriété** valeurs sont stockées dans une base de données et par conséquent ont une charge plus importante que **champs distinctifs**. **Champs distinctifs** ne nécessitent pas de stockage supplémentaire ; ils sont essentiellement un alias pour une **XPath**, permettant ainsi aux orchestrations plus accéder facilement aux valeurs pertinentes directement à partir du message.  
  
### <a name="to-promote-a-property-as-a-distinguished-field"></a>Pour promouvoir une propriété en tant que Champ distinctif  
  
1.  Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ distinctif**.  
  
    > [!NOTE]
    >  Nœuds d’enregistrement ne peuvent jamais être promus en tant que **champs distinctifs**, quel que soit le type de contenu qu’ils contiennent.  
  
2.  Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **afficher les Promotions**.  
  
     Le **promouvoir les propriétés** boîte de dialogue s’ouvre avec apparaît le nœud sélectionné dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue.  
  
3.  Dans le **promouvoir les propriétés** boîte de dialogue, sélectionnez le **champs distinctifs** onglet.  
  
4.  Avec le nœud à promouvoir est toujours sélectionné dans l’arborescence de schéma sur le côté gauche de la **promouvoir les propriétés** boîte de dialogue, cliquez sur **ajouter**.  
  
     Si autorisé, le nœud sélectionné est ajouté à la liste dans le **champs distinctifs** onglet. Sinon, une zone de message fournit une explication  
  
5.  Vous pouvez sélectionner pour la promotion des nœuds supplémentaires dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue en cliquant sur **ajouter** après chaque sélection.  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
     Les nœuds que vous avez sélectionné pour promouvoir sont désormais **champs distinctifs**.  
  
## <a name="see-also"></a>Voir aussi  
 [Promotion des propriétés](../core/promoting-properties.md)   
 [Comment créer des schémas de propriété](../core/how-to-create-property-schemas.md)   
 [Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md)