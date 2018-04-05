---
title: ReceiveLocationTransportType (nœud ReceiveLocation) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveLocationTransportType node [binding file]
ms.assetid: 375076c3-d5e6-4c25-b054-b452e29717e0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0eae3e2c4fd9f5f668cb12ffd630640b1b63c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocationtransporttype-receivelocation-node"></a><span data-ttu-id="9a45c-102">ReceiveLocationTransportType (nœud ReceiveLocation)</span><span class="sxs-lookup"><span data-stu-id="9a45c-102">ReceiveLocationTransportType (ReceiveLocation Node)</span></span>
<span data-ttu-id="9a45c-103">Le nœud ReceiveLocationTransportType du nœud ReceiveLocation d'un fichier de liaison contient des informations sur l'adaptateur associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="9a45c-103">The ReceiveLocationTransportType node of the ReceiveLocation node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivelocationtransporttype-node"></a><span data-ttu-id="9a45c-104">Nœuds du nœud ReceiveLocationTransportType</span><span class="sxs-lookup"><span data-stu-id="9a45c-104">Nodes in the ReceiveLocationTransportType node</span></span>  
 <span data-ttu-id="9a45c-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="9a45c-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="9a45c-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="9a45c-106">**Name**</span></span>|<span data-ttu-id="9a45c-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="9a45c-107">**Node Type**</span></span>|<span data-ttu-id="9a45c-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="9a45c-108">**Data Type**</span></span>|<span data-ttu-id="9a45c-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="9a45c-109">**Description**</span></span>|<span data-ttu-id="9a45c-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="9a45c-110">**Restrictions**</span></span>|<span data-ttu-id="9a45c-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="9a45c-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="9a45c-112">Nom</span><span class="sxs-lookup"><span data-stu-id="9a45c-112">Name</span></span>|<span data-ttu-id="9a45c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9a45c-113">Attribute</span></span>|<span data-ttu-id="9a45c-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a45c-114">xs:string</span></span>|<span data-ttu-id="9a45c-115">Spécifie le nom de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="9a45c-115">Specifies the name of the adapter associated with the transport.</span></span>|<span data-ttu-id="9a45c-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="9a45c-116">Not required</span></span>|<span data-ttu-id="9a45c-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="9a45c-117">Default value: empty</span></span>|  
|<span data-ttu-id="9a45c-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="9a45c-118">Capabilities</span></span>|<span data-ttu-id="9a45c-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="9a45c-119">Attribute</span></span>|<span data-ttu-id="9a45c-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="9a45c-120">xs:int</span></span>|<span data-ttu-id="9a45c-121">Spécifie les fonctions de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="9a45c-121">Specifies the capabilities of the adapter associated with the transport.</span></span>|<span data-ttu-id="9a45c-122">Requis</span><span class="sxs-lookup"><span data-stu-id="9a45c-122">Required</span></span>|<span data-ttu-id="9a45c-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="9a45c-123">Default value: none</span></span><br /><br /> <span data-ttu-id="9a45c-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="9a45c-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="9a45c-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="9a45c-125">ConfigurationClsid</span></span>|<span data-ttu-id="9a45c-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="9a45c-126">Attribute</span></span>|<span data-ttu-id="9a45c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a45c-127">xs:string</span></span>|<span data-ttu-id="9a45c-128">Spécifie le GUID de configuration de l'adaptateur associé au transport.</span><span class="sxs-lookup"><span data-stu-id="9a45c-128">Specifies the configuration GUID of the adapter associated with the transport.</span></span>|<span data-ttu-id="9a45c-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="9a45c-129">Not required</span></span>|<span data-ttu-id="9a45c-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="9a45c-130">Default value: empty</span></span>|