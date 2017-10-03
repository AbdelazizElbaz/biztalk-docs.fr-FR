---
title: "Livraison chronologique des Messages avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, ordered delivery
- MSMQ adapters, ordered delivery
ms.assetid: e8dafc76-e894-4120-9cea-d014d635850e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac842fcd1e9b386fa885844f3a797504ed7c4c3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ordered-delivery-of-messages-with-the-msmq-adapter"></a><span data-ttu-id="647f5-102">Livraison chronologique des Messages avec l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="647f5-102">Ordered Delivery of Messages with the MSMQ Adapter</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="647f5-103">fournit un **livraison chronologique des messages** option statique pour les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="647f5-103"> provides an **Ordered Delivery** option for static send ports.</span></span> <span data-ttu-id="647f5-104">Définition de la **livraison chronologique des messages** option sur un port d’envoi à **True** permet de s’assurer que BizTalk Server remet les messages au port d’envoi dans le même ordre qu’ils sont publiés dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="647f5-104">Setting the **Ordered Delivery** option on a send port to **True** ensures that BizTalk Server delivers messages to the send port in the same order that they are published to the MessageBox database.</span></span> <span data-ttu-id="647f5-105">Pour garantir une livraison chronologique des messages de bout en bout, les conditions ci-dessous doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="647f5-105">To provide end-to-end ordered delivery the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="647f5-106">Les messages doivent être reçus avec un adaptateur qui conserve leur ordre d'arrivée lors de leur envoi à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="647f5-106">Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="647f5-107">Vous devez vous abonner à ces messages avec un port d’envoi de la **livraison chronologique des messages** option **True**.</span><span class="sxs-lookup"><span data-stu-id="647f5-107">You must subscribe to these messages with a send port that has the **Ordered Delivery** option to **True**.</span></span>  
  
-   <span data-ttu-id="647f5-108">Si une orchestration permet de traiter les messages, une seule instance de l’orchestration doivent être utilisés, l’orchestration doit être configurée pour utiliser un convoi séquentiel et la **livraison chronologique des messages** propriété de la port de réception de l’orchestration doit être défini sur **True**.</span><span class="sxs-lookup"><span data-stu-id="647f5-108">If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to **True**.</span></span>  
  
## <a name="using-the-msmq-adapter-for-ordered-delivery-of-messages"></a><span data-ttu-id="647f5-109">Utilisation de l'adaptateur MSMQ pour la livraison chronologique des messages</span><span class="sxs-lookup"><span data-stu-id="647f5-109">Using the MSMQ Adapter for Ordered Delivery of Messages</span></span>  
 <span data-ttu-id="647f5-110">L'adaptateur de réception MSMQ offre une prise en charge de la conservation de l'ordre des messages lors de leur envoi à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="647f5-110">The MSMQ receive adapter provides support for preserving the order of messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="647f5-111">Bout en bout chronologique de remise des messages via BizTalk Server peut être obtenue lors de leur réception avec l’adaptateur MSMQ si les messages sont traités par un port d’envoi configuré avec le **livraison chronologique des messages** lavaleurd’option **True**.</span><span class="sxs-lookup"><span data-stu-id="647f5-111">End-to-end ordered delivery of messages through BizTalk Server can be achieved when receiving messages with the MSMQ adapter if the messages are processed by a send port that is configured with the **Ordered Delivery** option set to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647f5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="647f5-112">See Also</span></span>  
 <span data-ttu-id="647f5-113">[Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="647f5-113">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="647f5-114">Pour configurer un MSMQ emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="647f5-114">How to Configure an MSMQ Receive Location</span></span>](../core/how-to-configure-an-msmq-receive-location.md)