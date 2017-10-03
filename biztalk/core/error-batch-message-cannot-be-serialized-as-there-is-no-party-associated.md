---
title: "Message du lot ne peut pas être sérialisé car il y a aucun tiers associé à un port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d697ff9c-a6d1-4a3c-9ec3-4cd496f7eec2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b20d10a2c7b584eccc7d1fb57e5132a4ac0d608
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a><span data-ttu-id="21939-102">Le message de traitement par lot ne peut pas être sérialisé car il n'y a aucun tiers associé au port d'envoi</span><span class="sxs-lookup"><span data-stu-id="21939-102">Batch message cannot be serialized as there is no party associated with send port</span></span>
## <a name="details"></a><span data-ttu-id="21939-103">Détails</span><span class="sxs-lookup"><span data-stu-id="21939-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21939-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="21939-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="21939-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="21939-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="21939-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="21939-106">Event ID</span></span>|-|  
|<span data-ttu-id="21939-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="21939-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="21939-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="21939-108"> EDI</span></span>|  
|<span data-ttu-id="21939-109">Composant</span><span class="sxs-lookup"><span data-stu-id="21939-109">Component</span></span>|<span data-ttu-id="21939-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="21939-110">Batching Engine</span></span>|  
|<span data-ttu-id="21939-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="21939-111">Symbolic Name</span></span>|<span data-ttu-id="21939-112">BatchMessageSerializationFailureDueToMissingParty</span><span class="sxs-lookup"><span data-stu-id="21939-112">BatchMessageSerializationFailureDueToMissingParty</span></span>|  
|<span data-ttu-id="21939-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="21939-113">Message Text</span></span>|<span data-ttu-id="21939-114">Le message de traitement par lot ne peut pas être sérialisé car il n'y a aucun tiers associé au port d'envoi {0}.</span><span class="sxs-lookup"><span data-stu-id="21939-114">Batch message can not be serialized as there is no party associated with send port {0}.</span></span> <span data-ttu-id="21939-115">Assurez-vous qu'un tiers est associé à ce port</span><span class="sxs-lookup"><span data-stu-id="21939-115">Make sure that a party is associated with the port</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21939-116">Explication</span><span class="sxs-lookup"><span data-stu-id="21939-116">Explanation</span></span>  
 <span data-ttu-id="21939-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter un échange conservé, car il n'a pas réussi à déterminer le tiers auquel le message doit être envoyé.</span><span class="sxs-lookup"><span data-stu-id="21939-117">This Error/Warning/Information event indicates that the send pipeline could not process a preserved interchange because it could not determine the party that the message should be sent to.</span></span> <span data-ttu-id="21939-118">Il n'a pas pu identifier le tiers, car la propriété de contexte DestinationPartyName n'était pas définie.</span><span class="sxs-lookup"><span data-stu-id="21939-118">It could not determine the party because the DestinationPartyName context property was not set.</span></span> <span data-ttu-id="21939-119">Par conséquent, le pipeline d'envoi n'a pas réussi à déterminer les paramètres de l'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="21939-119">As a result, the send pipeline could not determine the envelope settings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21939-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="21939-120">User Action</span></span>  
 <span data-ttu-id="21939-121">Pour résoudre cette erreur, transmettez le message via un pipeline d'envoi PassThrough, puis déterminez la propriété de contexte DestinationPartyName pour le message.</span><span class="sxs-lookup"><span data-stu-id="21939-121">To resolve this error, pass the message through a passthrough send pipeline, and then determine the DestinationPartyName context property for the message.</span></span> <span data-ttu-id="21939-122">Vérifiez également que le tiers existe.</span><span class="sxs-lookup"><span data-stu-id="21939-122">Verify that the party exists.</span></span> <span data-ttu-id="21939-123">Si ce n'est pas le cas, créez-le, puis renvoyez le message.</span><span class="sxs-lookup"><span data-stu-id="21939-123">If not, create the party, and then resend the message.</span></span>