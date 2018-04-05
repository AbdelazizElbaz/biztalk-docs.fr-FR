---
title: TransportType (nœud ReceiveHandler) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: d893b3ac-8e2c-41fb-926c-cea23f6f93b3
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df0e041a322b8bb9a144b9ea2bdab5ebb58ac01e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-receivehandler-node"></a><span data-ttu-id="87156-102">TransportType (nœud ReceiveHandler)</span><span class="sxs-lookup"><span data-stu-id="87156-102">TransportType (ReceiveHandler Node)</span></span>
<span data-ttu-id="87156-103">Le nœud TransportType du nœud ReceiveHandler d'un fichier de liaison contient des informations sur l'adaptateur associé à un gestionnaire de réception exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="87156-103">The TransportType node of the ReceiveHandler node of a binding file contains specific information about the adapter associated with a receive handler that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="87156-104">Nœuds du nœud TransportType</span><span class="sxs-lookup"><span data-stu-id="87156-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="87156-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="87156-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="87156-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="87156-106">**Name**</span></span>|<span data-ttu-id="87156-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="87156-107">**Node Type**</span></span>|<span data-ttu-id="87156-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="87156-108">**Data Type**</span></span>|<span data-ttu-id="87156-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="87156-109">**Description**</span></span>|<span data-ttu-id="87156-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="87156-110">**Restrictions**</span></span>|<span data-ttu-id="87156-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="87156-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="87156-112">Nom</span><span class="sxs-lookup"><span data-stu-id="87156-112">Name</span></span>|<span data-ttu-id="87156-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="87156-113">Attribute</span></span>|<span data-ttu-id="87156-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="87156-114">xs:string</span></span>|<span data-ttu-id="87156-115">Spécifie le nom de l'adaptateur associé au gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="87156-115">Specifies the name of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="87156-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="87156-116">Not Required</span></span>|<span data-ttu-id="87156-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="87156-117">Default value: empty</span></span>|  
|<span data-ttu-id="87156-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="87156-118">Capabilities</span></span>|<span data-ttu-id="87156-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="87156-119">Attribute</span></span>|<span data-ttu-id="87156-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="87156-120">xs:int</span></span>|<span data-ttu-id="87156-121">Spécifie les fonctions de l'adaptateur associé au gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="87156-121">Specifies the capabilities of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="87156-122">Requis</span><span class="sxs-lookup"><span data-stu-id="87156-122">Required</span></span>|<span data-ttu-id="87156-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="87156-123">Default value: none</span></span><br /><br /> <span data-ttu-id="87156-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="87156-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="87156-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="87156-125">ConfigurationClsid</span></span>|<span data-ttu-id="87156-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="87156-126">Attribute</span></span>|<span data-ttu-id="87156-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="87156-127">xs:string</span></span>|<span data-ttu-id="87156-128">Spécifie le GUID de configuration de l'adaptateur associé au gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="87156-128">Specifies the configuration GUID of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="87156-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="87156-129">Not Required</span></span>|<span data-ttu-id="87156-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="87156-130">Default value: empty</span></span>|