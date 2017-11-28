---
title: "Le premier élément du lot dépasse l’ensemble de critères de mise en production de nombre caractère | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 746fbfabb2fe411310735f66c6d8a8398a94a5dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-first-element-of-the-batch-exceeded-the-character-count-release-criteria-set"></a><span data-ttu-id="5d509-102">Le premier élément du lot dépasse l'ensemble de critères de diffusion « nombre de caractères »</span><span class="sxs-lookup"><span data-stu-id="5d509-102">The first element of the batch exceeded the character count release criteria set</span></span>
## <a name="details"></a><span data-ttu-id="5d509-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5d509-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d509-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5d509-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5d509-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5d509-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5d509-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5d509-106">Event ID</span></span>|-|  
|<span data-ttu-id="5d509-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5d509-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5d509-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5d509-108"> EDI</span></span>|  
|<span data-ttu-id="5d509-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5d509-109">Component</span></span>|<span data-ttu-id="5d509-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="5d509-110">Batching Engine</span></span>|  
|<span data-ttu-id="5d509-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5d509-111">Symbolic Name</span></span>|<span data-ttu-id="5d509-112">FirstElementExceededCharCount</span><span class="sxs-lookup"><span data-stu-id="5d509-112">FirstElementExceededCharCount</span></span>|  
|<span data-ttu-id="5d509-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5d509-113">Message Text</span></span>|<span data-ttu-id="5d509-114">Le premier élément du lot dépasse l'ensemble de critères de diffusion « nombre de caractères ».</span><span class="sxs-lookup"><span data-stu-id="5d509-114">The first element of the batch exceeded the character count release criteria set.</span></span> <span data-ttu-id="5d509-115">Modifiez le critère de diffusion « nombre de caractères » pour pouvoir traiter ce message.</span><span class="sxs-lookup"><span data-stu-id="5d509-115">Please change the character count release criteria to be able to process this message.</span></span> <span data-ttu-id="5d509-116">Ce message devra être renvoyé au système de traitement par lot après modification des paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d509-116">The message will need to be resent to the batching system after the settings are modified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5d509-117">Explication</span><span class="sxs-lookup"><span data-stu-id="5d509-117">Explanation</span></span>  
 <span data-ttu-id="5d509-118">Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu générer l'échange traité par lot, car le nombre de caractères du premier élément de lot récupéré par l'orchestration de traitement par lot dépasse le nombre de caractères spécifié par la propriété « Nombre maximal de caractères dans un échange » des critères de déclenchement du lot.</span><span class="sxs-lookup"><span data-stu-id="5d509-118">This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in the first batch element picked up by the batching orchestration exceeded the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria.</span></span> <span data-ttu-id="5d509-119">Notez que le nombre de caractères par rapport au maximum n'inclut pas le nombre de caractères dans l'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="5d509-119">Note that the number of characters compared to the maximum does not include the number of characters in the envelope.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5d509-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5d509-120">User Action</span></span>  
 <span data-ttu-id="5d509-121">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d509-121">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="5d509-122">Dans la boîte de dialogue Propriétés EDI pour le tiers en tant que récepteur d'échanges, dans la page Paramètres de création de lots d'échange, augmentez la valeur de la propriété Nombre maximal de caractères dans un échange.</span><span class="sxs-lookup"><span data-stu-id="5d509-122">Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver.</span></span> <span data-ttu-id="5d509-123">Pour ce faire, vous devez arrêter l'instance d'orchestration, augmenter le nombre maximal de caractères de la propriété, puis redémarrer l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5d509-123">To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.</span></span> <span data-ttu-id="5d509-124">Demandez à l'expéditeur de renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="5d509-124">Have the sender resend the message.</span></span>  
  
2.  <span data-ttu-id="5d509-125">Demandez à l'expéditeur d'envoyer des documents informatisés possédant un nombre de caractères inférieur au nombre maximal autorisé.</span><span class="sxs-lookup"><span data-stu-id="5d509-125">Have the sender send transaction sets that have fewer characters than the maximum number of characters.</span></span>