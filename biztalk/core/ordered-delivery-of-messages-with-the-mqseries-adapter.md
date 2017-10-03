---
title: "Livraison chronologique des Messages avec l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MQSeries adapters, ordered delivery
ms.assetid: 517ff2a4-7315-43b5-8d4b-7494adf141e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8b602adf93152f6af1e5dbbc576180d570a4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-mqseries-adapter"></a><span data-ttu-id="bf628-102">Livraison chronologique des messages à l'aide de l'adaptateur MQSeries Adapter</span><span class="sxs-lookup"><span data-stu-id="bf628-102">Ordered Delivery of Messages with the MQSeries Adapter</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bf628-103">fournit un **livraison chronologique des messages** option statique pour les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="bf628-103"> provides an **Ordered Delivery** option for static send ports.</span></span> <span data-ttu-id="bf628-104">Définition de la **livraison chronologique des messages** option sur un port d’envoi à **True** permet de s’assurer que BizTalk Server remet les messages au port d’envoi dans le même ordre qu’ils sont publiés dans la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bf628-104">Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the BizTalk MessageBox database.</span></span> <span data-ttu-id="bf628-105">Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="bf628-105">To provide end-to-end ordered delivery the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="bf628-106">Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf628-106">Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="bf628-107">Par exemple, lors de la réception des messages avec l’adaptateur de réception MQSeries, l’emplacement de réception doit être configuré avec l’option **classer avec arrêt** ou **classer avec suspension**.</span><span class="sxs-lookup"><span data-stu-id="bf628-107">For example, when receiving messages with the MQSeries receive adapter, the receive location should be configured with the option **Order with Stop** or **Order with Suspend**.</span></span>  
  
-   <span data-ttu-id="bf628-108">Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option **True**.</span><span class="sxs-lookup"><span data-stu-id="bf628-108">You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.</span></span>  
  
-   <span data-ttu-id="bf628-109">Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur **True**.</span><span class="sxs-lookup"><span data-stu-id="bf628-109">If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.</span></span>  
  
## <a name="using-the-mqseries-adapter-for-ordered-delivery-of-messages"></a><span data-ttu-id="bf628-110">Utilisation de l'adaptateur MQSeries pour la livraison chronologique des messages</span><span class="sxs-lookup"><span data-stu-id="bf628-110">Using the MQSeries Adapter for Ordered Delivery of Messages</span></span>  
 <span data-ttu-id="bf628-111">L'adaptateur de réception MQSeries offre une prise en charge de la conservation de l'ordre des messages lors de leur envoi à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf628-111">The MQSeries receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="bf628-112">Bout en bout chronologique de remise des messages via BizTalk Server peut être obtenue lors de leur réception avec l’adaptateur MQSeries si les messages sont traités par un port d’envoi configuré avec le **livraison chronologique des messages** option définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="bf628-112">End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MQSeries adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf628-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf628-113">See Also</span></span>  
 <span data-ttu-id="bf628-114">[Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="bf628-114">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="bf628-115">Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="bf628-115">How to Configure MQSeries Adapter Receive Locations and Send Ports</span></span>](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)