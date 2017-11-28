---
title: "Autorisation du récepteur d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, messages
- messages, receive authorization
- receive authorization
- messages, security
ms.assetid: c0cdb3ef-ee8e-40a1-9362-13cd26495951
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7317cd9c54568edd2c49df026790ee7a1e70fb2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="authorizing-the-receiver-of-a-message"></a><span data-ttu-id="5c243-102">Autorisation du récepteur d’un Message</span><span class="sxs-lookup"><span data-stu-id="5c243-102">Authorizing the Receiver of a Message</span></span>
<span data-ttu-id="5c243-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de restreindre la réception de messages à un nombre de processus et de tiers autorisés.</span><span class="sxs-lookup"><span data-stu-id="5c243-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to limit the processes and parties that you authorize to receive messages.</span></span>  
  
 <span data-ttu-id="5c243-104">Le schéma suivant représente les fonctionnalités de sécurité dans BizTalk Server auxquelles vous pouvez faire appel pour approuver le récepteur d'un message.</span><span class="sxs-lookup"><span data-stu-id="5c243-104">The following figure shows the security features in BizTalk Server that you use to authorize the receiver of a message.</span></span>  
  
 <span data-ttu-id="5c243-105">![Fonctionnalités de sécurité autorisant le destinataire du message](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")</span><span class="sxs-lookup"><span data-stu-id="5c243-105">![Security features authorizing the message receiver](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")</span></span>  
<span data-ttu-id="5c243-106">Fonctionnalités de sécurité utilisées par BizTalk Server pour approuver le récepteur d'un message.</span><span class="sxs-lookup"><span data-stu-id="5c243-106">Security features BizTalk Server uses to authorize the receiver of a message.</span></span>  
  
 <span data-ttu-id="5c243-107">Vous pouvez utiliser les mécanismes de sécurité suivants pour identifier les utilisateurs qui sont autorisés à recevoir les messages que vous envoyez :</span><span class="sxs-lookup"><span data-stu-id="5c243-107">You can use the following security mechanisms to establish who has permission (authorization) to receive the messages that you send:</span></span>  
  
-   <span data-ttu-id="5c243-108">**Déchiffrement.**</span><span class="sxs-lookup"><span data-stu-id="5c243-108">**Decryption.**</span></span> <span data-ttu-id="5c243-109">veillez à ce que les tiers expéditeurs de messages à BizTalk Server disposent du certificat de clé publique permettant de chiffrer les messages qu'ils lui envoient.</span><span class="sxs-lookup"><span data-stu-id="5c243-109">Make sure the parties that send messages to BizTalk Server have the public key certificate for encrypting messages they send to BizTalk Server.</span></span> <span data-ttu-id="5c243-110">BizTalk Server utilise le certificat de clé privée pour déchiffrer un message.</span><span class="sxs-lookup"><span data-stu-id="5c243-110">BizTalk Server uses the private key certificate to decrypt the message.</span></span>  
  
-   <span data-ttu-id="5c243-111">**L’autorisation de réception.**</span><span class="sxs-lookup"><span data-stu-id="5c243-111">**Receive Authorization.**</span></span> <span data-ttu-id="5c243-112">cette méthode permet de contrôler, au sein de l'environnement BizTalk Server, les hôtes qui peuvent recevoir un message donné.</span><span class="sxs-lookup"><span data-stu-id="5c243-112">You can use this method to control which hosts within the BizTalk Server environment can receive a given message.</span></span>  
  
-   <span data-ttu-id="5c243-113">**Chiffrement.**</span><span class="sxs-lookup"><span data-stu-id="5c243-113">**Encryption.**</span></span> <span data-ttu-id="5c243-114">lorsque BizTalk chiffre un message, le certificat de clé publique d'un tiers donné permet de garantir que seul le tiers auquel ce message est destiné sera en mesure de le lire.</span><span class="sxs-lookup"><span data-stu-id="5c243-114">By using the public key certificate from a given party when BizTalk encrypts a message, you can ensure that only the intended party is able to read the message.</span></span>  
  
