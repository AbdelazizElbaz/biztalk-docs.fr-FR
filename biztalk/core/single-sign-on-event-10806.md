---
title: "Single Sign-On : Événement 10806 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23650d6b-b6a4-4c41-96cd-476e5b0f7f63
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd3f432a408cffcbd1ccd27508550fd0888c5213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10806"></a><span data-ttu-id="50162-102">Single Sign-On : Événement 10806</span><span class="sxs-lookup"><span data-stu-id="50162-102">Single Sign-On: Event 10806</span></span>
## <a name="details"></a><span data-ttu-id="50162-103">Détails</span><span class="sxs-lookup"><span data-stu-id="50162-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50162-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="50162-104">Product Name</span></span>|<span data-ttu-id="50162-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="50162-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="50162-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="50162-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="50162-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="50162-107">Event ID</span></span>|<span data-ttu-id="50162-108">10806</span><span class="sxs-lookup"><span data-stu-id="50162-108">10806</span></span>|  
|<span data-ttu-id="50162-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="50162-109">Event Source</span></span>|<span data-ttu-id="50162-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="50162-110">ENTSSO</span></span>|  
|<span data-ttu-id="50162-111">Composant</span><span class="sxs-lookup"><span data-stu-id="50162-111">Component</span></span>|<span data-ttu-id="50162-112">Néant</span><span class="sxs-lookup"><span data-stu-id="50162-112">N/A</span></span>|  
|<span data-ttu-id="50162-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="50162-113">Symbolic Name</span></span>|<span data-ttu-id="50162-114">ENTSSO_E_APP_ASSIGNED_TO_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="50162-114">ENTSSO_E_APP_ASSIGNED_TO_ADAPTER</span></span>|  
|<span data-ttu-id="50162-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="50162-115">Message Text</span></span>|<span data-ttu-id="50162-116">L'application ne peut pas être supprimée car elle est actuellement affectée à un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="50162-116">The application cannot be deleted because it is currently assigned to an adapter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="50162-117">Explication</span><span class="sxs-lookup"><span data-stu-id="50162-117">Explanation</span></span>  
 <span data-ttu-id="50162-118">Une application ne peut pas être supprimée lorsqu'elle est affectée à un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="50162-118">An application cannot be deleted when it is assigned to an adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="50162-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="50162-119">User Action</span></span>  
 <span data-ttu-id="50162-120">Supprimez l'affectation de l'application à l'adaptateur, puis supprimez l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="50162-120">Unassign the application from the adapter, and then delete it.</span></span>