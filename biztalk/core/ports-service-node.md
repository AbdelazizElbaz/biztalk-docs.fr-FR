---
title: Ports (nœud de Service) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Ports node [binding file]
ms.assetid: 498d4310-4e9e-4e74-bc3d-5cbf1319c4ff
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e09470b9f3287cce5ce15c2941d2165157ec48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ports-service-node"></a><span data-ttu-id="676fa-102">Ports (nœud de service)</span><span class="sxs-lookup"><span data-stu-id="676fa-102">Ports (Service Node)</span></span>
<span data-ttu-id="676fa-103">Le nœud Ports d'un fichier de liaison est le nœud parent de tous les nœuds Port qui contiennent des informations spécifiques sur les ports liés à un service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="676fa-103">The Ports node of a binding file is the parent node for all of the Port nodes which contain specific information about ports bound to a service that is exported with the binding file.</span></span>  
  
## <a name="node-in-the-ports-node"></a><span data-ttu-id="676fa-104">Nœud du nœud Ports</span><span class="sxs-lookup"><span data-stu-id="676fa-104">Node in the Ports node</span></span>  
 <span data-ttu-id="676fa-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="676fa-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="676fa-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="676fa-106">**Name**</span></span>|<span data-ttu-id="676fa-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="676fa-107">**Node Type**</span></span>|<span data-ttu-id="676fa-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="676fa-108">**Data Type**</span></span>|<span data-ttu-id="676fa-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="676fa-109">**Description**</span></span>|<span data-ttu-id="676fa-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="676fa-110">**Restrictions**</span></span>|<span data-ttu-id="676fa-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="676fa-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="676fa-112">Port</span><span class="sxs-lookup"><span data-stu-id="676fa-112">Port</span></span>](../core/port-ports-node.md)|<span data-ttu-id="676fa-113">Record</span><span class="sxs-lookup"><span data-stu-id="676fa-113">Record</span></span>|<span data-ttu-id="676fa-114">ServicePortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="676fa-114">ServicePortRef (ComplexType)</span></span>|<span data-ttu-id="676fa-115">Spécifie des informations sur un port lié à un service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="676fa-115">Specifies information about a port that is bound to a service that is exported with the binding file.</span></span>|<span data-ttu-id="676fa-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="676fa-116">Not required</span></span>|<span data-ttu-id="676fa-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="676fa-117">Default value: none</span></span>|