---
title: "Certificats utilisés par BizTalk Server pour des Messages chiffrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow [encrypted messages]
- encrypted messages
- messages, encryption
ms.assetid: 44b06488-4ecd-436d-af3d-b95e285ecb3e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f2dbd51506da7b505f66b3001b8bdc6fa0a58ac
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="certificates-that-biztalk-server-uses-for-encrypted-messages"></a><span data-ttu-id="94c37-102">Certificats utilisés par BizTalk Server pour les messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="94c37-102">Certificates that BizTalk Server Uses for Encrypted Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="94c37-103"> prend en charge le chiffrement à clé publique des messages sortants et le déchiffrement des messages entrants basé sur S/MIME.</span><span class="sxs-lookup"><span data-stu-id="94c37-103"> supports public key encryption of outbound messages and decryption of inbound messages based on Secure Multipurpose Internet Mail Extensions (S/MIME).</span></span> <span data-ttu-id="94c37-104">BizTalk Server utilise S/MIME version 3 pour le chiffrement des messages sortants et S/MIME versions 2 et 3 pour le déchiffrement des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="94c37-104">BizTalk Server uses S/MIME version 3 for encryption of outbound messages, and S/MIME versions 2 and 3 for decryption of inbound messages.</span></span>  
  
-   <span data-ttu-id="94c37-105">BizTalk Server prend en charge les certificats de chiffrement RSA et Diffie Hellman.</span><span class="sxs-lookup"><span data-stu-id="94c37-105">BizTalk Server supports RSA and Diffie Hellman encryption certificates.</span></span>  
  
-   <span data-ttu-id="94c37-106">BizTalk Server prend en charge les algorithmes de chiffrement Data Encryption Standard (DES), 3DES et RC2.</span><span class="sxs-lookup"><span data-stu-id="94c37-106">BizTalk Server supports Data Encryption Standard (DES), 3DES, and RC2 encryption algorithms.</span></span>  
  
 <span data-ttu-id="94c37-107">La figure suivante illustre le flux de message lorsque BizTalk Server reçoit un message chiffré.</span><span class="sxs-lookup"><span data-stu-id="94c37-107">The following figure shows the message flow when BizTalk Server receives an encrypted message.</span></span>  
  
 <span data-ttu-id="94c37-108">![Flux de messages lors de la réception d’un message chiffré](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")</span><span class="sxs-lookup"><span data-stu-id="94c37-108">![Message flow when receiving an encrypted message](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")</span></span>  
  
 <span data-ttu-id="94c37-109">Le flux de message lorsque BizTalk Server reçoit un message chiffré est le suivant :</span><span class="sxs-lookup"><span data-stu-id="94c37-109">The message flow when BizTalk Server receives an encrypted message is as follows:</span></span>  
  
1.  <span data-ttu-id="94c37-110">Un partenaire envoie un message à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="94c37-110">A partner sends a message to BizTalk Server.</span></span> <span data-ttu-id="94c37-111">Le partenaire chiffre le message avec la clé publique de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="94c37-111">The partner encrypts the message with the BizTalk Server public key.</span></span>  
  
2.  <span data-ttu-id="94c37-112">Le gestionnaire de réception BizTalk Server approprié reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="94c37-112">The appropriate BizTalk Server receive handler receives the message.</span></span>  
  
