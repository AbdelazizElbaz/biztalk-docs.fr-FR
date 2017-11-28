---
title: "Erreur lors du chargement d’assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 600973e0-3142-455f-9afa-74430af31e38
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13be3acf6974565c86cc87b14ed58929553d5220
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-loading-assembly"></a><span data-ttu-id="a451d-102">Erreur lors du chargement de l'assembly</span><span class="sxs-lookup"><span data-stu-id="a451d-102">Error loading assembly</span></span>
## <a name="details"></a><span data-ttu-id="a451d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a451d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a451d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a451d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a451d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a451d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a451d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a451d-106">Event ID</span></span>|<span data-ttu-id="a451d-107">0</span><span class="sxs-lookup"><span data-stu-id="a451d-107">0</span></span>|  
|<span data-ttu-id="a451d-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a451d-108">Event Source</span></span>|<span data-ttu-id="a451d-109">0</span><span class="sxs-lookup"><span data-stu-id="a451d-109">0</span></span>|  
|<span data-ttu-id="a451d-110">Composant</span><span class="sxs-lookup"><span data-stu-id="a451d-110">Component</span></span>|<span data-ttu-id="a451d-111">0</span><span class="sxs-lookup"><span data-stu-id="a451d-111">0</span></span>|  
|<span data-ttu-id="a451d-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a451d-112">Symbolic Name</span></span>|<span data-ttu-id="a451d-113">0</span><span class="sxs-lookup"><span data-stu-id="a451d-113">0</span></span>|  
|<span data-ttu-id="a451d-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a451d-114">Message Text</span></span>|<span data-ttu-id="a451d-115">Cette erreur indique que l'emplacement n'est peut-être pas entièrement fiable s'il est situé sur un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="a451d-115">This error indicates the location may not be fully trusted if it is on a network share.</span></span> <span data-ttu-id="a451d-116">Vérifiez la stratégie de sécurité d'accès du code pour la zone.</span><span class="sxs-lookup"><span data-stu-id="a451d-116">Check the Code Access Security policy for the Zone.</span></span> <span data-ttu-id="a451d-117">Il se peut que le fichier ne corresponde pas à un assembly .NET de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a451d-117">Or the file may not be a BizTalk .NET assembly.</span></span> <span data-ttu-id="a451d-118">Vérifiez l’assembly pour le [assembly : assembly BizTalk] attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a451d-118">Check the assembly for the [assembly: BizTalkAssembly] custom attribute.</span></span> <span data-ttu-id="a451d-119">Il se peut que le fichier ne corresponde pas à un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="a451d-119">Or the file may not be a .NET assembly.</span></span> <span data-ttu-id="a451d-120">Il peut s'agir d'un fichier .dll ou .exe qui inclut du code non géré</span><span class="sxs-lookup"><span data-stu-id="a451d-120">If the file is a .dll or  exe, it may be unmanaged code</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a451d-121">Explication</span><span class="sxs-lookup"><span data-stu-id="a451d-121">Explanation</span></span>  
 <span data-ttu-id="a451d-122">Cette erreur indique que l'emplacement n'est peut-être pas entièrement fiable s'il est situé sur un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="a451d-122">This error indicates the location may not be fully trusted if it is on a network share.</span></span> <span data-ttu-id="a451d-123">Vérifiez la stratégie de sécurité d'accès du code pour la zone.</span><span class="sxs-lookup"><span data-stu-id="a451d-123">Check the Code Access Security policy for the Zone.</span></span> <span data-ttu-id="a451d-124">Il se peut que le fichier ne corresponde pas à un assembly .NET de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a451d-124">Or the file may not be a BizTalk .NET assembly.</span></span> <span data-ttu-id="a451d-125">Vérifiez l’assembly pour le [*assembly : assembly BizTalk*] attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a451d-125">Check the assembly for the [*assembly: BizTalkAssembly*] custom attribute.</span></span> <span data-ttu-id="a451d-126">Il se peut que le fichier ne corresponde pas à un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="a451d-126">Or the file may not be a .NET assembly.</span></span> <span data-ttu-id="a451d-127">Il peut s'agir d'un fichier .dll ou exe qui inclut du code non géré.</span><span class="sxs-lookup"><span data-stu-id="a451d-127">If the file is a .dll or  exe, it may be unmanaged code.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a451d-128">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a451d-128">User Action</span></span>  
 <span data-ttu-id="a451d-129">Accordez un niveau Confiance totale à l'emplacement s'il provient d'une source fiable.</span><span class="sxs-lookup"><span data-stu-id="a451d-129">Grant Full trust level to the location if it’s from a reliable source.</span></span>  <span data-ttu-id="a451d-130">Vérifiez que le fichier .dll est un assembly .Net de BizTalk valide.</span><span class="sxs-lookup"><span data-stu-id="a451d-130">Ensure the dll is a valid BizTalk .net assembly.</span></span>