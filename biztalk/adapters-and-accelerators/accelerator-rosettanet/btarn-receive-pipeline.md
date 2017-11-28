---
title: "Pipeline de réception BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, receive pipelines
- RNMimeDecoder component
- ReceiveMessageNonRepudiate component
- RNDAsm component
- receive pipelines, message flow
- RNPartyRes component
- receive pipelines, BTARN
- MessageUpdater component
- messages, message flow
ms.assetid: 811f2a6a-ddd2-49cc-a00b-4c9d0110a0d1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80d7d5951b40b5c76b533e6425ee4d898b41c6cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btarn-receive-pipeline"></a><span data-ttu-id="5be5e-102">BTARN, pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="5be5e-102">BTARN Receive Pipeline</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="5be5e-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] effectue la réception des messages Framework RNIF (RosettaNet Implementation) avec le pipeline RNIFReceive (RNIFReceive.btp).</span><span class="sxs-lookup"><span data-stu-id="5be5e-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] performs RosettaNet Implementation Framework (RNIF) message reception with the RNIFReceive pipeline (RNIFReceive.btp).</span></span> <span data-ttu-id="5be5e-104">Le pipeline de réception inclut les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="5be5e-104">The receive pipeline includes the following components:</span></span>  
  
-   <span data-ttu-id="5be5e-105">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="5be5e-105">ReceiveMessageNonRepudiate</span></span>  
  
-   <span data-ttu-id="5be5e-106">RNMimeDecoder (préprocesseur/décodeur MIME)</span><span class="sxs-lookup"><span data-stu-id="5be5e-106">RNMimeDecoder (MIME Preprocessor/Decoder)</span></span>  
  
-   <span data-ttu-id="5be5e-107">RNDAsm (désassembleur XML)</span><span class="sxs-lookup"><span data-stu-id="5be5e-107">RNDAsm (XML Disassembler)</span></span>  
  
-   <span data-ttu-id="5be5e-108">RNPartyRes (composant Résolution du tiers)</span><span class="sxs-lookup"><span data-stu-id="5be5e-108">RNPartyRes (Party Resolution component)</span></span>  
  
-   <span data-ttu-id="5be5e-109">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="5be5e-109">MessageUpdater</span></span>  
  
## <a name="receivemessagenonrepudiate"></a><span data-ttu-id="5be5e-110">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="5be5e-110">ReceiveMessageNonRepudiate</span></span>  
 <span data-ttu-id="5be5e-111">Ce composant stocke le message reçu dans la table MessageStorageIn.</span><span class="sxs-lookup"><span data-stu-id="5be5e-111">This component stores the received message in the MessageStorageIn table.</span></span> <span data-ttu-id="5be5e-112">Ce composant effectue le traitement de non répudiation requis par les normes RNIF.</span><span class="sxs-lookup"><span data-stu-id="5be5e-112">This component performs the non-repudiation processing required by the RNIF standards.</span></span>  
  
## <a name="rnmimedecoder"></a><span data-ttu-id="5be5e-113">RNMimeDecoder</span><span class="sxs-lookup"><span data-stu-id="5be5e-113">RNMimeDecoder</span></span>  
 <span data-ttu-id="5be5e-114">Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] préprocesseur/décodeur MIME.</span><span class="sxs-lookup"><span data-stu-id="5be5e-114">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] MIME Preprocessor/Decoder.</span></span> <span data-ttu-id="5be5e-115">RNMimeDecoder ajoute les fonctionnalités suivantes pour le traitement RNIF :</span><span class="sxs-lookup"><span data-stu-id="5be5e-115">RNMimeDecoder adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="5be5e-116">Pour RNIF 2.01, déchiffre le contenu de service et les pièces jointes, s’ils sont présents.</span><span class="sxs-lookup"><span data-stu-id="5be5e-116">For RNIF 2.01, decrypts the service content and attachments, if they are present.</span></span>  
  
