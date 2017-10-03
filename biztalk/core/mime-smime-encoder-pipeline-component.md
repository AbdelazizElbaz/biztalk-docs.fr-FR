---
title: Composant de Pipeline encodeur MIME-SMIME | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Encoder
- MIME/SMIME Encoder [pipeline component]
- BTS.EncryptionCert property
ms.assetid: 397505e6-47d0-4b63-9197-814ee4388369
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c6a79052d3294420c46bff2a1ce3c0ed869e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-encoder-pipeline-component"></a><span data-ttu-id="1a3d8-102">Composant de Pipeline encodeur MIME-SMIME</span><span class="sxs-lookup"><span data-stu-id="1a3d8-102">MIME-SMIME Encoder Pipeline Component</span></span>
<span data-ttu-id="1a3d8-103">Le composant de pipeline Encodeur MIME/SMIME peut être placé dans la phase de codage d'un pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-103">The MIME/SMIME Encoder component can be placed into the Encode stage of a send pipeline.</span></span> <span data-ttu-id="1a3d8-104">Il prend en charge les codages 7 bits, 8 bits, binaire, quoted-printable, base64 et UUencode.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-104">It supports 7bit, 8bit, binary, quoted-printable, base64, and UUencode encoding.</span></span> <span data-ttu-id="1a3d8-105">Les modifications des jeux de caractères de données localisées n'affectent pas le codage.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-105">Localized data character set changes do not affect the encoding.</span></span>  
  
 <span data-ttu-id="1a3d8-106">Ce composant peut être utilisé pour coder en MIME, pour signer ou chiffrer un message sortant avec des certificats de chiffrement et de signature.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-106">This component can be used to either MIME encode, sign or encrypt an outgoing message with encryption and signing certificates.</span></span>  
  
 <span data-ttu-id="1a3d8-107">S’il existe un composant de codage dans le pipeline d'envoi configuré pour signer des messages et que le groupe BizTalk comprenant l’hôte exécutant le pipeline n’est pas configuré avec un certificat de signature, le message sortant sera interrompu (avec l’erreur correspondante) et placé dans la file d’attente des messages interrompus de l'hôte exécutant le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-107">If there is an encoding component in the send pipeline that is configured to sign messages, and the BizTalk group that includes the host running the pipeline is not configured with a signing certificate, the outgoing message will be suspended (with the appropriate error) to the suspended queue of the host that is running the pipeline.</span></span> <span data-ttu-id="1a3d8-108">Si le certificat de signature ne peut pas être trouvé dans le magasin de certificats personnels de l'utilisateur sous lequel le service s'exécute, le message sera interrompu et placé dans la file d'attente des messages interrompus de l'hôte exécutant le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-108">If the signing certificate cannot be found in the personal certificate store of the current user under which the service is running, the message will be suspended to the suspended queue of the host that is running the pipeline.</span></span>  
  
 <span data-ttu-id="1a3d8-109">S’il existe un composant de codage dans le pipeline de sortie configuré pour chiffrer les messages sortants, et que le certificat est introuvable dans le magasin de certificats, le message sera interrompu et placé dans la file d’attente des messages interrompus de l’hôte exécutant le pipeline.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-109">If there is an encoding component in the outbound pipeline configured to encrypt outbound messages, and the certificate cannot be found in the certificate store, the message will be suspended to the suspended queue of the host that is running the pipeline.</span></span>  
  
 <span data-ttu-id="1a3d8-110">Pour chiffrer une réponse sur un port de requête-réponse recevant des messages signés et chiffrés, un composant de pipeline personnalisé doit être ajouté au pipeline avant le composant de pipeline Encodeur MIME/SMIME.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-110">To perform response encryption on a request-response port that is receiving signed and encrypted messages, a custom pipeline component must be added to the pipeline before the MIME/SMIME Encoder pipeline component.</span></span> <span data-ttu-id="1a3d8-111">Ce composant de pipeline personnalisé doit identifier l’empreinte correspondant au certificat de chiffrement et affectez-lui le **BTS. EncryptionCert** propriété dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="1a3d8-111">This custom pipeline component must identify the thumbprint corresponding to the encryption certificate and set it to the **BTS.EncryptionCert** property on the message context.</span></span> <span data-ttu-id="1a3d8-112">Pour plus d’informations sur les propriétés de contexte de message, consultez [comment modifier les propriétés de groupe](../core/how-to-modify-group-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1a3d8-112">For more information about message context properties, see [How to Modify Group Properties](../core/how-to-modify-group-properties.md).</span></span>  
  
 <span data-ttu-id="1a3d8-113">Pour plus d’informations sur la configuration du composant de pipeline Encodeur MIME/SMIME, consultez [comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="1a3d8-113">For information about configuring the MIME/SMIME Encoder pipeline component, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span> <span data-ttu-id="1a3d8-114">Pour plus d’informations sur la prise en charge de BizTalk Server pour le chiffrement, la signature et l’utilisation de certificats, consultez [sécurité pour l’envoi et réception de Messages](../core/security-for-sending-and-receiving-messages.md).</span><span class="sxs-lookup"><span data-stu-id="1a3d8-114">For more information about BizTalk Server support for encryption, signing, and usage of certificates, see [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3d8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a3d8-115">See Also</span></span>  
 <span data-ttu-id="1a3d8-116">[Composants de pipeline](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="1a3d8-116">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 <span data-ttu-id="1a3d8-117">[Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1a3d8-117">[MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="1a3d8-118">MIME (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="1a3d8-118">MIME (BizTalk Server Sample)</span></span>](../core/mime-biztalk-server-sample.md)