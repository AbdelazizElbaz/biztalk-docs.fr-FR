---
title: "Single Sign-On : Événement 11010 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22fcd9f3-83bb-44b0-88fc-197c2ef3e72d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f81bef87439c4607a32f2547d5bf44b19491140b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11010"></a><span data-ttu-id="db29b-102">Single Sign-On : Événement 11010</span><span class="sxs-lookup"><span data-stu-id="db29b-102">Single Sign-On: Event 11010</span></span>
## <a name="details"></a><span data-ttu-id="db29b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="db29b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db29b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="db29b-104">Product Name</span></span>|<span data-ttu-id="db29b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="db29b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="db29b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="db29b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="db29b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="db29b-107">Event ID</span></span>|<span data-ttu-id="db29b-108">11010</span><span class="sxs-lookup"><span data-stu-id="db29b-108">11010</span></span>|  
|<span data-ttu-id="db29b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="db29b-109">Event Source</span></span>|<span data-ttu-id="db29b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="db29b-110">ENTSSO</span></span>|  
|<span data-ttu-id="db29b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="db29b-111">Component</span></span>|<span data-ttu-id="db29b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="db29b-112">N/A</span></span>|  
|<span data-ttu-id="db29b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="db29b-113">Symbolic Name</span></span>|<span data-ttu-id="db29b-114">SSO_WARN_NOT_SSO_AFF_ADMIN</span><span class="sxs-lookup"><span data-stu-id="db29b-114">SSO_WARN_NOT_SSO_AFF_ADMIN</span></span>|  
|<span data-ttu-id="db29b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="db29b-115">Message Text</span></span>|<span data-ttu-id="db29b-116">L'utilisateur du client n'est pas membre du compte Administrateurs d'applications associées à authentification unique.%r</span><span class="sxs-lookup"><span data-stu-id="db29b-116">Client user is not a member of the SSO Affiliate Administrators account.%r</span></span><br /><br /> <span data-ttu-id="db29b-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="db29b-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="db29b-118">L’utilisateur client : %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="db29b-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="db29b-119">Les administrateurs d’applications associées SSO : %4</span><span class="sxs-lookup"><span data-stu-id="db29b-119">SSO Affiliate Administrators: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="db29b-120">Explication</span><span class="sxs-lookup"><span data-stu-id="db29b-120">Explanation</span></span>  
 <span data-ttu-id="db29b-121">L'utilisateur du client n'est pas membre du compte Administrateurs d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="db29b-121">The client user is not a member of the SSO Affiliate Administrators account.</span></span> <span data-ttu-id="db29b-122">Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.</span><span class="sxs-lookup"><span data-stu-id="db29b-122">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="db29b-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="db29b-123">User Action</span></span>  
 <span data-ttu-id="db29b-124">Pour remédier à cette situation, vous devez définir l'utilisateur du client comme membre du compte Administrateurs d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="db29b-124">To remedy the situation, you must make the client user a member of the SSO Affiliate Administrators account.</span></span> <span data-ttu-id="db29b-125">Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.</span><span class="sxs-lookup"><span data-stu-id="db29b-125">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>