-   <span data-ttu-id="5be5e-117">Pour RNIF 1.1, gère l’en-tête de 8 octets et l’en-tête de signature détachée à la fin de la charge utile.</span><span class="sxs-lookup"><span data-stu-id="5be5e-117">For RNIF 1.1, handles the 8-byte header and the detached signature header at the end of the payload.</span></span>  
  
 <span data-ttu-id="5be5e-118">Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] préprocesseur/décodeur, consultez « Composant de Pipeline décodeur MIME/SMIME » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="5be5e-118">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] preprocessor/decoder, see "MIME/SMIME Decoder Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="rndasm"></a><span data-ttu-id="5be5e-119">RNDAsm</span><span class="sxs-lookup"><span data-stu-id="5be5e-119">RNDAsm</span></span>  
 <span data-ttu-id="5be5e-120">Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="5be5e-120">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] XML Disassembler.</span></span> <span data-ttu-id="5be5e-121">RNDAsm ajoute les fonctionnalités suivantes pour le traitement RNIF :</span><span class="sxs-lookup"><span data-stu-id="5be5e-121">RNDAsm adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="5be5e-122">Si un document entrant comporte un en-tête de type de document, ce composant génère un espace de noms à partir de celui-ci et déplace tous les nœuds dans le document entrant pour cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5be5e-122">If an incoming document has a DOCTYPE header, this component generates a namespace from it and moves all nodes in the incoming document to that namespace.</span></span>  
  
-   <span data-ttu-id="5be5e-123">Effectue la corrélation de message pour déterminer si un message entrant est un doublon et génère un message d’erreur si le message est un doublon.</span><span class="sxs-lookup"><span data-stu-id="5be5e-123">Performs message correlation to determine whether an incoming message is a duplicate, and generates an error message if the message is a duplicate.</span></span>  
  
-   <span data-ttu-id="5be5e-124">Stocke des pièces jointes en tant que parties supplémentaires du message.</span><span class="sxs-lookup"><span data-stu-id="5be5e-124">Stores attachments as additional parts of the message.</span></span>  
  
-   <span data-ttu-id="5be5e-125">Promeut les propriétés de message.</span><span class="sxs-lookup"><span data-stu-id="5be5e-125">Promotes message properties.</span></span>  
  
 <span data-ttu-id="5be5e-126">Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] désassembleur, consultez « Composant de Pipeline désassembleur XML » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="5be5e-126">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Disassembler, see "XML Disassembler Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="rnpartyres"></a><span data-ttu-id="5be5e-127">RNPartyRes</span><span class="sxs-lookup"><span data-stu-id="5be5e-127">RNPartyRes</span></span>  
 <span data-ttu-id="5be5e-128">Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] composant résolution du tiers.</span><span class="sxs-lookup"><span data-stu-id="5be5e-128">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Party Resolution component.</span></span> <span data-ttu-id="5be5e-129">RNPartyRes ajoute les fonctionnalités suivantes pour le traitement RNIF :</span><span class="sxs-lookup"><span data-stu-id="5be5e-129">RNPartyRes adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="5be5e-130">Mappe le certificat de l’expéditeur si le message entrant est signé à un tiers BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5be5e-130">Maps the sender certificate if the incoming message is signed to a BizTalk party.</span></span> <span data-ttu-id="5be5e-131">Si le message entrant n’est pas signé, et permet l’accord de partenariat commercial, ce composant extrait le tiers expéditeur à partir de l’en-tête de remise pour RNIF 2.01 ou l’en-tête de Service pour RNIF 1.1.</span><span class="sxs-lookup"><span data-stu-id="5be5e-131">If the incoming message is not signed, and the trading partner agreement allows for it, this component retrieves the sender party from the Delivery header for RNIF 2.01 or the Service header for RNIF 1.1.</span></span>  
  
-   <span data-ttu-id="5be5e-132">Valide que l’expéditeur existe et que l’expéditeur a un accord de partenariat commercial avec l’organisation d’origine.</span><span class="sxs-lookup"><span data-stu-id="5be5e-132">Validates that the sender exists and that the sender has a trading partner agreement with the home organization.</span></span>  
  
 <span data-ttu-id="5be5e-133">Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composant résolution de tiers, consultez « Composant de Pipeline résolution de tiers » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="5be5e-133">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] party resolution component, see "Party Resolution Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="messageupdater"></a><span data-ttu-id="5be5e-134">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="5be5e-134">MessageUpdater</span></span>  
 <span data-ttu-id="5be5e-135">Ce composant ajoute les fonctionnalités suivantes pour le traitement RNIF :</span><span class="sxs-lookup"><span data-stu-id="5be5e-135">This component adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="5be5e-136">Met à jour la table MessageStorageIn avec des détails sur le Code PIP PIP Version, tiers Source, tiers de Destination et ID de suivi de Message du message qui a été enregistrée par le receivemessagenonrepudiate, composant câble.</span><span class="sxs-lookup"><span data-stu-id="5be5e-136">Updates the MessageStorageIn table with details about the PIP Code, PIP Version, Source Party, Destination Party, and Message Tracking ID of the wire message that was stored by the ReceiveMessageNonRepudiate component.</span></span>  
  
