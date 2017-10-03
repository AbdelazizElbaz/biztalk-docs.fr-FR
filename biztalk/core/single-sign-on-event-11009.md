---
title: "Single Sign-On : Événement 11009 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5f06f8c-1614-4538-83e6-689657135776
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99308e7a9e709cff5c0e1e15963eeb4769c00f05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11009"></a><span data-ttu-id="db9d1-102">Single Sign-On : Événement 11009</span><span class="sxs-lookup"><span data-stu-id="db9d1-102">Single Sign-On: Event 11009</span></span>
## <a name="details"></a><span data-ttu-id="db9d1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="db9d1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db9d1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="db9d1-104">Product Name</span></span>|<span data-ttu-id="db9d1-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="db9d1-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="db9d1-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="db9d1-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="db9d1-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="db9d1-107">Event ID</span></span>|<span data-ttu-id="db9d1-108">11009</span><span class="sxs-lookup"><span data-stu-id="db9d1-108">11009</span></span>|  
|<span data-ttu-id="db9d1-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="db9d1-109">Event Source</span></span>|<span data-ttu-id="db9d1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="db9d1-110">ENTSSO</span></span>|  
|<span data-ttu-id="db9d1-111">Composant</span><span class="sxs-lookup"><span data-stu-id="db9d1-111">Component</span></span>|<span data-ttu-id="db9d1-112">Néant</span><span class="sxs-lookup"><span data-stu-id="db9d1-112">N/A</span></span>|  
|<span data-ttu-id="db9d1-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="db9d1-113">Symbolic Name</span></span>|<span data-ttu-id="db9d1-114">SSO_WARN_NOT_SSO_ADMIN</span><span class="sxs-lookup"><span data-stu-id="db9d1-114">SSO_WARN_NOT_SSO_ADMIN</span></span>|  
|<span data-ttu-id="db9d1-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="db9d1-115">Message Text</span></span>|<span data-ttu-id="db9d1-116">L'utilisateur client ne correspond pas à un membre du compte Administrateurs SSO.%r</span><span class="sxs-lookup"><span data-stu-id="db9d1-116">Client user is not a member of the SSO Administrators account.%r</span></span><br /><br /> <span data-ttu-id="db9d1-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="db9d1-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="db9d1-118">L’utilisateur client : %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="db9d1-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="db9d1-119">Les administrateurs SSO : %4</span><span class="sxs-lookup"><span data-stu-id="db9d1-119">SSO Administrators: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="db9d1-120">Explication</span><span class="sxs-lookup"><span data-stu-id="db9d1-120">Explanation</span></span>  
 <span data-ttu-id="db9d1-121">L'utilisateur client ne correspond pas à un membre du compte Administrateurs SSO.</span><span class="sxs-lookup"><span data-stu-id="db9d1-121">The client user is not a member of the SSO Administrators account.</span></span> <span data-ttu-id="db9d1-122">Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.</span><span class="sxs-lookup"><span data-stu-id="db9d1-122">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="db9d1-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="db9d1-123">User Action</span></span>  
 <span data-ttu-id="db9d1-124">Pour résoudre cette situation, l'utilisateur client doit être membre du compte Administrateurs SSO.</span><span class="sxs-lookup"><span data-stu-id="db9d1-124">To remedy the situation, you must make the client user a member of the SSO Administrators account.</span></span> <span data-ttu-id="db9d1-125">Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.</span><span class="sxs-lookup"><span data-stu-id="db9d1-125">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>