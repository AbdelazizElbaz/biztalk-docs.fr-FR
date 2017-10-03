---
title: Configuration requise et Limitations pour les Expressions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Expression Editor, about Expression Editor
- Expression Editor, requirements
- Orchestration Designer, Expression Editor
- Expression Editor, limitations
- Expression Editor
- Expression Editor, Orchestration Designer
ms.assetid: 1e0353d3-c2f3-4c10-86e3-8620e62dd0d5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd819850f62d47c640753e843325c9851da177b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-and-limitations-for-expressions"></a>Impératifs et restrictions des expressions
L'Éditeur d'expression BizTalk du Concepteur d'orchestration est un éditeur de texte Visual Studio standard offrant les options IntelliSense. Dans l'Éditeur d'expression BizTalk, il est possible d'entrer une expression sous forme textuelle.  
  
 Utilisez la zone de texte pour entrer une expression unique sous forme textuelle. L'expression peut s'étendre sur plusieurs lignes et doit se terminer par un seul point-virgule.  
  
 Voici la liste des limitations applicables aux expressions dans l'Éditeur d'expression BizTalk :  
  
-   L'assignation composée de la forme « += », « -= » ou « *= » n'est pas prise en charge.  
  
-   L'utilisation de plus d'un opérateur d'assignation dans une instruction n'est pas prise en charge.  
  
-   L'assignation dans un prédicat « if » ou « while » n'est pas prise en charge.  
  
-   Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge. Par exemple, « ++ » et « -- ».  
  
-   Pour les parties de message, les membres sont autorisés à accéder aux méthodes publiques, aux types imbriqués, aux champs de données statiques, aux propriétés .NET en lecture seule annotées Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute, à tous les champs de données publics et aux propriétés .NET autres qu'en lecture seule.  
  
-   Les indexeurs et les propriétés .NET paramétrées ne sont pas pris en charge.  
  
-   Les délégués et les événements ne sont pas pris en charge.  
  
-   Les génériques ne sont pas pris en charge.  
  
-   Les éléments de syntaxe de contrôle de flux tels que « foreach », « for », « do-while », « break » et « continue » ne sont pas pris en charge.  
  
-   Les opérateurs ternaires ne sont pas pris en charge. Par exemple, « ?; ».  
  
-   Vous pouvez ajouter des commentaires à la forme Expression, mais celle-ci doit contenir au moins une instruction.  
  
-   Les tableaux ne sont pas pris en charge.  
  
-   Lorsque la forme Expression est placée dans une forme Construire un message, vous ne pouvez pas procéder au contrôle de flux. Par exemple, « if-then-else » ou « while ».  
  
-   Toutes les instructions d'expression valides sont de la forme :  
  
    -   Dotted-name = expression;  
  
    -   Dotted-name = expression;  
  
 Vous pouvez utiliser l'Éditeur d'expression BizTalk pour entrer des expressions complexes rapidement et en toute simplicité, mais pas pour entrer une quantité arbitraire de code. Cela permet de distinguer le code du processus d'entreprise de son code d'implémentation.