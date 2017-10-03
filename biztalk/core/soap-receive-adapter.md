---
title: "Adaptateur de réception SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, receive adapters
- receive adapters, SOAP adapters
ms.assetid: bb968fa8-0515-4f3a-bb39-9effb83e960c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fac19580d6083ed1b0d4be315d3285acf14fcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-receive-adapter"></a>Adaptateur de réception SOAP
Vous utilisez l'adaptateur de réception SOAP pour recevoir des demandes de service Web. L'adaptateur de réception SOAP crée un objet de message BizTalk et promeut les propriétés associées vers le contexte du message.  
  
 Réception SOAP adaptateur URI doit être associé à une ou plusieurs orchestrations BizTalk ou les schémas qui ont été publiés comme service web avec le **Assistant Publication des Services Web BizTalk**. L'URI de l'adaptateur de réception SOAP doit être associé à un ou plusieurs schémas ou orchestrations BizTalk ayant été publiés comme service Web à l'aide de l'Assistant Publication de services Web BizTalk. En effet, le service Web publié joue le rôle de serveur proxy pour les orchestrations ou schémas BizTalk et transmet les requêtes et réponses échangées entre le client et les orchestrations ou les schémas BizTalk. Pour plus d’informations sur la publication d’orchestrations BizTalk ou schémas en tant que services web, consultez [publication de Services Web](../core/publishing-web-services.md).  
  
 Un emplacement de réception qui utilise l'adaptateur SOAP peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel). Lorsqu'un emplacement de réception unidirectionnel est configuré pour utiliser l'adaptateur SOAP, le service Web associé appelle l'assembly BizTalk lié au port de réception et renvoie l'état de la demande au client. Lorsqu'un emplacement de réception configuré comme requête-réponse (bidirectionnel) utilise l'adaptateur SOAP, le service Web associé appelle l'assembly BizTalk lié au port de réception, et renvoie un document de réponse au client. Pour plus d’informations sur les messages de réponse de demande, consultez [de messagerie requête-réponse](../core/request-response-messaging.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur SOAP ?](../core/what-is-the-soap-adapter.md)   
 [Recommandations de sécurité de l’adaptateur SOAP](../core/soap-adapter-security-recommendations.md)