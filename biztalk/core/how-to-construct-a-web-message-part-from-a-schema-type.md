---
title: "Comment construire une partie de Message Web à partir d’un Type de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, schema types
- Web messages, creating
- Transform shape [Orchestration Designer]
- Web messages, Transform shape [Orchestration Designer]
ms.assetid: 4452ade6-b10f-4564-bffc-18114896aeeb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3434dc46be2fa43885346ac8d146e9326ab1ea73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-construct-a-web-message-part-from-a-schema-type"></a>Création d'une partie de message Web à partir d'un type de schéma
Vous créez une partie de message Web à partir d’un type de schéma en utilisant un **transformer** forme. Vous pouvez également utiliser une classe d'assistance .NET pour définir les parties. Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
### <a name="to-construct-a-web-message-part-from-a-schema-type"></a>Pour construire une partie de message Web à partir d'un type de schéma  
  
1.  Ajoutez un nouveau mappage. Pour plus d’informations sur la création de mappages, consultez [comment créer un nouveau mappe](../core/how-to-create-new-maps.md).  
  
2.  Dans le Mappeur BizTalk, cliquez sur **ouvrir le schéma de Destination** dans les **schéma de Destination** volet de la carte et dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le  **Schémas** nœud, sélectionnez le schéma de la référence Web ajoutée, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le format du schéma de référence Web est  **\<espace de noms par défaut du projet >.\< Nom de la référence Web >. Référence**.  
  
3.  Dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez un nœud racine pour le schéma de destination, puis cliquez sur **OK**. Pour plus d’informations sur la façon de déterminer un nœud racine pour un type de partie de message Web, consultez [comment déterminer un Type de partie de Message Web](../core/how-to-determine-a-web-message-part-type.md).  
  
4.  Cliquez sur **ouvrir le schéma Source** dans les **schéma Source** volet de la carte et dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud, sélectionnez le schéma source à mapper des données à partir de, puis cliquez sur **OK**.  
  
5.  Dans le Mappeur BizTalk, créez des liens entre le schéma source et le schéma cible.  
  
6.  Ouvrez une orchestration existante (ou créer une nouvelle orchestration), ouvrez le **boîte à outils**, puis cliquez sur le **Orchestrations BizTalk** onglet.  
  
7.  Faites glisser un **construire un Message** forme à l’orchestration.  
  
8.  Modifier la **Message construit** propriété à inclure le message d’instance qui créée pour le type de message Web.  
  
9. Faites glisser un **transformer** forme sur le **construire un Message** mettre en forme et double-cliquez pour ouvrir la **transformer la Configuration** boîte de dialogue.  
  
10. Cliquez sur le **mappage existant** bouton et sélectionnez le mappage que vous avez créé à l’étape 1 dans le **nom de mappage complet** zone de liste.  
  
11. Dans le **transformer** volet, sélectionnez **Source**. Dans le **transformation Source** volet, sélectionnez un message valide de l’instance à partir de la zone de liste.  
  
12. Dans le **transformer** volet, sélectionnez **Destination**. Dans le **transformation de Destination** , sélectionnez le message Web de l’instance à partir de la zone de liste, puis cliquez sur **OK**.  
  
 Pour plus d’informations sur l’utilisation de la **transformer la Configuration** boîte de dialogue, consultez [comment configurer la forme transformer](../core/how-to-configure-the-transform-shape.md).  
  
 Vous pouvez également utiliser cette procédure pour mapper l'instance de message de réponse de la méthode Web à une autre instance de message Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de Messages Web](../core/constructing-web-messages.md)