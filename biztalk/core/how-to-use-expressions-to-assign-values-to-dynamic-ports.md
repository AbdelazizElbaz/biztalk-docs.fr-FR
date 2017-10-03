---
title: "Comment utiliser des Expressions pour affecter des valeurs à des Ports dynamiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic send ports, variables
- send ports, dynamic
ms.assetid: 6bdb937c-8702-43ff-914a-a02adc88658b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59c2d11b5da44e94beee914704f46ac6b0346e85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-expressions-to-assign-values-to-dynamic-ports"></a>Utiliser des Expressions pour affecter des valeurs à des Ports dynamiques

## <a name="assign-values"></a>Affecter des valeurs
Si un port d'envoi est marqué comme dynamique, vous pouvez lui affecter la valeur d'une variable quelconque de type chaîne contenant l'URI du port que vous souhaitez utiliser dans la forme Expression. Par exemple :  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"file://C:\MyLocation\%SourceFileName%.xml";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"msmq://.\private$\MyQueue";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="http://MyOrder.contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="ftp://MyServer/MyDirectory/%MessageID%.xml";  
```  
  
 Vous pouvez ensuite poursuivre l'attribution des propriétés aux messages sortants. Par exemple :  
  
```  
MyOutgoingMessage(SMTP.Subject)="Purcahse Order Received";  
MyOutgoingMessage(FILE.ReceivedFileName)="MyFileName.xml";  
MyOutgoingMessage(FTP.UserName)="MyUserName";  
MyOutgoingMessage(FTP.Password)="MyPassword";  
MyOutgoingMessage((MSMQ.Transactional)=true;  
```  
  
## <a name="see-also"></a>Voir aussi  
[Restrictions relatives à la configuration de l’adaptateur de fichier](restrictions-when-configuring-the-file-adapter.md)