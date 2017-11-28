---
title: "Certificats utilisés par BizTalk Server pour les Messages signés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, signed messages
- messages, message flow [digital signatures]
- S/MIME messages
- signed messages
- digital signatures, message flow
- messages, certificates
ms.assetid: 0b521e11-73ef-424f-9e6a-4fb42dc263ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cce82b634fffac4af0f75cdff26c7f512a132de9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-signed-messages"></a><span data-ttu-id="1f633-102">Certificats utilisés par BizTalk Server pour les messages signés</span><span class="sxs-lookup"><span data-stu-id="1f633-102">Certificates that BizTalk Server Uses for Signed Messages</span></span>
<span data-ttu-id="1f633-103">BizTalk Server prend en charge la signature des messages sortants et la vérification de signature des messages S/MIME (Secure Multipurpose Internet Mail Extensions) entrants.</span><span class="sxs-lookup"><span data-stu-id="1f633-103">BizTalk Server supports signing outbound messages and signature verification for inbound Secure Multipurpose Internet Mail Extensions (S/MIME) messages.</span></span> <span data-ttu-id="1f633-104">BizTalk Server utilise S/MIME versions 2 et 3 pour signer les messages sortants et valider la signature des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="1f633-104">BizTalk Server uses S/MIME versions 2 and 3 to sign outbound messages and to validate the signature of inbound messages.</span></span> <span data-ttu-id="1f633-105">De même, vous pouvez configurer BizTalk Server pour signer puis chiffrer les messages qu'il envoie aux partenaires.</span><span class="sxs-lookup"><span data-stu-id="1f633-105">Similarly, you can configure BizTalk Server to sign and then encrypt the messages it sends to its partners.</span></span>  
  
-   <span data-ttu-id="1f633-106">BizTalk Server prend en charge les algorithmes de signature SHA-1 et MD5 pour la vérification des signatures numériques.</span><span class="sxs-lookup"><span data-stu-id="1f633-106">BizTalk Server supports the SHA-1 and MD5 signing algorithms for verifying digital signatures.</span></span> <span data-ttu-id="1f633-107">BizTalk Server utilise l'algorithme de signature SHA-1 pour signer les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="1f633-107">BizTalk Server uses the SHA-1 signing algorithm to sign outbound messages.</span></span>  
  
-   <span data-ttu-id="1f633-108">Les systèmes d'échange de clés pris en charge par BizTalk Server pour les clés de signature sont les algorithmes RSA (Rivest-Shamir-Adleman) et la norme DSS (Digital Signature Standard).</span><span class="sxs-lookup"><span data-stu-id="1f633-108">The key exchange systems supported by BizTalk Server for signature keys are the Rivest-Shamir-Adleman (RSA) algorithms and the Digital Signature Standard (DSS).</span></span> <span data-ttu-id="1f633-109">BizTalk Server ne prend pas en charge le système d'échange AES (Advanced Encryption Standard) pour les clés de signature.</span><span class="sxs-lookup"><span data-stu-id="1f633-109">BizTalk Server does not support the Advanced Encryption Standard (AES) exchange system for signature keys.</span></span>  
  
