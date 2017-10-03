---
title: "Messages d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages
- ports, error messages
- Catch Exception block [Orchestration Designer], error messages
- error messages, receiving
- messages, errors
- error messages, sending
ms.assetid: 33d62260-b5e0-4d14-b2d2-996733d588e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4127fd5718ee910cb298436c0d0f7058ccba55b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fault-messages"></a><span data-ttu-id="1f135-102">Messages d'erreur</span><span class="sxs-lookup"><span data-stu-id="1f135-102">Fault Messages</span></span>
<span data-ttu-id="1f135-103">Les ports avec requête-réponse peuvent être associés à des messages d'erreur, de sorte que si une erreur survient après l'envoi d'une requête, le service de réponse peut communiquer l'erreur au demandeur, au lieu de la réponse.</span><span class="sxs-lookup"><span data-stu-id="1f135-103">Request-response ports can have fault messages associated with them, so that if something goes wrong after a request is sent, the responding service can communicate the error to the requester, in lieu of the response.</span></span>  
  
 <span data-ttu-id="1f135-104">Chaque opération d'un port avec requête-réponse peut gérer un nombre arbitraire d'erreurs différentes.</span><span class="sxs-lookup"><span data-stu-id="1f135-104">Each operation of a request-response port can handle an arbitrary number of different faults.</span></span> <span data-ttu-id="1f135-105">Un message d'erreur peut être de n'importe quel type, mais le type du message doit être unique pour chaque opération et ne doit pas être celui utilisé par la réponse.</span><span class="sxs-lookup"><span data-stu-id="1f135-105">A fault message can have any message type, but the message type must be unique for the operation, and it must not be the type used by the response in that port operation.</span></span>  
  
## <a name="receiving-fault-messages"></a><span data-ttu-id="1f135-106">Réception de messages d'erreur</span><span class="sxs-lookup"><span data-stu-id="1f135-106">Receiving fault messages</span></span>  
 <span data-ttu-id="1f135-107">Si votre port envoie une requête avant de recevoir une réponse, vous avez la possibilité de recevoir un ou plusieurs types de messages d'erreur différents.</span><span class="sxs-lookup"><span data-stu-id="1f135-107">If your port operation sends a request, then receives a response, you can use it to receive one or more different fault message types.</span></span>  
  
 <span data-ttu-id="1f135-108">Vous pouvez configurer un **intercepter l’Exception** bloc pour gérer un message d’erreur entrant en sélectionnant l’erreur appropriée à partir de l’opération de port requête-réponse en tant que son Type d’objet Exception.</span><span class="sxs-lookup"><span data-stu-id="1f135-108">You can configure a **Catch Exception** block to handle an incoming fault message by selecting the appropriate fault from the request-response port operation as its Exception Object Type.</span></span>  
  
## <a name="sending-fault-messages"></a><span data-ttu-id="1f135-109">Envoi de messages d'erreur</span><span class="sxs-lookup"><span data-stu-id="1f135-109">Sending fault messages</span></span>  
 <span data-ttu-id="1f135-110">Si votre port reçoit une réponse avant d'envoyer une requête, vous avez la possibilité d'envoyer un ou plusieurs types de messages d'erreur différents.</span><span class="sxs-lookup"><span data-stu-id="1f135-110">If your port operation receives a response, then sends a request, you can use it to send one or more different fault message types.</span></span>  
  
 <span data-ttu-id="1f135-111">Si par exemple, votre orchestration rencontre une condition d’erreur et lève une exception, vous pouvez envoyer un message d’erreur depuis le **intercepter l’Exception** bloc qui gère l’exception.</span><span class="sxs-lookup"><span data-stu-id="1f135-111">If for example your orchestration encounters an error condition and throws an exception, you can send a fault message from within the **Catch Exception** block that handles the exception.</span></span> <span data-ttu-id="1f135-112">Vous créez un message d'erreur du type approprié pour qu'il transmette la situation au service participant et spécifiez ce message sur une forme Envoi qui utilisera l'erreur correspondante dans l'opération du port.</span><span class="sxs-lookup"><span data-stu-id="1f135-112">You construct a fault message of an appropriate type to convey the situation to the participating service, and specify that fault message on a Send shape that will use the corresponding fault in the port operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f135-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f135-113">See Also</span></span>  
 [<span data-ttu-id="1f135-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="1f135-114">Exceptions</span></span>](../core/exceptions.md)