---
title: "Erreur de configuration. Le n de signature de message &#39; t correspond à la signature configurée pour ce tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cea0016-12e8-4ee8-ac44-11024b5e74ef
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23214832300fe6125318ce67083f6bee0a364158
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-the-message-signature-doesn39t-match-the-signature-configured-for-this-party"></a><span data-ttu-id="7a400-103">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="7a400-103">Configuration error.</span></span> <span data-ttu-id="7a400-104">Le n de signature de message &#39; t correspond à la signature configurée pour ce tiers</span><span class="sxs-lookup"><span data-stu-id="7a400-104">The message signature doesn&#39;t match the signature configured for this party</span></span>
## <a name="details"></a><span data-ttu-id="7a400-105">Détails</span><span class="sxs-lookup"><span data-stu-id="7a400-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7a400-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7a400-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7a400-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7a400-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7a400-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7a400-108">Event ID</span></span>|-|  
|<span data-ttu-id="7a400-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7a400-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7a400-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="7a400-110"> EDI</span></span>|  
|<span data-ttu-id="7a400-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7a400-111">Component</span></span>|<span data-ttu-id="7a400-112">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="7a400-112">AS2 Engine</span></span>|  
|<span data-ttu-id="7a400-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7a400-113">Symbolic Name</span></span>|-|  
|<span data-ttu-id="7a400-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7a400-114">Message Text</span></span>|<span data-ttu-id="7a400-115">Erreur de configuration.</span><span class="sxs-lookup"><span data-stu-id="7a400-115">Configuration error.</span></span> <span data-ttu-id="7a400-116">La signature du message ne correspond pas à la signature configurée pour ce tiers.</span><span class="sxs-lookup"><span data-stu-id="7a400-116">The message signature doesn't match the signature configured for this party.</span></span> <span data-ttu-id="7a400-117">Contactez le partenaire émetteur et vérifiez le certificat utilisé.</span><span class="sxs-lookup"><span data-stu-id="7a400-117">Contact the sending partner and verify the certificate used.</span></span> <span data-ttu-id="7a400-118">AS2-à partir de : « {0} » AS2-à : « \ {1\\} » MessageID : « \ {2\} »</span><span class="sxs-lookup"><span data-stu-id="7a400-118">AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7a400-119">Explication</span><span class="sxs-lookup"><span data-stu-id="7a400-119">Explanation</span></span>  
 <span data-ttu-id="7a400-120">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 n'a pas pu vérifier la signature lors de l'exécution du traitement MIME.</span><span class="sxs-lookup"><span data-stu-id="7a400-120">This Error/Warning/Information event indicates that the AS2 receive pipeline could not verify the signature when performing MIME processing.</span></span> <span data-ttu-id="7a400-121">Cela peut être dû à l'utilisation, lors du traitement du message reçu, d'un certificat différent de celui que l'expéditeur a utilisé pour signer le message.</span><span class="sxs-lookup"><span data-stu-id="7a400-121">This could result from using a different certificate to process the received message than the sender used to sign the message.</span></span> <span data-ttu-id="7a400-122">Cette situation peut se produire lorsque BizTalk Server utilise les paramètres d'un tiers erroné pour vérifier la signature d'un message AS2 entrant.</span><span class="sxs-lookup"><span data-stu-id="7a400-122">This can occur if BizTalk Server uses the settings of the wrong party to verify the signature of the incoming AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7a400-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7a400-123">User Action</span></span>  
 <span data-ttu-id="7a400-124">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="7a400-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="7a400-125">Assurez-vous que le tiers approprié est déterminé par le processus de résolution de tiers pour le message AS2 entrant.</span><span class="sxs-lookup"><span data-stu-id="7a400-125">Ensure that the correct party is determined by the party resolution process for the incoming AS2 message.</span></span> <span data-ttu-id="7a400-126">Pour ce faire, vérifiez que le tiers approprié est résolu lorsque BizTalk Server tente de trouver une correspondance entre l'en-tête AS2-From du message entrant et la valeur de EDIINT-AS2 From dans la liste des alias de la page Général de la boîte de dialogue Propriétés du tiers.</span><span class="sxs-lookup"><span data-stu-id="7a400-126">Do so by verifying that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From header in the incoming message and the value for EDIINT-AS2 From in the Aliases list in the General page of the Party Properties dialog box.</span></span> <span data-ttu-id="7a400-127">Si cette opération ne résout pas le tiers, vérifiez que le tiers adéquat est résolu lorsque BizTalk Server tente de trouver une correspondance entre la propriété de contexte AS2-From définie pour le message entrant et le nom d'un tiers.</span><span class="sxs-lookup"><span data-stu-id="7a400-127">If that does not resolve the party, verify that the correct party is resolved when BizTalk Server attempts to find a match between the AS2-From context property that is set for the incoming message and the name of a party.</span></span>  
  
-   <span data-ttu-id="7a400-128">Assurez-vous que le certificat défini dans la page Certificat de la boîte de dialogue Propriétés du tiers, et stocké dans le magasin Ordinateur local\Autres personnes, correspond à celui utilisé pour signer le message.</span><span class="sxs-lookup"><span data-stu-id="7a400-128">Ensure that the certificate defined in the Certificate page of the Party Properties dialog box, and stored in the Local computer\Other People store, corresponds to the certificate used to sign the message.</span></span>