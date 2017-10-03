---
title: "Scénarios à l’aide de Transactions à Long terme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions, long-running
- long-running transactions, timeouts
- transactions, examples
- long-running transactions, examples
- long-running compensations
- examples, long-running transactions
- examples, custom compensations
ms.assetid: 76b3e0f8-44dc-419e-a73a-c2908b1d8795
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05ac14bc6e333f963dda7cb9b33d1ebf371c0546
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenarios-using-long-running-transactions"></a>Utilisation de transactions à long terme
Les scénarios suivants décrivent l'utilisation des transactions à long terme.  
  
## <a name="scenario-1-using-long-running-transactions-with-timeouts"></a>Scénario 1 : Utilisation de longues Transactions avec des délais d’attente  
 Les étendues à long terme peuvent être associées à un délai, qui est une durée logique au terme de laquelle le travail à long terme doit être fini. Si l’étendue ne se termine pas dans le délai spécifié, une exception de système prédéfini **TimeoutException** est déclenché.  
  
 Vous pouvez créer des processus à long terme soit en marquant l'intégralité de l'orchestration à long terme soit en imbriquant les autres étendues dans une étendue à long terme externe. Dans le premier cas, un gestionnaire d'exceptions fourni par le système est exécuté, tandis que le second cas permet l'association de gestionnaires d'exceptions spécifiques à l'étendue externe. Le gestionnaire d'exceptions fourni par le système exécute le gestionnaire de compensation pour chacune des étendues transactionnelles imbriquées correctement terminées, le cas échéant, dans l'ordre inverse de leur achèvement. Vous pouvez obtenir le même résultat par le biais d'une auto-compensation en utilisant la forme Compenser dans le gestionnaire d'exceptions pour une transaction à long terme.  
  
 L'orchestration suivante illustre l'association des délais aux transactions à long terme.  
  
 **Transactions à long terme avec délais d’attente**  
  
 ![Transactions de longue avec délais d’attente](../core/media/bts-trans-orch-fig7.gif "BTS_Trans_Orch_Fig7")  
  
 Parfois, il est nécessaire d'assurer l'interface avec les systèmes hérités fonctionnant en mode par lots. Ce scénario présente un bon de commande reçu et envoyé au système hérité. Le système hérité traite le bon de commande et renvoi un accusé de réception de bon de commande. L'opération d'envoi initialise un ensemble de corrélations en utilisant le numéro du bon de commande et l'opération de réception suit cet ensemble de corrélations. L'opération de réception est une étendue à long terme avec une valeur de délai.  
  
 Le moteur d'orchestration met l'instance d'orchestration en attente de la réception. La corrélation garantit que la même instance d'orchestration est appelée une fois le message reçu. Si l’accusé de réception de commande d’achat n’arrive pas dans l’intervalle de temps spécifié par les valeurs de délai d’attente, un **TimeoutException** sera levée.  
  
## <a name="scenario-2-using-long-running-transactions-with-custom-compensation"></a>Scénario 2 : Utilisation de longues Transactions avec Compensation personnalisée  
 Les orchestrations suivantes montrent comment associer et appeler des compensations personnalisées liées à des orchestrations entières. Ce scénario insère un nouveau client et des informations de commande pour le client. La logique de l'orchestration impose qu'en cas d'échec de l'insertion de la commande, l'insertion du client doit être annulée. L'insertion du client peut être effectuée par un système hérité, et donc illustrée dans une orchestration pouvant être appelée séparément. L’orchestration appelée a la **personnalisé** propriété définie pour la compensation, qui fournit une feuille distincte pour le processus de compensation. La compensation doit supprimer le client récemment inséré.  
  
 L'orchestration appelante dispose d'une étendue à long terme pour effectuer l'insertion de la commande. Cette étendue est imbriquée dans une étendue à long terme. L'étendue externe dispose d'un gestionnaire d'exceptions associé pour intercepter les exceptions. Le gestionnaire utilise la forme Compenser pour appeler l'exception personnalisée associée à l'orchestration appelée pour annuler les modifications qui pourraient avoir été apportées pendant l'appel de l'orchestration.  
  
 **Transactions à long terme avec compensation personnalisée**  
  
 ![Transactions de longue avec compensation personnalisée](../core/media/bts-trans-orch-fig8.gif "BTS_Trans_Orch_Fig8")  
  
 **Orchestration appelée (principal)**  
  
 ![Appelée orchestration &#40; principal &#41; ] (../core/media/bts-trans-orch-fig9.gif "BTS_Trans_Orch_Fig9")  
  
 **Orchestration appelée (compensation)**  
  
 ![Appelée orchestration &#40; compensation &#41; ] (../core/media/bts-trans-orch-fig10.gif "BTS_Trans_Orch_Fig10")