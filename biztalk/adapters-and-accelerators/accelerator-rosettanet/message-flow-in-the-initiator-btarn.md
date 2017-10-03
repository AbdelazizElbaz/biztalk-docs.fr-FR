---
title: "Message de flux dans l’initiateur BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, message flow
- BTARN, components
- messages, message flow
- initiator BTARN
ms.assetid: 315f3d4c-5e40-4b8e-b135-9da98dc2db1e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85fed6404627fd8abfa9d50e7d56d98ff7306f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-initiator-btarn"></a><span data-ttu-id="7719c-102">Flux de messages de l’initiateur BTARN</span><span class="sxs-lookup"><span data-stu-id="7719c-102">Message Flow in the Initiator BTARN</span></span>
<span data-ttu-id="7719c-103">Flux de messages sur un ordinateur de l’initiateur démarre avec la réception d’un message de l’application métier-terminale, dans son format propriétaire.</span><span class="sxs-lookup"><span data-stu-id="7719c-103">Message flow on an initiator computer starts with receiving a message from the back-end line-of-business application, in its proprietary format.</span></span> <span data-ttu-id="7719c-104">Elle implique la conversion de ce message pour un Framework RNIF (RosettaNet Implementation)-message compatible, puis envoyer le message via Internet à l’ordinateur de répondeur.</span><span class="sxs-lookup"><span data-stu-id="7719c-104">It involves converting that message to a RosettaNet Implementation Framework (RNIF)-compliant message, and then sending the message over the Internet to the responder computer.</span></span>  
  
 <span data-ttu-id="7719c-105">Si le processus PIP (Partner Interface) est l’action unique, la réponse uniquement est un message de signal d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="7719c-105">If the Partner Interface Process (PIP) is single-action, the only response is an acknowledgement signal message.</span></span> <span data-ttu-id="7719c-106">Pour plus d’informations sur les flux de messages d’action unique, consultez « Flux d’un initiée par Message » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7719c-106">For information about single-action message flow, see "Flow of an Initiated Message" later in this topic.</span></span> <span data-ttu-id="7719c-107">Si l’adresse PIP est de double action, l’initiateur recevra un message de réponse et répondre avec un accusé de réception, en plus du flux de messages d’action unique.</span><span class="sxs-lookup"><span data-stu-id="7719c-107">If the PIP is double-action, the initiator will receive a response message, and reply with an acknowledgement, in addition to the single-action message flow.</span></span>  
  
 <span data-ttu-id="7719c-108">Si l’adresse PIP est asynchrone, chaque transmission de messages sur Internet se produit sur une autre connexion HTTP.</span><span class="sxs-lookup"><span data-stu-id="7719c-108">If the PIP is asynchronous, each message transmission over the Internet occurs on a different HTTP connection.</span></span> <span data-ttu-id="7719c-109">Si l’adresse PIP est synchrone, chaque transmission de message se produit sur la même connexion, qui contient de l’adaptateur HTTP jusqu'à ce que le processus est terminé.</span><span class="sxs-lookup"><span data-stu-id="7719c-109">If the PIP is synchronous, each message transmission occurs on the same connection, which the HTTP adapter holds until the process is complete.</span></span> <span data-ttu-id="7719c-110">Dans un scénario synchrone double action, l’ordinateur récepteur n’envoie pas d’accusé de réception à l’ordinateur initiateur en réponse au message de demande initiale.</span><span class="sxs-lookup"><span data-stu-id="7719c-110">In a double-action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial request message.</span></span> <span data-ttu-id="7719c-111">Le message de réponse sert d'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="7719c-111">The response message serves as the acknowledgement.</span></span>  
  
