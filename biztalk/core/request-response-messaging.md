---
title: "Messages de requête-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- request/response messaging, about request/response messaging
- SOAP adapters, message processing
- SOAP adapters, request/response messaging
- request/response messaging
- patterns, messages
- messages, request/response messaging
- request/response messaging, processing
- request/response messaging, SOAP adapters
- messages, patterns
ms.assetid: 1a2f79b5-1f44-4191-8ce1-b3c9043be4f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd612d5f41e4648625a2a28398f20ecf74e0a4e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="request-response-messaging"></a>Messages de requête-réponse
Dans un modèle de messages de type requête-réponse, le tiers expéditeur envoie un message de requête et le tiers destinataire renvoie un message de réponse. Il existe deux exemples types de traitement requête/réponse : l'interaction entre un navigateur et un serveur Web via l'adaptateur HTTP et le traitement du service Web à l'aide de l'adaptateur SOAP (Simple Object Access Protocol). Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les messages de requête et de réponse sont tous deux traités d'une manière classique par publication/abonnement. Ceci est important pour savoir à quel moment vous devez ajuster les performances d'une application BizTalk, parce qu'un système nécessitant un débit élevé peut être configuré autrement qu'un système requérant une faible latence pour chaque message individuel.  
  
 ![Demande &#47; Messages de réponse](../core/media/arch-request-response-1.gif "arch_request-réponse-1")  
  
 Lorsqu'un message est reçu par un adaptateur de réception de type requête/réponse, BizTalk Server publie le message demandé dans la base de données MessageBox. Ce message est ensuite reçu par l'abonné approprié qui correspond, sans doute, à une orchestration liée à un port de réception. Cet abonné formule un message de réponse et le publie dans la base de données MessageBox avec les propriétés qui ont provoqué son renvoi au port de réception duquel émane la requête. Enfin, le message de réponse est recueilli par le distributeur de la requête, à savoir l'adaptateur de réception qui a soumis la requête, et est renvoyé à l'application d'appel. Le diagramme ci-dessous fournit une représentation graphique détaillée de cette procédure.  
  
 ![Demande &#47; message de réponse reçu par l’adaptateur SOAP](../core/media/arch-request-response-2.gif "arch_request-réponse-2")  
  
 **Flux de message de demande/réponse reçu par l’adaptateur SOAP**  
  
1.  L'adaptateur SOAP soumet des messages au Gestionnaire des points de terminaison.  
  
2.  Ce gestionnaire publie le message dans la base de données MessageBox.  
  
3.  L'orchestration, qui est liée au port de réception et qui dispose donc d'un abonnement au message, reçoit celui-ci et le traite.  
  
4.  L'orchestration envoie un message de réponse qui est publié dans la base de données MessageBox.  
  
5.  Le Gestionnaire des points de terminaison reçoit le message de réponse.  
  
6.  Il renvoie la réponse à l'adaptateur SOAP.  
  
 Les implications de ce type de comportement sur les performances risquent de ne pas être suffisamment appréciées si l'implémentation interne n'est pas comprise. À l'origine, BizTalk Server est configuré pour des scénarios de débits élevés. Toutefois, il peut aussi être configuré pour un environnement avec de faibles débits et des besoins de latence peu élevée surtout dans des scénarios de requête/réponse. Plusieurs éléments doivent être pris en considération pour ce scénario. Tout d'abord, les abonnés trouvent des messages publiés via un mécanisme d'interrogation. Si l'intervalle d'interrogation est trop grand, les interactions de type requête/réponse risquent d'avoir une latence plus élevée que celle souhaitée.  
  
 Notez que dans ce scénario, il existe deux abonnements doivent être remplis : l’abonnement pour le message initial et celui pour le message de réponse et cela augmente l’impact de cet intervalle d’interrogation. Ensuite, les adaptateurs de réception sont configurés pour insérer des messages dans la base de données MessageBox par lots de taille variable. La plupart des adaptateurs vous permettent de configurer la taille de lot via l'interface de configuration type de l'adaptateur ou via des paramètres de BizTalk Server ou du Registre. Si le lot est trop volumineux, la latence des messages individuels peut être augmentée. Pour plus d’informations sur les caractéristiques de performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [planification des performances de débit soutenu](../core/planning-for-sustained-performance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)