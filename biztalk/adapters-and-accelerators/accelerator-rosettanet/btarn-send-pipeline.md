---
title: "Pipeline d’envoi BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler
- send pipelines, message flow
- DOCTYPE headers
- MIME/SMIME Encoder
- send pipelines, BTARN
- BTARN, send pipelines
- XML Preprocessor
- messages, message flow
ms.assetid: 88562132-0ea4-4b5a-9445-b69f6c84e5ea
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bd102c58f85fd38c2f769f6e4aca2b5fd0d7919
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btarn-send-pipeline"></a><span data-ttu-id="d5a8d-102">Pipeline d’envoi BTARN</span><span class="sxs-lookup"><span data-stu-id="d5a8d-102">BTARN Send Pipeline</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="d5a8d-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prépare un message Framework RNIF (RosettaNet Implementation) pour la transmission du pipeline RNIFSend (RNIFSend.btp).</span><span class="sxs-lookup"><span data-stu-id="d5a8d-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prepares a RosettaNet Implementation Framework (RNIF) message for transmission in the RNIFSend pipeline (RNIFSend.btp).</span></span> <span data-ttu-id="d5a8d-104">Le pipeline d’envoi inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-104">The send pipeline includes the following:</span></span>  
  
-   <span data-ttu-id="d5a8d-105">XML de préprocesseur</span><span class="sxs-lookup"><span data-stu-id="d5a8d-105">XML preprocessor</span></span>  
  
-   <span data-ttu-id="d5a8d-106">Assembleur XML</span><span class="sxs-lookup"><span data-stu-id="d5a8d-106">XML assembler</span></span>  
  
-   <span data-ttu-id="d5a8d-107">Encodeur de Multipurpose Internet Mail Extensions/Secure Multipurpose Internet Mail Extensions (MIME/SMIME)</span><span class="sxs-lookup"><span data-stu-id="d5a8d-107">Multipurpose Internet Mail Extensions/Secure Multipurpose Internet Mail Extensions (MIME/SMIME) encoder</span></span>  
  
## <a name="xml-preprocessor"></a><span data-ttu-id="d5a8d-108">Préprocesseur XML</span><span class="sxs-lookup"><span data-stu-id="d5a8d-108">XML Preprocessor</span></span>  
 <span data-ttu-id="d5a8d-109">Le préprocesseur XML ajoute un en-tête de type de document au message.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-109">The XML preprocessor adds a DOCTYPE header to the message.</span></span> <span data-ttu-id="d5a8d-110">L’en-tête identifie le schéma DTD (définition) de type de document associé au message.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-110">The header identifies the document type definition (DTD) schema associated with the message.</span></span> <span data-ttu-id="d5a8d-111">La spécification RNIF nécessite la présence d’un en-tête de type de document pour la transmission de RNIF.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-111">The RNIF specification requires the presence of a DOCTYPE header for RNIF transmission.</span></span>  
  
## <a name="xml-assembler"></a><span data-ttu-id="d5a8d-112">Assembleur XML</span><span class="sxs-lookup"><span data-stu-id="d5a8d-112">XML Assembler</span></span>  
 <span data-ttu-id="d5a8d-113">L’assembleur XML est basé sur le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] assembleur XML.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-113">The XML assembler is based on the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] XML assembler.</span></span> <span data-ttu-id="d5a8d-114">Il transfère les propriétés à partir du contexte de message dans les documents et les enveloppes.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-114">It transfers properties from the message context back into envelopes and documents.</span></span> <span data-ttu-id="d5a8d-115">Il assemble le message à partir de ses parties XML et les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-115">It assembles the message from its XML parts and attachments.</span></span> <span data-ttu-id="d5a8d-116">Il n’effectue pas de validation de message.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-116">It does not perform message validation.</span></span>  
  
 <span data-ttu-id="d5a8d-117">Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembleur XML, consultez « Composant de Pipeline assembleur XML » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-117">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] XML assembler, see "XML Assembler Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="mimesmime-encoder"></a><span data-ttu-id="d5a8d-118">Encodeur MIME/SMIME</span><span class="sxs-lookup"><span data-stu-id="d5a8d-118">MIME/SMIME Encoder</span></span>  
 <span data-ttu-id="d5a8d-119">L’encodeur MIME/SMIME est basé sur le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] encodeur MIME/SMIME.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-119">The MIME/SMIME encoder is based on the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] MIME/SMIME Encoder.</span></span> <span data-ttu-id="d5a8d-120">Selon les paramètres de protocole dans l’accord de partenariat commercial et les paramètres de la [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] encodeur MIME/SMIME, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encodeur exécute les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-120">Depending on the protocol settings in the trading partner agreement, and the settings of the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] MIME/SMIME Encoder, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encoder performs the following:</span></span>  
  