-   <span data-ttu-id="5be5e-137">Si le PIP ne requiert pas la non répudiation, marque l’enregistrement pour la suppression, le paramètre `ToBePurged = True`.</span><span class="sxs-lookup"><span data-stu-id="5be5e-137">If the PIP does not require non-repudiation, marks the record for deletion, setting `ToBePurged = True`.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="5be5e-138">Flux de messages</span><span class="sxs-lookup"><span data-stu-id="5be5e-138">Message Flow</span></span>  
 <span data-ttu-id="5be5e-139">Le flux de messages via le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] réception pipeline est comme suit :</span><span class="sxs-lookup"><span data-stu-id="5be5e-139">The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline is as follows:</span></span>  
  
1.  <span data-ttu-id="5be5e-140">L’adaptateur HTTP reçoit un objet RNIF 1.1 ou un message d’entreprise RNIF 2.01 via HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="5be5e-140">The HTTP adapter receives an RNIF 1.1 object or an RNIF 2.01 business message through HTTP POST.</span></span>  
  
2.  <span data-ttu-id="5be5e-141">Si l’adaptateur reçoit correctement le message, l’adaptateur extrait le message d’objet ou d’entreprise RosettaNet et l’achemine vers le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="5be5e-141">If the adapter successfully receives the message, the adapter extracts the RosettaNet object or business message, and routes it to the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="5be5e-142">Si le message de l’objet ou business est signé, le préprocesseur/décodeur MIME supprime la signature.</span><span class="sxs-lookup"><span data-stu-id="5be5e-142">If the object or business message is signed, the MIME Preprocessor/Decoder removes the signature.</span></span>  
  
4.  <span data-ttu-id="5be5e-143">Si la signature est valide, le désassembleur lit le préambule.</span><span class="sxs-lookup"><span data-stu-id="5be5e-143">If the signature is valid, the disassembler reads the preamble.</span></span>  
  
5.  <span data-ttu-id="5be5e-144">Si le message est un message d’action, et non répudiation est requise (le **non-répudiation de l’origine et du contenu** paramètre dans les paramètres de configuration de processus est `True`), le décodeur calcule et persiste le résumé.</span><span class="sxs-lookup"><span data-stu-id="5be5e-144">If the message is an action message, and non-repudiation is required (the **Non-Repudiation of Origin and Content** setting in the process configuration settings is `True`), the Decoder calculates and persists the digest.</span></span>  
  
6.  <span data-ttu-id="5be5e-145">Le désassembleur valide le préambule (avec les instructions du message (message) et le schéma de préambule dans les variables globales).</span><span class="sxs-lookup"><span data-stu-id="5be5e-145">The disassembler validates the preamble (with message (MSG) guidelines and the preamble schema in the global variables).</span></span>  
  
7.  <span data-ttu-id="5be5e-146">Pour RNIF 2.01, le désassembleur lit l’en-tête de remise et valide l’en-tête en utilisant les instructions du message et le schéma d’en-tête de remise dans les variables globales.</span><span class="sxs-lookup"><span data-stu-id="5be5e-146">For RNIF 2.01, the disassembler reads the delivery header, and validates the header using the MSG guidelines and the delivery header schema in the global variables.</span></span>  
  
8.  <span data-ttu-id="5be5e-147">Pour RNIF 2.01, le désassembleur extrait les informations du partenaire à partir de l’en-tête de remise et examine la signature pour vérifier qu’il appartient au partenaire.</span><span class="sxs-lookup"><span data-stu-id="5be5e-147">For RNIF 2.01, the disassembler extracts the partner information from the delivery header, and examines the signature to verify that it belongs to the partner.</span></span>  
  
9. <span data-ttu-id="5be5e-148">Pour RNIF 2.01, si la charge utile est chiffrée, le décodeur déchiffre le conteneur de charge utile.</span><span class="sxs-lookup"><span data-stu-id="5be5e-148">For RNIF 2.01, if the payload is encrypted, the decoder decrypts the payload container.</span></span>  
  
10. <span data-ttu-id="5be5e-149">Le désassembleur lit l’en-tête de service et valide l’en-tête en utilisant les instructions du message et le schéma d’en-tête de service dans les variables globales.</span><span class="sxs-lookup"><span data-stu-id="5be5e-149">The disassembler reads the service header, and validates the header using the MSG guidelines and the service header schema in the global variables.</span></span>  
  
