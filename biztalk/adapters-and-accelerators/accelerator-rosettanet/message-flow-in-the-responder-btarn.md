---
title: "Message de flux dans le répondeur BTARN | Documents Microsoft"
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
- responder BTARN
ms.assetid: 66de8694-a248-47e8-9483-9eedf2324b33
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ad33db4f67336f41ac868a7a14e1266a85dd45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-responder-btarn"></a><span data-ttu-id="0bd10-102">Flux de messages de répondeur BTARN</span><span class="sxs-lookup"><span data-stu-id="0bd10-102">Message Flow in the Responder BTARN</span></span>
<span data-ttu-id="0bd10-103">Flux de messages sur un ordinateur de répondeur démarre avec la réception d’un message via Internet à partir de l’ordinateur de l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="0bd10-103">Message flow on a responder computer starts with receiving a message over the Internet from the initiator computer.</span></span> <span data-ttu-id="0bd10-104">Elle implique la conversion de ce message à partir d’un Framework RNIF (RosettaNet Implementation)-message conforme à un message dans le format propriétaire de l’application principale et puis d’acheminer le message à l’application line-of-business.</span><span class="sxs-lookup"><span data-stu-id="0bd10-104">It involves converting that message from a RosettaNet Implementation Framework (RNIF)-compliant message to a message in the proprietary format of the back-end application, and then routing the message to the line-of-business application.</span></span>  
  
 <span data-ttu-id="0bd10-105">Si le processus PIP (Partner Interface) est l’action unique, la réponse uniquement est un message de signal d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="0bd10-105">If the Partner Interface Process (PIP) is single-action, the only response is an acknowledgement signal message.</span></span> <span data-ttu-id="0bd10-106">Si l’adresse PIP est de double action, le répondeur doit traiter et envoyer un message de réponse et par la suite de recevoir un accusé de réception pour cette réponse.</span><span class="sxs-lookup"><span data-stu-id="0bd10-106">If the PIP is double-action, the responder will process and send a response message, and subsequently receive an acknowledgment for that response.</span></span>  
  
 <span data-ttu-id="0bd10-107">Si l’adresse PIP est asynchrone, chaque transmission de messages sur Internet se produit sur une autre connexion HTTP.</span><span class="sxs-lookup"><span data-stu-id="0bd10-107">If the PIP is asynchronous, each message transmission over the Internet occurs on a different HTTP connection.</span></span> <span data-ttu-id="0bd10-108">Si l’adresse PIP est synchrone, chaque transmission de message se produit sur la même connexion, qui contient de l’adaptateur HTTP jusqu'à ce que le processus est terminé.</span><span class="sxs-lookup"><span data-stu-id="0bd10-108">If the PIP is synchronous, each message transmission occurs on the same connection, which the HTTP adapter holds until the process is complete.</span></span> <span data-ttu-id="0bd10-109">Dans un scénario synchrone double action, l’ordinateur récepteur n’envoie pas d’accusé de réception à l’ordinateur initiateur en réponse au message de demande initiale.</span><span class="sxs-lookup"><span data-stu-id="0bd10-109">In a double-action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial request message.</span></span> <span data-ttu-id="0bd10-110">Le message de réponse sert d'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="0bd10-110">The response message serves as the acknowledgement.</span></span>  
  
