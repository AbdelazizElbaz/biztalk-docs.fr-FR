---
title: Comment utiliser la forme Expression | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Expression shapes
- Expression shape [Orchestration Designer]
- Expression shape [Orchestration Designer], configuring
- Expression shape [Orchestration Designer], about Expression shape
ms.assetid: 2d702aa9-b824-4f47-a416-70707ce8ef29
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e263454db9674d5bc86b6b7dae1649003f3d129c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expression-shape"></a>Utilisation de la forme Expression
Le **Expression** forme vous permet d’entrer une expression XLANG/s choisie dans l’orchestration. Par exemple, vous pouvez effectuer un appel de type .NET pour exécuter un programme externe ou simplement modifier la valeur des variables de l'orchestration.  
  
 Alors que le **Expression** forme est très souple, il n’est pas recommandé d’utiliser pour exécuter la logique d’orchestration de niveau supérieur, ce qui serait préférable visible dans l’orchestration de dessin elle-même. En général, il est plus facile à comprendre et à gérer vos orchestrations si votre **Expression** formes contiennent des expressions simples et modulables.  
  
### <a name="to-configure-an-expression-shape"></a>Pour configurer une forme Expression  
  
1.  Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur le **Expression** mettre en forme et cliquez sur **modifier l’Expression** ou, dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) bouton pour le **Expression** propriété.  
  
2.  Dans l'Éditeur d'expression BizTalk, créez une expression pour affecter des valeurs. Pour plus d’informations, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Langage XLANG-s](../core/xlang-s-language.md)