---
title: "Interdépendances des propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ed5b75e-db1c-43d4-a287-fc4cd1c529f5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15e1a02d82d294c63a33c0682e77585a7934b8ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-interdependencies"></a>Interdépendances des propriétés

## <a name="overview"></a>Vue d'ensemble
Lorsque vous utilisez l'Éditeur BizTalk et plus particulièrement la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour modifier les valeurs de propriétés, vous pouvez remarquer qu'il existe une forte interdépendance entre les propriétés. Il arrive qu’en raison d’un paramètre particulier d'une propriété, toutes les autres propriétés soient automatiquement effacées, désactivées ou activées, ou encore apparaissent ou disparaissent complètement de la fenêtre Propriétés. Ces interdépendances sont trop nombreuses pour être toutes présentées. 

Toutefois, la liste suivante décrit quelques exemples courants pour vous permettre de vous faire une idée de la façon dont elles fonctionnent :  
  
-   Lors de la définition des propriétés d’un **Fieldelement** nœud ou **attribut de champ** nœud pour lequel un type de données est dérivé d’un type simple à l’aide du mécanisme de restriction, une toute nouvelle catégorie de propriétés devient disponible : **Restriction**. De plus, les propriétés de cette nouvelle catégorie sont activées ou désactivées selon que le type de données de base est un type chaîne ou un type numérique. Pour plus d’informations sur cette forme de dérivation de type simple, consultez [Simple Type dérivation à l’aide du mécanisme de Restriction](../core/simple-type-derivation-using-the-restriction-mechanism.md).  
  
-   Lors de la définition des propriétés d’un **élément de champ** nœud ou **attribut de champ** nœud pour lequel un type de données est dérivé d’un type simple à l’aide de la liste ou du mécanisme d’union, le **Base Type de données** propriété est modifiée en le **Type d’élément** propriété ou le **Types de membres** propriété, respectivement. Dans le dernier cas, la liste déroulante correspondante est modifiée de manière à inclure des cases à cocher, ce qui vous permet de sélectionner plusieurs types. Pour plus d’informations sur ces formes de dérivation de type simple, consultez [Simple Type dérivation à l’aide du mécanisme de liste](../core/simple-type-derivation-using-the-list-mechanism.md) et [Simple Type dérivation à l’aide du mécanisme d’Union](../core/simple-type-derivation-using-the-union-mechanism.md).  
  
-   Pour exposer les propriétés associées aux schémas de fichier plat, vous devez définir le **Extensions de l’éditeur de schéma** propriété de la **schéma** nœd à inclure le **Extension de fichier plat** . Les propriétés personnalisées associées aux autres extensions de l’éditeur, telles que l’extension EDI, sont exposées de la même façon : en choisissant l’extension correspondante à l’aide du **Extensions de l’éditeur de schéma** propriété.  
  
 Cette liste comprend des exemples destinés à illustrer les types d’interdépendances de propriété que vous observerez lors de l’utilisation de la fenêtre Propriétés, mais il ne s’agit pas d’une liste exhaustive de ces interdépendances.  
  
## <a name="see-also"></a>Voir aussi  
-  [Propriétés de nœud](../core/node-properties.md)   
-  Les propriétés suivantes[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
    -  Liste alphabétique des propriétés de nœud
    -  Propriétés de nœud de tous les schémas 
    -  Extensions de l'Éditeur de schéma