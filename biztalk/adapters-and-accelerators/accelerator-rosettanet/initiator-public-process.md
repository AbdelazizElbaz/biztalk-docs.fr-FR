---
title: Les processus Public initiateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, initiator
- CIDX, 0A1 messages
- messages, 0A1 messages
- messages, message flow
- messages, public processes
- 0A1 messages
- public processes, message flow
ms.assetid: 371d0792-d346-405b-a8f4-2dfa64dd1566
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df1565915d36f3036543ff69c5da680d5949dc74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="initiator-public-process"></a><span data-ttu-id="e7531-102">Processus Public d’initiateur</span><span class="sxs-lookup"><span data-stu-id="e7531-102">Initiator Public Process</span></span>
<span data-ttu-id="e7531-103">Ce processus lance Framework RNIF (RosettaNet Implementation) sur le système de l’initiateur de messagerie en créant et en envoyant le message d’entreprise RNIF initial.</span><span class="sxs-lookup"><span data-stu-id="e7531-103">This process initiates RosettaNet Implementation Framework (RNIF) messaging on the initiator system by creating and sending the initial RNIF business message.</span></span>  
  
## <a name="message-flow-in-the-initiator-public-process"></a><span data-ttu-id="e7531-104">Flux de messages dans le processus Public initiateur</span><span class="sxs-lookup"><span data-stu-id="e7531-104">Message Flow in the Initiator Public Process</span></span>  
 <span data-ttu-id="e7531-105">Le flux de messages via le processus public initiateur est comme suit :</span><span class="sxs-lookup"><span data-stu-id="e7531-105">The message flow through the initiator public process is as follows:</span></span>  
  
1.  <span data-ttu-id="e7531-106">Le processus public initiateur reçoit le contenu du service et les pièces jointes à partir du processus privé via le port de service-content.</span><span class="sxs-lookup"><span data-stu-id="e7531-106">The initiator public process receives the service content and attachments from the private process through the service-content port.</span></span>  
  
2.  <span data-ttu-id="e7531-107">Le processus public envoie la réponse au processus privé et n’est aucun traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e7531-107">The public process sends the response to the private process, and does no further processing.</span></span>  
  
3.  <span data-ttu-id="e7531-108">Si le processus public reçoit une notification qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] n’a pas été envoyer le message, le processus public envoie cet état au processus privé de l’initiateur, puis se termine.</span><span class="sxs-lookup"><span data-stu-id="e7531-108">If the public process receives notification that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] did not successfully send the message, the public process sends that status back to the initiator private process, and then ends.</span></span>  
  
4.  <span data-ttu-id="e7531-109">Si le processus public reçoit une notification qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] a bien envoyé le message, le processus passe à un état d’attente (en attente pour l’action par le répondeur).</span><span class="sxs-lookup"><span data-stu-id="e7531-109">If the public process receives notification that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] successfully sent the message, the process enters a wait state (waiting for action by the responder).</span></span>  
  
