---
title: DistributionListRef (nœud Port) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DistributionListRef node [binding file]
ms.assetid: 5d0d0121-1bcc-4c26-a1a3-8937ac7c282a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 665b8c2115c5c4681f7cff057481b6ce7da320ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="distributionlistref-port-node"></a><span data-ttu-id="05b19-102">DistributionListRef (Nœud Port)</span><span class="sxs-lookup"><span data-stu-id="05b19-102">DistributionListRef (Port Node)</span></span>
<span data-ttu-id="05b19-103">Le nœud DistributionListRef du nœud Port d'un fichier de liaison contient des informations sur une liste de distribution référencée par un service.</span><span class="sxs-lookup"><span data-stu-id="05b19-103">The DistributionListRef node of the Port node of a binding file contains information about a distribution list that is referenced by a service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b19-104">Les listes de distribution sont appelées « groupes de ports d'envoi » dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="05b19-104">Distribution lists are referred to as send port groups in the BizTalk Server Administration Console.</span></span>  
  
## <a name="nodes-in-the-distributionlistref-node"></a><span data-ttu-id="05b19-105">Nœuds du nœud DistributionListRef</span><span class="sxs-lookup"><span data-stu-id="05b19-105">Nodes in the DistributionListRef node</span></span>  
 <span data-ttu-id="05b19-106">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="05b19-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="05b19-107">**Nom**</span><span class="sxs-lookup"><span data-stu-id="05b19-107">**Name**</span></span>|<span data-ttu-id="05b19-108">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="05b19-108">**Node Type**</span></span>|<span data-ttu-id="05b19-109">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="05b19-109">**Data Type**</span></span>|<span data-ttu-id="05b19-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="05b19-110">**Description**</span></span>|<span data-ttu-id="05b19-111">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="05b19-111">**Restrictions**</span></span>|<span data-ttu-id="05b19-112">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="05b19-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="05b19-113">Nom</span><span class="sxs-lookup"><span data-stu-id="05b19-113">Name</span></span>|<span data-ttu-id="05b19-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="05b19-114">Attribute</span></span>|<span data-ttu-id="05b19-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="05b19-115">xs:string</span></span>|<span data-ttu-id="05b19-116">Spécifie le nom d'une liste de distribution référencée par un service.</span><span class="sxs-lookup"><span data-stu-id="05b19-116">Specifies the name of a distribution list that is referenced by a service.</span></span>|<span data-ttu-id="05b19-117">Facultatif</span><span class="sxs-lookup"><span data-stu-id="05b19-117">Not required</span></span>|<span data-ttu-id="05b19-118">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="05b19-118">Default value: empty</span></span>|