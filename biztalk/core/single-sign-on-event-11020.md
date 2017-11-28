---
title: "Single Sign-On : Événement 11020 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a0d72-ece6-4094-9263-dbf69bb068c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444a61beec74a9d7141df79d05d8863cc10d6dc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11020"></a><span data-ttu-id="5fc08-102">Single Sign-On : Événement 11020</span><span class="sxs-lookup"><span data-stu-id="5fc08-102">Single Sign-On: Event 11020</span></span>
## <a name="details"></a><span data-ttu-id="5fc08-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5fc08-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fc08-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5fc08-104">Product Name</span></span>|<span data-ttu-id="5fc08-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="5fc08-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5fc08-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5fc08-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5fc08-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5fc08-107">Event ID</span></span>|<span data-ttu-id="5fc08-108">11020</span><span class="sxs-lookup"><span data-stu-id="5fc08-108">11020</span></span>|  
|<span data-ttu-id="5fc08-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5fc08-109">Event Source</span></span>|<span data-ttu-id="5fc08-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5fc08-110">ENTSSO</span></span>|  
|<span data-ttu-id="5fc08-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5fc08-111">Component</span></span>|<span data-ttu-id="5fc08-112">Néant</span><span class="sxs-lookup"><span data-stu-id="5fc08-112">N/A</span></span>|  
|<span data-ttu-id="5fc08-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5fc08-113">Symbolic Name</span></span>|<span data-ttu-id="5fc08-114">SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="5fc08-114">SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="5fc08-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5fc08-115">Message Text</span></span>|<span data-ttu-id="5fc08-116">La modification d'un mot de passe Windows entraînera la modification d'un autre compte Windows.%r</span><span class="sxs-lookup"><span data-stu-id="5fc08-116">A Windows password change will cause a different Windows account to be changed.%r</span></span><br /><br /> <span data-ttu-id="5fc08-117">Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="5fc08-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="5fc08-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="5fc08-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="5fc08-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="5fc08-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="5fc08-120">Compte externe : %3 %r</span><span class="sxs-lookup"><span data-stu-id="5fc08-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="5fc08-121">Compte Windows 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="5fc08-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="5fc08-122">Le compte Windows 2 : %5</span><span class="sxs-lookup"><span data-stu-id="5fc08-122">Windows Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5fc08-123">Explication</span><span class="sxs-lookup"><span data-stu-id="5fc08-123">Explanation</span></span>  
 <span data-ttu-id="5fc08-124">Ce message d'information indique que la modification d'un mot de passe Windows entraînera la modification d'un autre compte Windows.</span><span class="sxs-lookup"><span data-stu-id="5fc08-124">This is an informational message stating that a Windows password change will cause a different Windows account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5fc08-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5fc08-125">User Action</span></span>  
 <span data-ttu-id="5fc08-126">Vous devez vérifier immédiatement que vous aviez connaissance de cette modification et l'aviez autorisée.</span><span class="sxs-lookup"><span data-stu-id="5fc08-126">You should confirm immediately that this change was made with your knowledge and authorization.</span></span> <span data-ttu-id="5fc08-127">Dans ce cas, aucune action n'est requise.</span><span class="sxs-lookup"><span data-stu-id="5fc08-127">If so, no action is required.</span></span> <span data-ttu-id="5fc08-128">Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. </span><span class="sxs-lookup"><span data-stu-id="5fc08-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>