---
title: "Single Sign-On : Événement 11021 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70b987aa-8097-4243-a25b-f1cc12c5bc6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e246ac3d0bbab4e991b17c091567b4b59131b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11021"></a><span data-ttu-id="904cf-102">Single Sign-On : Événement 11021</span><span class="sxs-lookup"><span data-stu-id="904cf-102">Single Sign-On: Event 11021</span></span>
## <a name="details"></a><span data-ttu-id="904cf-103">Détails</span><span class="sxs-lookup"><span data-stu-id="904cf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="904cf-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="904cf-104">Product Name</span></span>|<span data-ttu-id="904cf-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="904cf-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="904cf-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="904cf-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="904cf-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="904cf-107">Event ID</span></span>|<span data-ttu-id="904cf-108">11021</span><span class="sxs-lookup"><span data-stu-id="904cf-108">11021</span></span>|  
|<span data-ttu-id="904cf-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="904cf-109">Event Source</span></span>|<span data-ttu-id="904cf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="904cf-110">ENTSSO</span></span>|  
|<span data-ttu-id="904cf-111">Composant</span><span class="sxs-lookup"><span data-stu-id="904cf-111">Component</span></span>|<span data-ttu-id="904cf-112">Néant</span><span class="sxs-lookup"><span data-stu-id="904cf-112">N/A</span></span>|  
|<span data-ttu-id="904cf-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="904cf-113">Symbolic Name</span></span>|<span data-ttu-id="904cf-114">SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="904cf-114">SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="904cf-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="904cf-115">Message Text</span></span>|<span data-ttu-id="904cf-116">La modification d'un mot de passe externe entraînera la modification d'un autre compte externe.%r</span><span class="sxs-lookup"><span data-stu-id="904cf-116">An external password change will cause a different external account to be changed.%r</span></span><br /><br /> <span data-ttu-id="904cf-117">Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="904cf-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="904cf-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="904cf-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="904cf-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="904cf-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="904cf-120">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="904cf-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="904cf-121">Compte externe 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="904cf-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="904cf-122">Compte externe 2 : %5</span><span class="sxs-lookup"><span data-stu-id="904cf-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="904cf-123">Explication</span><span class="sxs-lookup"><span data-stu-id="904cf-123">Explanation</span></span>  
 <span data-ttu-id="904cf-124">Ce message d'information indique que la modification d'un mot de passe externe entraînera la modification d'un autre compte externe.</span><span class="sxs-lookup"><span data-stu-id="904cf-124">This is an informational message stating that an external password change will cause a different external account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="904cf-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="904cf-125">User Action</span></span>  
 <span data-ttu-id="904cf-126">Vous devez vérifier immédiatement que vous aviez connaissance de cette modification et l'aviez autorisée.</span><span class="sxs-lookup"><span data-stu-id="904cf-126">You should confirm immediately that this change was made with your knowledge and authorization.</span></span> <span data-ttu-id="904cf-127">Dans ce cas, aucune action n'est requise.</span><span class="sxs-lookup"><span data-stu-id="904cf-127">If so, no action is required.</span></span> <span data-ttu-id="904cf-128">Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. </span><span class="sxs-lookup"><span data-stu-id="904cf-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>