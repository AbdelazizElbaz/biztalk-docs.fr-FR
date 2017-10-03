---
title: "Single Sign-On : Événement 10601 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2624025e-b7a8-43b9-aa7e-6811a2fc3278
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c34711cf02711ec0ee2a259cc7d8f8fca9c87b7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10601"></a><span data-ttu-id="fa3ef-102">Single Sign-On : Événement 10601</span><span class="sxs-lookup"><span data-stu-id="fa3ef-102">Single Sign-On: Event 10601</span></span>
## <a name="details"></a><span data-ttu-id="fa3ef-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fa3ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa3ef-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fa3ef-104">Product Name</span></span>|<span data-ttu-id="fa3ef-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="fa3ef-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fa3ef-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fa3ef-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fa3ef-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fa3ef-107">Event ID</span></span>|<span data-ttu-id="fa3ef-108">10601</span><span class="sxs-lookup"><span data-stu-id="fa3ef-108">10601</span></span>|  
|<span data-ttu-id="fa3ef-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fa3ef-109">Event Source</span></span>|<span data-ttu-id="fa3ef-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fa3ef-110">ENTSSO</span></span>|  
|<span data-ttu-id="fa3ef-111">Composant</span><span class="sxs-lookup"><span data-stu-id="fa3ef-111">Component</span></span>|<span data-ttu-id="fa3ef-112">Néant</span><span class="sxs-lookup"><span data-stu-id="fa3ef-112">N/A</span></span>|  
|<span data-ttu-id="fa3ef-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fa3ef-113">Symbolic Name</span></span>|<span data-ttu-id="fa3ef-114">SSO_WARN_INVALID_FLAGS</span><span class="sxs-lookup"><span data-stu-id="fa3ef-114">SSO_WARN_INVALID_FLAGS</span></span>|  
|<span data-ttu-id="fa3ef-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fa3ef-115">Message Text</span></span>|<span data-ttu-id="fa3ef-116">Les indicateurs spécifiés ne sont pas valides pour la création de ce type d'application.</span><span class="sxs-lookup"><span data-stu-id="fa3ef-116">The specified flags are not valid for creating this type of application.</span></span><br /><br /> <span data-ttu-id="fa3ef-117">Pour plus d'informations, reportez-vous à la documentation.%r</span><span class="sxs-lookup"><span data-stu-id="fa3ef-117">See documentation for details.%r</span></span><br /><br /> <span data-ttu-id="fa3ef-118">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="fa3ef-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="fa3ef-119">Les indicateurs spécifiés : %2 %r</span><span class="sxs-lookup"><span data-stu-id="fa3ef-119">Specified Flags: %2%r</span></span><br /><br /> <span data-ttu-id="fa3ef-120">Les indicateurs autorisés : %3 %r</span><span class="sxs-lookup"><span data-stu-id="fa3ef-120">Allowed Flags: %3%r</span></span><br /><br /> <span data-ttu-id="fa3ef-121">Indicateurs non autorisés : %4</span><span class="sxs-lookup"><span data-stu-id="fa3ef-121">Not Allowed Flags: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa3ef-122">Explication</span><span class="sxs-lookup"><span data-stu-id="fa3ef-122">Explanation</span></span>  
 <span data-ttu-id="fa3ef-123">Les indicateurs spécifiés ne sont pas valides pour la création de ce type d'application.</span><span class="sxs-lookup"><span data-stu-id="fa3ef-123">The specified flags are not valid for creating this type of application.</span></span> <span data-ttu-id="fa3ef-124">L'avertissement indique l'application concernée, ainsi que les indicateurs autorisés et non autorisés.</span><span class="sxs-lookup"><span data-stu-id="fa3ef-124">The warning lists the application concerned, as well as the flags that are allowed and those that are not.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa3ef-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fa3ef-125">User Action</span></span>  
 <span data-ttu-id="fa3ef-126">Recréez l'application en suivant les instructions du message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="fa3ef-126">Recreate the application following the guidelines outlined in the warning message.</span></span>