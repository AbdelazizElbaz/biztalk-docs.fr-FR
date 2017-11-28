---
title: "TransportType (nœud SendHandler) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransportType node [binding file]
ms.assetid: ee87a409-33dd-4111-ba6a-ead3bacc80aa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3525b78fa9812c1e4fa8690a622f9b8cccce8d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-sendhandler-node"></a><span data-ttu-id="19e25-102">TransportType (nœud SendHandler)</span><span class="sxs-lookup"><span data-stu-id="19e25-102">TransportType (SendHandler Node)</span></span>
<span data-ttu-id="19e25-103">Le nœud TransportType du nœud SendHandler d'un fichier de liaison contient des informations sur l'adaptateur associé à un gestionnaire d'envoi exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="19e25-103">The TransportType node of the SendHandler node of a binding file contains specific information about the adapter associated with a send handler that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="19e25-104">Nœuds du nœud TransportType</span><span class="sxs-lookup"><span data-stu-id="19e25-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="19e25-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="19e25-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="19e25-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="19e25-106">**Name**</span></span>|<span data-ttu-id="19e25-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="19e25-107">**Node Type**</span></span>|<span data-ttu-id="19e25-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="19e25-108">**Data Type**</span></span>|<span data-ttu-id="19e25-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="19e25-109">**Description**</span></span>|<span data-ttu-id="19e25-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="19e25-110">**Restrictions**</span></span>|<span data-ttu-id="19e25-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="19e25-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="19e25-112">Nom</span><span class="sxs-lookup"><span data-stu-id="19e25-112">Name</span></span>|<span data-ttu-id="19e25-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="19e25-113">Attribute</span></span>|<span data-ttu-id="19e25-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="19e25-114">xs:string</span></span>|<span data-ttu-id="19e25-115">Spécifie le nom de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="19e25-115">Specifies the name of the adapter associated with the send handler.</span></span>|<span data-ttu-id="19e25-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="19e25-116">Not required</span></span>|<span data-ttu-id="19e25-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="19e25-117">Default value: empty</span></span>|  
|<span data-ttu-id="19e25-118">Fonctions</span><span class="sxs-lookup"><span data-stu-id="19e25-118">Capabilities</span></span>|<span data-ttu-id="19e25-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="19e25-119">Attribute</span></span>|<span data-ttu-id="19e25-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="19e25-120">xs:int</span></span>|<span data-ttu-id="19e25-121">Spécifie les fonctions de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="19e25-121">Specifies the capabilities of the adapter associated with the send handler.</span></span>|<span data-ttu-id="19e25-122">Requis</span><span class="sxs-lookup"><span data-stu-id="19e25-122">Required</span></span>|<span data-ttu-id="19e25-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="19e25-123">Default value: none</span></span><br /><br /> <span data-ttu-id="19e25-124">Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .</span><span class="sxs-lookup"><span data-stu-id="19e25-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="19e25-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="19e25-125">ConfigurationClsid</span></span>|<span data-ttu-id="19e25-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="19e25-126">Attribute</span></span>|<span data-ttu-id="19e25-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="19e25-127">xs:string</span></span>|<span data-ttu-id="19e25-128">Spécifie le GUID de configuration de l'adaptateur associé au gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="19e25-128">Specifies the configuration GUID of the adapter associated with the send handler.</span></span>|<span data-ttu-id="19e25-129">Facultatif</span><span class="sxs-lookup"><span data-stu-id="19e25-129">Not required</span></span>|<span data-ttu-id="19e25-130">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="19e25-130">Default value: empty</span></span>|