---
title: "Erreur de configuration. Le message de signature ne &#39; t correspond à la valeur attendue. | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f067351-b6b0-479d-b2ff-81e9f45b5924
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7aaba3aa00b15b3e015cbc010901c6d50818c42
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuration-error-the-message-signing-doesn39t-match-the-expected-value"></a><span data-ttu-id="67d48-104">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="67d48-104">Configuration error.</span></span> <span data-ttu-id="67d48-105">Le message de signature ne &#39; t correspond à la valeur attendue.</span><span class="sxs-lookup"><span data-stu-id="67d48-105">The message signing doesn&#39;t match the expected value.</span></span>
## <a name="details"></a><span data-ttu-id="67d48-106">Détails</span><span class="sxs-lookup"><span data-stu-id="67d48-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67d48-107">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="67d48-107">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="67d48-108">Version du produit</span><span class="sxs-lookup"><span data-stu-id="67d48-108">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="67d48-109">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="67d48-109">Event ID</span></span>|-|  
|<span data-ttu-id="67d48-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="67d48-110">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="67d48-111"> EDI</span><span class="sxs-lookup"><span data-stu-id="67d48-111"> EDI</span></span>|  
|<span data-ttu-id="67d48-112">Composant</span><span class="sxs-lookup"><span data-stu-id="67d48-112">Component</span></span>|<span data-ttu-id="67d48-113">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="67d48-113">AS2 Engine</span></span>|  
|<span data-ttu-id="67d48-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="67d48-114">Symbolic Name</span></span>|<span data-ttu-id="67d48-115">AS2DecoderPartySigningConfigurationError</span><span class="sxs-lookup"><span data-stu-id="67d48-115">AS2DecoderPartySigningConfigurationError</span></span>|  
|<span data-ttu-id="67d48-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="67d48-116">Message Text</span></span>|<span data-ttu-id="67d48-117">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="67d48-117">Configuration error.</span></span> <span data-ttu-id="67d48-118">La signature du message ne correspond pas à la valeur attendue.</span><span class="sxs-lookup"><span data-stu-id="67d48-118">The message signing doesn't match the expected value.</span></span> <span data-ttu-id="67d48-119">Contactez le partenaire émetteur et vérifiez l'utilisation de la signature.</span><span class="sxs-lookup"><span data-stu-id="67d48-119">Contact the sending partner and verify signature use.</span></span> <span data-ttu-id="67d48-120">AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »</span><span class="sxs-lookup"><span data-stu-id="67d48-120">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="67d48-121">Explication</span><span class="sxs-lookup"><span data-stu-id="67d48-121">Explanation</span></span>  
 <span data-ttu-id="67d48-122">Cet événement de type erreur/avertissement/information indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu traiter le message AS2, car la signature est définie dans les paramètres du tiers, mais le message AS2 n'est pas signé, ou car la signature est spécifiée de façon à ne pas être activée, mais le message est signé.</span><span class="sxs-lookup"><span data-stu-id="67d48-122">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because signing is specified in the party settings, but the AS2 message is not signed, or signing is specified not to be enabled, but the message is signed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67d48-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="67d48-123">User Action</span></span>  
 <span data-ttu-id="67d48-124">Pour résoudre cette erreur, vérifiez que le message AS2 entrant est signé si la signature est spécifiée dans les paramètres du tiers, ou qu'il n'est pas signé si la signature est définie comme n'étant pas activée dans ces mêmes paramètres.</span><span class="sxs-lookup"><span data-stu-id="67d48-124">To resolve this error, verify that the incoming AS2 message is signed if signing is specified in the party settings or that the incoming AS2 message is not signed if signing is specified as not enabled in the party settings.</span></span> <span data-ttu-id="67d48-125">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="67d48-125">Do one of the following:</span></span>  
  
1.  <span data-ttu-id="67d48-126">Si le **remplacer les propriétés du message entrant** propriété est sélectionnée dans la partie en tant que page de l’expéditeur du Message AS2 de la boîte de dialogue propriétés AS2 dans la Console Administration de BizTalk Server, le **Message doit être signé** propriété est sélectionnée, mais le message n’est pas signé, contactez le tiers qui a envoyé le message et demandez-lui de signer le message et le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="67d48-126">If the **Override inbound message properties** property is selected in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be signed** property is selected, but the message is not signed, contact the party that sent the message and ask them to sign the message, and resend it.</span></span> <span data-ttu-id="67d48-127">Vous pouvez désactiver le **Message doit être signé** propriété, ou le **remplacer les propriétés du message entrant** propriété.</span><span class="sxs-lookup"><span data-stu-id="67d48-127">Or you can clear the **Message should be signed** property, or the **Override inbound message properties** property.</span></span>  
  
2.  <span data-ttu-id="67d48-128">Si le **remplacer les propriétés du message entrant** propriété est sélectionnée, le **Message doit être signé** propriété est désactivée, mais le message est signé, contactez le tiers qui a envoyé le message et demandez-lui de ne pas signer le message et le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="67d48-128">If the **Override inbound message properties** property is selected, the **Message should be signed** property is cleared, but the message is signed, contact the party that sent the message and ask them not to sign the message, and resend it.</span></span> <span data-ttu-id="67d48-129">Vous pouvez également sélectionner le **Message doit être signé** propriété.</span><span class="sxs-lookup"><span data-stu-id="67d48-129">Or you can select the **Message should be signed** property.</span></span>