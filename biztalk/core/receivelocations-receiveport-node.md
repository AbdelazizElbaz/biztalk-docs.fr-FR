---
title: "ReceiveLocations (nœud ReceivePort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceiveLocations node [binding file]
ms.assetid: c12acc1b-f8fe-4a27-8386-d9f4f4455e3f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c9fb5b64466e32ae27d53852b3383eb79531d60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocations-receiveport-node"></a><span data-ttu-id="dc148-102">ReceiveLocations (nœud ReceivePort)</span><span class="sxs-lookup"><span data-stu-id="dc148-102">ReceiveLocations (ReceivePort Node)</span></span>
<span data-ttu-id="dc148-103">Le nœud ReceiveLocations du nœud ReceivePort d'un fichier de liaison est le nœud parent de tous les nœuds ReceiveLocation qui contiennent des informations spécifiques sur les emplacements de réception exportés avec ce fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="dc148-103">The ReceiveLocations node of the ReceivePort node of a binding file is the parent node for all of the ReceiveLocation nodes which contain specific information about the receive locations that are exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivelocations-node"></a><span data-ttu-id="dc148-104">Nœuds du nœud ReceiveLocations</span><span class="sxs-lookup"><span data-stu-id="dc148-104">Nodes in the ReceiveLocations node</span></span>  
 <span data-ttu-id="dc148-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="dc148-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="dc148-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="dc148-106">**Name**</span></span>|<span data-ttu-id="dc148-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="dc148-107">**Node Type**</span></span>|<span data-ttu-id="dc148-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="dc148-108">**Data Type**</span></span>|<span data-ttu-id="dc148-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="dc148-109">**Description**</span></span>|<span data-ttu-id="dc148-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="dc148-110">**Restrictions**</span></span>|<span data-ttu-id="dc148-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="dc148-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="dc148-112">Emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="dc148-112">ReceiveLocation</span></span>](../core/receivelocation-receivelocations-node.md)|<span data-ttu-id="dc148-113">Record</span><span class="sxs-lookup"><span data-stu-id="dc148-113">Record</span></span>|<span data-ttu-id="dc148-114">ReceiveLocation (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="dc148-114">ReceiveLocation (ComplexType)</span></span>|<span data-ttu-id="dc148-115">Spécifie les informations relatives à un emplacement de réception exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="dc148-115">Specifies information about a receive location that is exported with the binding file.</span></span>|<span data-ttu-id="dc148-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="dc148-116">Not required</span></span>|<span data-ttu-id="dc148-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="dc148-117">Default value: none</span></span>|