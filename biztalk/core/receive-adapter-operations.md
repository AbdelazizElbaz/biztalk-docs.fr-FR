---
title: "Opérations de l’adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b61ea356-f2a1-4604-8e52-13d2961399d0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804a136841c33977b350b8d59dfbf18c7108cc79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-adapter-operations"></a><span data-ttu-id="b3d2c-102">Opérations de l'adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="b3d2c-102">Receive Adapter Operations</span></span>
<span data-ttu-id="b3d2c-103">Les adaptateurs de réception peuvent effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3d2c-103">Receive adapters can perform the following operations:</span></span>  
  
-   <span data-ttu-id="b3d2c-104">**Soumission unidirectionnelle : void SubmitMessage (IBaseMessage msg).**</span><span class="sxs-lookup"><span data-stu-id="b3d2c-104">**One-way submit: void SubmitMessage(IBaseMessage msg).**</span></span> <span data-ttu-id="b3d2c-105">Après avoir reçu un message du port de réception, l'adaptateur le soumet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin qu'il soit traité par une orchestration d'abonnement ou un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b3d2c-105">After receiving a message from a receive port, the adapter submits it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be processed by a subscribing orchestration or send port.</span></span>  
  
-   <span data-ttu-id="b3d2c-106">**Suspendre : void MoveToSuspendQ (IBaseMessage msg).**</span><span class="sxs-lookup"><span data-stu-id="b3d2c-106">**Suspend: void MoveToSuspendQ(IBaseMessage msg).**</span></span> <span data-ttu-id="b3d2c-107">Lorsque l'adaptateur détermine qu'une analyse, transmission, sérialisation, ou toute autre erreur applicable s'est produite après la soumission, il déplace le message vers la file d'attente des messages interrompus.</span><span class="sxs-lookup"><span data-stu-id="b3d2c-107">When the adapter determines a parsing, transmission, serialization, or other applicable failure has occurred after submission, it moves the message to the Suspended queue.</span></span>  
  
-   <span data-ttu-id="b3d2c-108">**Soumettre la demande : void SubmitRequestMessage (IBaseMessage requestMsg, string correlationToken, [MarshalAs (UnmanagedType.bool)] bool firstResponseOnly, heure de la date/heure, IBTTransmitter responseCallback).**</span><span class="sxs-lookup"><span data-stu-id="b3d2c-108">**Submit request: void SubmitRequestMessage(IBaseMessage requestMsg, string correlationToken, [MarshalAs(UnmanagedType.Bool)]bool firstResponseOnly, DateTime expirationTime, IBTTransmitter responseCallback).**</span></span> <span data-ttu-id="b3d2c-109">Un adaptateur de réception soumet un message entrant à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une paire requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="b3d2c-109">A receive adapter submits an incoming message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a request-response pair.</span></span> <span data-ttu-id="b3d2c-110">Après avoir correctement traité ce message de requête, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie la réponse à l'adaptateur afin qu'il la transmette au point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="b3d2c-110">After [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] successfully processes this request message, it sends the response to the adapter to transmit it to the specific endpoint.</span></span>