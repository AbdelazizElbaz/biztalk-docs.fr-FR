---
title: "SendHandler (nœud PrimaryTransport) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendHandler node [binding file]
ms.assetid: c0b200ee-ecbc-4708-a2c8-c37cd6cd0060
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029285e9b56aeb91bbca7a7c9eacf6abedc7ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendhandler-primarytransport-node"></a><span data-ttu-id="1411e-102">SendHandler (nœud PrimaryTransport)</span><span class="sxs-lookup"><span data-stu-id="1411e-102">SendHandler (PrimaryTransport Node)</span></span>
<span data-ttu-id="1411e-103">Le nœud SendHandler du nœud PrimaryTransport d'un fichier de liaison contient des informations sur le gestionnaire d'envoi associé à un transport exporté avec ce fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="1411e-103">The SendHandler node of the PrimaryTransport node of a binding file contains specific information about the send handler associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-sendhandler-node"></a><span data-ttu-id="1411e-104">Nœuds du nœud SendHandler</span><span class="sxs-lookup"><span data-stu-id="1411e-104">Nodes in the SendHandler node</span></span>  
 <span data-ttu-id="1411e-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="1411e-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="1411e-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="1411e-106">**Name**</span></span>|<span data-ttu-id="1411e-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="1411e-107">**Node Type**</span></span>|<span data-ttu-id="1411e-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="1411e-108">**Data Type**</span></span>|<span data-ttu-id="1411e-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="1411e-109">**Description**</span></span>|<span data-ttu-id="1411e-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="1411e-110">**Restrictions**</span></span>|<span data-ttu-id="1411e-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="1411e-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="1411e-112">Nom</span><span class="sxs-lookup"><span data-stu-id="1411e-112">Name</span></span>|<span data-ttu-id="1411e-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="1411e-113">Attribute</span></span>|<span data-ttu-id="1411e-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="1411e-114">xs:string</span></span>|<span data-ttu-id="1411e-115">Spécifie le nom du gestionnaire d'envoi associé au transport.</span><span class="sxs-lookup"><span data-stu-id="1411e-115">Specifies the name of the send handler associated with the transport.</span></span>|<span data-ttu-id="1411e-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="1411e-116">Not required</span></span>|<span data-ttu-id="1411e-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="1411e-117">Default value: empty</span></span>|  
|<span data-ttu-id="1411e-118">HostTrusted</span><span class="sxs-lookup"><span data-stu-id="1411e-118">HostTrusted</span></span>|<span data-ttu-id="1411e-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="1411e-119">Attribute</span></span>|<span data-ttu-id="1411e-120">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="1411e-120">xs:boolean</span></span>|<span data-ttu-id="1411e-121">Spécifie si l'hôte associé au gestionnaire d'envoi est approuvé.</span><span class="sxs-lookup"><span data-stu-id="1411e-121">Specifies whether the host associated with the send handler is trusted.</span></span>|<span data-ttu-id="1411e-122">Requis</span><span class="sxs-lookup"><span data-stu-id="1411e-122">Required</span></span>|<span data-ttu-id="1411e-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="1411e-123">Default value: none</span></span><br /><br /> <span data-ttu-id="1411e-124">La valeur **true** si l’hôte est approuvé, sinon la valeur **false**.</span><span class="sxs-lookup"><span data-stu-id="1411e-124">Set to **true** if host is trusted, otherwise set to **false**.</span></span>|  
|[<span data-ttu-id="1411e-125">Type de transport</span><span class="sxs-lookup"><span data-stu-id="1411e-125">TransportType</span></span>](../core/transporttype.md)|<span data-ttu-id="1411e-126">Record</span><span class="sxs-lookup"><span data-stu-id="1411e-126">Record</span></span>|<span data-ttu-id="1411e-127">ProtocolType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="1411e-127">ProtocolType (ComplexType)</span></span>|<span data-ttu-id="1411e-128">Spécifie le type de transport, qui correspond également au nom de l'adaptateur utilisé avec ce gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1411e-128">Specifies the transport type, which is also the name of the adapter used with this send handler.</span></span>|<span data-ttu-id="1411e-129">Requis</span><span class="sxs-lookup"><span data-stu-id="1411e-129">Required</span></span>|<span data-ttu-id="1411e-130">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="1411e-130">Default value: none</span></span>|