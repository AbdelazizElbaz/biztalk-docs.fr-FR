---
title: "Erreur de configuration. Le n chiffrement de message &#39; t correspond à la valeur attendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4920a4c26cb60c3215f58297445dc49551b1befe
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuration-error-the-message-encryption-doesn39t-match-the-expected-value"></a><span data-ttu-id="3c167-103">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="3c167-103">Configuration error.</span></span> <span data-ttu-id="3c167-104">Le n chiffrement de message &#39; t correspond à la valeur attendue</span><span class="sxs-lookup"><span data-stu-id="3c167-104">The message encryption doesn&#39;t match the expected value</span></span>
## <a name="details"></a><span data-ttu-id="3c167-105">Détails</span><span class="sxs-lookup"><span data-stu-id="3c167-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c167-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3c167-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3c167-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3c167-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3c167-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3c167-108">Event ID</span></span>|-|  
|<span data-ttu-id="3c167-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3c167-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c167-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="3c167-110"> EDI</span></span>|  
|<span data-ttu-id="3c167-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3c167-111">Component</span></span>|<span data-ttu-id="3c167-112">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="3c167-112">AS2 Engine</span></span>|  
|<span data-ttu-id="3c167-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3c167-113">Symbolic Name</span></span>|<span data-ttu-id="3c167-114">AS2DecoderPartyEncryptionConfigurationError</span><span class="sxs-lookup"><span data-stu-id="3c167-114">AS2DecoderPartyEncryptionConfigurationError</span></span>|  
|<span data-ttu-id="3c167-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3c167-115">Message Text</span></span>|<span data-ttu-id="3c167-116">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="3c167-116">Configuration error.</span></span> <span data-ttu-id="3c167-117">Le chiffrement du message ne correspondait pas à la valeur attendue.</span><span class="sxs-lookup"><span data-stu-id="3c167-117">The message encryption doesn't match the expected value.</span></span> <span data-ttu-id="3c167-118">Contactez le partenaire émetteur et vérifiez l'utilisation du chiffrement.</span><span class="sxs-lookup"><span data-stu-id="3c167-118">Contact the sending partner and verify encryption use.</span></span> <span data-ttu-id="3c167-119">AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »</span><span class="sxs-lookup"><span data-stu-id="3c167-119">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c167-120">Explication</span><span class="sxs-lookup"><span data-stu-id="3c167-120">Explanation</span></span>  
 <span data-ttu-id="3c167-121">Cet événement d'erreur/d'avertissement/d'informations indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu traiter le message AS2 car le chiffrement est spécifié dans les paramètres de tiers, mais le message AS2 n'est pas chiffré ou il l'est bien que le chiffrement ne soit pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="3c167-121">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because encryption is specified in the party settings, but the AS2 message is not encrypted, or encryption is specified not to be enabled, but the message is encrypted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c167-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3c167-122">User Action</span></span>  
 <span data-ttu-id="3c167-123">Pour résoudre cette erreur, vérifiez que le message AS2 entrant est chiffré si le chiffrement est spécifié dans les paramètres de tiers ou qu'il ne l'est pas dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="3c167-123">To resolve this error, verify that the incoming AS2 message is encrypted if encryption is specified in the party settings or that the incoming AS2 message is not encrypted if encryption is specified as not enabled in the party settings.</span></span> <span data-ttu-id="3c167-124">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c167-124">Do one of the following:</span></span>  
  
1.  <span data-ttu-id="3c167-125">Si le **remplacement de propriété des propriétés de message entrant est sélectionnée** dans la page tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue propriétés AS2 dans la Console Administration de BizTalk Server, le **Message doit être chiffré.**  propriété est sélectionnée, mais le message n’est pas chiffré, contactez le tiers qui a envoyé le message et demandez-lui de chiffrer le message et le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="3c167-125">If the **Override inbound message properties property is selected** in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be encrypted** property is selected, but the message is not encrypted, contact the party that sent the message and ask them to encrypt the message, and resend it.</span></span> <span data-ttu-id="3c167-126">Ou vous pouvez effacer le **Message doit être chiffré** propriété, ou la **remplacer les propriétés du message entrant** propriété.</span><span class="sxs-lookup"><span data-stu-id="3c167-126">Or you can clear the **Message should be encrypted** property, or the **Override inbound message properties** property.</span></span>  
  
2.  <span data-ttu-id="3c167-127">Si le **remplacer les propriétés du message entrant** propriété est sélectionnée, le **Message doit être chiffré** propriété est désactivée, mais le message est chiffré, contactez le tiers qui a envoyé le message et demandez-lui de ne pas chiffrer le message et le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="3c167-127">If the **Override inbound message properties** property is selected, the **Message should be encrypted** property is cleared, but the message is encrypted, contact the party that sent the message and ask them not to encrypt the message, and resend it.</span></span> <span data-ttu-id="3c167-128">Vous pouvez également sélectionner le **Message doit être chiffré** propriété.</span><span class="sxs-lookup"><span data-stu-id="3c167-128">Or you can select the **Message should be encrypted** property.</span></span>