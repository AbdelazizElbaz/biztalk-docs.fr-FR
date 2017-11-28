---
title: "Adaptateur de réception SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, receive adapters
- receive adapters, SOAP adapters
ms.assetid: bb968fa8-0515-4f3a-bb39-9effb83e960c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fac19580d6083ed1b0d4be315d3285acf14fcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-receive-adapter"></a><span data-ttu-id="a465c-102">Adaptateur de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="a465c-102">SOAP Receive Adapter</span></span>
<span data-ttu-id="a465c-103">Vous utilisez l'adaptateur de réception SOAP pour recevoir des demandes de service Web.</span><span class="sxs-lookup"><span data-stu-id="a465c-103">You use the SOAP receive adapter to receive Web service requests.</span></span> <span data-ttu-id="a465c-104">L'adaptateur de réception SOAP crée un objet de message BizTalk et promeut les propriétés associées vers le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="a465c-104">The SOAP receive adapter creates a BizTalk Message object, and promotes the associated properties to the message context.</span></span>  
  
 <span data-ttu-id="a465c-105">Réception SOAP adaptateur URI doit être associé à une ou plusieurs orchestrations BizTalk ou les schémas qui ont été publiés comme service web avec le **Assistant Publication des Services Web BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="a465c-105">A SOAP receive adapter URI must correlate to one or more BizTalk orchestrations or schemas that have been published as a web service with the **BizTalk Web Services Publishing Wizard**.</span></span> <span data-ttu-id="a465c-106">L'URI de l'adaptateur de réception SOAP doit être associé à un ou plusieurs schémas ou orchestrations BizTalk ayant été publiés comme service Web à l'aide de l'Assistant Publication de services Web BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a465c-106">The published web service exposes one or more web methods which correlate to one or more BizTalk Server orchestrations or schemas in a BizTalk assembly.</span></span> <span data-ttu-id="a465c-107">En effet, le service Web publié joue le rôle de serveur proxy pour les orchestrations ou schémas BizTalk et transmet les requêtes et réponses échangées entre le client et les orchestrations ou les schémas BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a465c-107">In effect, the published web service acts as a server proxy for the BizTalk orchestration(s) or schema(s) and forwards requests and responses between the client and the BizTalk orchestration(s) or schema(s).</span></span> <span data-ttu-id="a465c-108">Pour plus d’informations sur la publication d’orchestrations BizTalk ou schémas en tant que services web, consultez [publication de Services Web](../core/publishing-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="a465c-108">For more information about publishing BizTalk orchestrations or schemas as web services see [Publishing Web Services](../core/publishing-web-services.md).</span></span>  
  
 <span data-ttu-id="a465c-109">Un emplacement de réception qui utilise l'adaptateur SOAP peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="a465c-109">A receive location that uses the SOAP adapter can be configured as one-way or request response (two way).</span></span> <span data-ttu-id="a465c-110">Lorsqu'un emplacement de réception unidirectionnel est configuré pour utiliser l'adaptateur SOAP, le service Web associé appelle l'assembly BizTalk lié au port de réception et renvoie l'état de la demande au client.</span><span class="sxs-lookup"><span data-stu-id="a465c-110">When a one-way receive location is configured to use the SOAP adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns the status of the request to the client.</span></span> <span data-ttu-id="a465c-111">Lorsqu'un emplacement de réception configuré comme requête-réponse (bidirectionnel) utilise l'adaptateur SOAP, le service Web associé appelle l'assembly BizTalk lié au port de réception, et renvoie un document de réponse au client.</span><span class="sxs-lookup"><span data-stu-id="a465c-111">When a request response (two way) receive location is configured to use the SOAP Adapter, the associated web service invokes the BizTalk assembly bound to the receive port, and returns a response document to the client.</span></span> <span data-ttu-id="a465c-112">Pour plus d’informations sur les messages de réponse de demande, consultez [de messagerie requête-réponse](../core/request-response-messaging.md).</span><span class="sxs-lookup"><span data-stu-id="a465c-112">For more information about request response messaging see [Request-Response Messaging](../core/request-response-messaging.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a465c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a465c-113">See Also</span></span>  
 <span data-ttu-id="a465c-114">[Nouveautés de l’adaptateur SOAP ?](../core/what-is-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="a465c-114">[What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="a465c-115">Recommandations de sécurité de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="a465c-115">SOAP Adapter Security Recommendations</span></span>](../core/soap-adapter-security-recommendations.md)