-   <span data-ttu-id="d5a8d-121">Ajoute un en-tête binaire de 8 octets pour le message, tel que requis pour les messages RNIF 1.1.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-121">Adds an 8-byte binary header to the message, as required for RNIF 1.1 messages.</span></span>  
  
-   <span data-ttu-id="d5a8d-122">Encode les parties de message et calcule le condensat.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-122">Encodes the message parts, and calculates the digest.</span></span>  
  
-   <span data-ttu-id="d5a8d-123">Chiffre la charge utile (contenu du service et les pièces jointes), ou le conteneur de charge utile (contenu du service plus en-tête service ainsi que les pièces jointes).</span><span class="sxs-lookup"><span data-stu-id="d5a8d-123">Encrypts the payload (service content plus attachments), or the payload container (service content plus service header plus attachments).</span></span> <span data-ttu-id="d5a8d-124">Si vous avez défini le **Encoder tous les ports** définition sur le **protocole** onglet de l’accord de partenariat commercial à `False`, l’encodeur chiffre uniquement la charge utile.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-124">If you have set the **Encode all ports** setting on the **Protocol** tab of the trading partner agreement to `False`, the encoder will encrypt only the payload.</span></span> <span data-ttu-id="d5a8d-125">Si vous avez défini le **Encoder tous les ports** à `True`, l’encodeur chiffrera le conteneur de charge utile.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-125">If you have set the **Encode all ports** setting to `True`, the encoder will encrypt the payload container.</span></span>  
  
 <span data-ttu-id="d5a8d-126">Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] encodeur MIME/SMIME, voir « Composant de Pipeline encodeur MIME/SMIME » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-126">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] MIME/SMIME Encoder, see "MIME/SMIME Encoder Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="d5a8d-127">Flux de messages</span><span class="sxs-lookup"><span data-stu-id="d5a8d-127">Message Flow</span></span>  
 <span data-ttu-id="d5a8d-128">Le flux de messages via le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoyer le pipeline est comme suit :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-128">The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline is as follows:</span></span>  
  
1.  <span data-ttu-id="d5a8d-129">Si vous avez défini le **encoder toutes les parties** définition de l’accord de partenariat commercial à `True`, l’encodeur MIME/SMIME codera toutes les parties de message.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-129">If you have set the **Encode all parts** setting of the trading partner agreement to `True`, the MIME/SMIME encoder will encode all message parts.</span></span> <span data-ttu-id="d5a8d-130">Il utilise la méthode de codage définie dans le `Encoding` propriété de l’accord.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-130">It will use the encoding method set in the `Encoding` property of the agreement.</span></span>  
  
2.  <span data-ttu-id="d5a8d-131">Pour RNIF 2.01, si le message est un message d’action et il existe une pièce jointe, l’encodeur procède comme suit pour chaque pièce jointe :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-131">For RNIF 2.01, if the message is an action message and there is an attachment, the encoder will do the following for each attachment:</span></span>  
  
    1.  <span data-ttu-id="d5a8d-132">Si la pièce jointe est binaire, l’encodeur Encoder.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-132">If the attachment is binary, the encoder will encode it.</span></span>  
  
    2.  <span data-ttu-id="d5a8d-133">L’encodeur génère un ID de contenu de la pièce jointe.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-133">The encoder will generate a content ID for the attachment.</span></span>  
  
    3.  <span data-ttu-id="d5a8d-134">L’encodeur créera une partie MIME de la pièce jointe.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-134">The encoder will create a MIME part for the attachment.</span></span>  
  
