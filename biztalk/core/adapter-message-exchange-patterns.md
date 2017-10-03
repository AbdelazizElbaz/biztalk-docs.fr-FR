---
title: "Modèles d’échange de Message adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54a3fc8f-33d0-4b7e-ad4c-b00912dc3328
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f42368d8687bbed4cbce60243a3b8528364b5fda
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-message-exchange-patterns"></a>Modèles d’échange de Message de l’adaptateur
L'infrastructure d'adaptateurs BizTalk prend en charge une grande variété de modèles d'échange de messages auxquels peuvent avoir recours les adaptateurs dans le cadre de divers scénarios de messagerie.  
  
## <a name="one-way-asynchronous"></a>Unidirectionnel (asynchrone)  
 Le flux de messages de ce concept s'effectue dans une seule direction.  
  
 Dans ce modèle d'échange de messages, les messages sont transmis de manière unidirectionnelle vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] via un adaptateur. Le moteur de messagerie publie le message dans la base de données MessageBox. Si une orchestration possède un abonnement actif à un message de ce type, le message lui est acheminé.  
  
 Une fois le message traité, il est de nouveau publié par l'orchestration dans la base de données MessageBox avant d'être acheminé vers un adaptateur pour être transmis à un point de terminaison.  
  
 Lorsqu'il est soumis au moteur, aucune réponse n'est attendue. Du côté sortant, aucune réponse n'est attendue lorsque le message est transmis. Ce concept fait essentiellement référence à la messagerie asynchrone. Il s'agit principalement du bloc de construction de base utilisé par le moteur pour tous les scénarios de messagerie.  
  
## <a name="request-response-style-protocols-sync-on-async"></a>Protocoles de style requête-réponse (synchrone sur asynchrone)  
 Le scénario de requête-réponse consiste à recevoir un message de requête, à le traiter et à envoyer un message de réponse. Ce concept est également appelé synchrone-sur-asynchrone, car l'architecture [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sous-jacente est asynchrone pour des raisons d'évolutivité. L'architecture du moteur de messagerie BizTalk, toutefois, permet d'utiliser un modèle d'échange de messages synchrone sur des échanges asynchrones. Pour ce faire, le moteur gère la tâche complexe consistant à corréler les messages de requête et réponse sur une architecture évolutive en liant un certain nombre d'échanges de messages asynchrones afin d'afficher une interface synchrone.  
  
 Par exemple, une page Web qui vérifie le stock peut être un appel SOAP vers SOAP BizTalk : adaptateur de réception. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]orchestre une série de services Web qui regroupent les informations et la retourner dans une seule réponse SOAP. Pour le client, cela ressemble à un appel SOAP synchrone, mais en fait, le moteur regroupe un certain nombre d'échanges de messages asynchrones.  
  
## <a name="solicit-response-style-protocols"></a>Protocoles de style sollicitation-réponse  
 Ce scénario commence par l'envoi d'un message de sollicitation et se termine avec la réception d'un message de réponse. Il est dit « sollicitation-réponse », car le message initial envoyé sollicite une réponse de la part du point de terminaison. Il peut s'agir d'une orchestration effectuant un appel HTTP sortant (sollicitation d'une réponse) et attendant une réponse.  
  
## <a name="request-multiresponse"></a>Requête-multiréponse  
 Ce scénario est similaire au scénario de requête-réponse, sauf que pour une requête donnée, plusieurs réponses peuvent être renvoyées. Les API permettent de spécifier un délai d'expiration et toutes les réponses reçues pendant ce délai sont renvoyées à l'adaptateur de réception.  
  
## <a name="loop-back"></a>Bouclage  
 Ce scénario est similaire au scénario de requête-réponse, Le message de requête est publié normalement, mais le moteur veille à ce que le message de réponse soit réacheminé vers l'instance d'adaptateur qui a publié le message de requête. La requête étant publiée dans la base de données MessageBox, l'infrastructure de suivi garantit que les messages de réponse et de requête sont tous les deux suivis. Ce scénario permet à un pipeline d'envoi de traiter un message, puis d'obtenir immédiatement que le message de sortie soit renvoyé vers l'adaptateur pour de nouveaux traitements.  
  
 Exemple : un client qui aurait besoin d'un reçu pour un message. Le message entrant est publié dans la base de données MessageBox. Ce message et le reçu sont tous deux retournés à l'adaptateur dans le même lot. Dans ce cas, une copie du message entrant est effectuée, une instance est retournée au client et l'autre est traitée de manière normale. Ce scénario requiert également l'écriture d'un désassembleur XML personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md)