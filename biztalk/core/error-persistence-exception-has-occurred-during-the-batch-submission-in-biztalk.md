---
title: "Une exception de persistance s’est produite lors de l’envoi du lot dans l’Orchestration de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eae4f48209dc4f5afefbc69c40706a31f2b00b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-persistence-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="200aa-102">Une exception de persistance s'est produite durant l'envoi par lot de l'orchestration de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="200aa-102">A persistence exception has occurred during the batch submission in the batching Orchestration</span></span>
## <a name="details"></a><span data-ttu-id="200aa-103">Détails</span><span class="sxs-lookup"><span data-stu-id="200aa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="200aa-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="200aa-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="200aa-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="200aa-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="200aa-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="200aa-106">Event ID</span></span>|-|  
|<span data-ttu-id="200aa-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="200aa-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="200aa-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="200aa-108"> EDI</span></span>|  
|<span data-ttu-id="200aa-109">Composant</span><span class="sxs-lookup"><span data-stu-id="200aa-109">Component</span></span>|<span data-ttu-id="200aa-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="200aa-110">Batching Engine</span></span>|  
|<span data-ttu-id="200aa-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="200aa-111">Symbolic Name</span></span>|<span data-ttu-id="200aa-112">PersistenceExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="200aa-112">PersistenceExceptionOccured</span></span>|  
|<span data-ttu-id="200aa-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="200aa-113">Message Text</span></span>|<span data-ttu-id="200aa-114">Une exception de persistance s'est produite durant l'envoi par lot de l'orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="200aa-114">A persistence exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="200aa-115">Id de lot = {0}, message d’erreur = {{1}.</span><span class="sxs-lookup"><span data-stu-id="200aa-115">Batch Id = {0}, ErrorMessage = {1}.</span></span> <span data-ttu-id="200aa-116">Vérifiez vos abonnements de port d'envoi et corrigez-les.</span><span class="sxs-lookup"><span data-stu-id="200aa-116">Please check your send port subscriptions and fix them.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="200aa-117">Explication</span><span class="sxs-lookup"><span data-stu-id="200aa-117">Explanation</span></span>  
 <span data-ttu-id="200aa-118">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu envoyer un échange traité par lot, car aucun port d'envoi n'est abonné à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="200aa-118">This Error/Warning/Information event indicates that BizTalk Server could not send a batched interchange because no send port subscribed to the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="200aa-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="200aa-119">User Action</span></span>  
 <span data-ttu-id="200aa-120">Pour résoudre cette erreur, assurez-vous qu’un port d’envoi s’abonne au lot en définissant les propriétés de filtre suivantes pour le port d’envoi : EDI. DestinationPartyName = \<Nom_tiers >, EDI. BatchEncodingType = EDIFACT ou X12 et EDI. ToBeBatched = False.</span><span class="sxs-lookup"><span data-stu-id="200aa-120">To resolve this error, ensure that a send port subscribes to the batch by setting the following filter properties for the send port: EDI.DestinationPartyName = \<PartyName>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.</span></span>