3.  <span data-ttu-id="d5a8d-135">Pour RNIF 2.01, le pipeline chiffre des parties de message et générer le message RNIF selon le paramètre de **est persistant requis de la confidentialité** (tel que défini dans les paramètres de configuration de processus) :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-135">For RNIF 2.01, the pipeline will encrypt message parts and build the RNIF message depending on the setting of **Is Persistent Confidentiality Required** (as set in the process configuration settings):</span></span>  
  
    1.  <span data-ttu-id="d5a8d-136">Si vous avez défini **est persistant requis de la confidentialité** à **charge utile**, l’encodeur chiffre le contenu du service et les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-136">If you have set **Is Persistent Confidentiality Required** to **Payload**, the encoder will encrypt the service content and the attachments.</span></span> <span data-ttu-id="d5a8d-137">L’assembleur ajoute ensuite l’en-tête de service, l’en-tête de remise et préambule pour construire le message RNIF final.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-137">The assembler will then add the service header, delivery header, and preamble to construct the final RNIF message.</span></span>  
  
    2.  <span data-ttu-id="d5a8d-138">Si vous avez défini **est persistant requis de la confidentialité** à **conteneur de charge utile**, l’encodeur chiffrera l’en-tête de service, le contenu de service et les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-138">If you have set **Is Persistent Confidentiality Required** to **Payload Container**, the encoder will encrypt the service header, service content, and the attachments.</span></span> <span data-ttu-id="d5a8d-139">L’assembleur ajoute ensuite l’en-tête de remise et le préambule pour construire le message RNIF final.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-139">The assembler will then add the delivery header and preamble to construct the final RNIF message.</span></span>  
  
    3.  <span data-ttu-id="d5a8d-140">Si vous avez défini **est persistant requis de la confidentialité** à **aucun**, l’assembleur pour le contenu de service et les pièces jointes (sans ajouterez l’en-tête de service, l’en-tête de remise et préambule chiffrement) pour construire le message RNIF final.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-140">If you have set **Is Persistent Confidentiality Required** to **None**, the assembler will add the service header, delivery header, and preamble to the service content and the attachments (without encryption) to construct the final RNIF message.</span></span>  
  
4.  <span data-ttu-id="d5a8d-141">Pour RNIF 1.1, l’assembleur construira du dernier message RNIF sans chiffrement.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-141">For RNIF 1.1, the assembler will construct the final RNIF message without encryption.</span></span>  
  
5.  <span data-ttu-id="d5a8d-142">L’encodeur signe le message dans le cas suivant :</span><span class="sxs-lookup"><span data-stu-id="d5a8d-142">The encoder will sign the message in the following case:</span></span>  
  
    1.  <span data-ttu-id="d5a8d-143">Le message est un message de signal et le **requis Non répudiation** propriété (dans les paramètres de configuration de processus) est `True`.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-143">The message is a signal message, and the **Non-Repudiation Required** property (in the process configuration settings) is `True`.</span></span>  
  
    2.  <span data-ttu-id="d5a8d-144">Le message est un message d’action et le **non-répudiation de l’origine et du contenu** propriété (dans les paramètres de configuration de processus) est `True`.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-144">The message is an action message, and the **Non-Repudiation of Origin and Content** property (in the process configuration settings) is `True`.</span></span>  
  
6.  <span data-ttu-id="d5a8d-145">Pour RNIF 2.01, l’encodeur de calculer le digest sur la première partie du corps du message MIME et conserver le résumé.</span><span class="sxs-lookup"><span data-stu-id="d5a8d-145">For RNIF 2.01, the encoder will calculate the digest on the first body part of the MIME message, and persist the digest.</span></span> <span data-ttu-id="d5a8d-146">Elle calcule le digest à l’aide de la méthode définie dans le `Digest` propriété de méthode dans l’accord de partenariat commercial (SHA-1 ou MD5).</span><span class="sxs-lookup"><span data-stu-id="d5a8d-146">It will calculate the digest using the method set in the `Digest` method property in the trading partner agreement (SHA-1 or MD5).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a8d-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5a8d-147">See Also</span></span>  
 [<span data-ttu-id="d5a8d-148">Traitement des messages dans BTARN</span><span class="sxs-lookup"><span data-stu-id="d5a8d-148">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)