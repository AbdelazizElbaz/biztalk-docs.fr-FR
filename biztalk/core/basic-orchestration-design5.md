---
title: Orchestration de base Design5 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, design
- exception handling, orchestration design
ms.assetid: 0941d617-e30c-4ca7-852f-193e16781ca7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224b8e507fc9319a2a4b66006914b3ebc27a8421
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-orchestration-design"></a>Conception d'une orchestration de base
Lorsque vous créez une orchestration de base dans l'adaptateur BizTalk pour PeopleSoft Enterprise, vous recevez le contenu XML sur le port de réception de votre orchestration. Le contenu XML est ensuite envoyé au système principal pour traitement. Dans le système principal, une exception peut se produire qui serait arrêter l’orchestration et générer une erreur. Cette erreur, qui indique simplement que l'orchestration n'a pas été exécutée, n'est pas véritablement utile pour déterminer la cause de l'erreur.  
  
 ![](../core/media/siebeladapter-15-exceptionhandling-start.gif "SiebelAdapter_15_ExceptionHandling_Start")  
Gestion des exceptions  
  
 Lorsqu'une erreur survient, l'appel est interrompu et défini sur FAILED dans le journal d'audit. Cliquer avec le bouton droit sur FAILED dans le journal d'audit permet d'ouvrir un message contextuel. Lorsque vous cliquez sur la sélection de rapports, l’erreur et la raison de l’échec à partir du système principal sont affichés.  
  
 Pour empêcher l'orchestration de passer à l'état Suspendu et rediriger l'erreur, vous pouvez créer une CatchExpression. Pour intercepter l'exception générée par le système principal et identifier la cause de l'erreur, vous pouvez utiliser la forme Étendue dans votre orchestration.  
  
 ![](../core/media/siebeladapter-16-exceptionhandling-total.gif "SiebelAdapter_16_ExceptionHandling_Total")  
Total de la gestion des exceptions  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling2.md)