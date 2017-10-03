---
title: "Configuration des propriétés de l’accord Global ou de secours | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c375d03-6f22-4a67-9eac-d8896de2f7ee
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb693a17cad17eadaf0d005d12075dde30daa33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-global-or-fallback-agreement-properties"></a>Configuration des propriétés d'un accord global ou de secours
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite les propriétés d'accord de secours pour traiter un message lorsqu'il ne détecte aucun accord correspondant à un échange. Ces propriétés restent inexploitées lorsque l'accord est connu et ne s'appliquent à aucun accord.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message, il tente de trouver une correspondance entre les informations d'accord de l'expéditeur et les informations de l'expéditeur se trouvant dans le message. Les informations de l'expéditeur se trouvent dans les éléments de données ISA5 et ISA6 d'un message X12 et dans les éléments de données UNB2.1 et UNB2.2 d'un message EDIFACT. Les informations de contrat sont dans les onglets identificateur dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne détecte pas l’accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les propriétés de l’accord de secours pour déterminer l’espace de noms, de traiter le message et d’envoyer les accusés de réception.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message, le pipeline de réception EDI détermine l'accord correspondant à celui-ci en recherchant une correspondance entre le port d'envoi s'abonnant au message XML dans MessageBox et le port d'envoi associé à l'accord. Si le port d'envoi n'est associé à aucun accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait appel aux propriétés d'accord de secours pour traiter l'envoi du message.  
  
> [!NOTE]
>  L'association des ports d'envoi ne représente qu'une méthode de résolution d'accord parmi d'autres. Pour plus d’informations sur la résolution de l’accord pour les messages sortants, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration X12 propriétés de l’accord de secours](../core/configuring-x12-fallback-agreement-properties.md)  
  
-   [Configuration des propriétés d’accord de secours EDIFACT](../core/configuring-edifact-fallback-agreement-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md)