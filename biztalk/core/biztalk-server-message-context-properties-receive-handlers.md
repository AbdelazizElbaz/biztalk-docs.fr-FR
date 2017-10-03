---
title: "Propriétés de contexte de Message BizTalk Server (gestionnaires de réception) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message context properties
- receive handlers, message context properties
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a60896a8e1cace909a160c1dc942e63e9258d85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-message-context-properties-receive-handlers"></a>Propriétés de contexte de Message BizTalk Server (gestionnaires de réception)
En plus de la charge, les informations supplémentaires composant le message doivent être accessibles à partir d'une orchestration BizTalk Server au moment de l'exécution.  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a>Informations de message TIBCO RV promues en tant que propriétés de contexte  
 Le tableau suivant répertorie ces informations supplémentaires :  
  
|Identification des données|Type|Routable|Emplacement de réception|  
|-------------------------|----------|--------------|----------------------|  
|Objet d'envoi [null]|chaîne|Oui|Communique à l'orchestration l'objet auquel ce message a été envoyé.|  
|Objet de réponse [null]|chaîne|Oui|Communique à l'orchestration l'emplacement où l'expéditeur attend que la réponse soit envoyée, si une réponse est attendue.|  
|Nombre de champs [lecture seule]|nombre entier non signé|Non|Nombre de champs dans un message de niveau supérieur. Cette propriété est fournie par TIBCO RV.|  
|Nom de l'expéditeur CM [lecture seule]|chaîne|Oui|Nom du destinataire CM de l'expéditeur.|  
|Numéro de séquence CM [lecture seule]|long|Non|Numéro de séquence attribué par l'objet de transport TIBCO d'envoi.|  
|Délai CM [lecture seule]|double|Non|Délai après lequel le programme d'envoi n'attend plus que son transport CM certifie la livraison du message.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md)   
 [Gestionnaires de réception création TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)