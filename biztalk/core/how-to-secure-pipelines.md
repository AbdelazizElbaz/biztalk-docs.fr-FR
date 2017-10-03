---
title: "Sécurisation des Pipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3a717f-acf8-4f08-a6fb-6d1d48b5b80a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 903e9faec81ce58aac243fb7a22bac6678a81a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-secure-pipelines"></a><span data-ttu-id="c7d6c-102">Sécurisation des pipelines</span><span class="sxs-lookup"><span data-stu-id="c7d6c-102">How to Secure Pipelines</span></span>

## <a name="authentication-trusted"></a><span data-ttu-id="c7d6c-103">Approuvé par authentification</span><span class="sxs-lookup"><span data-stu-id="c7d6c-103">Authentication trusted</span></span>
<span data-ttu-id="c7d6c-104">Ordinateurs hôtes peuvent être marquées dans la console d’administration en tant que **approuvé par authentification**.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-104">Hosts can be marked in the administration console as **Authentication Trusted**.</span></span> <span data-ttu-id="c7d6c-105">Lorsqu'un hôte est approuvé par authentification, le serveur Microsoft BizTalk Server approuve les propriétés liées à la sécurité envoyées dans le contexte d'un message à partir de cet hôte.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-105">Denoting a host as Authentication Trusted means that the Microsoft BizTalk Server will trust the security-related properties sent on the message context of a message from that host.</span></span> <span data-ttu-id="c7d6c-106">Les propriétés relatives à la sécurité dans le contexte du message sont les **OriginatorPID**, qui correspond à la propriété de contexte de message BizTalk Server. SourcePartyID et le **OriginatorSID**, qui correspond à la propriété de contexte de message **BTS. WindowsUser**.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-106">The security-related properties on the message context are the **OriginatorPID**, which corresponds to the message context property BTS.SourcePartyID, and the **OriginatorSID**, which corresponds to the message context property **BTS.WindowsUser**.</span></span> <span data-ttu-id="c7d6c-107">Pour plus d’informations, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="c7d6c-107">For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="c7d6c-108">Un ordinateur hôte qui est marqué comme étant **approuvé par authentification** est autorisée pour indiquer que l’hôte approuvé ajoute un message à la file d’attente d’une personne autre que lui-même en tant que l’expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-108">A host that is marked as **Authentication Trusted** is allowed to indicate that the trusted host is adding a message to the queue from someone other than itself as the sender of the message.</span></span> <span data-ttu-id="c7d6c-109">En d’autres termes, les hôtes qui ne sont pas marqués en tant que **approuvé par authentification** ne sont pas autorisés pour ajouter un message à la file d’attente d’un expéditeur de message autres qu’eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-109">In other words, hosts that are not marked as **Authentication Trusted** are not allowed to add a message to the queue from a message sender other than themselves.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7d6c-110">Le composant de pipeline Décodeur MIME/SMIME ne vérifie pas la date d'expiration des certificats de déchiffrement.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-110">The MIME/SMIME Decoder pipeline component does not check the expiration date of decryption certificates.</span></span> <span data-ttu-id="c7d6c-111">Toutefois, il vérifie celle des certificats de signature.</span><span class="sxs-lookup"><span data-stu-id="c7d6c-111">However, it does check the expiration date of signing certificates.</span></span>  
  
 <span data-ttu-id="c7d6c-112">Pour plus d’informations sur le codage et décodage des messages envoyés via SMTP ou HTTP, consultez [composant de Pipeline encodeur MIME-SMIME](../core/mime-smime-encoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="c7d6c-112">For information about encoding and decoding messages sent over SMTP or HTTP, see [MIME-SMIME Encoder Pipeline Component](../core/mime-smime-encoder-pipeline-component.md).</span></span> <span data-ttu-id="c7d6c-113">Consultez également [composant de Pipeline décodeur MIME-SMIME](../core/mime-smime-decoder-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="c7d6c-113">Also see [MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md).</span></span>  
  
 <span data-ttu-id="c7d6c-114">Pour plus d’informations sur la vérification de signature lors de la communication avec des tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="c7d6c-114">For information about signature verification when dealing with third parties, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span> <span data-ttu-id="c7d6c-115">Consultez également [la création d’un accord](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span><span class="sxs-lookup"><span data-stu-id="c7d6c-115">Also see [How to Create an Agreement](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d6c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7d6c-116">See Also</span></span>  
 <span data-ttu-id="c7d6c-117">[Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c7d6c-117">[Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="c7d6c-118">Développement de composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="c7d6c-118">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)