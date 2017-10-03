---
title: "Messages d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages
- ports, error messages
- Catch Exception block [Orchestration Designer], error messages
- error messages, receiving
- messages, errors
- error messages, sending
ms.assetid: 33d62260-b5e0-4d14-b2d2-996733d588e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4127fd5718ee910cb298436c0d0f7058ccba55b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fault-messages"></a>Messages d'erreur
Les ports avec requête-réponse peuvent être associés à des messages d'erreur, de sorte que si une erreur survient après l'envoi d'une requête, le service de réponse peut communiquer l'erreur au demandeur, au lieu de la réponse.  
  
 Chaque opération d'un port avec requête-réponse peut gérer un nombre arbitraire d'erreurs différentes. Un message d'erreur peut être de n'importe quel type, mais le type du message doit être unique pour chaque opération et ne doit pas être celui utilisé par la réponse.  
  
## <a name="receiving-fault-messages"></a>Réception de messages d'erreur  
 Si votre port envoie une requête avant de recevoir une réponse, vous avez la possibilité de recevoir un ou plusieurs types de messages d'erreur différents.  
  
 Vous pouvez configurer un **intercepter l’Exception** bloc pour gérer un message d’erreur entrant en sélectionnant l’erreur appropriée à partir de l’opération de port requête-réponse en tant que son Type d’objet Exception.  
  
## <a name="sending-fault-messages"></a>Envoi de messages d'erreur  
 Si votre port reçoit une réponse avant d'envoyer une requête, vous avez la possibilité d'envoyer un ou plusieurs types de messages d'erreur différents.  
  
 Si par exemple, votre orchestration rencontre une condition d’erreur et lève une exception, vous pouvez envoyer un message d’erreur depuis le **intercepter l’Exception** bloc qui gère l’exception. Vous créez un message d'erreur du type approprié pour qu'il transmette la situation au service participant et spécifiez ce message sur une forme Envoi qui utilisera l'erreur correspondante dans l'opération du port.  
  
## <a name="see-also"></a>Voir aussi  
 [Exceptions](../core/exceptions.md)