---
title: SendPorts (nœud DistributionList) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendPorts node [binding file]
ms.assetid: 9cb645fa-cb9c-44eb-9f98-2fc507b2be67
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9eaf692bd61913e604731fc2e2cea373fd31f48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendports-distributionlist-node"></a><span data-ttu-id="ed6b8-102">SendPorts (nœud DistributionList)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-102">SendPorts (DistributionList Node)</span></span>
<span data-ttu-id="ed6b8-103">Le nœud SendPorts du nœud DistributionList d'un fichier de liaison est le nœud conteneur des références de port d'envoi dans la liste de distribution.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-103">The SendPorts node of the DistributionList node of a binding file is the container node for the send port references in the distribution list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed6b8-104">Une liste de distribution est appelée groupe de ports d'envoi dans l'Administrateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-104">A distribution list is referred to as a send port group in the BizTalk Administrator.</span></span>  
  
## <a name="nodes-in-the-sendports-node"></a><span data-ttu-id="ed6b8-105">Nœuds du nœud SendPorts</span><span class="sxs-lookup"><span data-stu-id="ed6b8-105">Nodes in the SendPorts node</span></span>  
 <span data-ttu-id="ed6b8-106">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="ed6b8-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="ed6b8-107">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-107">**Name**</span></span>|<span data-ttu-id="ed6b8-108">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-108">**Node Type**</span></span>|<span data-ttu-id="ed6b8-109">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-109">**Data Type**</span></span>|<span data-ttu-id="ed6b8-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-110">**Description**</span></span>|<span data-ttu-id="ed6b8-111">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-111">**Restrictions**</span></span>|<span data-ttu-id="ed6b8-112">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="ed6b8-113">SendPortRef</span><span class="sxs-lookup"><span data-stu-id="ed6b8-113">SendPortRef</span></span>](../core/sendportref-sendports-node.md)|<span data-ttu-id="ed6b8-114">Record</span><span class="sxs-lookup"><span data-stu-id="ed6b8-114">Record</span></span>|<span data-ttu-id="ed6b8-115">SendPortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-115">SendPortRef (ComplexType)</span></span>|<span data-ttu-id="ed6b8-116">Nœud conteneur pour une référence à un port d'envoi effectuée par la liste de distribution.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-116">Container node for a reference to a send port made by the distribution list.</span></span>|<span data-ttu-id="ed6b8-117">Facultatif</span><span class="sxs-lookup"><span data-stu-id="ed6b8-117">Not required</span></span>|<span data-ttu-id="ed6b8-118">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="ed6b8-118">Default value: none</span></span>|