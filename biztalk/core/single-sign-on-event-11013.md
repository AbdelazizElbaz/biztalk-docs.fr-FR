---
title: "Single Sign-On : Événement 11013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 450836dc-ddeb-4423-9966-69ad173f2c87
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4765f542f7694b8ca5019af9effb8eace1ffbb60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11013"></a><span data-ttu-id="1d0c2-102">Single Sign-On : Événement 11013</span><span class="sxs-lookup"><span data-stu-id="1d0c2-102">Single Sign-On: Event 11013</span></span>
## <a name="details"></a><span data-ttu-id="1d0c2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1d0c2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d0c2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1d0c2-104">Product Name</span></span>|<span data-ttu-id="1d0c2-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1d0c2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1d0c2-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1d0c2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1d0c2-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1d0c2-107">Event ID</span></span>|<span data-ttu-id="1d0c2-108">11013</span><span class="sxs-lookup"><span data-stu-id="1d0c2-108">11013</span></span>|  
|<span data-ttu-id="1d0c2-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1d0c2-109">Event Source</span></span>|<span data-ttu-id="1d0c2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1d0c2-110">ENTSSO</span></span>|  
|<span data-ttu-id="1d0c2-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1d0c2-111">Component</span></span>|<span data-ttu-id="1d0c2-112">Néant</span><span class="sxs-lookup"><span data-stu-id="1d0c2-112">N/A</span></span>|  
|<span data-ttu-id="1d0c2-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1d0c2-113">Symbolic Name</span></span>|<span data-ttu-id="1d0c2-114">SSO_WARN_NOT_APP_USER</span><span class="sxs-lookup"><span data-stu-id="1d0c2-114">SSO_WARN_NOT_APP_USER</span></span>|  
|<span data-ttu-id="1d0c2-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1d0c2-115">Message Text</span></span>|<span data-ttu-id="1d0c2-116">L'utilisateur du client n'est pas membre du compte Utilisateurs d'applications.%r</span><span class="sxs-lookup"><span data-stu-id="1d0c2-116">Client user is not a member of the Application Users account.%r</span></span><br /><br /> <span data-ttu-id="1d0c2-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="1d0c2-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="1d0c2-118">L’utilisateur client : %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="1d0c2-118">Client User: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="1d0c2-119">Nom de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="1d0c2-119">Application Name: %4%r</span></span><br /><br /> <span data-ttu-id="1d0c2-120">Utilisateurs de l’application : %5</span><span class="sxs-lookup"><span data-stu-id="1d0c2-120">Application Users: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d0c2-121">Explication</span><span class="sxs-lookup"><span data-stu-id="1d0c2-121">Explanation</span></span>  
 <span data-ttu-id="1d0c2-122">L'utilisateur du client n'est pas membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-122">The client user is not a member of the Application Users account.</span></span> <span data-ttu-id="1d0c2-123">Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-123">This warning only appears when the audit levels are set to high.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d0c2-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1d0c2-124">User Action</span></span>  
 <span data-ttu-id="1d0c2-125">Pour remédier à cette situation, vous devez définir l'utilisateur du client comme membre du compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-125">To remedy the situation, you must make the client user a member of the Application Users account.</span></span> <span data-ttu-id="1d0c2-126">Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-126">To stop this warning from appearing in the future, you can lower the audit levels.</span></span>