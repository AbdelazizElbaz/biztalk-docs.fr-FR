---
title: "Règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, actions
- Business Rules Engine, business rules
- business rules, about business rules
- business rules, conditions
- business rules, facts
- business rules
ms.assetid: b288dd07-33f1-42fe-bbfb-02674ef3b3ca
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35f398cf98181d17833be79fbe9d282e8515e052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rules"></a>Règles
Les règles d'entreprise sont des instructions déclaratives qui régissent le fonctionnement des processus d'entreprise. Une règle se compose d'une condition et d'actions. La condition est évaluée, et si elle a la valeur **true**, le moteur de règles initie une ou plusieurs actions.  
  
 Dans l'infrastructure des règles d'entreprise, les règles sont définies selon le format suivant :  
  
 IF`condition` PUIS`action`  
  
 Prenons l'exemple suivant :  
  
 IF le montant est inférieur ou égal aux fonds disponibles  
  
 THEN exécute la transaction et imprime un reçu  
  
 Cette règle détermine si une transaction sera réalisée en appliquant la logique d'entreprise (comparaison de deux valeurs monétaires) à des données ou des faits (montant de transaction et fonds disponibles).  
  
 Vous pouvez utiliser l'Éditeur des règles d'entreprise pour créer, modifier, déployer et définir la version des règles d'entreprise. Vous pouvez également effectuer ces tâches à l'aide d'un programme.  
  
## <a name="conditions"></a>Conditions  
 Une condition est une expression de type vrai/faux (booléenne) composée d'un ou plusieurs prédicats qui sont appliqués à des faits.  
  
 Dans notre exemple, le prédicat **inférieure ou égale à** est appliqué aux faits **quantité** et **fonds disponibles**. Cette condition sera toujours la valeur **true** ou **false**.  
  
 Les prédicats peuvent être combinées avec les opérateurs logiques **AND**, **ou**, et **pas** pour former une expression logique potentiellement volumineuse, mais sera toujours évaluée en soit **true** ou **false**.  
  
## <a name="actions"></a>Actions  
 Les actions sont les conséquences fonctionnelles de l'évaluation des conditions. Si une condition de règle est satisfaite, une ou plusieurs actions correspondantes sont exécutées.  
  
 Dans notre exemple, « exécuter la transaction » et « imprimer un reçu » sont les actions exécutées si et seulement si la condition (« IF le montant est inférieur ou égal aux fonds disponibles ») a la valeur vrai.  
  
 Les actions sont représentées dans l'infrastructure des règles d'entreprise en appelant des méthodes ou en définissant des propriétés pour des objets, ou en exécutant des opérations de définition sur des documents XML ou des tables de base de données.  
  
## <a name="facts"></a>Faits  
 Les faits sont les données auxquelles les règles s'appliquent. Dans notre exemple, les faits sont « montant » et « fonds disponibles ». Pour plus d’informations, consultez [faits](../core/facts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des règles et stratégies](../core/how-to-create-policies-and-rules.md)