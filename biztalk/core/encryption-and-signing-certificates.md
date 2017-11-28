---
title: Chiffrement et les certificats de signature | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, security
- security, certificates
- security, messages
- certificates, encryption
- encryption certificates, messages
- messages, encryption
- messages, certificates
- security, encryption
ms.assetid: 3c3f9de5-4156-4133-8d5e-c30b142b6d61
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633484a6c5599b9323bfd7798f621b27a501ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="encryption-and-signing-certificates"></a><span data-ttu-id="5b414-102">Chiffrement et les certificats de signature</span><span class="sxs-lookup"><span data-stu-id="5b414-102">Encryption and Signing Certificates</span></span>
<span data-ttu-id="5b414-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appuie en grande partie sur la sécurité fournie par les certificats.</span><span class="sxs-lookup"><span data-stu-id="5b414-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies heavily on the security provided by certificates.</span></span> <span data-ttu-id="5b414-104">En utilisant les certificats pour le chiffrement et les signatures numériques, BizTalk Server peut envoyer et recevoir des données fiables et garantir que les données qu'il traite sont sécurisées.</span><span class="sxs-lookup"><span data-stu-id="5b414-104">By using certificates for encryption and digital signatures, BizTalk Server can send and receive data that can be trusted, and can help ensure that the data it processes is secure.</span></span> <span data-ttu-id="5b414-105">Pour le chiffrement et les signatures numériques, un certificat de clé publique et un certificat de clé privée sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="5b414-105">For both encryption and digital signatures, there is a public key certificate and a private key certificate.</span></span> <span data-ttu-id="5b414-106">Pour le chiffrement, l'expéditeur du message utilise le certificat de clé publique du récepteur pour chiffrer le message, tandis que le récepteur du message (BizTalk Server) utilise sa clé privée pour déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="5b414-106">For encryption, the sender of the message uses the receiver's public key certificate to encrypt the message, while the receiver of the message (BizTalk Server) uses its private key to decrypt the message.</span></span> <span data-ttu-id="5b414-107">Pour les signatures numériques, l'expéditeur du message utilise un certificat de clé privée pour signer le message, et le récepteur du message (BizTalk Server) utilise le certificat de clé publique de l'expéditeur pour vérifier la signature.</span><span class="sxs-lookup"><span data-stu-id="5b414-107">For digital signatures, the sender of the message uses a private key certificate to sign the message, and the receiver of the message (BizTalk Server) uses the public key certificate of the sender to verify the signature.</span></span>  
  
 <span data-ttu-id="5b414-108">BizTalk Server utilise les certificats de clé publique pour vérifier les signatures numériques des messages entrants et chiffrer les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="5b414-108">BizTalk Server uses public key certificates to verify the digital signatures of inbound messages and for encrypting outbound messages.</span></span> <span data-ttu-id="5b414-109">BizTalk Server utilise les certificats de clé privée pour déchiffrer les messages entrants et signer les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="5b414-109">BizTalk Server uses private key certificates for decrypting inbound messages and signing outbound messages.</span></span>  
  
 <span data-ttu-id="5b414-110">Les certificats utilisés par BizTalk Server sont configurés dans l'Explorateur BizTalk et la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5b414-110">You configure the certificates BizTalk Server uses in BizTalk Explorer and in the BizTalk Administration Console.</span></span>  
  
 <span data-ttu-id="5b414-111">Pour plus d’informations sur les certificats numériques, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508).</span><span class="sxs-lookup"><span data-stu-id="5b414-111">For more information about digital certificates, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b414-112">Dans le cadre du traitement des messages S/MIME (Secure Multipurpose Internet Mail Extensions), vous pouvez choisir de faire vérifier la liste de révocation des certificats par le moteur BizTalk Server pour vous assurer qu'un certificat n'a pas expiré et qu'il est approuvé par une autorité de certification racine.</span><span class="sxs-lookup"><span data-stu-id="5b414-112">While processing Secure Multipurpose Internet Mail Extensions (S/MIME) messages, you can choose to have the BizTalk Server engine check the Certificate Revocation List (CRL) to ensure that a certificate has not expired and that it is trusted down to a Root Certificate Authority (CA).</span></span> <span data-ttu-id="5b414-113">Cette vérification est effectuée pendant le traitement du message par le pipeline, dans le composant Décodeur MIME/SMIME.</span><span class="sxs-lookup"><span data-stu-id="5b414-113">This verification occurs while the pipeline processes the message, in the MIME/SMIME decoder component.</span></span> <span data-ttu-id="5b414-114">Pour plus d’informations sur la définition **vérifier la liste de révocation** propriété, consultez [comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="5b414-114">For more information about how to set **Check Revocation List** property, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b414-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5b414-115">In This Section</span></span>  
  
-   [<span data-ttu-id="5b414-116">Magasins de certificats par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5b414-116">Certificate Stores that BizTalk Server Uses</span></span>](../core/certificate-stores-that-biztalk-server-uses.md)  
  
-   [<span data-ttu-id="5b414-117">Certificats utilisés par BizTalk Server pour les Messages signés</span><span class="sxs-lookup"><span data-stu-id="5b414-117">Certificates that BizTalk Server Uses for Signed Messages</span></span>](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)  
  
-   [<span data-ttu-id="5b414-118">Certificats utilisés par BizTalk Server pour les Messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="5b414-118">Certificates that BizTalk Server Uses for Encrypted Messages</span></span>](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)