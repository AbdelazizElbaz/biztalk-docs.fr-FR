---
title: "L’écriture des propriétés de contexte AS2 pour la résolution de tiers sortante | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 808d63d9-076d-4eed-8420-aee12b130fee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c89804c42554825e387d01ff592e3a628e8225b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="writing-as2-context-properties-for-outbound-party-resolution"></a>Écriture de propriétés de contexte AS2 pour la résolution d'un tiers sortant
La résolution de l'accord d'un message AS2 sortant peut être réalisée à l'aide de la propriété de contexte AS2To ou de la propriété AS2To contenue dans la propriété de contexte `Http.UserHttpHeaders`. Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'écrit pas la propriété AS2To dans le contexte au moment de la réception d'un message AS2. Si vous souhaitez que la résolution de l'accord se déroule sur la propriété de contexte AS2To ou UserHttpHeaders, vous devez écrire une orchestration personnalisée ou un composant de pipeline personnalisé chargé d'exécuter cette opération. Cette opération est requise uniquement si le port d'envoi n'est pas lié à l'accord.  
  
 Dans une orchestration personnalisée, vous pouvez ajouter AS2-To au début de la propriété de contexte `Http.UserHttpHeaders` existante à l'aide du code suivant :  
  
```  
Message_1(Http.UserHttpHeaders) = “AS2-To: MyPartner\r\n” + Message_1(Http.UserHttpHeaders);  
```  
  
 Dans un composant de pipeline personnalisé, vous pouvez ajouter AS2-To au début de la propriété de contexte `Http.UserHttpHeaders` existante à l'aide du code suivant. Vous devez ajouter AS2-pour à `Http.UserHttpHeaders` propriété de contexte avant que le message est traité par le composant As2Encoder.  
  
```  
string strName="UserHttpHeaders";  
string strValue = "AS2-To: MyPartner\r\n" + (string)baseMessage.Context.Read(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties");  
baseMessage.Context.Write(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties", strValue);  
```  
  
 Pour plus d’informations sur la promotion du `EDIIntAS.AS2To` propriété ou le `BTS.UseHttpHeaders` propriété au contexte, consultez « Promotion des propriétés AS2 en-tête de contexte » dans le [envoyer un Message AS2 via un Port d’envoi de fichier](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
 Pour le code que vous pouvez ajouter à un composant de pipeline personnalisé pour écrire les en-têtes à partir de HTTP. Propriété de contexte UserHttpHeaders dans le message, voir [envoyer un Message AS2 via un Port d’envoi de fichier](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)