-   <span data-ttu-id="1f633-110">Le certificat de signature pris en charge par BizTalk Server est x.509 version 3.</span><span class="sxs-lookup"><span data-stu-id="1f633-110">The signing certificate supported by BizTalk Server is x.509 version 3.</span></span>  
  
 <span data-ttu-id="1f633-111">La figure suivante illustre le flux de messages lorsque BizTalk Server reçoit un message signé numériquement et utilise la signature (facultatif) pour résoudre l'identité du partenaire vers un tiers dans l'environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1f633-111">The following figure shows the message flow when BizTalk Server receives a digitally signed message and optionally uses the signature to resolve the partner identity to a party in the BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="1f633-112">![Flux de messages lors de l’envoi d’un message signé](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")</span><span class="sxs-lookup"><span data-stu-id="1f633-112">![Message flow when sending a signed message](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")</span></span>  
  
 <span data-ttu-id="1f633-113">Lorsque BizTalk Server reçoit un message signé numériquement, le flux de messages est le suivant :</span><span class="sxs-lookup"><span data-stu-id="1f633-113">The message flow when BizTalk Server receives a digitally signed message is as follows:</span></span>  
  
1.  <span data-ttu-id="1f633-114">Un partenaire envoie un message à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1f633-114">A partner sends a message to BizTalk Server.</span></span> <span data-ttu-id="1f633-115">Il signe le message avec son certificat de clé privée.</span><span class="sxs-lookup"><span data-stu-id="1f633-115">The partner signs the message with its private key certificate.</span></span>  
  
2.  <span data-ttu-id="1f633-116">Le gestionnaire de réception BizTalk Server approprié reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="1f633-116">The appropriate BizTalk Server receive handler receives the message.</span></span>  
  
3.  <span data-ttu-id="1f633-117">Durant l'exécution du pipeline de réception, le composant de pipeline Décodeur MIME/SMIME vérifie la signature numérique à l'aide de la clé publique du partenaire.</span><span class="sxs-lookup"><span data-stu-id="1f633-117">During the execution of the receive pipeline, the MIME/SMIME Decoder pipeline component verifies the digital signature by using the partner's public key.</span></span>  
  
4.  <span data-ttu-id="1f633-118">Si le composant Résolution du tiers est configuré, le certificat de clé publique du partenaire est utilisé pour identifier le tiers dans le système BizTalk Server durant l'exécution du composant de pipeline de réception Résolution du tiers.</span><span class="sxs-lookup"><span data-stu-id="1f633-118">If party resolution component is configured, the partner's public key certificate is used to identify the party in the BizTalk Server system during the execution of the receive pipeline party resolution component.</span></span>  
  
5.  <span data-ttu-id="1f633-119">Un traitement supplémentaire se produit.</span><span class="sxs-lookup"><span data-stu-id="1f633-119">Additional processing occurs.</span></span>  
  
 <span data-ttu-id="1f633-120">La figure suivante illustre le flux de messages lorsque BizTalk Server envoie un message signé numériquement.</span><span class="sxs-lookup"><span data-stu-id="1f633-120">The following figure shows the message flow when BizTalk Server sends a digitally signed message.</span></span>  
  
 ![](../core/media/bts-bpi-sp-msgsec-outboundsigning-r2c.gif "bts_BPI_SP_MSGSEC_OutboundSigning_R2c")  
  
 <span data-ttu-id="1f633-121">Lorsque BizTalk Server envoie un message signé numériquement à un partenaire, le flux de messages est le suivant :</span><span class="sxs-lookup"><span data-stu-id="1f633-121">The message flow when BizTalk Server sends a digitally signed message to a partner is as follows:</span></span>  
  
1.  <span data-ttu-id="1f633-122">Le gestionnaire d'envoi BizTalk Server approprié envoie un message au partenaire.</span><span class="sxs-lookup"><span data-stu-id="1f633-122">The appropriate BizTalk Server send handler sends a message to the partner.</span></span>  
  
2.  <span data-ttu-id="1f633-123">Durant l'exécution du pipeline d'envoi, le composant de pipeline Encodeur MIME/SMIME signe le message à l'aide de la clé privée de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1f633-123">During the execution of the send pipeline, the MIME/SMIME Encoder pipeline component signs the message by using the BizTalk Server private key.</span></span>  
  
3.  <span data-ttu-id="1f633-124">Le partenaire reçoit le message de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1f633-124">The partner receives the message from BizTalk Server.</span></span> <span data-ttu-id="1f633-125">Il utilise la clé publique de BizTalk Server pour vérifier la signature numérique.</span><span class="sxs-lookup"><span data-stu-id="1f633-125">The partner uses the BizTalk Server public key to verify the digital signature.</span></span>  
  
 <span data-ttu-id="1f633-126">BizTalk Server contrôle la validité des certificats associés aux messages signés entrants en validant la chaîne d'approbation de l'autorité de certification associée et en s'assurant que le certificat n'est pas arrivé à expiration.</span><span class="sxs-lookup"><span data-stu-id="1f633-126">BizTalk Server verifies the validity of the certificates associated with the incoming signed messages by validating the certification authority (CA) trust chain for the certificate and by verifying that the certificate has not expired.</span></span> <span data-ttu-id="1f633-127">Pour valider la chaîne d'approbation de l'autorité de certification, il parcourt la chaîne d'approbation des certificats jusqu'à ce qu'il atteigne une autorité de certification racine.</span><span class="sxs-lookup"><span data-stu-id="1f633-127">The process of validating the CA trust chain involves traversing the chain of trust on certificates until a root certification authority is reached.</span></span> <span data-ttu-id="1f633-128">Il s'assure ainsi que le certificat employé pour signer un message provient effectivement du tiers identifié.</span><span class="sxs-lookup"><span data-stu-id="1f633-128">This validates that the certificate used to sign a message is indeed from the identified party.</span></span> <span data-ttu-id="1f633-129">Cette validation est effectuée lors de l'exécution de chaque message signé.</span><span class="sxs-lookup"><span data-stu-id="1f633-129">This validation occurs at runtime for each and every signed message.</span></span>  
  
 <span data-ttu-id="1f633-130">BizTalk Server peut en outre vérifier que l'autorité de certification n'a pas révoqué le certificat utilisé pour signer ou chiffrer le message ;</span><span class="sxs-lookup"><span data-stu-id="1f633-130">In addition, BizTalk Server can verify that the certification authority has not revoked the certificate used to sign or encrypt the message.</span></span> <span data-ttu-id="1f633-131">pour cela, vous devez télécharger la liste de révocation des certificats de l'autorité de certification et l'installer avec l'Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="1f633-131">To do this, you must download the certificate revocation list (CRL) from the certification authority and install it using Windows Explorer.</span></span> <span data-ttu-id="1f633-132">Pour plus d’informations sur la façon de valider un certificat, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="1f633-132">For more information about how to validate a certificate, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f633-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f633-133">See Also</span></span>  
 <span data-ttu-id="1f633-134">[Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1f633-134">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 <span data-ttu-id="1f633-135">[Magasins de certificats par BizTalk Server](../core/certificate-stores-that-biztalk-server-uses.md) </span><span class="sxs-lookup"><span data-stu-id="1f633-135">[Certificate Stores that BizTalk Server Uses](../core/certificate-stores-that-biztalk-server-uses.md) </span></span>  
 <span data-ttu-id="1f633-136">[Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md) </span><span class="sxs-lookup"><span data-stu-id="1f633-136">[Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md) </span></span>  
 [<span data-ttu-id="1f633-137">Envoyer et recevoir des Messages signés</span><span class="sxs-lookup"><span data-stu-id="1f633-137">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)