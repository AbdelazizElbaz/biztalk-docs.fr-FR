---
title: TransportType (nœud SecondaryTransport) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: ed66c7ef-32b6-4110-b932-f96a45a29618
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bb0b9460e6c4689dab169a37a9d6b6c51753598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-secondarytransport-node"></a><span data-ttu-id="105de-102">TransportType (nœud SecondaryTransport)</span><span class="sxs-lookup"><span data-stu-id="105de-102">TransportType (SecondaryTransport Node)</span></span>
<span data-ttu-id="105de-103">Le nœud TransportType du nœud SecondaryTransport d'un fichier de liaison contient des informations sur l'adaptateur associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="105de-103">The TransportType node of the SecondaryTransport node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="105de-104">Nœuds du nœud TransportType</span><span class="sxs-lookup"><span data-stu-id="105de-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="105de-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="105de-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="105de-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="105de-106">**Name**</span></span>|<span data-ttu-id="105de-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="105de-107">**Node Type**</span></span>|<span data-ttu-id="105de-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="105de-108">**Data Type**</span></span>|<span data-ttu-id="105de-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="105de-109">**Description**</span></span>|<span data-ttu-id="105de-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="105de-110">**Restrictions**</span></span>|<span data-ttu-id="105de-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="105de-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="105de-112">Nom</span><span class="sxs-lookup"><span data-stu-id="105de-112">Name</span></span>|<span data-ttu-id="105de-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="105de-113">Attribute</span></span>|<span data-ttu-id="105de-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="105de-114">xs:string</span></span>|<span data-ttu-id="105de-115">Spécifie le nom de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="105de-115">Specifies the name of the adapter associated with the transport.</span></span>|<span data-ttu-id="105de-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="105de-116">Not required</span></span>|<span data-ttu-id="105de-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="105de-117">Default value: empty</span></span>|  
|<span data-ttu-id="105de-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="105de-118">Capabilities</span></span>|<span data-ttu-id="105de-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="105de-119">Attribute</span></span>|<span data-ttu-id="105de-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="105de-120">xs:int</span></span>|<span data-ttu-id="105de-121">Spécifie les fonctions de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="105de-121">Specifies the capabilities of the adapter associated with the transport.</span></span>|<span data-ttu-id="105de-122">Requis</span><span class="sxs-lookup"><span data-stu-id="105de-122">Required</span></span>|<span data-ttu-id="105de-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="105de-123">Default value: none</span></span><br /><br /> <span data-ttu-id="105de-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="105de-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="105de-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="105de-125">ConfigurationClsid</span></span>|<span data-ttu-id="105de-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="105de-126">Attribute</span></span>|<span data-ttu-id="105de-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="105de-127">xs:string</span></span>|<span data-ttu-id="105de-128">Spécifie le GUID de configuration de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="105de-128">Specifies the configuration GUID of the adapter associated with the transport.</span></span>|<span data-ttu-id="105de-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="105de-129">Not required</span></span>|<span data-ttu-id="105de-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="105de-130">Default value: empty</span></span>|