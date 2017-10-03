---
title: "Types de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, correlation types
- correlation types, correlation sets
- correlation types
- validating, correlation types
- correlation types, about correlation types
- correlation types, validating
ms.assetid: 1aa5ca5c-c37d-4091-9f5d-331a6b202d4e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3da5fad8cb4edc1d6a528f481616b4f10efb71d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlation-types"></a>Types de corrélations
Chaque ensemble de corrélations est basé sur un **type de corrélation**, qui est simplement une liste de propriétés. Ces propriétés peuvent être relatives aux données contenues dans le message lui-même, ou au contexte qui décrit le système ou les messages non associés aux données transmises dans le message.  
  
 Vous pouvez utiliser un type de corrélation dans plus d'un ensemble de corrélations. Si vous avez besoin de corréler différentes valeurs de propriétés dans un type de corrélation, vous devez créer un nouvel ensemble de corrélations ; chaque ensemble de corrélations ne peut être initialisé qu'une seule fois.  
  
 Vous pouvez promouvoir des propriétés dans un schéma de propriété afin de déclarer que certaines propriétés dans un message sont accessibles à votre orchestration. Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
> [!CAUTION]
>  Ne définissez pas la propriété définie par le système **BTS. CorrelationToken** qui est associé à chaque message. Elle est utilisée par le moteur pour la corrélation des messages, et la modifier pourrait faire perdre des messages à votre orchestration.  
  
## <a name="validating-message-correlation-on-send-actions"></a>Validation de la corrélation des messages dans les actions Envoi  
 Vous pouvez valider les propriétés d'un message que vous envoyez depuis votre orchestration pour vous assurer qu'il reflète les propriétés de son ensemble de corrélations. Cette validation est désactivée par défaut. Pour plus d’informations sur comment l’activer, consultez [Validation d’exécution pour le moteur d’Orchestration](../core/runtime-validation-for-the-orchestration-engine.md).