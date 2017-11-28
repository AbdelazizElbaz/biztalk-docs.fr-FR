---
title: "Aucun élément de lot pour envoyer et un message vide ne peut pas être envoyé car il n’est pas configuré pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0752079a-173e-4de3-96f4-e5de01b799b5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80dcf96feef006a2576afc5829e7927e003524a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-batch-elements-to-send-and-an-empty-message-cannot-be-sent-as-it-is-not-configured-for-party"></a><span data-ttu-id="f4fd9-102">Il n'y a pas d'éléments par lot à envoyer et un message vide ne peut pas être envoyé car il n'est pas configuré pour le tiers</span><span class="sxs-lookup"><span data-stu-id="f4fd9-102">There are no batch elements to send and an empty message cannot be sent as it is not configured for party</span></span>
## <a name="details"></a><span data-ttu-id="f4fd9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f4fd9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4fd9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f4fd9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f4fd9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f4fd9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f4fd9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f4fd9-106">Event ID</span></span>|-|  
|<span data-ttu-id="f4fd9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f4fd9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f4fd9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f4fd9-108"> EDI</span></span>|  
|<span data-ttu-id="f4fd9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f4fd9-109">Component</span></span>|<span data-ttu-id="f4fd9-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="f4fd9-110">Batching Engine</span></span>|  
|<span data-ttu-id="f4fd9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f4fd9-111">Symbolic Name</span></span>|<span data-ttu-id="f4fd9-112">EmptyMessageNotAllowed</span><span class="sxs-lookup"><span data-stu-id="f4fd9-112">EmptyMessageNotAllowed</span></span>|  
|<span data-ttu-id="f4fd9-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f4fd9-113">Message Text</span></span>|<span data-ttu-id="f4fd9-114">Il n'y a pas d'éléments par lot à envoyer et un message vide ne peut pas être envoyé car il n'est pas configuré pour le tiers {0}</span><span class="sxs-lookup"><span data-stu-id="f4fd9-114">There are no batch elements to send and an empty message cannot be sent as it is not configured for party {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4fd9-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f4fd9-115">Explanation</span></span>  
 <span data-ttu-id="f4fd9-116">Cet avertissement indique qu'aucun message de traitement par lot n'a été envoyé dans un processus de traitement par lot basé sur la planification, car aucun élément par lot n'a été reçu lorsque le déclenchement du lot fut planifié et l'alerte signalant un lot vide n'a pas été activée.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-116">This Warning indicates that no batch message was sent in a schedule-based batching process because no batch elements had been received when the batch release was scheduled, and the empty batch signal has not been enabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4fd9-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f4fd9-117">User Action</span></span>  
 <span data-ttu-id="f4fd9-118">Afin d'éviter que cet avertissement ne s'affiche, configurez l'alerte signalant un lot vide comme suit :</span><span class="sxs-lookup"><span data-stu-id="f4fd9-118">To prevent this warning from being posted, configure the empty batch signal by doing the following:</span></span>  
  
1.  <span data-ttu-id="f4fd9-119">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-119">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="f4fd9-120">Accédez au nœud Tiers.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-120">Move to the Parties node.</span></span>  
  
3.  <span data-ttu-id="f4fd9-121">Ouvrez la boîte de dialogue Propriétés EDI du tiers.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-121">Open the EDI Properties dialog box for the party.</span></span>  
  
4.  <span data-ttu-id="f4fd9-122">Cliquez sur le nœud Paramètres de création de lots d'échange (pour obtenir le codage approprié).</span><span class="sxs-lookup"><span data-stu-id="f4fd9-122">Click the Interchange Batch Creation Settings node (for the appropriate encoding).</span></span>  
  
5.  <span data-ttu-id="f4fd9-123">Cliquez sur Planificateur.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-123">Click the Scheduler.</span></span>  
  
6.  <span data-ttu-id="f4fd9-124">Cliquez sur la propriété Envoyer une alerte signalant un lot vide.</span><span class="sxs-lookup"><span data-stu-id="f4fd9-124">Click the Send empty batch signal property.</span></span>