## <a name="receive-authorization"></a><span data-ttu-id="5c243-115">Autorisation de réception</span><span class="sxs-lookup"><span data-stu-id="5c243-115">Receive Authorization</span></span>  
 <span data-ttu-id="5c243-116">L'autorisation de réception constitue la méthode vous permettant de contrôler les hôtes qui sont autorisés à recevoir (s'abonner à) un message donné.</span><span class="sxs-lookup"><span data-stu-id="5c243-116">Receive authorization is the method you can use to control which hosts can receive (subscribe for) a given message.</span></span> <span data-ttu-id="5c243-117">BizTalk Server utilise les informations de certificat comme une propriété d’abonnement pour faire correspondre les prédicats sur le message : la base de données MessageBox achemine uniquement les messages marqués comme requérant une autorisation aux hôtes disposant du certificat de déchiffrement pour ce message.</span><span class="sxs-lookup"><span data-stu-id="5c243-117">BizTalk Server uses the certificate information as a subscription property to match predicates on the message: the MessageBox database only routes messages marked as authorization required to the hosts that have the decryption certificate for that message.</span></span> <span data-ttu-id="5c243-118">Pour illustrer le processus, considérons les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="5c243-118">To illustrate the process, consider the following scenarios:</span></span>  
  
-   <span data-ttu-id="5c243-119">**Routage d’un message non chiffré :** lorsque BizTalk Server reçoit un message indiquant que l’expéditeur n’a pas chiffrées, il n’existe aucune limitation de déchiffrement comment BizTalk achemine le message.</span><span class="sxs-lookup"><span data-stu-id="5c243-119">**Routing an un-encrypted message:** When BizTalk Server receives a message that the sender did not encrypt, there is no decryption limitation as to how BizTalk routes the message.</span></span> <span data-ttu-id="5c243-120">Les hôtes disposant d'un certificat d'autorisation de réception configuré et ceux n'en disposant pas peuvent recevoir le message.</span><span class="sxs-lookup"><span data-stu-id="5c243-120">Both hosts with and hosts without receive authorization certificates configured can receive the message.</span></span>  
  
-   <span data-ttu-id="5c243-121">**Routage d’un message chiffré :** lors de l’arrivée d’un message chiffré, le pipeline de réception doit contenir un composant de décodage qui déchiffre le message.</span><span class="sxs-lookup"><span data-stu-id="5c243-121">**Routing an encrypted message:** When an encrypted message arrives, the receiving pipeline must contain a decoding component that decrypts the message.</span></span> <span data-ttu-id="5c243-122">Lorsque BizTalk Server achemine un message après que celui-ci ait été déchiffré, il fait appel à l'empreinte du certificat qui a été utilisée pour déchiffrer le message en tant que preuve dans le mécanisme d'abonnement à la base de données MessageBox, et seuls les hôtes configurés avec ce certificat recevront le message.</span><span class="sxs-lookup"><span data-stu-id="5c243-122">When BizTalk Server routes a message after it is decrypted, BizTalk uses the certificate thumbprint used to decrypt the message as evidence in the MessageBox database subscription mechanism, and only those hosts configured with that certificate receive the message.</span></span>  
  
 <span data-ttu-id="5c243-123">Si vous souhaitez utiliser l'autorisation de réception, vous devez indiquer l'empreinte du certificat de déchiffrement dans les propriétés de l'hôte auquel vous voulez octroyer l'autorisation de réception du message.</span><span class="sxs-lookup"><span data-stu-id="5c243-123">If you want to use receive authorization, you must provide the thumbprint of the decryption certificate in the properties of the host that you want to authorize to receive the message.</span></span> <span data-ttu-id="5c243-124">Pour plus d’informations sur l’autorisation de réception, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5c243-124">For more information about receive authorization, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c243-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c243-125">See Also</span></span>  
 <span data-ttu-id="5c243-126">[Authentification des messages entrants](../core/inbound-message-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="5c243-126">[Inbound Message Authentication](../core/inbound-message-authentication.md) </span></span>  
 <span data-ttu-id="5c243-127">[Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md) </span><span class="sxs-lookup"><span data-stu-id="5c243-127">[Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md) </span></span>  
 <span data-ttu-id="5c243-128">[Protection des messages sortants](../core/outbound-message-protection.md) </span><span class="sxs-lookup"><span data-stu-id="5c243-128">[Outbound Message Protection](../core/outbound-message-protection.md) </span></span>  
 <span data-ttu-id="5c243-129">[Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="5c243-129">[Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) </span></span>  
 [<span data-ttu-id="5c243-130">Planification de la sécurité de Message</span><span class="sxs-lookup"><span data-stu-id="5c243-130">Planning Message Security</span></span>](../core/planning-message-security.md)