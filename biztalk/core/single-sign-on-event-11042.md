---
title: "Single Sign-On : Événement 11042 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1927bb5-a400-4e3a-8f80-95ef5693216c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da20346fbf2f73ac2ab64db3c9137394aa5bd366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11042"></a><span data-ttu-id="e4a0c-102">Single Sign-On : Événement 11042</span><span class="sxs-lookup"><span data-stu-id="e4a0c-102">Single Sign-On: Event 11042</span></span>
## <a name="details"></a><span data-ttu-id="e4a0c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e4a0c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4a0c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e4a0c-104">Product Name</span></span>|<span data-ttu-id="e4a0c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e4a0c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e4a0c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e4a0c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e4a0c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e4a0c-107">Event ID</span></span>|<span data-ttu-id="e4a0c-108">11042</span><span class="sxs-lookup"><span data-stu-id="e4a0c-108">11042</span></span>|  
|<span data-ttu-id="e4a0c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e4a0c-109">Event Source</span></span>|<span data-ttu-id="e4a0c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e4a0c-110">ENTSSO</span></span>|  
|<span data-ttu-id="e4a0c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e4a0c-111">Component</span></span>|<span data-ttu-id="e4a0c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="e4a0c-112">N/A</span></span>|  
|<span data-ttu-id="e4a0c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e4a0c-113">Symbolic Name</span></span>|<span data-ttu-id="e4a0c-114">SSO_WARN_ACCESS_DENIED_ACCOUNTS</span><span class="sxs-lookup"><span data-stu-id="e4a0c-114">SSO_WARN_ACCESS_DENIED_ACCOUNTS</span></span>|  
|<span data-ttu-id="e4a0c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e4a0c-115">Message Text</span></span>|<span data-ttu-id="e4a0c-116">Accès refusé.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-116">Access denied.</span></span><br /><br /> <span data-ttu-id="e4a0c-117">L'utilisateur client doit être membre de l'un des comptes suivants pour exécuter cette fonction.%r</span><span class="sxs-lookup"><span data-stu-id="e4a0c-117">The client user must be a member of one of the following accounts to perform this function.%r</span></span><br /><br /> <span data-ttu-id="e4a0c-118">Les administrateurs de l’authentification unique : %1 %r</span><span class="sxs-lookup"><span data-stu-id="e4a0c-118">SSO Administrators: %1%r</span></span><br /><br /> <span data-ttu-id="e4a0c-119">Administrateurs d’applications associées SSO : %2 %r</span><span class="sxs-lookup"><span data-stu-id="e4a0c-119">SSO Affiliate Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="e4a0c-120">Administrateurs d’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="e4a0c-120">Application Administrators: %3%r</span></span><br /><br /> <span data-ttu-id="e4a0c-121">Utilisateurs de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="e4a0c-121">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="e4a0c-122">Données supplémentaires : %5</span><span class="sxs-lookup"><span data-stu-id="e4a0c-122">Additional Data: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e4a0c-123">Explication</span><span class="sxs-lookup"><span data-stu-id="e4a0c-123">Explanation</span></span>  
 <span data-ttu-id="e4a0c-124">L'utilisateur client doit être membre de l'un des comptes répertoriés dans l'avertissement pour exécuter cette fonction.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-124">The client user must be a member of one of the accounts listed in the warning to perform this function.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e4a0c-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e4a0c-125">User Action</span></span>  
 <span data-ttu-id="e4a0c-126">Vous devez souscrire à l'un de ces comptes pour exécuter cette fonction.</span><span class="sxs-lookup"><span data-stu-id="e4a0c-126">You must join one of the accounts to perform this function.</span></span>