---
title: Gestion des erreurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Messaging Engine, errors
- errors, Messaging Engine
- errors, messages
- messages, errors
ms.assetid: ebc889cc-eeac-483c-baf3-407a218f6d14
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cbf0d898f7af193220cf8f1c24e809aefa1b782
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-handling"></a>Gestion des erreurs
Le parcours que suit un message dans le sous-système de messagerie de BizTalk Server comporte plusieurs points de traitement et de transfert. Tout au long de ce parcours, des erreurs peuvent se produire au niveau de l'infrastructure de BizTalk Server et des éléments d'application, au nombre desquels on compte les composants de pipeline personnalisés et les orchestrations.  
  
 Cette section et celles qu'elle contient sont consacrées aux modes d'échec typiques de phases connues du traitement et à la manière dont ces modes sont résolus grâce à la configuration de BizTalk Server et aux éléments fournis par l'application, des orchestrations par exemple. Les échecs peuvent notamment avoir une incidence sur la disposition du message, sur les diagnostics capturés et consignés et sur les considérations opérationnelles.  
  
 Les événements qui se produisent en cas d'échec d'un message dépendent de l'emplacement de l'échec et de l'état du routage du message et du traitement d'échange récupérable. Le tableau suivant récapitule le comportement en cas d'échec et l'emplacement de reprise pour les échecs de pipeline et d'abonnement.  
  
|Type d'échec|Routage des messages ayant échoué|Traitement des échanges récupérables|Comportement en cas d'échec|Emplacement de reprise|  
|------------------|----------------------------|----------------------------------------|----------------------|---------------------|  
|Pipeline|Désactivé|Désactivé|Le message est suspendu avant le pipeline.|Avant le pipeline.|  
|Pipeline|Désactivé|Activé|Le message est suspendu après le pipeline.|Avant le pipeline. Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).|  
|Pipeline|Activé|Désactivé|Le message est publié avec des propriétés de contexte de message de rapport d'erreur promues.|Le message n'est pas suspendu. Pour plus d’informations sur le routage des messages ayant échouées, consultez [à l’aide d’échec Message Routing](../core/using-failed-message-routing.md).|  
|Pipeline|Activé|Activé|Message est publié avec les propriétés de contexte de message de rapport d’erreur promues.|Le message n'est pas suspendu.|  
|Abonnement|Désactivé|Désactivé|Message est interrompu avant le pipeline. Rapport d'échec du routage créé.|Le message reprendra avant le pipeline. Le rapport d'échec de routage ne peut être repris.|  
|Abonnement|Désactivé|Activé|Message est suspendu après le pipeline. Rapport d'échec du routage créé.|Le message reprendra avant le pipeline. Le rapport d'échec de routage ne peut être repris. Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).|  
|Abonnement|Activé|Désactivé|Message est publié avec les propriétés de contexte de message de rapport d’erreur promues. Rapport d'échec du routage créé.|Le message n'est pas suspendu. Le rapport d'échec de routage ne peut être repris. Pour plus d’informations sur le routage des messages ayant échouées, consultez [à l’aide d’échec Message Routing](../core/using-failed-message-routing.md).|  
|Abonnement|Activé|Activé|Message est publié avec les propriétés de contexte de message de rapport d’erreur promues. Rapport d'échec du routage créé.|Le message n'est pas suspendu. Le rapport d'échec de routage ne peut être repris.|  
  
 Bon nombre de ces modes d'échec énumérés correspondent à des composants spécifiques de BizTalk Server, conçus pour résoudre le mode d'échec et parmi lesquels on trouve le traitement des échanges récupérables et le signalement des erreurs. D'autres modes d'échec ont trait à la manière dont BizTalk Server communique les informations d'échec aux éléments d'application et, à l'inverse, à la façon dont les éléments d'application tels que des composants de pipeline personnalisés, des adaptateurs et des orchestrations, communiquent les informations d'échec à BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À l’aide de routage des messages ayant échoué](../core/using-failed-message-routing.md)  
  
-   [Comment activer le routage des Messages ayant échoué](../core/how-to-enable-routing-for-failed-messages.md)  
  
-   [À l’aide des accusés de réception](../core/using-acknowledgments.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des échanges récupérables](../core/recoverable-interchange-processing.md)   
 [Types d’échecs de Message](../core/types-of-message-failures.md)