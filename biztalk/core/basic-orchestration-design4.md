---
title: Orchestration de base Design4 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, design
ms.assetid: 53f90bba-5786-49ca-b4d0-21601ec04045
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80a1ed1359370c6b048ed7e0753cd32f4ff787c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-orchestration-design"></a>Conception d'une orchestration de base
Lorsque vous créez une orchestration de base, vous recevez XML dans le port de réception de l’orchestration. Le contenu XML est ensuite envoyé au système principal pour traitement. Dans le système principal, une exception peut se produire que pu arrêter l’orchestration. Cette exception indique simplement que l'orchestration n'a pas été exécutée.  
  
 Lorsqu’une erreur se produit, l’appel est interrompu. Dans le journal de l'Observateur d'événements, vous pouvez consulter l'erreur et la raison de la défaillance.  
  
 Pour empêcher l'orchestration de passer à l'état Suspendu et rediriger l'erreur, vous pouvez créer une CatchExpression. Pour intercepter l'exception générée par le système principal et identifier la cause du problème, vous pouvez utiliser la forme Étendue dans votre orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling4.md)