---
title: "Application cliente de l’adaptateur interAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdab4624-0fc2-42a3-9867-8f77e144b40c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac8f459799f59b63976c29f4a87dfe22b56e7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-client-application"></a>Application cliente de l’adaptateur interAct
Interagir de requête d’application cliente adaptateur les messages sont des documents XML passés à partir de l’application cliente pour le lien de SWIFTNet côté client (SNL). Messages de ce type se produisent en tant que la première partie des primitives SWIFTNet demande/réponse testés côté client.  
  
 Cette rubrique décrit le message SwInt:ExchangeRequest. Il est utilisé pour les appels de côté client « synchrones » à SWIFTNet. Dans ce contexte, « synchrone » signifie que l’appel de fonction bloque l’application cliente, en la forçant à patienter jusqu'à ce que la réponse est reçue à partir de l’application côté serveur. (Ou, sinon, une condition d’erreur se produit et cette erreur est renvoyée au client.)  
  
 Les blocs de chiffrement (SwSec:Crypto), s’ils existent, contient les résultats de la signature de message et/ou le traitement de la vérification. En outre, à certaines étapes de traitement, ils peuvent contenir des instructions qui régissent le traitement des services de chiffrement qui doit être effectuée par le SNL.  
  
## <a name="interact-adapter-payload-format"></a>Interagir de Format de charge utile de l’adaptateur  
 La charge utile de demande contient le contenu de message d’entreprise. La structure de la charge utile doit être conforme aux exigences du code XML bien formé (cela signifie simplement que la charge utile n’interrompt pas l’analyse XML, mais par conséquent, il n’a pas d’utiliser la structure du document XML). Si la Validation du Message SWIFTNet est appliquée, il existe autres exigences structurelles à laquelle la charge utile doit être conforme. À part cela, la structure de charge utile et le contenu est déterminés par l’application d’entreprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)