---
title: "Nœud ModuleRefCollection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ModuleRefCollection node [binding file]
ms.assetid: fa8593bf-6548-4615-9f98-1e0eadde9aa4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 039cabd380195f840e9ffb99de5071026b3810c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="modulerefcollection-node"></a><span data-ttu-id="81c2d-102">Nœud ModuleRefCollection</span><span class="sxs-lookup"><span data-stu-id="81c2d-102">ModuleRefCollection Node</span></span>
<span data-ttu-id="81c2d-103">La section ModuleRefCollection  d'un fichier de liaison est le nœud parent de tous les nœuds ModuleRef qui contiennent des informations spécifiques concernant les assemblys .NET exportés avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="81c2d-103">The ModuleRefCollection section of a binding file is the parent node for all of the ModuleRef nodes which contain specific information about .NET assemblies exported with the binding file.</span></span>  
  
## <a name="entries-in-the-modulerefcollection-section"></a><span data-ttu-id="81c2d-104">Entrées dans la section ModuleRefCollection.</span><span class="sxs-lookup"><span data-stu-id="81c2d-104">Entries in the ModuleRefCollection section</span></span>  
 <span data-ttu-id="81c2d-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour les nœuds de cette section d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="81c2d-105">The following table lists the properties that can be set for the nodes in this section of a binding file:</span></span>  
  
|<span data-ttu-id="81c2d-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="81c2d-106">**Name**</span></span>|<span data-ttu-id="81c2d-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="81c2d-107">**Node Type**</span></span>|<span data-ttu-id="81c2d-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="81c2d-108">**Data Type**</span></span>|<span data-ttu-id="81c2d-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="81c2d-109">**Description**</span></span>|<span data-ttu-id="81c2d-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="81c2d-110">**Restrictions**</span></span>|<span data-ttu-id="81c2d-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="81c2d-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="81c2d-112">ModuleRef</span><span class="sxs-lookup"><span data-stu-id="81c2d-112">ModuleRef</span></span>](../core/moduleref-modulerefcollection-node.md)|<span data-ttu-id="81c2d-113">Record</span><span class="sxs-lookup"><span data-stu-id="81c2d-113">Record</span></span>|<span data-ttu-id="81c2d-114">ModuleRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="81c2d-114">ModuleRef (ComplexType)</span></span>|<span data-ttu-id="81c2d-115">Nœud conteneur pour un module d’assembly .NET exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="81c2d-115">Container node for a .NET assembly module exported with the binding file.</span></span>|<span data-ttu-id="81c2d-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="81c2d-116">Not required</span></span>|<span data-ttu-id="81c2d-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="81c2d-117">Default value: None</span></span>|