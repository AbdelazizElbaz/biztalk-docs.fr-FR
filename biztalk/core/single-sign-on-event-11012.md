---
title: "Single Sign-On : Événement 11012 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 252bedc8-8dc3-4962-b078-465f9b064ead
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7c559f7416e0f882b4487629033e5b059802d20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11012"></a><span data-ttu-id="95ee7-102">Single Sign-On : Événement 11012</span><span class="sxs-lookup"><span data-stu-id="95ee7-102">Single Sign-On: Event 11012</span></span>
## <a name="details"></a><span data-ttu-id="95ee7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="95ee7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95ee7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="95ee7-104">Product Name</span></span>|<span data-ttu-id="95ee7-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="95ee7-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="95ee7-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="95ee7-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="95ee7-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="95ee7-107">Event ID</span></span>|<span data-ttu-id="95ee7-108">11012</span><span class="sxs-lookup"><span data-stu-id="95ee7-108">11012</span></span>|  
|<span data-ttu-id="95ee7-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="95ee7-109">Event Source</span></span>|<span data-ttu-id="95ee7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="95ee7-110">ENTSSO</span></span>|  
|<span data-ttu-id="95ee7-111">Composant</span><span class="sxs-lookup"><span data-stu-id="95ee7-111">Component</span></span>|<span data-ttu-id="95ee7-112">Néant</span><span class="sxs-lookup"><span data-stu-id="95ee7-112">N/A</span></span>|  
|<span data-ttu-id="95ee7-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="95ee7-113">Symbolic Name</span></span>|<span data-ttu-id="95ee7-114">SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME</span><span class="sxs-lookup"><span data-stu-id="95ee7-114">SSO_WARN_NOT_APP_ADMIN_ADMIN_SAME</span></span>|  
|<span data-ttu-id="95ee7-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="95ee7-115">Message Text</span></span>|<span data-ttu-id="95ee7-116">L'utilisateur client ne correspond pas à un membre du compte Administrateurs d'application.%r</span><span class="sxs-lookup"><span data-stu-id="95ee7-116">Client user is not a member of the Application Administrators account.%r</span></span><br /><br /> <span data-ttu-id="95ee7-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="95ee7-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="95ee7-118">L’utilisateur client : %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="95ee7-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="95ee7-119">Nom de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="95ee7-119">Application Name: %4%r</span></span><br /><br /> <span data-ttu-id="95ee7-120">Administrateurs de l’application : %5</span><span class="sxs-lookup"><span data-stu-id="95ee7-120">Application Administrators: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95ee7-121">Explication</span><span class="sxs-lookup"><span data-stu-id="95ee7-121">Explanation</span></span>  
 <span data-ttu-id="95ee7-122">L'utilisateur client ne correspond pas à un membre du compte Administrateurs d'application.</span><span class="sxs-lookup"><span data-stu-id="95ee7-122">The client user is not a member of the Application Administrators account.</span></span> <span data-ttu-id="95ee7-123">Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.</span><span class="sxs-lookup"><span data-stu-id="95ee7-123">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95ee7-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="95ee7-124">User Action</span></span>  
 <span data-ttu-id="95ee7-125">Pour résoudre cette situation, l'utilisateur client doit être membre du compte Administrateurs d'application.</span><span class="sxs-lookup"><span data-stu-id="95ee7-125">To remedy the situation, you must make the client user a member of the Application Administrators account.</span></span> <span data-ttu-id="95ee7-126">Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.</span><span class="sxs-lookup"><span data-stu-id="95ee7-126">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>