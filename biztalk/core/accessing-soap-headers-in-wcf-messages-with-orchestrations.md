---
title: "Accès aux en-têtes SOAP des Messages WCF avec les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- orchestrations, WCF services
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: fe02fb02-18d6-4fc6-89e0-b06bdbfa5cb4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bfd1dd4e09071c3d7bcccf28878f19e13acad8a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-soap-headers-in-wcf-messages-with-orchestrations"></a>Accès aux en-têtes SOAP des messages WCF à l'aide des orchestrations
Pour accéder aux valeurs d’en-tête SOAP des messages WCF entrants dans les orchestrations, vous utilisez la propriété de contexte **WCF. InboundHeaders**. Les adaptateurs WCF copient les en-têtes SOAP personnalisés et des en-têtes SOAP standard utilisés dans les messages entrants vers le **WCF. InboundHeaders** propriété. Ils permettent également de sélectionner les propriétés que vous souhaitez promouvoir ou écrire vers les propriétés de contexte par programme. Consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md) pour plus d’informations.  
  
 La valeur contenue dans la propriété de contexte est une chaîne contenant des données XML avec le \< **en-têtes** \> élément racine et les en-têtes SOAP entrants sont copiés comme éléments enfants de la \< **en-têtes** \> élément. Pour accéder à ces données le plus simple consiste à utiliser l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** mettre en forme, de charger la chaîne dans un **XmlDocument**et utiliser Requêtes XPath pour accéder aux champs spécifiques. Pour plus d’informations sur la création de documents XML dans l’éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).  
  
 L’exemple de code suivant obtient l’en-tête SOAP de demande dans un **assignation du Message** ou **Expression** pour mettre en forme le **WCF. InboundHeaders** propriété :  
  
```  
stringVar = inboundMessageInstance(WCF.InboundHeaders);  
```  
  
 Les propriétés de contexte sont associées à un message spécifique. Le moteur de messagerie ne mappe pas automatiquement les valeurs des en-têtes SOAP d'un message de requête vers un message de réponse. Lorsque vous créez un message de réponse pour un service WCF, vous devez définir plus précisément des valeurs d’en-tête SOAP via la **WCF. OutboundCustomHeaders** propriété. La commande suivante est la méthode la plus simple de configurer une propriété de contexte d’en-tête SOAP :  
  
```  
outboundMessageInstance(WCF.OutbounCustomHeaders) = "<headers><Origination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Home</Origination><Destination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Work</Destination></headers>"  
```  
  
 Vous pouvez également définir la propriété de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.  
  
 Pour plus d’informations sur l’accès aux en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel « À l’aide personnalisée SOAP en-têtes with the WCF Adapters » à [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux en-têtes SOAP des Messages WCF avec les composants de Pipeline](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md)   
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En-têtes SOAP avec les services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md)