## <a name="btarn-components-on-the-responder-computer"></a><span data-ttu-id="0bd10-111">Composants BTARN sur l’ordinateur de répondeur</span><span class="sxs-lookup"><span data-stu-id="0bd10-111">BTARN Components on the Responder Computer</span></span>  
 <span data-ttu-id="0bd10-112">Comme un message transite par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur l’ordinateur de répondeur, les composants suivants traitent le message :</span><span class="sxs-lookup"><span data-stu-id="0bd10-112">As a message flows through [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on the responder computer, the following components will process the message:</span></span>  
  
-   <span data-ttu-id="0bd10-113">Page de RNIFReceive.aspx</span><span class="sxs-lookup"><span data-stu-id="0bd10-113">RNIFReceive.aspx page</span></span>  
  
-   <span data-ttu-id="0bd10-114">adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="0bd10-114">HTTP adapter</span></span>  
  
-   <span data-ttu-id="0bd10-115">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="0bd10-115">Receive pipeline</span></span>  
  
-   <span data-ttu-id="0bd10-116">Processus public de répondeur</span><span class="sxs-lookup"><span data-stu-id="0bd10-116">Responder public process</span></span>  
  
-   <span data-ttu-id="0bd10-117">Processus privés répondeur</span><span class="sxs-lookup"><span data-stu-id="0bd10-117">Responder private process</span></span>  
  
-   <span data-ttu-id="0bd10-118">Adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="0bd10-118">SQL adapter</span></span>  
  
-   <span data-ttu-id="0bd10-119">Pipeline d’envoi</span><span class="sxs-lookup"><span data-stu-id="0bd10-119">Send pipeline</span></span>  
  
 <span data-ttu-id="0bd10-120">Pour plus d’informations sur ces composants, et comment ils traitent un message, consultez [de traitement du Message dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span><span class="sxs-lookup"><span data-stu-id="0bd10-120">For more information about these components, and how they process a message, see [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span></span>  
  
## <a name="message-flow-on-the-responder-computer"></a><span data-ttu-id="0bd10-121">Flux de messages sur l’ordinateur de répondeur</span><span class="sxs-lookup"><span data-stu-id="0bd10-121">Message Flow on the Responder Computer</span></span>  
 <span data-ttu-id="0bd10-122">Le flux de messages d’un message reçu via le répondeur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ordinateur est comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bd10-122">The message flow of a received message through the responder [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] computer is as follows:</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-responder-receive-message-flow.gif "RN3_Responder_Receive_Message_Flow")  
  
1.  <span data-ttu-id="0bd10-123">La page aspx RNIFReceive reçoit le message entrant à partir de l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="0bd10-123">The RNIFReceive aspx page receives the incoming message from the initiator.</span></span>  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0bd10-124">envoie le message à l’adaptateur HTTP qui soumet au pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="0bd10-124"> submits the message to the HTTP adapter, which submits it to the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="0bd10-125">Le pipeline de réception décode, désassemble, effectue la résolution du tiers dans le message et convertit ensuite le message au format propriétaire de l’application de line-of-business back-end.</span><span class="sxs-lookup"><span data-stu-id="0bd10-125">The receive pipeline decodes, disassembles, and performs party resolution on the message, and then converts the message into the proprietary format of the back-end line-of-business application.</span></span>  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0bd10-126">achemine le message vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="0bd10-126"> routes the message to the MessageBox database.</span></span>  
  
5.  <span data-ttu-id="0bd10-127">Le processus public traite les en-têtes RNIF du message.</span><span class="sxs-lookup"><span data-stu-id="0bd10-127">The public process processes the RNIF headers of the message.</span></span>  
  
6.  <span data-ttu-id="0bd10-128">Le processus privé traite le contenu du message du service.</span><span class="sxs-lookup"><span data-stu-id="0bd10-128">The private process processes the service content of the message.</span></span> <span data-ttu-id="0bd10-129">Il génère un accusé de réception qui est retourné pour le processus public, à la base de données MessageBox, au pipeline d’envoi, puis à l’adaptateur HTTP pour un retour sur Internet à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="0bd10-129">It generates an acknowledgement that is returned to the public process, to the MessageBox database, to the send pipeline, and then to the HTTP adapter for return over the Internet to the initiator.</span></span>  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0bd10-130">achemine le message vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="0bd10-130"> routes the message to the MessageBox database.</span></span>  
  
8.  <span data-ttu-id="0bd10-131">Le pipeline d’envoi assemble et puis signes/chiffre/encode le message.</span><span class="sxs-lookup"><span data-stu-id="0bd10-131">The send pipeline assembles, and then signs/encrypts/encodes the message.</span></span>  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0bd10-132">achemine le message vers l’adaptateur SQL.</span><span class="sxs-lookup"><span data-stu-id="0bd10-132"> routes the message to the SQL adapter.</span></span>  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0bd10-133">envoie le message à [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]et à l’application métier-sur le serveur principal.</span><span class="sxs-lookup"><span data-stu-id="0bd10-133"> submits the message to [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and to the line-of-business application on the back end.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd10-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bd10-134">See Also</span></span>  
 <span data-ttu-id="0bd10-135">[Flux de messages de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="0bd10-135">[Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span></span>  
 [<span data-ttu-id="0bd10-136">Flux de messages de l’initiateur BTARN</span><span class="sxs-lookup"><span data-stu-id="0bd10-136">Message Flow in the Initiator BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-initiator-btarn.md)