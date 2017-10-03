---
title: "TransmitPipeline (nœud SendPort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransmitPipeline node [binding file]
ms.assetid: cee55451-6c3f-4e37-aef9-870d4b5d23aa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4addad5ea98781865b44470f2d07b577afce6c0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transmitpipeline-sendport-node"></a><span data-ttu-id="bcd6d-102">TransmitPipeline (nœud SendPort)</span><span class="sxs-lookup"><span data-stu-id="bcd6d-102">TransmitPipeline (SendPort Node)</span></span>
<span data-ttu-id="bcd6d-103">Le nœud TransmitPipeline du nœud SendPort d'un fichier de liaison fournit des informations spécifiques sur le pipeline d'envoi associé à un port d'envoi exporté avec un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-103">The TransmitPipeline node of the SendPort node of a binding file provides specific information about the send pipeline bound to a send port exported with a binding file.</span></span>  
  
## <a name="nodes-in-the-transmitpipeline-node"></a><span data-ttu-id="bcd6d-104">Nœuds du nœud TransmitPipeline</span><span class="sxs-lookup"><span data-stu-id="bcd6d-104">Nodes in the TransmitPipeline node</span></span>  
 <span data-ttu-id="bcd6d-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="bcd6d-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="bcd6d-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-106">**Name**</span></span>|<span data-ttu-id="bcd6d-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-107">**Node Type**</span></span>|<span data-ttu-id="bcd6d-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-108">**Data Type**</span></span>|<span data-ttu-id="bcd6d-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-109">**Description**</span></span>|<span data-ttu-id="bcd6d-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-110">**Restrictions**</span></span>|<span data-ttu-id="bcd6d-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="bcd6d-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="bcd6d-112">Nom</span><span class="sxs-lookup"><span data-stu-id="bcd6d-112">Name</span></span>|<span data-ttu-id="bcd6d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcd6d-113">Attribute</span></span>|<span data-ttu-id="bcd6d-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="bcd6d-114">xs:string</span></span>|<span data-ttu-id="bcd6d-115">Indique le nom du pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-115">Specifies the name of the send pipeline.</span></span>|<span data-ttu-id="bcd6d-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="bcd6d-116">Not required</span></span>|<span data-ttu-id="bcd6d-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="bcd6d-117">Default value: empty</span></span>|  
|<span data-ttu-id="bcd6d-118">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bcd6d-118">FullyQualifiedName</span></span>|<span data-ttu-id="bcd6d-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcd6d-119">Attribute</span></span>|<span data-ttu-id="bcd6d-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="bcd6d-120">xs:string</span></span>|<span data-ttu-id="bcd6d-121">Indique le nom complet du pipeline, qui inclut le nom de l'assembly dans le cadre duquel le pipeline a été déployé.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-121">Specifies the fully qualified name of the pipeline, which includes the name of the assembly that the pipeline was deployed as a part of</span></span>|<span data-ttu-id="bcd6d-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="bcd6d-122">Not required</span></span>|<span data-ttu-id="bcd6d-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="bcd6d-123">Default value: empty</span></span>|  
|<span data-ttu-id="bcd6d-124">Type</span><span class="sxs-lookup"><span data-stu-id="bcd6d-124">Type</span></span>|<span data-ttu-id="bcd6d-125">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcd6d-125">Attribute</span></span>|<span data-ttu-id="bcd6d-126">xs:int</span><span class="sxs-lookup"><span data-stu-id="bcd6d-126">xs:int</span></span>|<span data-ttu-id="bcd6d-127">Indique le type du pipeline.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-127">Specifies the type of pipeline.</span></span>|<span data-ttu-id="bcd6d-128">Requis</span><span class="sxs-lookup"><span data-stu-id="bcd6d-128">Required</span></span>|<span data-ttu-id="bcd6d-129">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="bcd6d-129">Default value: none</span></span><br /><br /> <span data-ttu-id="bcd6d-130">Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) .</span><span class="sxs-lookup"><span data-stu-id="bcd6d-130">Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) enumeration.</span></span>|  
|<span data-ttu-id="bcd6d-131">TrackingOption</span><span class="sxs-lookup"><span data-stu-id="bcd6d-131">TrackingOption</span></span>|<span data-ttu-id="bcd6d-132">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcd6d-132">Attribute</span></span>|<span data-ttu-id="bcd6d-133">PipelineTrackingTypes (SimpleType)</span><span class="sxs-lookup"><span data-stu-id="bcd6d-133">PipelineTrackingTypes (SimpleType)</span></span>|<span data-ttu-id="bcd6d-134">Spécifie les options de suivi pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-134">Specifies the tracking options for the pipeline.</span></span>|<span data-ttu-id="bcd6d-135">Requis</span><span class="sxs-lookup"><span data-stu-id="bcd6d-135">Required</span></span>|<span data-ttu-id="bcd6d-136">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="bcd6d-136">Default value: none</span></span><br /><br /> <span data-ttu-id="bcd6d-137">Les valeurs possibles sont documentées dans l'énumération [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) .</span><span class="sxs-lookup"><span data-stu-id="bcd6d-137">Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) enumeration.</span></span>|  
|<span data-ttu-id="bcd6d-138">Description</span><span class="sxs-lookup"><span data-stu-id="bcd6d-138">Description</span></span>|<span data-ttu-id="bcd6d-139">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcd6d-139">Attribute</span></span>|<span data-ttu-id="bcd6d-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="bcd6d-140">xs:string</span></span>|<span data-ttu-id="bcd6d-141">Spécifie une description pour le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bcd6d-141">Specifies a description for the send pipeline.</span></span>|<span data-ttu-id="bcd6d-142">Facultatif</span><span class="sxs-lookup"><span data-stu-id="bcd6d-142">Not required</span></span>|<span data-ttu-id="bcd6d-143">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="bcd6d-143">Default value: empty</span></span>|