11. <span data-ttu-id="5be5e-150">Pour RNIF 1.1, le désassembleur extrait les informations du partenaire à partir de l’en-tête de service et examine la signature pour vérifier qu’il appartient au partenaire.</span><span class="sxs-lookup"><span data-stu-id="5be5e-150">For RNIF 1.1, the disassembler extracts the partner information from the service header, and examines the signature to verify that it belongs to the partner.</span></span>  
  
12. <span data-ttu-id="5be5e-151">Le désassembleur vérifie si le partenaire est autorisé pour le PIP.</span><span class="sxs-lookup"><span data-stu-id="5be5e-151">The disassembler checks whether the partner is authorized for the PIP.</span></span> <span data-ttu-id="5be5e-152">Si ce n’est pas le cas, le désassembleur de répondre à un HTTP POST avec un message d’état HTTP 403, si nécessaire et consigne une erreur.</span><span class="sxs-lookup"><span data-stu-id="5be5e-152">If not, the disassembler will reply an HTTP POST with an HTTP 403 status message, if necessary, and post an error.</span></span>  
  
13. <span data-ttu-id="5be5e-153">Si le message est un message d’action signé et **non-répudiation de l’origine et du contenu** a la valeur `True`, le receivemessagenonrepudiate, composant stocke le message d’origine dans la table MessageStorageIn.</span><span class="sxs-lookup"><span data-stu-id="5be5e-153">If the message is a signed action message and **Non-Repudiation of Origin and Content** is set to `True`, the ReceiveMessageNonRepudiate component persists the original message in the MessageStorageIn table.</span></span>  
  
14. <span data-ttu-id="5be5e-154">Si le message est un message de signal signé et **requis Non répudiation** a la valeur `True`, le receivemessagenonrepudiate, composant stocke le message de signal dans la table MessageStorageIn.</span><span class="sxs-lookup"><span data-stu-id="5be5e-154">If the message is a signed signal message and **Non-Repudiation Required** is set to `True`, the ReceiveMessageNonRepudiate component persists the signal message in the MessageStorageIn table.</span></span>  
  
15. <span data-ttu-id="5be5e-155">Si le message a été conservé dans la table MessageStorageIn de non répudiation, la MessageUpdater met à jour la table MessageStorageIn avec les propriétés de la configuration de processus du message.</span><span class="sxs-lookup"><span data-stu-id="5be5e-155">If the message was persisted in the MessageStorageIn table for non-repudiation, the MessageUpdater updates the MessageStorageIn table with properties of the process configuration of the message.</span></span>  
  
16. <span data-ttu-id="5be5e-156">Si le message est un message d’action qui est un doublon d’un message d’action traités précédemment, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="5be5e-156">If the message is an action message that is a duplicate of a previously processed action message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will post an error.</span></span>  
  
17. <span data-ttu-id="5be5e-157">Pour RNIF 2.01, le décodeur déchiffrera la charge utile si le message d’action est chiffré et il existe une correspondance entre le synchronisme HTTP et les exigences de synchronisme PIP.</span><span class="sxs-lookup"><span data-stu-id="5be5e-157">For RNIF 2.01, the decoder will decrypt the payload if the action message is encrypted and there is a match between the HTTP synchronicity and PIP synchronicity requirements.</span></span>  
  
18. <span data-ttu-id="5be5e-158">Le désassembleur lit le contenu de service et le valide utilisant les instructions du message et le schéma.</span><span class="sxs-lookup"><span data-stu-id="5be5e-158">The disassembler reads the service content, and validates it using the MSG guidelines and the schema.</span></span>  
  
19. <span data-ttu-id="5be5e-159">Le désassembleur RNIF 2.01, vérifie que le manifeste est valide et que l’ID de contenu est présente.</span><span class="sxs-lookup"><span data-stu-id="5be5e-159">For RNIF 2.01, the disassembler verifies that the manifest is valid and the content ID is present.</span></span>  
  
20. <span data-ttu-id="5be5e-160">Pour RNIF 2.01, le désassembleur lit les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="5be5e-160">For RNIF 2.01, the disassembler will read any attachments.</span></span>  
  
21. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="5be5e-161">achemine les en-têtes, le contenu de service et les pièces jointes dans le processus public RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="5be5e-161"> routes the RosettaNet headers, service content, and attachments to the public process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be5e-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be5e-162">See Also</span></span>  
 [<span data-ttu-id="5be5e-163">Traitement des messages dans BTARN</span><span class="sxs-lookup"><span data-stu-id="5be5e-163">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)