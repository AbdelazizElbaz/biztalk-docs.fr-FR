---
title: "Planification de la sécurité de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- planning, security
- security, messages
- security, planning
- messages, security
ms.assetid: c0f93515-a822-425c-9155-270a179d6b61
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826db8480d378342ee30993f67bbd60e27751d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-message-security"></a><span data-ttu-id="fb021-102">Planification de la sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="fb021-102">Planning Message Security</span></span>
<span data-ttu-id="fb021-103">Selon les stratégies de sécurité en vigueur dans votre société, vous souhaitez peut-être tenir compte des questions soulevées dans le tableau suivant pour déterminer le niveau de sécurité à implémenter au sein de votre environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fb021-103">Based on the security policies in your company, you may want to consider the questions in the following table to determine the level of security that you must implement in your BizTalk Server environment.</span></span> <span data-ttu-id="fb021-104">Les réponses à ces questions déterminent les fonctionnalités de sécurité appropriées à une messagerie.</span><span class="sxs-lookup"><span data-stu-id="fb021-104">The answers to these questions will determine the security features that you need for messaging.</span></span>  
  
|<span data-ttu-id="fb021-105">Question</span><span class="sxs-lookup"><span data-stu-id="fb021-105">Question</span></span>|<span data-ttu-id="fb021-106">Fonctionnalité de sécurité de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fb021-106">BizTalk Server Security Feature</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="fb021-107">**Lors de la réception d’un message :**</span><span class="sxs-lookup"><span data-stu-id="fb021-107">**When receiving a message:**</span></span>||  
|<span data-ttu-id="fb021-108">Comment déterminer l'identité de l'expéditeur d'un message ?</span><span class="sxs-lookup"><span data-stu-id="fb021-108">How do you determine the identity of the sender of the message?</span></span>|<span data-ttu-id="fb021-109">Le composant Résolution du tiers d'un pipeline BizTalk et le certificat de signature ou l'ID de sécurité Windows (SID) permettent d'identifier clairement l'expéditeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="fb021-109">You can use the party resolution component in the BizTalk pipeline and the signing certificate or Windows Security ID (SID) to identify the sender of a message positively.</span></span> <span data-ttu-id="fb021-110">Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb021-110">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="fb021-111">Connaissez-vous le tiers expéditeur du message ?</span><span class="sxs-lookup"><span data-stu-id="fb021-111">Do you know the party that sent you the message?</span></span>|<span data-ttu-id="fb021-112">Le composant Résolution du tiers d'un pipeline BizTalk permet de déterminer si le tiers expéditeur d'un message est un partenaire commercial déjà présent dans votre système.</span><span class="sxs-lookup"><span data-stu-id="fb021-112">You can use the party resolution component in the BizTalk pipeline to determine whether the party that sent you the message is a trading partner already in your system.</span></span> <span data-ttu-id="fb021-113">Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb021-113">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="fb021-114">Comment éviter de recevoir des messages en provenance de tiers que vous ne connaissez pas ?</span><span class="sxs-lookup"><span data-stu-id="fb021-114">Do you want to avoid receiving messages from parties you do not know?</span></span>|<span data-ttu-id="fb021-115">La fonctionnalité d'authentification requise d'un port permet d'exiger qu'un serveur BizTalk traite uniquement les messages en provenance de tiers connus.</span><span class="sxs-lookup"><span data-stu-id="fb021-115">You can use the authentication required feature in the port to require that BizTalk server processes only the messages from parties that you know.</span></span> <span data-ttu-id="fb021-116">Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb021-116">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>|  
|<span data-ttu-id="fb021-117">**Lors de l’envoi d’un message :**</span><span class="sxs-lookup"><span data-stu-id="fb021-117">**When sending a message:**</span></span>||  
|<span data-ttu-id="fb021-118">Comment garantir la confidentialité d'un message sortant ?</span><span class="sxs-lookup"><span data-stu-id="fb021-118">How do you ensure the privacy of outgoing messages?</span></span>|<span data-ttu-id="fb021-119">Vous pouvez chiffrer un message pour garantir que seul le tiers auquel il est destiné pourra le lire.</span><span class="sxs-lookup"><span data-stu-id="fb021-119">You can encrypt the message to ensure that only the intended party can read the message.</span></span> <span data-ttu-id="fb021-120">Pour plus d’informations, consultez [Protection des messages sortants](../core/outbound-message-protection.md).</span><span class="sxs-lookup"><span data-stu-id="fb021-120">For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).</span></span>|  
|<span data-ttu-id="fb021-121">Comment empêcher les utilisateurs malveillants de falsifier un message lors de sa transmission ?</span><span class="sxs-lookup"><span data-stu-id="fb021-121">How do you prevent malicious users from tampering with the message during transmission?</span></span>|<span data-ttu-id="fb021-122">Les signatures numériques permettent de garantir l'intégrité d'un message.</span><span class="sxs-lookup"><span data-stu-id="fb021-122">You can use digital signatures to ensure the integrity of the message.</span></span> <span data-ttu-id="fb021-123">Pour plus d’informations, consultez [Protection des messages sortants](../core/outbound-message-protection.md).</span><span class="sxs-lookup"><span data-stu-id="fb021-123">For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="fb021-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fb021-124">In This Section</span></span>  
  
-   [<span data-ttu-id="fb021-125">Sécurité pour envoyer et recevoir des Messages</span><span class="sxs-lookup"><span data-stu-id="fb021-125">Security for Sending and Receiving Messages</span></span>](../core/security-for-sending-and-receiving-messages.md)  
  
-   [<span data-ttu-id="fb021-126">Chiffrement et les certificats de signature</span><span class="sxs-lookup"><span data-stu-id="fb021-126">Encryption and Signing Certificates</span></span>](../core/encryption-and-signing-certificates.md)  
  
-   [<span data-ttu-id="fb021-127">Authentification de l’expéditeur d’un Message</span><span class="sxs-lookup"><span data-stu-id="fb021-127">Authenticating the Sender of a Message</span></span>](../core/authenticating-the-sender-of-a-message.md)  
  
-   [<span data-ttu-id="fb021-128">Autorisation du récepteur d’un Message</span><span class="sxs-lookup"><span data-stu-id="fb021-128">Authorizing the Receiver of a Message</span></span>](../core/authorizing-the-receiver-of-a-message.md)