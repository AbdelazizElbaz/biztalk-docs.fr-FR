---
title: "Optimisation des performances de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, performance
- performance, MSMQ adapters
- configuring [MSMQ adapters], performance
ms.assetid: f8537ea8-a96e-4874-bcaf-cd1442a50bd4
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e554de9b00869db4a258f03984fe1ebc71e99c38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-performance-of-the-msmq-adapter"></a>Optimisation des performances de l’adaptateur MSMQ
L'optimisation de l'adaptateur MSMQ diffère entre les côtés envoi et réception. Vous contrôlez l'optimisation côté réception en définissant une propriété sur l'emplacement de réception. Côté envoi, vous pouvez contrôler l'optimisation à l'aide d'une orchestration.  
  
## <a name="receive-optimization"></a>Optimisation de la réception  
 Côté réception, vous pouvez configurer l'adaptateur pour qu'il n'utilise qu'un seul thread d'exécution. Indique si l’adaptateur utilise un thread unique ou plusieurs threads varie selon le paramètre de la **traitement chronologique** propriété sur l’emplacement de réception, comme suit :  
  
-   Lorsque la propriété est **True**, l’adaptateur ne fonctionne que sur un seul thread. Ceci limite l'adaptateur à un message à la fois et permet d'économiser de la mémoire. Notez qu’il définit efficacement **taille de lot** à un (1), quelle que soit la valeur affectée à ce dernier dans la feuille de propriétés.  
  
-   Lorsque **traitement chronologique** est **False**, l’adaptateur s’exécute plusieurs threads et peut traiter plusieurs messages à la fois, augmentant ainsi les performances.  
  
 Vous devez définir **traitement chronologique** à **True** si vous placez une prime sur la gestion des ressources du serveur, ou si le nombre ou la taille des messages peut saturer la mémoire disponible.  
  
 Vous pouvez également contrôler l’utilisation de la mémoire en réduisant la valeur de **taille de lot** sur l’emplacement de réception. Une taille de lot réduite conserve un plus petit nombre de messages en mémoire, et utilise donc moins de mémoire.  
  
 Le placement des ports d'envoi et des emplacements de réception sur des ordinateurs distincts peut également réduire l'utilisation de la mémoire.  
  
## <a name="send-optimization"></a>Optimisation côté envoi  
 Côté envoi, vous pouvez obtenir un traitement par message unique à l'aide de l'exemple d'orchestration. Celui-ci envoie un message unique, puis attend de recevoir un accusé de réception pour envoyer le message suivant. Pour plus d’informations, consultez [comment créer des emplacements de réception MSMQ et les Ports d’envoi à partir de Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).  
  
## <a name="remote-transactional-read-operations"></a>Opérations de lectures transactionnelles distantes  
 Avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], l'adaptateur MSMQ est capable d'effectuer des opérations de lectures distantes à partir de files d'attente MSMQ transactionnelles.  Cela est dû au fait que MSMQ 4.0 et les versions ultérieures prennent en charge les opérations de lectures transactionnelles distantes.  Cependant, les opérations de lectures transactionnelles sont des opérations généralement lentes. Pour optimiser les performances, elles ne doivent être utilisées qu'en dernier recours.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer un MSMQ emplacement de réception](../core/how-to-configure-an-msmq-receive-location.md)   
 [Comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md)   
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)