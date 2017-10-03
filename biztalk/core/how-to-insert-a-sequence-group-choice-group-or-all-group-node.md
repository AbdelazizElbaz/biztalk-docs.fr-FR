---
title: "Insertion d’un groupe de séquences, un groupe de choix ou un nœud groupe tous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19aee400-1369-4310-b1b4-1bfeb2643236
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e498eb5ec8e7aa1398cfb58732f978faa9d0b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-sequence-group-choice-group-or-all-group-node"></a>Insertion d’un groupe de séquences, un groupe de choix ou un nœud groupe tous
L’Éditeur BizTalk prend en charge trois types de nœuds de groupe pour les éléments : **groupe séquence**, **groupe choix**, et **groupe tous**. Ces différents types de nœuds de groupe établissent des contraintes différentes sur les nœuds enfants du groupe dans les messages d'instance correspondants. Pour obtenir des informations sur les contraintes appliquées à ces différents types de groupes, consultez directement les informations concernant le langage XSD (XML Schema definition) sur le Web. Pour accéder à ces informations, voir [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
 L’Éditeur BizTalk prend également en charge un nœud de groupe pour les attributs, la **groupe d’attributs** nœud. Ce type de nœud permet un ensemble d’attributs pour être défini une fois et ensuite être associé à plusieurs **enregistrement** nœud dans le schéma.  
  
 Lorsque vous créez une structure dans votre schéma, **enregistrement** nœuds sont supposés pour contenir les séquences ordonnées de nœuds enfants par défaut et sont représentées à l’aide de **séquence** éléments dans la représentation XSD du le schéma. Vous pouvez modifier le type d’un nœud de groupe en modifiant son **Type d’ordre** propriété.  
  
### <a name="to-insert-a-sequence-group-node-or-a-choice-group-node"></a>Pour insérer un nœud Groupe Séquence ou Groupe Choix   
  
1.  Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe séquence** nœud ou la **groupe choix** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe séquence** ou **groupe choix**, le cas échéant.  
  
### <a name="to-insert-an-all-group-node"></a>Pour insérer un nœud Groupe Tous  
  
1.  Dans l’arborescence du schéma, sélectionnez la nouvelle **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe tous** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe tous**.  
  
> [!NOTE]
>  Le **groupe tous** option est uniquement disponible dans le menu BizTalk (ou raccourci) lorsque le parent pertinentes **enregistrement** nœud satisfasse aux contraintes imposées par XSD sur l’utilisation de la **tousles**élément.  
  
> [!NOTE]
>  Le **groupe tous** choix requiert que le **enregistrement** nœud ont un type de base de données. Un moyen rapide de donner le nœud à un type de données consiste à définir son **le Type de contenu** à **complexes**.  
  
### <a name="to-insert-an-attribute-group-node"></a>Pour insérer un nœud Groupe Attribut  
  
1.  Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe d’attributs** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe d’attributs**.  
  
> [!NOTE]
>  Si vous souhaitez modifier le nom de récemment insérées **groupe d’attributs** nœud, tapez le nouveau nom dans sa **référence du groupe** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Insertion de nœuds dans un schéma](../core/inserting-nodes-into-a-schema.md)