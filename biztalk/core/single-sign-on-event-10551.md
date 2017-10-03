---
title: "Single Sign-On : Événement 10551 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c4b315744749d232c30f4cc28c4d297a0f5243
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10551"></a><span data-ttu-id="7aff9-102">Single Sign-On : Événement 10551</span><span class="sxs-lookup"><span data-stu-id="7aff9-102">Single Sign-On: Event 10551</span></span>
## <a name="details"></a><span data-ttu-id="7aff9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7aff9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7aff9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7aff9-104">Product Name</span></span>|<span data-ttu-id="7aff9-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7aff9-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7aff9-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7aff9-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7aff9-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7aff9-107">Event ID</span></span>|<span data-ttu-id="7aff9-108">10551</span><span class="sxs-lookup"><span data-stu-id="7aff9-108">10551</span></span>|  
|<span data-ttu-id="7aff9-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7aff9-109">Event Source</span></span>|<span data-ttu-id="7aff9-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7aff9-110">ENTSSO</span></span>|  
|<span data-ttu-id="7aff9-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7aff9-111">Component</span></span>|<span data-ttu-id="7aff9-112">Néant</span><span class="sxs-lookup"><span data-stu-id="7aff9-112">N/A</span></span>|  
|<span data-ttu-id="7aff9-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7aff9-113">Symbolic Name</span></span>|<span data-ttu-id="7aff9-114">SSO_WARN_INVALID_USER</span><span class="sxs-lookup"><span data-stu-id="7aff9-114">SSO_WARN_INVALID_USER</span></span>|  
|<span data-ttu-id="7aff9-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7aff9-115">Message Text</span></span>|<span data-ttu-id="7aff9-116">Un mappage n'a pas pu être créé car l'utilisateur spécifié n'est pas valide pour cette application.%r</span><span class="sxs-lookup"><span data-stu-id="7aff9-116">A mapping could not be created because the specified user is not valid for this application.%r</span></span><br /><br /> <span data-ttu-id="7aff9-117">Nom de domaine : %1 %r</span><span class="sxs-lookup"><span data-stu-id="7aff9-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="7aff9-118">Nom d’utilisateur : %2 %r</span><span class="sxs-lookup"><span data-stu-id="7aff9-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="7aff9-119">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="7aff9-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="7aff9-120">Utilisateurs de l’application : %4</span><span class="sxs-lookup"><span data-stu-id="7aff9-120">Application Users: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7aff9-121">Explication</span><span class="sxs-lookup"><span data-stu-id="7aff9-121">Explanation</span></span>  
 <span data-ttu-id="7aff9-122">L'utilisateur spécifié n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="7aff9-122">The specified user is not valid.</span></span> <span data-ttu-id="7aff9-123">Il peut s'agir d'une erreur de frappe.</span><span class="sxs-lookup"><span data-stu-id="7aff9-123">This could be a typing error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7aff9-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7aff9-124">User Action</span></span>  
 <span data-ttu-id="7aff9-125">Vérifiez le nom d'utilisateur indiqué dans les informations de l'avertissement, vérifiez qu'il est correct, puis recréez le mappage.</span><span class="sxs-lookup"><span data-stu-id="7aff9-125">Check the User Name listed in the warning information, confirm that it is correct, and then create the mapping again.</span></span>