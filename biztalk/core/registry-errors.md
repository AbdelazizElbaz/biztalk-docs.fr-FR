---
title: Erreurs de Registre | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5bf2cd-f807-4083-8687-4416a2ee2908
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c84ec2a1082f431fef8e06357f14cc9b621c6a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="registry-errors"></a><span data-ttu-id="2b76a-102">Erreurs en relation avec le Registre</span><span class="sxs-lookup"><span data-stu-id="2b76a-102">Registry Errors</span></span>
<span data-ttu-id="2b76a-103">Informations sur le diagnostic et résolution des erreurs de Registre WCF.</span><span class="sxs-lookup"><span data-stu-id="2b76a-103">Information for diagnosing and resolving WCF Registry errors.</span></span>  

## <a name="failed-to-access-the-registry"></a><span data-ttu-id="2b76a-104">Échec de l'accès au Registre</span><span class="sxs-lookup"><span data-stu-id="2b76a-104">Failed to access the registry</span></span>
  
||<span data-ttu-id="2b76a-105">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="2b76a-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="2b76a-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2b76a-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2b76a-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2b76a-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="2b76a-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2b76a-108">Event ID</span></span>|<span data-ttu-id="2b76a-109">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-109">0</span></span>|  
|<span data-ttu-id="2b76a-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2b76a-110">Event Source</span></span>|<span data-ttu-id="2b76a-111">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-111">0</span></span>|  
|<span data-ttu-id="2b76a-112">Composant</span><span class="sxs-lookup"><span data-stu-id="2b76a-112">Component</span></span>|<span data-ttu-id="2b76a-113">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-113">0</span></span>|  
|<span data-ttu-id="2b76a-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2b76a-114">Symbolic Name</span></span>|<span data-ttu-id="2b76a-115">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-115">0</span></span>|  
|<span data-ttu-id="2b76a-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2b76a-116">Message Text</span></span>|<span data-ttu-id="2b76a-117">Impossible d’ouvrir HKLM\\{0}.</span><span class="sxs-lookup"><span data-stu-id="2b76a-117">Failed to open HKLM\\{0}.</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="2b76a-118">Explication</span><span class="sxs-lookup"><span data-stu-id="2b76a-118">Explanation</span></span>  
 <span data-ttu-id="2b76a-119">Cette erreur indique l'échec de l'accès au Registre.</span><span class="sxs-lookup"><span data-stu-id="2b76a-119">This error indicates a failure to access the registry.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="2b76a-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2b76a-120">User Action</span></span>  
 <span data-ttu-id="2b76a-121">Vérifiez que vous disposez d'un accès en lecture au Registre</span><span class="sxs-lookup"><span data-stu-id="2b76a-121">Ensure you have read access to the registry.</span></span> <span data-ttu-id="2b76a-122">Pour accéder au Registre, assurez-vous de disposer d'autorisations Administrateur ou contactez l'administrateur de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2b76a-122">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span>
 
## <a name="failed-to-obtain-biztalk-install-path"></a><span data-ttu-id="2b76a-123">Impossible d'obtenir le chemin d'installation de BizTalk</span><span class="sxs-lookup"><span data-stu-id="2b76a-123">Failed to obtain BizTalk install path</span></span>
  
||<span data-ttu-id="2b76a-124">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="2b76a-124">Error Details</span></span>|  
|-|-|  
|<span data-ttu-id="2b76a-125">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2b76a-125">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2b76a-126">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2b76a-126">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="2b76a-127">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2b76a-127">Event ID</span></span>|<span data-ttu-id="2b76a-128">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-128">0</span></span>|  
|<span data-ttu-id="2b76a-129">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2b76a-129">Event Source</span></span>|<span data-ttu-id="2b76a-130">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-130">0</span></span>|  
|<span data-ttu-id="2b76a-131">Composant</span><span class="sxs-lookup"><span data-stu-id="2b76a-131">Component</span></span>|<span data-ttu-id="2b76a-132">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-132">0</span></span>|  
|<span data-ttu-id="2b76a-133">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2b76a-133">Symbolic Name</span></span>|<span data-ttu-id="2b76a-134">0</span><span class="sxs-lookup"><span data-stu-id="2b76a-134">0</span></span>|  
|<span data-ttu-id="2b76a-135">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2b76a-135">Message Text</span></span>|<span data-ttu-id="2b76a-136">Impossible d’obtenir le chemin d’installation de BizTalk à partir de HKLM\\{0}\\{{1}</span><span class="sxs-lookup"><span data-stu-id="2b76a-136">Failed to obtain BizTalk install path from HKLM\\{0}\\{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2b76a-137">Explication</span><span class="sxs-lookup"><span data-stu-id="2b76a-137">Explanation</span></span>  
 <span data-ttu-id="2b76a-138">Cette erreur indique l'échec de l'accès au Registre et une valeur de clé incorrecte.</span><span class="sxs-lookup"><span data-stu-id="2b76a-138">This error indicates a failure to access the registry, and that the key has an incorrect value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2b76a-139">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2b76a-139">User Action</span></span>  
 <span data-ttu-id="2b76a-140">Vérifiez que vous disposez d'un accès en lecture au Registre</span><span class="sxs-lookup"><span data-stu-id="2b76a-140">Ensure you have read access to the registry.</span></span> <span data-ttu-id="2b76a-141">et que la valeur de la clé est correcte.</span><span class="sxs-lookup"><span data-stu-id="2b76a-141">Ensure the key has the correct value.</span></span> <span data-ttu-id="2b76a-142">Pour accéder au Registre, assurez-vous de disposer d'autorisations Administrateur ou contactez l'administrateur de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2b76a-142">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span> 