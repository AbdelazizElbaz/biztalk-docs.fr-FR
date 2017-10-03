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
# <a name="writing-as2-context-properties-for-outbound-party-resolution"></a><span data-ttu-id="45f78-102">Écriture de propriétés de contexte AS2 pour la résolution d'un tiers sortant</span><span class="sxs-lookup"><span data-stu-id="45f78-102">Writing AS2 Context Properties for Outbound Party Resolution</span></span>
<span data-ttu-id="45f78-103">La résolution de l'accord d'un message AS2 sortant peut être réalisée à l'aide de la propriété de contexte AS2To ou de la propriété AS2To contenue dans la propriété de contexte `Http.UserHttpHeaders`.</span><span class="sxs-lookup"><span data-stu-id="45f78-103">Agreement resolution of outbound AS2 message can be performed using the AS2To context property or the AS2To property in the `Http.UserHttpHeaders` context property.</span></span> <span data-ttu-id="45f78-104">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'écrit pas la propriété AS2To dans le contexte au moment de la réception d'un message AS2.</span><span class="sxs-lookup"><span data-stu-id="45f78-104">However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write the AS2To property to the context upon receiving an AS2 message.</span></span> <span data-ttu-id="45f78-105">Si vous souhaitez que la résolution de l'accord se déroule sur la propriété de contexte AS2To ou UserHttpHeaders, vous devez écrire une orchestration personnalisée ou un composant de pipeline personnalisé chargé d'exécuter cette opération.</span><span class="sxs-lookup"><span data-stu-id="45f78-105">If you want to perform agreement resolution on the AS2To or UserHttpHeaders context property, you have to write a custom orchestration or a custom pipeline component to do so.</span></span> <span data-ttu-id="45f78-106">Cette opération est requise uniquement si le port d'envoi n'est pas lié à l'accord.</span><span class="sxs-lookup"><span data-stu-id="45f78-106">This is required only if the send port is not linked to the agreement.</span></span>  
  
 <span data-ttu-id="45f78-107">Dans une orchestration personnalisée, vous pouvez ajouter AS2-To au début de la propriété de contexte `Http.UserHttpHeaders` existante à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="45f78-107">In a custom orchestration, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code:</span></span>  
  
```  
Message_1(Http.UserHttpHeaders) = “AS2-To: MyPartner\r\n” + Message_1(Http.UserHttpHeaders);  
```  
  
 <span data-ttu-id="45f78-108">Dans un composant de pipeline personnalisé, vous pouvez ajouter AS2-To au début de la propriété de contexte `Http.UserHttpHeaders` existante à l'aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="45f78-108">In a custom pipeline component, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code.</span></span> <span data-ttu-id="45f78-109">Vous devez ajouter AS2-pour à `Http.UserHttpHeaders` propriété de contexte avant que le message est traité par le composant As2Encoder.</span><span class="sxs-lookup"><span data-stu-id="45f78-109">You need to append AS2-To to `Http.UserHttpHeaders` context property before the message is processed by the As2Encoder component.</span></span>  
  
```  
string strName="UserHttpHeaders";  
string strValue = "AS2-To: MyPartner\r\n" + (string)baseMessage.Context.Read(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties");  
baseMessage.Context.Write(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties", strValue);  
```  
  
 <span data-ttu-id="45f78-110">Pour plus d’informations sur la promotion du `EDIIntAS.AS2To` propriété ou le `BTS.UseHttpHeaders` propriété au contexte, consultez « Promotion des propriétés AS2 en-tête de contexte » dans le [envoyer un Message AS2 via un Port d’envoi de fichier](../core/sending-an-as2-message-over-a-file-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="45f78-110">For more information on promoting the `EDIIntAS.AS2To` property or the `BTS.UseHttpHeaders` property to the context, see "Promoting AS2 Header Context Properties" in the [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
 <span data-ttu-id="45f78-111">Pour le code que vous pouvez ajouter à un composant de pipeline personnalisé pour écrire les en-têtes à partir de HTTP. Propriété de contexte UserHttpHeaders dans le message, voir [envoyer un Message AS2 via un Port d’envoi de fichier](../core/sending-an-as2-message-over-a-file-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="45f78-111">For code that you can add to a custom pipeline component to write the headers from the HTTP.UserHttpHeaders context property into the message, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f78-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45f78-112">See Also</span></span>  
 [<span data-ttu-id="45f78-113">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="45f78-113">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)