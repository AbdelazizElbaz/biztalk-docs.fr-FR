---
title: "À l’aide de la messagerie BizTalk moteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Messaging Engine
- adapters, TransportProxy object
- Messaging Engine, adapters
- Messaging Engine, architecture
- TransportProxy object
- Messaging Engine, how to
- architecture, Messaging Engine
- messages, Messaging Engine
ms.assetid: e6b6d1ec-38cd-4721-9673-ae40da003dec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 701ed3e82eb75b98a948313a99bb4debc65a8cce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-messaging-engine"></a>Utilisation du moteur de messagerie BizTalk
Le diagramme suivant illustre l'architecture du moteur de messagerie. Il reflète un scénario dans lequel un message est reçu par un adaptateur et est envoyé dans BizTalk Server.  
  
 ![](../core/media/ebiz-prog-messaging1.gif "ebiz_prog_messaging1")  
Architecture du moteur de messagerie  
  
 Chaque adaptateur possède sa propre instance d’un **TransportProxy** objet qu’il utilise pour interagir avec le moteur de messagerie. Les adaptateurs fonctionnent par lots en fonction du moteur de messagerie. Ces lots sont traités de façon atomique. Un lot est un ensemble d'opérations tel que SubmitMessage, SuspendMessage ou DeleteMessage.  
  
 Ce qui suit est la séquence d'événements correspondant au scénario dans lequel un adaptateur envoie un message au moteur de messagerie :  
  
1.  L'adaptateur crée un message et connecte le flux de données au message.  
  
2.  L'adaptateur reçoit un nouveau lot du moteur de messagerie.  
  
3.  L'adaptateur ajoute le message au lot à envoyer.  
  
4.  Le lot est validé et mis en file d'attente dans la réserve de threads du moteur de messagerie.  
  
5.  La réserve de threads du moteur de messagerie commence à traiter le nouveau lot.  
  
6.  Le message est traité dans le pipeline de réception.  
  
7.  Le pipeline de réception génère zéro ou plusieurs messages. Les pipelines peuvent utiliser des messages dès lors qu'ils ne renvoient pas d'erreurs. Les pipelines de réception peuvent produire plusieurs messages. C'est le cas généralement quand le composant désassembleur désassemble un seul échange en plusieurs messages. En général, le pipeline de réception convertit le message envoyé au format XML.  
  
8.  Le ou les messages générés par le pipeline sont traités dans le mappeur si le mappage est configuré.  
  
9. Le ou les messages sont publiés dans l'agent des messages ou dans la base de données MessageBox.  
  
10. Le moteur de messagerie rappelle l'adaptateur pour l'informer du résultat du lot de travail.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Traitement des échanges récupérables](../core/recoverable-interchange-processing.md)  
  
-   [Livraison chronologique des messages](../core/ordered-delivery-of-messages.md)  
  
-   [Gestion des erreurs](../core/error-handling.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server traite les Messages volumineux](../core/how-biztalk-server-processes-large-messages.md)   
 [Caractéristiques de performances du moteur](../core/engine-performance-characteristics.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [À l’aide de l’outil Microsoft BizTalk LoadGen 2007](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)