## <a name="btarn-components-on-the-initiator-computer"></a><span data-ttu-id="7719c-112">Composants BTARN sur l’ordinateur de l’initiateur</span><span class="sxs-lookup"><span data-stu-id="7719c-112">BTARN Components on the Initiator Computer</span></span>  
 <span data-ttu-id="7719c-113">Comme un message transite par [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur l’ordinateur de l’initiateur, les composants suivants traitent le message :</span><span class="sxs-lookup"><span data-stu-id="7719c-113">As a message flows through [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on the initiator computer, the following components will process the message:</span></span>  
  
-   <span data-ttu-id="7719c-114">Adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="7719c-114">SQL adapter</span></span>  
  
-   <span data-ttu-id="7719c-115">Pipeline de réception XML</span><span class="sxs-lookup"><span data-stu-id="7719c-115">XML receive pipeline</span></span>  
  
-   <span data-ttu-id="7719c-116">Processus privés initiateur</span><span class="sxs-lookup"><span data-stu-id="7719c-116">Initiator private process</span></span>  
  
-   <span data-ttu-id="7719c-117">Processus public d’initiateur</span><span class="sxs-lookup"><span data-stu-id="7719c-117">Initiator public process</span></span>  
  
-   <span data-ttu-id="7719c-118">Pipeline d’envoi XML</span><span class="sxs-lookup"><span data-stu-id="7719c-118">XML send pipeline</span></span>  
  
-   <span data-ttu-id="7719c-119">adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="7719c-119">HTTP adapter</span></span>  
  
-   <span data-ttu-id="7719c-120">Page du fichier RNIFSend.aspx</span><span class="sxs-lookup"><span data-stu-id="7719c-120">RNIFSend.aspx page</span></span>  
  
 <span data-ttu-id="7719c-121">Pour plus d’informations sur ces composants, et comment ils traitent un message, consultez [de traitement du Message dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span><span class="sxs-lookup"><span data-stu-id="7719c-121">For more information about these components, and how they process a message, see [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span></span>  
  
## <a name="flow-of-an-initiated-message"></a><span data-ttu-id="7719c-122">Flux d’un Message de déclenchement</span><span class="sxs-lookup"><span data-stu-id="7719c-122">Flow of an Initiated Message</span></span>  
 <span data-ttu-id="7719c-123">Les étapes suivantes décrivent le flux de messages d’un message initié par l’initiateur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7719c-123">The following steps describe the message flow of an initiated message through the initiator [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] computer.</span></span> <span data-ttu-id="7719c-124">Ce processus est représenté dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="7719c-124">The following figure shows this process.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-initiator-send-message-flow.gif "RN3_Initiator_Send_Message_Flow")  
  
1.  <span data-ttu-id="7719c-125">L’application métier-envoie le message à [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7719c-125">The line-of-business application sends the message to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="7719c-126">envoie le message à partir de la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données à l’adaptateur SQL.</span><span class="sxs-lookup"><span data-stu-id="7719c-126"> sends the message from the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database to the SQL adapter.</span></span>  
  
3.  <span data-ttu-id="7719c-127">Le code XML de réception pipeline a simple XML validation du message.</span><span class="sxs-lookup"><span data-stu-id="7719c-127">The XML receive pipeline does simple XML validation of the message.</span></span>  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7719c-128">achemine le message vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7719c-128"> routes the message to the MessageBox database.</span></span>  
  
5.  <span data-ttu-id="7719c-129">Le processus privé traite le contenu du message du service.</span><span class="sxs-lookup"><span data-stu-id="7719c-129">The private process processes the service content of the message.</span></span>  
  
6.  <span data-ttu-id="7719c-130">Le processus public traite les en-têtes RNIF du message.</span><span class="sxs-lookup"><span data-stu-id="7719c-130">The public process processes the RNIF headers of the message.</span></span>  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="7719c-131">achemine le message à la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7719c-131"> routes the message back to the MessageBox database.</span></span>  
  
8.  <span data-ttu-id="7719c-132">Le pipeline d’envoi exécute l’assembly et signature, chiffrement/encodage du message.</span><span class="sxs-lookup"><span data-stu-id="7719c-132">The send pipeline performs assembly and signing/encryption/encoding of the message.</span></span>  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="7719c-133">achemine le message vers l’adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="7719c-133"> routes the message to the HTTP adapter.</span></span>  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="7719c-134">achemine le message vers la page du fichier RNIFSend.aspx, qui l’envoie vers sa destination sur Internet.</span><span class="sxs-lookup"><span data-stu-id="7719c-134"> routes the message to the RNIFSend.aspx page, which sends it over the Internet to its destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7719c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7719c-135">See Also</span></span>  
 <span data-ttu-id="7719c-136">[Flux de messages de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="7719c-136">[Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span></span>  
 <span data-ttu-id="7719c-137">[Flux de messages de répondeur BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="7719c-137">[Message Flow in the Responder BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md) </span></span>  
 [<span data-ttu-id="7719c-138">Traitement des messages dans BTARN</span><span class="sxs-lookup"><span data-stu-id="7719c-138">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)