---
title: "Adaptateur de réception WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- receive adapters, Web service headers
- SOAP messages, extracting information
- SOAP messages, WCF adapters
- WCF adapters, receive adapters
- messages, SOAP
- receive adapters, WCF adapters
- Web services, headers
- headers [messages]
- SOAP messages, receive adapters
ms.assetid: 6b3d5df1-5d9d-4240-a98f-ea29c3272e38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdd4d6335723d068333403b4c9d811d96db058e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-receive-adapter"></a>Adaptateur de réception WCF
L'adaptateur de réception WCF permet de recevoir des demandes de service WCF.  
  
## <a name="extracting-the-biztalk-message-body-from-the-soap-message"></a>Extraction du corps de message BizTalk dans le message SOAP  
 Le corps de message BizTalk entrant peut être extrait du message SOAP à l'aide de l'une des options suivantes :  
  
-   Extraction du contenu de l'élément SOAP Body  
  
-   Extraction de l'ensemble de l'enveloppe SOAP  
  
-   Extraction du contenu de l'élément se trouvant dans l'enveloppe SOAP à l'aide d'une expression XPath  
  
 Vous pouvez configurer ces options dans la boîte de dialogue des propriétés de transport.  
  
#### <a name="extract-the-content-of-the-soap-body-element"></a>Extraction du contenu de l’élément SOAP Body  
 Lorsque cette option est activée, le contenu interne de l'élément SOAP Body est lu dans le message SOAP, puis placé dans le corps du message BizTalk.  
  
#### <a name="extract-the-entire-soap-envelope"></a>Extraire l’enveloppe SOAP entière  
 Lorsque cette option est activée, l'ensemble de l'enveloppe SOAP, y compris la balise, est placé dans le corps du message BizTalk.  
  
#### <a name="extract-the-content-of-the-element-by-using-an-xpath-expression"></a>Extraction du contenu de l'élément à l'aide d'une expression XPath  
 Lorsque cette option est activée, le contenu interne de l'élément se trouvant à l'intérieur de l'élément SOAP Body localisé par l'expression XPath est placé dans le corps du message BizTalk. Le reste des données de l'élément Body est ignoré. Vous devez également spécifier le codage de nœud (par exemple un codage XML, Base64, Hex ou String).  
  
> [!NOTE]
>  Lorsque le codage XML est sélectionné, le contenu externe de l'élément est localisé par l'expression XPath, puis il est placé dans le corps.  
  
## <a name="handling-web-services-headers"></a>Traitement des en-têtes des services Web  
 L'adaptateur de réception promeut un sous-ensemble d'en-têtes des services Web standard dans le contexte du message BizTalk pour faciliter l'accès et l'acheminement sur la base des valeurs de ces en-têtes. Le tableau suivant répertorie les propriétés qui sont enregistrées par l'adaptateur de réception dans le message de contexte. Les propriétés sont définies dans les espaces de noms suivants : http://www.w3.org/2005/addressing et http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.  
  
|En-tête|Nom de la propriété BizTalk|Promue ?|  
|------------|---------------------------|------------------|  
|Action|Action|Oui|  
|MessageID|MessageID|Non|  
|Pour|Pour|Oui|  
|ReplyTo/Address|ReplyTo|Oui|  
|From/Address|De|Oui|  
|Sequence/Identifier|SequenceId|Oui|  
|Sequence/MessageNumber|SequenceNumber|Oui|  
|Sequence/LastMessage|SequenceLastMessage|Oui|  
|\<SOAP : Header\>|InboundHeaders|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Adaptateur d’envoi WCF](../core/wcf-send-adapter.md)   
 [Présentation des adaptateurs WCF](../core/what-are-the-wcf-adapters.md)