3.  <span data-ttu-id="94c37-113">Durant l'exécution du pipeline de réception, le composant de pipeline Décodeur MIME/SMIME déchiffre le message à l'aide de la clé privée de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="94c37-113">During the receive pipeline execution, the MIME/SMIME Decoder pipeline component decrypts the message by using the BizTalk Server private key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94c37-114">Pour le déchiffrement de pipeline réussisse sur un ordinateur IIS 7.0, vérifiez que le compte pour le pool d’applications IIS et le compte utilisé par l’instance d’hôte associé au Gestionnaire de réception sont identiques et que ce compte est un membre de la \<machineName \>\IIS_WPG groupe.</span><span class="sxs-lookup"><span data-stu-id="94c37-114">For pipeline decryption to succeed on an IIS 7.0 computer, ensure that the account for the IIS application pool and the account used by the host instance associated with the receive handler are the same and that this account is a member of the \<machineName\>\IIS_WPG group.</span></span> <span data-ttu-id="94c37-115">Pour plus d’informations sur la configuration IIS traiter identité pour IIS 7.0, consultez [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md).</span><span class="sxs-lookup"><span data-stu-id="94c37-115">For more information on setting IIS process identity for IIS 7.0 see [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md).</span></span> <span data-ttu-id="94c37-116">Ces processus doivent s'exécuter sous le même compte afin de garantir que le profil de compte est chargé, et qu'à son tour, il charge les clés de registre requises pour effectuer le déchiffrement dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="94c37-116">These processes must run under the same account to ensure that the account profile is loaded which in turns loads the registry keys required to perform decryption in the pipeline.</span></span> <span data-ttu-id="94c37-117">Pour des raisons de performances, IIS 7.0 ne charge pas le profil de compte lors du démarrage du processus w3wp.exe associé. L'instance de l'hôte BizTalk doit donc être configurée avec le même compte, de façon à ce que BizTalk charge le profil de compte et les clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="94c37-117">For performance reasons, IIS 7.0 does not load the account profile when starting the associated w3wp.exe process so the BizTalk host instance must be configured with the same account so that BizTalk will load the account profile and registry keys.</span></span>  
  
4.  <span data-ttu-id="94c37-118">Un traitement supplémentaire se produit.</span><span class="sxs-lookup"><span data-stu-id="94c37-118">Additional processing occurs.</span></span>  
  
 <span data-ttu-id="94c37-119">La figure suivante illustre le flux de message lorsque BizTalk Server envoie un message chiffré.</span><span class="sxs-lookup"><span data-stu-id="94c37-119">The following figure shows the message flow when BizTalk Server sends an encrypted message.</span></span>  
  
 <span data-ttu-id="94c37-120">![Flux de messages lors de l’envoi d’un message chiffré](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")</span><span class="sxs-lookup"><span data-stu-id="94c37-120">![Message flow when sending an encrypted message](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")</span></span>  
  
 <span data-ttu-id="94c37-121">Le flux de message lorsque BizTalk Server envoie un message chiffré à un partenaire est le suivant :</span><span class="sxs-lookup"><span data-stu-id="94c37-121">The message flow when BizTalk Server sends an encrypted message to a partner is as follows:</span></span>  
  
1.  <span data-ttu-id="94c37-122">Le gestionnaire d'envoi BizTalk Server approprié envoie un message au partenaire.</span><span class="sxs-lookup"><span data-stu-id="94c37-122">The appropriate BizTalk Server send handler sends a message to the partner.</span></span>  
  
2.  <span data-ttu-id="94c37-123">Durant l'exécution du pipeline d'envoi, le composant de pipeline Encodeur MIME/SMIME chiffre le message à l'aide de la clé publique du partenaire.</span><span class="sxs-lookup"><span data-stu-id="94c37-123">During the send pipeline execution, the MIME/SMIME Encoder pipeline component encrypts the message by using the partner's public key.</span></span>  
  
3.  <span data-ttu-id="94c37-124">Le partenaire reçoit le message de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="94c37-124">The partner receives the message from BizTalk Server.</span></span> <span data-ttu-id="94c37-125">Le partenaire utilise sa clé privée pour déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="94c37-125">The partner uses its private key to decrypt the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c37-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94c37-126">See Also</span></span>  
 <span data-ttu-id="94c37-127">[Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="94c37-127">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 <span data-ttu-id="94c37-128">[Magasins de certificats par BizTalk Server](../core/certificate-stores-that-biztalk-server-uses.md) </span><span class="sxs-lookup"><span data-stu-id="94c37-128">[Certificate Stores that BizTalk Server Uses](../core/certificate-stores-that-biztalk-server-uses.md) </span></span>  
 <span data-ttu-id="94c37-129">[Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md) </span><span class="sxs-lookup"><span data-stu-id="94c37-129">[Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md) </span></span>  
 [<span data-ttu-id="94c37-130">Envoi et réception des messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="94c37-130">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)