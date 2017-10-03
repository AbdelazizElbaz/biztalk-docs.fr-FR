---
title: Protection des messages sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, outbound messages
- outbound messages
- security, messages
- authenticating, warnings
- messages, outbound
ms.assetid: 839d3b44-bb44-454b-817c-67b7c8cd74c9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adbbae776edee8a4f563e2cd48ee035acc3fd7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="outbound-message-protection"></a><span data-ttu-id="cdd64-102">Protection des messages sortants</span><span class="sxs-lookup"><span data-stu-id="cdd64-102">Outbound Message Protection</span></span>
<span data-ttu-id="cdd64-103">La figure suivante illustre les fonctionnalités de sécurité dans BizTalk Server qui permettent d'empêcher la lecture des messages sortants par des tiers non autorisés.</span><span class="sxs-lookup"><span data-stu-id="cdd64-103">The following figure shows the security features in BizTalk Server that you use to help protect outbound messages from being read by unauthorized parties.</span></span>  
  
 <span data-ttu-id="cdd64-104">![Fonctionnalités de sécurité protégeant des messages sortants](../core/media/ebiz-plan-secoverview-auth-outbound.gif "ebiz_plan_secoverview_auth_outbound")</span><span class="sxs-lookup"><span data-stu-id="cdd64-104">![Security features protecting outbound messages](../core/media/ebiz-plan-secoverview-auth-outbound.gif "ebiz_plan_secoverview_auth_outbound")</span></span>  
<span data-ttu-id="cdd64-105">Fonctionnalités de sécurité utilisées par BizTalk Server pour protéger les messages sortants</span><span class="sxs-lookup"><span data-stu-id="cdd64-105">Security features BizTalk Server uses to protect outbound messages.</span></span>  
  
 <span data-ttu-id="cdd64-106">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message, il entreprend les actions suivantes pour assurer qu'il envoie le message de manière sécurisée, et que le tiers de réception peut déterminer l'expéditeur du message :</span><span class="sxs-lookup"><span data-stu-id="cdd64-106">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a message, it takes the following steps to help ensure that it sends the message securely, and that the receiving party can determine the message sender:</span></span>  
  
1.  <span data-ttu-id="cdd64-107">Si le pipeline d'envoi contient un composant de codage (par exemple, S/MIME) configuré pour signer tous les messages sortants, le certificat de signature pour le groupe BizTalk est extrait du magasin de certificats personnel pour le compte de service d'instance de l'hôte sous lequel le pipeline est exécuté, et le message est signé à l'aide de la clé privée associée au certificat.</span><span class="sxs-lookup"><span data-stu-id="cdd64-107">If the send pipeline contains an encoding component (such as S/MIME) that is configured to sign all outbound messages, the signing certificate for the BizTalk group is retrieved from the personal certificate store for the host instance service account under which the pipeline is running, and the message is signed using the private key associated with the certificate.</span></span>  
  
2.  <span data-ttu-id="cdd64-108">Si le pipeline d'envoi contient un composant de codage (par exemple, S/MIME) configuré pour chiffrer tous les messages sortants, l'empreinte du certificat de chiffrement est utilisée pour récupérer le certificat de clé publique du magasin de certificats Autres personnes, et le message est chiffré à l'aide de ce certificat.</span><span class="sxs-lookup"><span data-stu-id="cdd64-108">If the send pipeline contains an encoding component (such as S/MIME) that is configured to encrypt all outbound messages, the encryption certificate thumbprint is used to retrieve the public key certificate from the Other People certificate store, and the message is encrypted using that certificate.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cdd64-109">Bien que vous utilisiez un certificat de signature pour tous les pipelines d'envoi dans votre environnement BizTalk, vous devez vous assurer que ce certificat de signature est disponible dans le magasin de certificats du compte de service de chaque instance des hôtes dans lesquels les pipelines d'envoi sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="cdd64-109">Although you use one signing certificate for all the send pipelines in your BizTalk environment, you must ensure this signing certificate is available in the certificate store of the service account of each host instance of the hosts where the send pipelines are running.</span></span>  
  
 <span data-ttu-id="cdd64-110">Pour plus d’informations sur l’envoi de messages signés, consultez [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span><span class="sxs-lookup"><span data-stu-id="cdd64-110">For more information about how to send signed messages, see [How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd64-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdd64-111">See Also</span></span>  
 <span data-ttu-id="cdd64-112">[Authentification des messages entrants](../core/inbound-message-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="cdd64-112">[Inbound Message Authentication](../core/inbound-message-authentication.md) </span></span>  
 <span data-ttu-id="cdd64-113">[Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md) </span><span class="sxs-lookup"><span data-stu-id="cdd64-113">[Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md) </span></span>  
 <span data-ttu-id="cdd64-114">[Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="cdd64-114">[Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) </span></span>  
 <span data-ttu-id="cdd64-115">[Autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="cdd64-115">[Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md) </span></span>  
 [<span data-ttu-id="cdd64-116">Certificats utilisés par BizTalk Server pour les Messages signés</span><span class="sxs-lookup"><span data-stu-id="cdd64-116">Certificates that BizTalk Server Uses for Signed Messages</span></span>](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)