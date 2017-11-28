---
title: "Rôles (nœud de Service) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Roles node [binding file]
ms.assetid: 847755c9-1697-41a0-b870-f9e795a1a2a6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47f5ae94326b0555c0c9cd84752cb9f1c409daa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="roles-service-node"></a><span data-ttu-id="ac264-102">Rôles (nœud de service)</span><span class="sxs-lookup"><span data-stu-id="ac264-102">Roles (Service Node)</span></span>
<span data-ttu-id="ac264-103">Le nœud Rôles d'un fichier de liaison est le nœud parent de tous les nœuds Rôles qui fournissent des informations spécifiques sur chaque rôle lié à un service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac264-103">The Roles node of a binding file is the parent node for all of the Role nodes which provide specific information about each role bound to a service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-roles-node"></a><span data-ttu-id="ac264-104">Nœuds du nœud Rôles</span><span class="sxs-lookup"><span data-stu-id="ac264-104">Nodes in the Roles node</span></span>  
 <span data-ttu-id="ac264-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="ac264-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="ac264-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ac264-106">**Name**</span></span>|<span data-ttu-id="ac264-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="ac264-107">**Node Type**</span></span>|<span data-ttu-id="ac264-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="ac264-108">**Data Type**</span></span>|<span data-ttu-id="ac264-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="ac264-109">**Description**</span></span>|<span data-ttu-id="ac264-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="ac264-110">**Restrictions**</span></span>|<span data-ttu-id="ac264-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="ac264-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="ac264-112">Rôle</span><span class="sxs-lookup"><span data-stu-id="ac264-112">Role</span></span>](../core/role-roles-node.md)|<span data-ttu-id="ac264-113">Record</span><span class="sxs-lookup"><span data-stu-id="ac264-113">Record</span></span>|<span data-ttu-id="ac264-114">RoleRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ac264-114">RoleRef (ComplexType)</span></span>|<span data-ttu-id="ac264-115">Spécifie des informations sur un rôle lié à un service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ac264-115">Specifies information about a role that is bound to a service that is exported with the binding file.</span></span>|<span data-ttu-id="ac264-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="ac264-116">Not required</span></span>|<span data-ttu-id="ac264-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="ac264-117">Default value: none</span></span>|