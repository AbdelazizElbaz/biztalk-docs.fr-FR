---
title: "L’élément de lot a dépassé le nombre maximal de caractères configuré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ad12733-295a-43ba-8147-34c8716c2d37
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac259db250a88e434efb649a2baf2e75b805a40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a><span data-ttu-id="b9831-102">L'élément par lot a dépassé le nombre maximal de caractères configuré</span><span class="sxs-lookup"><span data-stu-id="b9831-102">The batch element exceeded the maximum configured character count</span></span>
## <a name="details"></a><span data-ttu-id="b9831-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b9831-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9831-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b9831-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b9831-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b9831-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b9831-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b9831-106">Event ID</span></span>|-|  
|<span data-ttu-id="b9831-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b9831-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b9831-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b9831-108"> EDI</span></span>|  
|<span data-ttu-id="b9831-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b9831-109">Component</span></span>|<span data-ttu-id="b9831-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="b9831-110">Batching Engine</span></span>|  
|<span data-ttu-id="b9831-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b9831-111">Symbolic Name</span></span>|<span data-ttu-id="b9831-112">MessageExceededCharacterCount</span><span class="sxs-lookup"><span data-stu-id="b9831-112">MessageExceededCharacterCount</span></span>|  
|<span data-ttu-id="b9831-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b9831-113">Message Text</span></span>|<span data-ttu-id="b9831-114">L'élément par lot a dépassé le nombre maximal de caractères configuré</span><span class="sxs-lookup"><span data-stu-id="b9831-114">The batch element exceeded the maximum configured character count</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9831-115">Explication</span><span class="sxs-lookup"><span data-stu-id="b9831-115">Explanation</span></span>  
 <span data-ttu-id="b9831-116">Cet événement d'erreur/d'avertissement/d'informations indique que l'orchestration de traitement par lot n'a pas pu générer l'échange traité par lot, car le nombre de caractères d'un élément de lot récupéré par l'orchestration de traitement par lot dépasse le nombre de caractères spécifié par la propriété « Nombre maximal de caractères dans un échange » des critères de déclenchement du lot.</span><span class="sxs-lookup"><span data-stu-id="b9831-116">This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in a batch element picked up by the batching orchestration exceeds the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria.</span></span> <span data-ttu-id="b9831-117">L'élément de lot à l'origine de ce message d'erreur ne sera pas le premier élément de lot à être récupéré pour un lot, mais un élément de lot suivant le premier élément a déjà été traité par lot.</span><span class="sxs-lookup"><span data-stu-id="b9831-117">The batch element that generates this error message will not be the first batch element picked up for a batch, but a batch element after the first element has already been batched.</span></span> <span data-ttu-id="b9831-118">Notez que le nombre de caractères par rapport au maximum n'inclut pas le nombre de caractères dans l'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="b9831-118">Note that the number of characters compared to the maximum does not include the number of characters in the envelope.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9831-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b9831-119">User Action</span></span>  
 <span data-ttu-id="b9831-120">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9831-120">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="b9831-121">Dans la boîte de dialogue Propriétés EDI pour le tiers en tant que récepteur d'échanges, dans la page Paramètres de création de lots d'échange, augmentez la valeur de la propriété Nombre maximal de caractères dans un échange.</span><span class="sxs-lookup"><span data-stu-id="b9831-121">Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver.</span></span> <span data-ttu-id="b9831-122">Pour ce faire, vous devez arrêter l'instance d'orchestration, augmenter le nombre maximal de caractères de la propriété, puis redémarrer l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b9831-122">To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.</span></span>  
  
2.  <span data-ttu-id="b9831-123">Demandez à l'expéditeur d'envoyer des documents informatisés possédant un nombre de caractères inférieur au nombre maximal autorisé.</span><span class="sxs-lookup"><span data-stu-id="b9831-123">Have the sender send transaction sets that have fewer characters than the maximum number of characters.</span></span>