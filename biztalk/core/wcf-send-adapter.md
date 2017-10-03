---
title: "Adaptateur d’envoi WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- serializing, SOAP messages
- WCF adapters, extracting information
- messages, extracting information
- SOAP messages, serializing
- WCF adapters, message bodies
- send adapters, WCF adapters
- Web services, headers
- WCF adapters, send adapters
ms.assetid: 226a020a-2e12-41fe-a4a2-6683d9e98219
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70604fbc15f5f15b0a7ff2325debdc28ac3a97c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-send-adapter"></a>adaptateur d'envoi WCF
L'adaptateur d'envoi WCF permet d'appeler un service WCF via un contrat sans type.  
  
## <a name="specifying-the-wcf-message-body"></a>Spécification du corps de message WCF  
 Le corps de message qui doit être envoyé à partir de BizTalk Server peut être inséré dans le message SOAP à l'aide de l'une des options suivantes :  
  
-   Extraire le contenu du corps du message de BizTalk  
  
-   Spécifier le contenu à l’aide du modèle  
  
 Vous pouvez configurer ces options dans la boîte de dialogue des propriétés de transport du port d'envoi.  
  
#### <a name="extract-the-content-of-the-biztalk-message-body"></a>Extraction du contenu du corps de message BizTalk  
 Lorsque cette option est activée, le contenu du corps de message BizTalk est inséré dans l'élément de corps SOAP du corps du message WCF sortant.  
  
#### <a name="specify-the-content-by-using-the-template"></a>Spécification du contenu à l'aide du modèle  
 Lorsque cette option est activée, le corps de message BizTalk est placé dans l'élément de corps SOAP sous le modèle XML donné pour le corps de message WCF sortant.  
  
## <a name="serializing-the-biztalk-message-into-a-soap-message"></a>Sérialisation du message BizTalk en un message SOAP  
 L'adaptateur d'envoi sérialise le message BizTalk en un message SOAP avant de l'envoyer. Les règles suivantes s'appliquent lors de la sérialisation du message :  
  
-   Si le message BizTalk est un message à parties multiples, seul le corps est utilisé.  
  
-   Si le message BizTalk contient l'ensemble de l'enveloppe SOAP, il est inséré dans une autre enveloppe SOAP.  
  
-   Si le message BizTalk contient des données XML arbitraires, il est placé dans l'élément de corps SOAP.  
  
## <a name="handling-web-services-headers"></a>Traitement des en-têtes des services Web  
 Lors des opérations d'envoi, BizTalk Server n'a pas le contrôle sur les en-têtes standard des services Web. Ceux-ci sont définis et traités par le WCF. Le seul en-tête standard qui peut être modifié par l’application BizTalk Server est la **un : Action** en-tête. Si la propriété de contexte **Action** est spécifié sur l’espace de noms de carte, l’adaptateur d’envoi WCF utilise la valeur de la propriété pour définir le **Action** sur le message SOAP.  
  
> [!NOTE]
>  Dynamique ports d’envoi, si **Action** est spécifié dans le **OutboundHeaders**, la propriété de contexte que vous définissez pour le **WCF. Action** sera ignoré.  
  
## <a name="specifying-the-btsisdynamicsend-context-property"></a>Spécification de la propriété de contexte BTS.IsDynamicSend  
 L'adaptateur d'envoi WCF met en cache la configuration pour les ports d'envoi. Si le **BTS. IsDynamicSend** est définie sur true, l’envoi WCF adaptateur n’utilise pas la configuration de mise en cache, mais au lieu de cela lit toutes les informations de configuration à partir du message des propriétés de contexte des messages sortants. Sur un port d’envoi statique, WCF adaptateur d’envoi utilise **BTS. SPLastUpdatedTime**, qui est l’heure à laquelle les paramètres de port d’envoi statique de la dernière modification, pour détecter s’il existe toute configuration de port d’envoi modifications sur la méthode statique. Ainsi, l'adaptateur d'envoi WCF n'a pas besoin de lire tous les paramètres de chaque contexte de message.  
  
 Si vous souhaitez remplacer les propriétés de port d’envoi statique autre que le **WCF. Action** propriété dans un pipeline d’envoi, vous devez définir le **BTS. IsDynamicSend** propriété la valeur true afin que l’adaptateur d’envoi WCF n’utilise pas de la configuration de mise en cache même si la dernière mise à jour d’horodatage n’a pas changé.  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Adaptateur de réception WCF](../core/wcf-receive-adapter.md)   
 [Quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md)   
 [Comment utiliser les propriétés de contexte de Message](../core/how-to-use-message-context-properties.md)