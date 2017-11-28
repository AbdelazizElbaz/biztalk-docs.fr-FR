---
title: "Il n’y aucune orchestration avec public les ports de réception dans cet assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e04c10119b617ebabe07169dcae999fe60210e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a><span data-ttu-id="63853-102">Cet assembly BizTalk ne comporte aucune orchestration avec ports de réception publics</span><span class="sxs-lookup"><span data-stu-id="63853-102">There are no orchestrations with public receive ports in this BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="63853-103">Détails</span><span class="sxs-lookup"><span data-stu-id="63853-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63853-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="63853-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="63853-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="63853-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="63853-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="63853-106">Event ID</span></span>|<span data-ttu-id="63853-107">0</span><span class="sxs-lookup"><span data-stu-id="63853-107">0</span></span>|  
|<span data-ttu-id="63853-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="63853-108">Event Source</span></span>|<span data-ttu-id="63853-109">0</span><span class="sxs-lookup"><span data-stu-id="63853-109">0</span></span>|  
|<span data-ttu-id="63853-110">Composant</span><span class="sxs-lookup"><span data-stu-id="63853-110">Component</span></span>|<span data-ttu-id="63853-111">0</span><span class="sxs-lookup"><span data-stu-id="63853-111">0</span></span>|  
|<span data-ttu-id="63853-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="63853-112">Symbolic Name</span></span>|<span data-ttu-id="63853-113">0</span><span class="sxs-lookup"><span data-stu-id="63853-113">0</span></span>|  
|<span data-ttu-id="63853-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="63853-114">Message Text</span></span>|<span data-ttu-id="63853-115">Cet assembly BizTalk ne comporte aucune orchestration avec ports de réception publics.</span><span class="sxs-lookup"><span data-stu-id="63853-115">There are no orchestrations with public receive ports in this BizTalk assembly.</span></span> <span data-ttu-id="63853-116">Cliquez sur Précédent et spécifiez un assembly BizTalk contenant des orchestrations avec ports de réception publics</span><span class="sxs-lookup"><span data-stu-id="63853-116">Click back and specify a BizTalk assembly containing orchestrations with public receive ports</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63853-117">Explication</span><span class="sxs-lookup"><span data-stu-id="63853-117">Explanation</span></span>  
 <span data-ttu-id="63853-118">Cette erreur indique que l'orchestration sélectionnée ne possède pas de port public.</span><span class="sxs-lookup"><span data-stu-id="63853-118">This error indicates the orchestration selected does not have a public port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63853-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="63853-119">User Action</span></span>  
 <span data-ttu-id="63853-120">La procédure suivante permet de configurer un port public.</span><span class="sxs-lookup"><span data-stu-id="63853-120">Use the following procedure to configure a public port.</span></span>  
  
#### <a name="to-configure-a-public-port"></a><span data-ttu-id="63853-121">Pour configurer un port public</span><span class="sxs-lookup"><span data-stu-id="63853-121">To configure a public port</span></span>  
  
1.  <span data-ttu-id="63853-122">Recherchez l'orchestration et définissez le port de réception souhaité comme étant public.</span><span class="sxs-lookup"><span data-stu-id="63853-122">Locate the orchestration and make the desired receive port public.</span></span>  
  
    1.  <span data-ttu-id="63853-123">Ouvrez l’Assistant Configuration du Port.</span><span class="sxs-lookup"><span data-stu-id="63853-123">Open the Port Configuration wizard.</span></span>  
  
    2.  <span data-ttu-id="63853-124">Dans **sélectionner un Type de Port**, modifiez **Restrictions d’accès** de **interne** (valeur par défaut) **Public-aucune limite**.</span><span class="sxs-lookup"><span data-stu-id="63853-124">In **Select a Port Type**, change **Access Restrictions** from **Internal** (default) to **Public-no limits**.</span></span>  
  
2.  <span data-ttu-id="63853-125">Recompilez l'assembly.</span><span class="sxs-lookup"><span data-stu-id="63853-125">Recompile the assembly.</span></span>  
  
     <span data-ttu-id="63853-126">\- - OU -</span><span class="sxs-lookup"><span data-stu-id="63853-126">\- OR -</span></span>  
  
     <span data-ttu-id="63853-127">Chargez un assembly BizTalk avec des ports de réception publics.</span><span class="sxs-lookup"><span data-stu-id="63853-127">Load a BizTalk assembly with public receive ports.</span></span>