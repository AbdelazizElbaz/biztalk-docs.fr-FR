---
title: "Pour insérer un élément Any ou n’importe quel nœud d’attribut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cbfdc04-6c83-4639-82de-169b6f009a2e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 913d7d0c68d61df1c457dd22500a9e4a8d90ec68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-an-any-element-or-any-attribute-node"></a>Pour insérer un élément Any ou n’importe quel nœud d’attribut
L’Éditeur BizTalk prend en charge deux types de nœuds : **tout élément** et **tout attribut**. Ces nœuds vous permettent de créer dans votre schéma des emplacements correspondant aux emplacements des messages d'instance correspondant où vous ignorez quels éléments ou attributs apparaîtront. Pour plus d'informations sur la manière dont ces nœuds sont interprétés lors du traitement des messages d'instance, reportez-vous directement aux informations relatives au langage XSD (XML Schema definition) sur le Web. Pour accéder à ces informations, voir [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
## <a name="insert-an-any-element-node-or-an-any-attribute-node"></a>Insérer un nœud tout élément ou un nœud tout attribut  
  
1.  Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **tout élément** nœud ou la **tout attribut** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **tout élément** ou **tout attribut**, le cas échéant.  
  
> [!IMPORTANT]
>  Définition de la **Process Contents** propriété **Lax** pour **tout élément** ou **tout attribut** nœuds peuvent ne pas fonctionnent correctement. Pour transmettre la validation **tout élément** ou **tout attribut** nœuds, affectez à la propriété **ignorer**.  Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
>
>  Pour créer un mappage qui contient **tout élément** ou **tout attribut** nœuds, vous devez utiliser soit le [copie de masse](mass-copy-functoid.md) fonctoid ou [script](scripting-functoid.md) fonctoid (avec Inline XSLT ou modèle d’appel XSLT Inline) pour effectuer le mappage pour ces nœuds ou ne simplement pas mapper ces nœuds.  
  
## <a name="see-also"></a>Voir aussi  
-  [Insertion de nœuds dans un schéma](../core/inserting-nodes-into-a-schema.md)
- **Référence du fonctoid**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]