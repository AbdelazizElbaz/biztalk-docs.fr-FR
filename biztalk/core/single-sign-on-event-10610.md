---
title: "Single Sign-On : Événement 10610 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e4edc579c18147ad34234fbf268ec8d867c60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10610"></a><span data-ttu-id="3460c-102">Single Sign-On : Événement 10610</span><span class="sxs-lookup"><span data-stu-id="3460c-102">Single Sign-On: Event 10610</span></span>
## <a name="details"></a><span data-ttu-id="3460c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3460c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3460c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3460c-104">Product Name</span></span>|<span data-ttu-id="3460c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3460c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3460c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3460c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3460c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3460c-107">Event ID</span></span>|<span data-ttu-id="3460c-108">10610</span><span class="sxs-lookup"><span data-stu-id="3460c-108">10610</span></span>|  
|<span data-ttu-id="3460c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3460c-109">Event Source</span></span>|<span data-ttu-id="3460c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3460c-110">ENTSSO</span></span>|  
|<span data-ttu-id="3460c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3460c-111">Component</span></span>|<span data-ttu-id="3460c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="3460c-112">N/A</span></span>|  
|<span data-ttu-id="3460c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3460c-113">Symbolic Name</span></span>|<span data-ttu-id="3460c-114">SSO_WARN_CRED_CACHE_FAILED</span><span class="sxs-lookup"><span data-stu-id="3460c-114">SSO_WARN_CRED_CACHE_FAILED</span></span>|  
|<span data-ttu-id="3460c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3460c-115">Message Text</span></span>|<span data-ttu-id="3460c-116">Le cache des informations d'identification a rencontré une erreur inattendue et s'est arrêté.</span><span class="sxs-lookup"><span data-stu-id="3460c-116">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="3460c-117">Cela peut avoir une incidence sur les performances.%r</span><span class="sxs-lookup"><span data-stu-id="3460c-117">This may affect performance.%r</span></span><br /><br /> <span data-ttu-id="3460c-118">Code d’erreur : %1</span><span class="sxs-lookup"><span data-stu-id="3460c-118">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3460c-119">Explication</span><span class="sxs-lookup"><span data-stu-id="3460c-119">Explanation</span></span>  
 <span data-ttu-id="3460c-120">Le cache des informations d'identification a rencontré une erreur inattendue et s'est arrêté.</span><span class="sxs-lookup"><span data-stu-id="3460c-120">The credential cache has encountered an unexpected error and has shut down.</span></span> <span data-ttu-id="3460c-121">Bien que cette situation puisse affecter les performances, cela n'aura aucune incidence sur les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3460c-121">While this may affect performance, it will not affect functionality.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3460c-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3460c-122">User Action</span></span>  
 <span data-ttu-id="3460c-123">Redémarrez le service SSO au moment opportun.</span><span class="sxs-lookup"><span data-stu-id="3460c-123">Restart the SSO service when convenient.</span></span>