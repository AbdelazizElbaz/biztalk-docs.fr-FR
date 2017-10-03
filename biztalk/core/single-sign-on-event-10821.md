---
title: "Single Sign-On : Événement 10821 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2200011e-3e4f-4fe4-b01f-f3b86cdc96db
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f212a77f85330d256f1415ec13f3ec267e4be7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10821"></a><span data-ttu-id="cd33d-102">Single Sign-On : Événement 10821</span><span class="sxs-lookup"><span data-stu-id="cd33d-102">Single Sign-On: Event 10821</span></span>
## <a name="details"></a><span data-ttu-id="cd33d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cd33d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd33d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cd33d-104">Product Name</span></span>|<span data-ttu-id="cd33d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cd33d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cd33d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cd33d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cd33d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cd33d-107">Event ID</span></span>|<span data-ttu-id="cd33d-108">10821</span><span class="sxs-lookup"><span data-stu-id="cd33d-108">10821</span></span>|  
|<span data-ttu-id="cd33d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cd33d-109">Event Source</span></span>|<span data-ttu-id="cd33d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cd33d-110">ENTSSO</span></span>|  
|<span data-ttu-id="cd33d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="cd33d-111">Component</span></span>|<span data-ttu-id="cd33d-112">Néant</span><span class="sxs-lookup"><span data-stu-id="cd33d-112">N/A</span></span>|  
|<span data-ttu-id="cd33d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cd33d-113">Symbolic Name</span></span>|<span data-ttu-id="cd33d-114">ENTSSO_E_ADAPTER_ASSIGNED_TO_GROUP_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="cd33d-114">ENTSSO_E_ADAPTER_ASSIGNED_TO_GROUP_ADAPTER</span></span>|  
|<span data-ttu-id="cd33d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cd33d-115">Message Text</span></span>|<span data-ttu-id="cd33d-116">L'adaptateur ne peut pas être supprimé car il est actuellement affecté à un adaptateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="cd33d-116">The adapter cannot be deleted because it is currently assigned to a group adapter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd33d-117">Explication</span><span class="sxs-lookup"><span data-stu-id="cd33d-117">Explanation</span></span>  
 <span data-ttu-id="cd33d-118">L'adaptateur ne peut pas être supprimé car il est actuellement affecté à un adaptateur de groupe.</span><span class="sxs-lookup"><span data-stu-id="cd33d-118">The adapter cannot be deleted because it is currently assigned to a group adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd33d-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cd33d-119">User Action</span></span>  
 <span data-ttu-id="cd33d-120">Supprimez l'affectation de l'adaptateur, puis supprimez-le.</span><span class="sxs-lookup"><span data-stu-id="cd33d-120">Unassign the adapter and then delete it.</span></span>