---
title: "Erreurs dans les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dce5fc9eb944eccbeed57073c2546f81825ec6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-errors"></a><span data-ttu-id="a8ed1-102">Erreurs en relation avec les métadonnées</span><span class="sxs-lookup"><span data-stu-id="a8ed1-102">Metadata Errors</span></span>
<span data-ttu-id="a8ed1-103">Informations sur le diagnostic et résolution des erreurs dans les métadonnées de WCF.</span><span class="sxs-lookup"><span data-stu-id="a8ed1-103">Information for diagnosing and resolving WCF Metadata errors.</span></span>  
  
## <a name="error-consuming-wcf-service-metadata"></a><span data-ttu-id="a8ed1-104">Erreur de consommation des métadonnées de service WCF</span><span class="sxs-lookup"><span data-stu-id="a8ed1-104">Error consuming WCF service metadata</span></span>

||<span data-ttu-id="a8ed1-105">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="a8ed1-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="a8ed1-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a8ed1-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a8ed1-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a8ed1-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a8ed1-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a8ed1-108">Event ID</span></span>|<span data-ttu-id="a8ed1-109">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-109">0</span></span>|  
|<span data-ttu-id="a8ed1-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a8ed1-110">Event Source</span></span>|<span data-ttu-id="a8ed1-111">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-111">0</span></span>|  
|<span data-ttu-id="a8ed1-112">Composant</span><span class="sxs-lookup"><span data-stu-id="a8ed1-112">Component</span></span>|<span data-ttu-id="a8ed1-113">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-113">0</span></span>|  
|<span data-ttu-id="a8ed1-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a8ed1-114">Symbolic Name</span></span>|<span data-ttu-id="a8ed1-115">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-115">0</span></span>|  
|<span data-ttu-id="a8ed1-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a8ed1-116">Message Text</span></span>|<span data-ttu-id="a8ed1-117">Erreur de consommation des métadonnées de service WCF</span><span class="sxs-lookup"><span data-stu-id="a8ed1-117">Error consuming WCF service metadata</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="a8ed1-118">Explication</span><span class="sxs-lookup"><span data-stu-id="a8ed1-118">Explanation</span></span>  
 <span data-ttu-id="a8ed1-119">Cette erreur indique que les métadonnées du service ne sont pas disponibles ou sont non valides.</span><span class="sxs-lookup"><span data-stu-id="a8ed1-119">This error indicates the metadata for the service is either not available or is not valid.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="a8ed1-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a8ed1-120">User Action</span></span>  
 <span data-ttu-id="a8ed1-121">Corrigez les métadonnées du service WCF et tentez de l'utiliser (si vous en êtes le propriétaire).</span><span class="sxs-lookup"><span data-stu-id="a8ed1-121">Correct the service metadata and try to consume (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="a8ed1-122">Accédez à l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et apporter des modifications au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a8ed1-122">Go to the Service Configuration Editor (**svcConfigEditor.exe**) and make changes to the configuration file.</span></span>  <span data-ttu-id="a8ed1-123">Sinon, contactez le fournisseur de services</span><span class="sxs-lookup"><span data-stu-id="a8ed1-123">Otherwise, contact the service provider</span></span>

## <a name="failed-to-get-metadata"></a><span data-ttu-id="a8ed1-124">Échec de l'obtention des métadonnées</span><span class="sxs-lookup"><span data-stu-id="a8ed1-124">Failed to get metadata</span></span>

||<span data-ttu-id="a8ed1-125">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="a8ed1-125">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="a8ed1-126">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a8ed1-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a8ed1-127">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a8ed1-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a8ed1-128">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a8ed1-128">Event ID</span></span>|<span data-ttu-id="a8ed1-129">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-129">0</span></span>|  
|<span data-ttu-id="a8ed1-130">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a8ed1-130">Event Source</span></span>|<span data-ttu-id="a8ed1-131">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-131">0</span></span>|  
|<span data-ttu-id="a8ed1-132">Composant</span><span class="sxs-lookup"><span data-stu-id="a8ed1-132">Component</span></span>|<span data-ttu-id="a8ed1-133">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-133">0</span></span>|  
|<span data-ttu-id="a8ed1-134">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a8ed1-134">Symbolic Name</span></span>|<span data-ttu-id="a8ed1-135">0</span><span class="sxs-lookup"><span data-stu-id="a8ed1-135">0</span></span>|  
|<span data-ttu-id="a8ed1-136">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a8ed1-136">Message Text</span></span>|<span data-ttu-id="a8ed1-137">Échec de l'obtention des métadonnées à partir de « {0} »</span><span class="sxs-lookup"><span data-stu-id="a8ed1-137">Failed to get metadata from "{0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8ed1-138">Explication</span><span class="sxs-lookup"><span data-stu-id="a8ed1-138">Explanation</span></span>  
 <span data-ttu-id="a8ed1-139">Cette erreur indique que les métadonnées ne sont pas disponibles pour ce service.</span><span class="sxs-lookup"><span data-stu-id="a8ed1-139">This error indicates the metadata is not available for that service.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8ed1-140">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a8ed1-140">User Action</span></span>  
 <span data-ttu-id="a8ed1-141">Activez les métadonnées pour le service, puis réexécutez l'Assistant Consommation (si vous êtes propriétaire du service WCF que vous tentez d'utiliser).</span><span class="sxs-lookup"><span data-stu-id="a8ed1-141">Enable metadata for the service and run the consuming wizard again (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="a8ed1-142">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="a8ed1-142">Otherwise, contact the service provider.</span></span>