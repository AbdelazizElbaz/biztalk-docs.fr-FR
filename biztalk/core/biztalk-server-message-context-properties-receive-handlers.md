---
title: "Les propriétés de contexte de Message de réception pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36f4de92dbe7c4c235a1c9ebd092b28b3a198c92
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
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
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)