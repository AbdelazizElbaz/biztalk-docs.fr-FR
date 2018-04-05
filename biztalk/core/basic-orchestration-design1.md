---
title: Orchestration de base Conception1 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, design
ms.assetid: fd2e1d89-6230-4634-8a33-1cda26fd55f5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d302428cd713b826e7c4629ea75eb6f6268d7400
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-orchestration-design"></a>Conception d'une orchestration de base
Lorsque vous créez une orchestration de base, vous recevez XML sur le port de réception de l’orchestration. Le contenu XML est envoyé au système principal pour traitement. Dans le système principal, une exception susceptible d'arrêter l'orchestration et de générer une erreur peut survenir. Exception qui est généré, fournit des informations que l’orchestration n’a pas abouti.  
  
 ![](../core/media/jdeoneworld-01.gif "JdeOneWorld_01")  
Gestion des exceptions  
  
 Lorsqu’une erreur se produit, l’appel est interrompu. Dans le journal de l'Observateur d'événements, vous pouvez consulter l'erreur et la raison de la défaillance.  
  
 Pour empêcher l'orchestration de passer à l'état Suspendu et rediriger l'erreur, vous pouvez créer une CatchExpression. Pour intercepter l’exception générée par le système principal et pour aider à identifier la cause du problème, vous pouvez utiliser la **étendue** forme dans l’orchestration.  
  
 ![](../core/media/jdeoneworld-02.gif "JdeOneWorld_02")  
Total de la gestion des exceptions  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling1.md)