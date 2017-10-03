---
title: "TransportType (nœud PrimaryTransport) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransportType node [binding file]
ms.assetid: 9eb377ec-35d8-4b72-85f9-f264f6553c5a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40e0f005e7279541a2cdcb5c2bf205b7731e5263
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-primarytransport-node"></a><span data-ttu-id="bff1a-102">TransportType (nœud PrimaryTransport)</span><span class="sxs-lookup"><span data-stu-id="bff1a-102">TransportType (PrimaryTransport Node)</span></span>
<span data-ttu-id="bff1a-103">Le nœud TransportType du nœud PrimaryTransport d'un fichier de liaison contient des informations sur l'adaptateur associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="bff1a-103">The TransportType node of the PrimaryTransport node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="bff1a-104">Nœuds du nœud TransportType</span><span class="sxs-lookup"><span data-stu-id="bff1a-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="bff1a-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="bff1a-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="bff1a-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="bff1a-106">**Name**</span></span>|<span data-ttu-id="bff1a-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="bff1a-107">**Node Type**</span></span>|<span data-ttu-id="bff1a-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="bff1a-108">**Data Type**</span></span>|<span data-ttu-id="bff1a-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="bff1a-109">**Description**</span></span>|<span data-ttu-id="bff1a-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="bff1a-110">**Restrictions**</span></span>|<span data-ttu-id="bff1a-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="bff1a-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="bff1a-112">Nom</span><span class="sxs-lookup"><span data-stu-id="bff1a-112">Name</span></span>|<span data-ttu-id="bff1a-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bff1a-113">Attribute</span></span>|<span data-ttu-id="bff1a-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="bff1a-114">xs:string</span></span>|<span data-ttu-id="bff1a-115">Spécifie le nom de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="bff1a-115">Specifies the name of the adapter associated with the transport.</span></span>|<span data-ttu-id="bff1a-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="bff1a-116">Not required</span></span>|<span data-ttu-id="bff1a-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="bff1a-117">Default value: empty</span></span>|  
|<span data-ttu-id="bff1a-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="bff1a-118">Capabilities</span></span>|<span data-ttu-id="bff1a-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="bff1a-119">Attribute</span></span>|<span data-ttu-id="bff1a-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="bff1a-120">xs:int</span></span>|<span data-ttu-id="bff1a-121">Spécifie les fonctions de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="bff1a-121">Specifies the capabilities of the adapter associated with the transport.</span></span>|<span data-ttu-id="bff1a-122">Requis</span><span class="sxs-lookup"><span data-stu-id="bff1a-122">Required</span></span>|<span data-ttu-id="bff1a-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="bff1a-123">Default value: none</span></span><br /><br /> <span data-ttu-id="bff1a-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="bff1a-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="bff1a-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="bff1a-125">ConfigurationClsid</span></span>|<span data-ttu-id="bff1a-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="bff1a-126">Attribute</span></span>|<span data-ttu-id="bff1a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bff1a-127">xs:string</span></span>|<span data-ttu-id="bff1a-128">Spécifie le GUID de configuration de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="bff1a-128">Specifies the configuration GUID of the adapter associated with the transport.</span></span>|<span data-ttu-id="bff1a-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="bff1a-129">Not required</span></span>|<span data-ttu-id="bff1a-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="bff1a-130">Default value: empty</span></span>|