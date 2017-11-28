---
title: "TrackedSchemas (nœud ModuleRef) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TrackedSchemas node [binding file]
ms.assetid: a2b99fbf-df6b-4a94-97b8-ac5eb819604f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 303aeb1ed17b001583a596d5b550faf63ea1200b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="trackedschemas-moduleref-node"></a><span data-ttu-id="66728-102">TrackedSchemas (nœud ModuleRef)</span><span class="sxs-lookup"><span data-stu-id="66728-102">TrackedSchemas (ModuleRef Node)</span></span>
<span data-ttu-id="66728-103">Le nœud TrackedSchemas d'un fichier de liaison est le nœud parent de tous les nœuds Schéma qui décrivent les schémas liés au service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="66728-103">The TrackedSchemas node of a binding file is the parent node for all of the Schema nodes which describe the schemas bound to the service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-trackedschemas-node"></a><span data-ttu-id="66728-104">Nœuds du nœud TrackedSchemas</span><span class="sxs-lookup"><span data-stu-id="66728-104">Nodes in the TrackedSchemas node</span></span>  
 <span data-ttu-id="66728-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="66728-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="66728-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="66728-106">**Name**</span></span>|<span data-ttu-id="66728-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="66728-107">**Node Type**</span></span>|<span data-ttu-id="66728-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="66728-108">**Data Type**</span></span>|<span data-ttu-id="66728-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="66728-109">**Description**</span></span>|<span data-ttu-id="66728-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="66728-110">**Restrictions**</span></span>|<span data-ttu-id="66728-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="66728-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="66728-112">Schéma</span><span class="sxs-lookup"><span data-stu-id="66728-112">Schema</span></span>](../core/schema-trackedschemas-node.md)|<span data-ttu-id="66728-113">Record</span><span class="sxs-lookup"><span data-stu-id="66728-113">Record</span></span>|<span data-ttu-id="66728-114">ArrayOfSchema (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="66728-114">ArrayOfSchema (ComplexType)</span></span>|<span data-ttu-id="66728-115">Nœud conteneur pour les schémas liés au service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="66728-115">Container node for the schemas that are bound to the service that is exported with the binding file.</span></span>|<span data-ttu-id="66728-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="66728-116">Not required</span></span>|<span data-ttu-id="66728-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="66728-117">Default value: none</span></span>|