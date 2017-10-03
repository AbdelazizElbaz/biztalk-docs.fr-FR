---
title: "Comment analyser plusieurs objets du même Type dans une règle d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, multiple types
- Business Rules Framework, programming
ms.assetid: ff9790c1-13b0-4eee-8cac-d4f25ef5f0b7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a1e4d2fb01513b1d4d314264ab74b84d3a0223a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule"></a>Comment analyser plusieurs objets du même Type dans une règle d’entreprise
Dans plusieurs scénarios, vous rédigerez une règle d'entreprise en fonction d'un type et chaque instance de ce type déclarée dans le moteur devra être analysée et traitée séparément par la règle. Dans certains scénarios, cependant, vous souhaiterez analyser simultanément plusieurs instances d'un certain type dans une règle.  
  
 Prenons par exemple une règle qui utilise des instances de la **FamilyMember** classe.  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember.Role == Son  
AND FamilyMember.Surname == FamilyMember.Surname  
THEN FamilyMember.AddChild(FamilyMember)  
```  
  
 La règle identifie un **FamilyMember** instance qui est un **père** et une autre instance est un **fils**. Si les instances sont liées par le nom de famille, le **fils** instance est ajoutée à une collection d’enfants sur l’instance père. Si chaque **FamilyMember** instance est analysée séparément dans la règle, la règle serait déclenchée jamais, car dans ce scénario, le **FamilyMember** a uniquement un seul rôle,**père** ou **fils**.  
  
 De ce fait, vous devez indiquer au moteur que plusieurs instances doivent être analysées ensemble dans une règle. En outre, vous devez définir un moyen de différencier l'identité de chaque instance dans la règle. Le **ID d’Instance** propriété est utilisée pour fournir cette fonctionnalité. Ce champ est disponible dans la fenêtre Propriétés lors de la sélection d'un fait dans l'Explorateur de faits. Vous devez modifier la valeur du champ avant de déplacer un fait ou un membre dans une règle.  
  
 À l’aide de la **ID d’Instance** propriété, la règle est reconstruite. Pour les arguments de règle qui utilisent la **fils** instance de **FamilyMember**, le **ID d’Instance** champ est modifié à partir de la valeur par défaut de 0 à 1. Lorsque l’ID d’Instance est passée de 0, et le fait ou le membre est déplacé dans l’éditeur de règles, la valeur de l’ID d’Instance s’afficheront dans la règle après la classe.  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember(1).Role== Son  
AND FamilyMember.Surname == FamilyMember(1).Surname  
THEN FamilyMember.AddChild(FamilyMember(1))  
```  
  
 Maintenant, supposons qu’un **père** instance et un **fils** instance sont déclarées dans le moteur. Le moteur évalue la règle par rapport aux diverses combinaisons d'instances. En supposant que le **père** et **fils** instance ont le même nom, le **fils** instance sera ajoutée à la **père** instance en tant que prévu.  
  
> [!NOTE]
>  Le **ID d’Instance** est utilisée uniquement dans le contexte d’une version d’évaluation de règles donné. Elle n'est pas ajoutée à une instance d'objet au cours de l'exécution de la stratégie et elle n'a pas de lien avec l'ordre dans lequel les objets sont déclarés. Chaque instance d'objet est évaluée dans tous les arguments de règle associés à ce type.