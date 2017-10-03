---
title: "Single Sign-On : Événement 11022 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccae36e9beef672e6c5fb7917c88341ce4bb3c08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11022"></a><span data-ttu-id="ccf68-102">Single Sign-On : Événement 11022</span><span class="sxs-lookup"><span data-stu-id="ccf68-102">Single Sign-On: Event 11022</span></span>
## <a name="details"></a><span data-ttu-id="ccf68-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ccf68-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccf68-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ccf68-104">Product Name</span></span>|<span data-ttu-id="ccf68-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ccf68-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ccf68-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ccf68-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ccf68-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ccf68-107">Event ID</span></span>|<span data-ttu-id="ccf68-108">11022</span><span class="sxs-lookup"><span data-stu-id="ccf68-108">11022</span></span>|  
|<span data-ttu-id="ccf68-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ccf68-109">Event Source</span></span>|<span data-ttu-id="ccf68-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ccf68-110">ENTSSO</span></span>|  
|<span data-ttu-id="ccf68-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ccf68-111">Component</span></span>|<span data-ttu-id="ccf68-112">Néant</span><span class="sxs-lookup"><span data-stu-id="ccf68-112">N/A</span></span>|  
|<span data-ttu-id="ccf68-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ccf68-113">Symbolic Name</span></span>|<span data-ttu-id="ccf68-114">SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="ccf68-114">SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="ccf68-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ccf68-115">Message Text</span></span>|<span data-ttu-id="ccf68-116">Un changement de mot de passe externe aurait entraîné la modification d'un compte externe différent.%r</span><span class="sxs-lookup"><span data-stu-id="ccf68-116">An external password change would have caused a different external account to be changed.%r</span></span><br /><br /> <span data-ttu-id="ccf68-117">Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="ccf68-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="ccf68-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="ccf68-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="ccf68-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="ccf68-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="ccf68-120">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="ccf68-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="ccf68-121">Compte externe 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="ccf68-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="ccf68-122">Compte externe 2 : %5</span><span class="sxs-lookup"><span data-stu-id="ccf68-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ccf68-123">Explication</span><span class="sxs-lookup"><span data-stu-id="ccf68-123">Explanation</span></span>  
 <span data-ttu-id="ccf68-124">Il s'agit d'un message informatif indiquant l'échec du changement de mot de passe externe qui aurait entraîné la modification d'un compte externe différent.</span><span class="sxs-lookup"><span data-stu-id="ccf68-124">This is an informational message reporting the failure of an external password change which would have caused a different external account to be changed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ccf68-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ccf68-125">User Action</span></span>  
 <span data-ttu-id="ccf68-126">Bien qu'aucun changement n'ait été effectué (car ce système est configuré afin de ne pas autoriser les conflits de mappage), vous devez confirmer immédiatement que cette tentative a été effectuée, sachant que vous en étiez informé et que vous l'avez autorisée.</span><span class="sxs-lookup"><span data-stu-id="ccf68-126">Although no change was made (because this system is configured to not allow mapping conflicts) you should confirm immediately that this attempt was made with your knowledge and authorization.</span></span> <span data-ttu-id="ccf68-127">Dans ce cas, aucune action n'est requise.</span><span class="sxs-lookup"><span data-stu-id="ccf68-127">If so, no action is required.</span></span> <span data-ttu-id="ccf68-128">Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. </span><span class="sxs-lookup"><span data-stu-id="ccf68-128">If not, find out where the change initiated, and confirm that it was a location safely within the system.</span></span>