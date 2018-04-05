---
title: Type de transport | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: 64eb00be-47c9-473f-aec6-03cb7f948e3b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d9636e7aa6dd8b09bb73678072242ed8b8725a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype"></a><span data-ttu-id="9ec52-102">TransportType</span><span class="sxs-lookup"><span data-stu-id="9ec52-102">TransportType</span></span>
<span data-ttu-id="9ec52-103">Le nœud TransportType du nœud SendHandler d'un fichier de liaison contient des informations sur l'adaptateur associé à un gestionnaire d'envoi exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="9ec52-103">The TransportType node of the SendHandler node of a binding file contains specific information about the adapter associated with a send handler that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="9ec52-104">Nœuds du nœud TransportType</span><span class="sxs-lookup"><span data-stu-id="9ec52-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="9ec52-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="9ec52-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="9ec52-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="9ec52-106">**Name**</span></span>|<span data-ttu-id="9ec52-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="9ec52-107">**Node Type**</span></span>|<span data-ttu-id="9ec52-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="9ec52-108">**Data Type**</span></span>|<span data-ttu-id="9ec52-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="9ec52-109">**Description**</span></span>|<span data-ttu-id="9ec52-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="9ec52-110">**Restrictions**</span></span>|<span data-ttu-id="9ec52-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="9ec52-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="9ec52-112">Nom</span><span class="sxs-lookup"><span data-stu-id="9ec52-112">Name</span></span>|<span data-ttu-id="9ec52-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ec52-113">Attribute</span></span>|<span data-ttu-id="9ec52-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ec52-114">xs:string</span></span>|<span data-ttu-id="9ec52-115">Spécifie le nom de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9ec52-115">Specifies the name of the adapter associated with the send handler.</span></span>|<span data-ttu-id="9ec52-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="9ec52-116">Not required</span></span>|<span data-ttu-id="9ec52-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="9ec52-117">Default value: empty</span></span>|  
|<span data-ttu-id="9ec52-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="9ec52-118">Capabilities</span></span>|<span data-ttu-id="9ec52-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ec52-119">Attribute</span></span>|<span data-ttu-id="9ec52-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="9ec52-120">xs:int</span></span>|<span data-ttu-id="9ec52-121">Spécifie les fonctions de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9ec52-121">Specifies the capabilities of the adapter associated with the send handler.</span></span>|<span data-ttu-id="9ec52-122">Requis</span><span class="sxs-lookup"><span data-stu-id="9ec52-122">Required</span></span>|<span data-ttu-id="9ec52-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="9ec52-123">Default value: none</span></span><br /><br /> <span data-ttu-id="9ec52-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="9ec52-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="9ec52-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="9ec52-125">ConfigurationClsid</span></span>|<span data-ttu-id="9ec52-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ec52-126">Attribute</span></span>|<span data-ttu-id="9ec52-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ec52-127">xs:string</span></span>|<span data-ttu-id="9ec52-128">Spécifie le GUID de configuration de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9ec52-128">Specifies the configuration GUID of the adapter associated with the send handler.</span></span>|<span data-ttu-id="9ec52-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="9ec52-129">Not required</span></span>|<span data-ttu-id="9ec52-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="9ec52-130">Default value: empty</span></span>|