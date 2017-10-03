---
title: Les formes qui prennent des Expressions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Expression Editor, shapes
- Decide shape [Orchestration Designer], expressions
- Message Assignment shape [Orchestration Designer], expressions
- Filter Expression property
- Listen shape [Orchestration Designer], expressions
- Delay shape [Orchestration Designer], expressions
- shapes, expressions
- Receive shape [Orchestration Designer], expressions
- Loop shape [Orchestration Designer], expressions
- Rule shape [Orchestration Designer]
ms.assetid: 0d27f711-ff7c-422b-b231-aa3c9a42ed0c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e78ada2c69205a0201c4bae9f3c7fa5b0656fa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="shapes-that-take-expressions"></a>Formes qui prennent des Expressions
Plusieurs formes dans le Concepteur d’Orchestration, y compris **décider** et **boucle**, utiliser des expressions booléennes pour former des règles qui contrôlent la création de branche. D’autres formes utilisent des expressions dans d’autres buts. Vous pouvez créer ou modifier une expression pour ces formes à l'aide de l'Éditeur d'expression BizTalk.  
  
 Le tableau suivant récapitule les formes utilisant des expressions dans le Concepteur d'orchestration et répertorie les types de données qui sont valides pour ces expressions.  
  
|Graphique à base de formes|Description d'utilisation d'expression|Types de données d'expression valides|  
|-----------|-----------------------------------|---------------------------------|  
|**Décider**|**Décidez** contiennent des formes **règle** formes, qui utilisent des expressions booléennes.|Booléen|  
|**Réception**|**Réception** formes qui ont la propriété Activer est définie sur True utilisent la **Expression de filtre** propriété à filtrer les messages entrants. L'expression figurant dans cette propriété doit correspondre à une valeur booléenne, qui déterminera si le message entrant doit être accepté ou non.<br /><br /> Le **Expression de filtre** boîte de dialogue permet de créer des expressions de filtre.|Booléen|  
|**Boucle**|A **boucle** forme requiert un **règle** forme, qui à son tour la doit contenir une expression booléenne.|Booléen|  
|**Règle**|**Règle** formes (affichés dans la zone de processus en tant que formes « branche ») sont des formes simples qui contiennent des expressions booléennes et sont utilisés dans d’autres formes (complexes) pour gérer les branches.|Booléen|  
|**Écouter**|Chaque branche d’un **écouter** forme contient, au minimum, soit un **réception** forme, qui utilise une expression booléenne uniquement pour les expressions de filtre (consultez l’entrée de **réception**) , ou un **délai** mettre en forme, qui utilise un **System.DateTime** objet ou **System.TimeSpan** objet.|Booléen, System.DateTime, System.TimeSpan|  
|**Délai**|L’expression utilisée dans un **délai** forme doit correspondre à un **System.DateTime** objet, pour exprimer une échéance, ou un **System.TimeSpan** objet, pour exprimer une durée.|System.DateTime, System.TimeSpan|  
|**Assignation du message**|L’expression dans une **assignation du Message** forme assigne une valeur à un message. La valeur affectée peut être de n'importe quel type, bien qu’il s’agisse généralement d'un message.|Tout|  
|**Expression**|Le **Expression** forme vous permet d’entrer une expression choisie dans l’orchestration. Par exemple, vous pouvez effectuer un appel de type .NET pour exécuter un programme externe ou simplement modifier la valeur des variables de l'orchestration.|Tout|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment utiliser la forme Expression](../core/how-to-use-expression-shape.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration requise et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md)   
 [Construction de Messages](../core/constructing-messages.md)   
 [Configuration des formes contrôle de flux](../core/configuring-flow-control-shapes.md)