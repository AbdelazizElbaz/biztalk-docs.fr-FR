---
title: "Single Sign-On : Événement 10558 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84637b67-09df-4c1e-b9f2-85a738ba0d7a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2ee5c21bdf90e6aedcdbe2ac83e0e51a7f48f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10558"></a><span data-ttu-id="757e5-102">Single Sign-On : Événement 10558</span><span class="sxs-lookup"><span data-stu-id="757e5-102">Single Sign-On: Event 10558</span></span>
## <a name="details"></a><span data-ttu-id="757e5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="757e5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="757e5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="757e5-104">Product Name</span></span>|<span data-ttu-id="757e5-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="757e5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="757e5-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="757e5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="757e5-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="757e5-107">Event ID</span></span>|<span data-ttu-id="757e5-108">10558</span><span class="sxs-lookup"><span data-stu-id="757e5-108">10558</span></span>|  
|<span data-ttu-id="757e5-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="757e5-109">Event Source</span></span>|<span data-ttu-id="757e5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="757e5-110">ENTSSO</span></span>|  
|<span data-ttu-id="757e5-111">Composant</span><span class="sxs-lookup"><span data-stu-id="757e5-111">Component</span></span>|<span data-ttu-id="757e5-112">Néant</span><span class="sxs-lookup"><span data-stu-id="757e5-112">N/A</span></span>|  
|<span data-ttu-id="757e5-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="757e5-113">Symbolic Name</span></span>|<span data-ttu-id="757e5-114">SSO_WARN_USER_OWN_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="757e5-114">SSO_WARN_USER_OWN_MAPPINGS</span></span>|  
|<span data-ttu-id="757e5-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="757e5-115">Message Text</span></span>|<span data-ttu-id="757e5-116">Les utilisateurs d'applications sont uniquement autorisés à contrôler leurs propres mappages.%r</span><span class="sxs-lookup"><span data-stu-id="757e5-116">Application Users are only allowed to control their own mappings.%r</span></span><br /><br /> <span data-ttu-id="757e5-117">Nom de domaine : %1 %r</span><span class="sxs-lookup"><span data-stu-id="757e5-117">Domain Name: %1%r</span></span><br /><br /> <span data-ttu-id="757e5-118">Nom d’utilisateur : %2 %r</span><span class="sxs-lookup"><span data-stu-id="757e5-118">User Name: %2%r</span></span><br /><br /> <span data-ttu-id="757e5-119">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="757e5-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="757e5-120">Utilisateur client : %4</span><span class="sxs-lookup"><span data-stu-id="757e5-120">Client User: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="757e5-121">Explication</span><span class="sxs-lookup"><span data-stu-id="757e5-121">Explanation</span></span>  
 <span data-ttu-id="757e5-122">Un utilisateur d'applications a tenté de contrôler les mappages d'un autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="757e5-122">An attempt was made by an Application User to control the mappings of a different user.</span></span> <span data-ttu-id="757e5-123">Cela n'est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="757e5-123">This is not allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="757e5-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="757e5-124">User Action</span></span>  
 <span data-ttu-id="757e5-125">Les mappages peuvent uniquement être contrôlés par les utilisateurs d'applications associés à ces mappages spécifiques.</span><span class="sxs-lookup"><span data-stu-id="757e5-125">Mappings can only be controlled by the Application Users for those specific mappings.</span></span>