5.  <span data-ttu-id="e7531-110">Les actions suivantes peuvent se terminer à l’état d’attente :</span><span class="sxs-lookup"><span data-stu-id="e7531-110">The following actions can end the wait state:</span></span>  
  
    1.  <span data-ttu-id="e7531-111">Le processus public reçoit un signal d’accusé de réception de répondeur.</span><span class="sxs-lookup"><span data-stu-id="e7531-111">The public process receives an acknowledgement signal from the responder.</span></span>  
  
         <span data-ttu-id="e7531-112">Si la non-répudiation pour le signal est requis (tel que défini dans les paramètres de configuration de processus), le processus lit le digest, met en corrélation le condensat du signal avec le résumé dans le message d’action d’origine, puis le signal.</span><span class="sxs-lookup"><span data-stu-id="e7531-112">If non-repudiation for the signal is required (as set in the process configuration settings), the process reads the digest, correlates the digest in the signal with the digest in the original action message, and then persists the signal.</span></span>  
  
         <span data-ttu-id="e7531-113">Le processus public envoie les en-têtes et le contenu du service du signal au processus privé.</span><span class="sxs-lookup"><span data-stu-id="e7531-113">The public process sends the headers and service content of the signal to the private process.</span></span>  
  
    2.  <span data-ttu-id="e7531-114">Le processus public reçoit un message de réponse de l’action de double de répondeur.</span><span class="sxs-lookup"><span data-stu-id="e7531-114">The public process receives a double-action response message from the responder.</span></span>  
  
         <span data-ttu-id="e7531-115">Le processus extrait le contenu de service et les en-têtes de message de réponse et les envoie au processus privé.</span><span class="sxs-lookup"><span data-stu-id="e7531-115">The process extracts the service content and headers from the response message, and sends them to the private process.</span></span>  
  
         <span data-ttu-id="e7531-116">Si l’activité est synchrone, le processus construit un message de signal RNIF en encapsulant la partie du message de contenu de service avec le préambule, en-tête de service et en-tête de remise (pour RNIF 2.01).</span><span class="sxs-lookup"><span data-stu-id="e7531-116">If the activity is synchronous, the process constructs an RNIF signal message by wrapping the service-content message part with the preamble, service header, and delivery header (for RNIF 2.01).</span></span> <span data-ttu-id="e7531-117">Le processus crée le préambule et les en-têtes à l’aide des informations de configuration sur les parties de la source et de destination et les variables PIP stockées dans l’accord de partenariat commercial entre les parties.</span><span class="sxs-lookup"><span data-stu-id="e7531-117">The process creates the preamble and headers using configuration information about the source and destination parties, and the PIP variables stored in the trading partner agreement between the parties.</span></span> <span data-ttu-id="e7531-118">Le processus envoie ensuite le message de signal au répondeur.</span><span class="sxs-lookup"><span data-stu-id="e7531-118">The process then sends the signal message to the responder.</span></span>  
  
         <span data-ttu-id="e7531-119">Si l’activité est asynchrone, le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="e7531-119">If the activity is asynchronous, the process ends.</span></span>  
  
    3.  <span data-ttu-id="e7531-120">Le processus public reçoit un message de Notification d’échec (n) de répondeur.</span><span class="sxs-lookup"><span data-stu-id="e7531-120">The public process receives a Notification of Failure (NoF) message from the responder.</span></span> <span data-ttu-id="e7531-121">Le processus public envoie un message d’état correspondant au processus privé initiateur.</span><span class="sxs-lookup"><span data-stu-id="e7531-121">The public process sends a corresponding status message to the initiator private process.</span></span> <span data-ttu-id="e7531-122">Ensuite, le processus privé gère l’erreur et met fin à la fois aux processus.</span><span class="sxs-lookup"><span data-stu-id="e7531-122">The private process then handles the error and ends both processes.</span></span>  
  
    4.  <span data-ttu-id="e7531-123">Le processus public ne reçoit pas une alerte signalant un accusé de réception du récepteur dans le temps à la période d’accusé de réception (tel que défini dans les paramètres de configuration de processus).</span><span class="sxs-lookup"><span data-stu-id="e7531-123">The public process does not receive an acknowledgement signal from the responder within the Time to Acknowledge period (as set in the process configuration settings).</span></span> <span data-ttu-id="e7531-124">Dans ce cas, une des opérations suivantes se produit :</span><span class="sxs-lookup"><span data-stu-id="e7531-124">If so, one of the following occurs:</span></span>  
  
         <span data-ttu-id="e7531-125">Si le nombre de tentatives (tel que défini dans les paramètres de configuration de processus) n’a pas atteint zéro, et que l’activité est asynchrone, le processus public envoie à nouveau le message.</span><span class="sxs-lookup"><span data-stu-id="e7531-125">If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is asynchronous, the public process sends the message again.</span></span>  
  
         <span data-ttu-id="e7531-126">Si le nombre de tentatives (tel que défini dans les paramètres de configuration de processus) n’a pas atteint zéro, et que l’activité est synchrone, le processus public envoie un message de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e7531-126">If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is synchronous, the public process initiates a 0A1 message.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e7531-127">CIDX ne prend pas en charge les messages de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e7531-127">CIDX does not support 0A1 messages.</span></span>  
  
         <span data-ttu-id="e7531-128">Si le nombre de tentatives atteint zéro sans un envoi réussi, le processus public publie un message d’erreur, et si ce n’est pas CIDX, le processus public envoie un message de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e7531-128">If the number of retries reaches zero without a successful send, the public process posts an error message, and if this is not CIDX, the public process sends a 0A1 message.</span></span>  
  
         <span data-ttu-id="e7531-129">Si l’activité est synchrone, et ce n’est pas CIDX, le processus public envoie un message de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e7531-129">If the activity is synchronous, and this is not CIDX, the public process initiates a 0A1 message.</span></span>  
  
    5.  <span data-ttu-id="e7531-130">Si aucune action se produit dans le temps à la période d’exécution, et ce n’est pas CIDX, le processus public envoie un message de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e7531-130">If no action occurs within the Time to Perform period, and this is not CIDX, the public process sends a 0A1 message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7531-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7531-131">See Also</span></span>  
 <span data-ttu-id="e7531-132">[Processus publics](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span><span class="sxs-lookup"><span data-stu-id="e7531-132">[Public Processes](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md) </span></span>  
 [<span data-ttu-id="e7531-133">Processus Public de répondeur</span><span class="sxs-lookup"><span data-stu-id="e7531-133">Responder Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)