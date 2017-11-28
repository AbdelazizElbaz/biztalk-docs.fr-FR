---
title: "ReceiveHandler (nœud ReceiveLocation) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceiveHandler node [binding file]
ms.assetid: dd105052-ec71-4762-aa74-e8cdb806a6bf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e865886624731414f979c77f3f2e898e417c8b11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivehandler-receivelocation-node"></a><span data-ttu-id="23b15-102">ReceiveHandler (nœud ReceiveLocation)</span><span class="sxs-lookup"><span data-stu-id="23b15-102">ReceiveHandler (ReceiveLocation Node)</span></span>
<span data-ttu-id="23b15-103">Le nœud ReceiveHandler du nœud ReceiveLocation d'un fichier de liaison contient des informations sur le gestionnaire de réception associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="23b15-103">The ReceiveHandler node of the ReceiveLocation node of a binding file contains specific information about the receive handler associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivehandler-node"></a><span data-ttu-id="23b15-104">Nœuds du nœud ReceiveHandler</span><span class="sxs-lookup"><span data-stu-id="23b15-104">Nodes in the ReceiveHandler node</span></span>  
 <span data-ttu-id="23b15-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="23b15-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="23b15-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="23b15-106">**Name**</span></span>|<span data-ttu-id="23b15-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="23b15-107">**Node Type**</span></span>|<span data-ttu-id="23b15-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="23b15-108">**Data Type**</span></span>|<span data-ttu-id="23b15-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="23b15-109">**Description**</span></span>|<span data-ttu-id="23b15-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="23b15-110">**Restrictions**</span></span>|<span data-ttu-id="23b15-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="23b15-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="23b15-112">Nom</span><span class="sxs-lookup"><span data-stu-id="23b15-112">Name</span></span>|<span data-ttu-id="23b15-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="23b15-113">Attribute</span></span>|<span data-ttu-id="23b15-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="23b15-114">xs:string</span></span>|<span data-ttu-id="23b15-115">Spécifie le nom du gestionnaire de réception associé au transport.</span><span class="sxs-lookup"><span data-stu-id="23b15-115">Specifies the name of the receive handler associated with the transport.</span></span>|<span data-ttu-id="23b15-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="23b15-116">Not required</span></span>|<span data-ttu-id="23b15-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="23b15-117">Default value: empty</span></span>|  
|<span data-ttu-id="23b15-118">HostTrusted</span><span class="sxs-lookup"><span data-stu-id="23b15-118">HostTrusted</span></span>|<span data-ttu-id="23b15-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="23b15-119">Attribute</span></span>|<span data-ttu-id="23b15-120">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="23b15-120">xs:boolean</span></span>|<span data-ttu-id="23b15-121">Spécifie si l'hôte associé au gestionnaire de réception est approuvé.</span><span class="sxs-lookup"><span data-stu-id="23b15-121">Specifies whether the host associated with the receive handler is trusted.</span></span>|<span data-ttu-id="23b15-122">Requis</span><span class="sxs-lookup"><span data-stu-id="23b15-122">Required</span></span>|<span data-ttu-id="23b15-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="23b15-123">Default value: none</span></span><br /><br /> <span data-ttu-id="23b15-124">La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.</span><span class="sxs-lookup"><span data-stu-id="23b15-124">Set to **true** if host is trusted, otherwise set to **false**.</span></span>|  
|[<span data-ttu-id="23b15-125">TransportType (nœud ReceiveHandler)</span><span class="sxs-lookup"><span data-stu-id="23b15-125">TransportType (ReceiveHandler Node)</span></span>](../core/transporttype-receivehandler-node.md)|<span data-ttu-id="23b15-126">Record</span><span class="sxs-lookup"><span data-stu-id="23b15-126">Record</span></span>|<span data-ttu-id="23b15-127">ProtocolType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="23b15-127">ProtocolType (ComplexType)</span></span>|<span data-ttu-id="23b15-128">Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé avec ce gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="23b15-128">Specifies the transport type, which is also the name of the adapter used with this receive handler.</span></span>|<span data-ttu-id="23b15-129">Requis</span><span class="sxs-lookup"><span data-stu-id="23b15-129">Required</span></span>|<span data-ttu-id="23b15-130">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="23b15-130">Default value: none</span></span>|