---
title: "Single Sign-On : Événement 11031 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aec5ae3a128da8a13379c574ddd2dba3c1065f79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11031"></a><span data-ttu-id="4a4f3-102">Single Sign-On : Événement 11031</span><span class="sxs-lookup"><span data-stu-id="4a4f3-102">Single Sign-On: Event 11031</span></span>
## <a name="details"></a><span data-ttu-id="4a4f3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4a4f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a4f3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4a4f3-104">Product Name</span></span>|<span data-ttu-id="4a4f3-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="4a4f3-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="4a4f3-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4a4f3-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="4a4f3-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4a4f3-107">Event ID</span></span>|<span data-ttu-id="4a4f3-108">11031</span><span class="sxs-lookup"><span data-stu-id="4a4f3-108">11031</span></span>|  
|<span data-ttu-id="4a4f3-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4a4f3-109">Event Source</span></span>|<span data-ttu-id="4a4f3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4a4f3-110">ENTSSO</span></span>|  
|<span data-ttu-id="4a4f3-111">Composant</span><span class="sxs-lookup"><span data-stu-id="4a4f3-111">Component</span></span>|<span data-ttu-id="4a4f3-112">Néant</span><span class="sxs-lookup"><span data-stu-id="4a4f3-112">N/A</span></span>|  
|<span data-ttu-id="4a4f3-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4a4f3-113">Symbolic Name</span></span>|<span data-ttu-id="4a4f3-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span><span class="sxs-lookup"><span data-stu-id="4a4f3-114">SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING</span></span>|  
|<span data-ttu-id="4a4f3-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4a4f3-115">Message Text</span></span>|<span data-ttu-id="4a4f3-116">Changement du mot de passe Windows.</span><span class="sxs-lookup"><span data-stu-id="4a4f3-116">Windows password change.</span></span> <span data-ttu-id="4a4f3-117">Le mappage détecté pour ce compte Windows a été ignoré car il est n'est plus valide.%r</span><span class="sxs-lookup"><span data-stu-id="4a4f3-117">A mapping for this Windows account has been detected but ignored because it is no longer valid.%r</span></span><br /><br /> <span data-ttu-id="4a4f3-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="4a4f3-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="4a4f3-119">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="4a4f3-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="4a4f3-120">Application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="4a4f3-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="4a4f3-121">Compte externe : %4 %r</span><span class="sxs-lookup"><span data-stu-id="4a4f3-121">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="4a4f3-122">Utilisateur client : %5</span><span class="sxs-lookup"><span data-stu-id="4a4f3-122">Client User: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4a4f3-123">Explication</span><span class="sxs-lookup"><span data-stu-id="4a4f3-123">Explanation</span></span>  
 <span data-ttu-id="4a4f3-124">Il se peut que le compte Windows existe et soit valide, mais ne figure pas dans le compte Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="4a4f3-124">It may be that the Windows account exists and is valid, but is not in the Application Users account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4a4f3-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4a4f3-125">User Action</span></span>  
 <span data-ttu-id="4a4f3-126">Supprimez le mappage, puis tentez de le recréer.</span><span class="sxs-lookup"><span data-stu-id="4a4f3-126">Delete the mapping and try to recreate it.</span></span>