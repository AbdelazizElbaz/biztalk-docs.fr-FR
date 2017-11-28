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
# <a name="use-expressions-to-assign-values-to-dynamic-ports"></a><span data-ttu-id="25047-102">Utiliser des Expressions pour affecter des valeurs à des Ports dynamiques</span><span class="sxs-lookup"><span data-stu-id="25047-102">Use Expressions to Assign Values to Dynamic Ports</span></span>

## <a name="assign-values"></a><span data-ttu-id="25047-103">Affecter des valeurs</span><span class="sxs-lookup"><span data-stu-id="25047-103">Assign values</span></span>
<span data-ttu-id="25047-104">Si un port d'envoi est marqué comme dynamique, vous pouvez lui affecter la valeur d'une variable quelconque de type chaîne contenant l'URI du port que vous souhaitez utiliser dans la forme Expression.</span><span class="sxs-lookup"><span data-stu-id="25047-104">If a send port is marked as dynamic, you can assign to it the value of some variable of type string that contains the URI of the port you want to use in the Expression shape.</span></span> <span data-ttu-id="25047-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="25047-105">For example,</span></span>  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"file://C:\MyLocation\%SourceFileName%.xml";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"msmq://.\private$\MyQueue";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="http://MyOrder.contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="ftp://MyServer/MyDirectory/%MessageID%.xml";  
```  
  
 <span data-ttu-id="25047-106">Vous pouvez ensuite poursuivre l'attribution des propriétés aux messages sortants.</span><span class="sxs-lookup"><span data-stu-id="25047-106">Then you can further assign the properties to the outgoing messages.</span></span> <span data-ttu-id="25047-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="25047-107">For example,</span></span>  
  
```  
MyOutgoingMessage(SMTP.Subject)="Purcahse Order Received";  
MyOutgoingMessage(FILE.ReceivedFileName)="MyFileName.xml";  
MyOutgoingMessage(FTP.UserName)="MyUserName";  
MyOutgoingMessage(FTP.Password)="MyPassword";  
MyOutgoingMessage((MSMQ.Transactional)=true;  
```  
  
## <a name="see-also"></a><span data-ttu-id="25047-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25047-108">See Also</span></span>  
[<span data-ttu-id="25047-109">Restrictions relatives à la configuration de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="25047-109">Restrictions when configuring the File adapter</span></span>](restrictions-when-configuring-the-file-adapter.md)