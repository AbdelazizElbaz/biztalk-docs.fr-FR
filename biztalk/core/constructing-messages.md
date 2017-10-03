---
title: Construction de Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- multi-part message types
- messages, modifying
- multi-part message types, about multi-part message types
- modifying, messages
- messages, creating
ms.assetid: c9fc1e97-ff53-42e2-848c-6c8fae7c9122
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fa87c4f3400a80ce83df132747d0004232323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-messages"></a>Construction de Messages
Vous construisez un message à chaque vous fois que vous introduisez un message dans votre orchestration, soit en le recevant, soit en attribuant des valeurs à une variable de message. Tout message que vous construisez doit avoir un type de message, de manière à ce que le moteur d'exécution dispose d'une description complète de l'objet avec lequel il travaille. Le type de message à parties multiples peut être défini par l'utilisateur, être une classe .NET ou être un schéma. Vous pouvez construire des messages de différentes manières : vous pouvez appeler une classe .NET pour créer un message, affecter un message à un autre ou utiliser une transformation pour mapper certaines valeurs au sein d’un message aux valeurs d’un autre message. Les messages peuvent également être construits par des actions de réception ou lorsque votre orchestration accepte un message en tant que paramètre.  
  
> [!NOTE]
>  Un type de message à parties multiples ne contient pas forcément plusieurs parties. Il peut très bien n'en contenir qu'une.  
  
> [!IMPORTANT]
>  Les messages sont immuables dans BizTalk : une fois que vous avez construit un message original, vous ne pouvez plus le modifier. Si vous avez besoin d'apporter une modification, vous devez construire une nouvelle copie du message et y attribuer les valeurs appropriées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment configurer la forme construire un Message](../core/how-to-configure-the-construct-message-shape.md)  
  
 [Comment configurer la forme assignation du Message](../core/how-to-configure-the-message-assignment-shape.md) 
  
 [Comment configurer la forme Transformer](../core/how-to-configure-the-transform-shape.md) 
  
 [Références de message dans la forme assignation du Message](../core/message-references-in-message-assignment-shape.md)  
  
 [Références de message dans le Code utilisateur](../core/message-references-in-user-code.md)  
  
 [Utilisation des XPaths dans une assignation de Message](../core/using-xpaths-in-message-assignments.md)  
  
 [À l’aide de XPath Non canoniques dans une assignation de Message](../core/using-non-canonical-xpaths-in-message-assignments.md)  
  
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)  
  
 [Ajout de nœuds pour les Messages dans le Code utilisateur](../core/appending-nodes-to-messages-in-user-code.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md)