---
title: "Single Sign-On : Événement 11037 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b523ff56-112e-4798-97d2-b1b19e130ec7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 245b4af07a88c4015048db0ea20fe04b714d0ed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11037"></a><span data-ttu-id="a893b-102">Single Sign-On : Événement 11037</span><span class="sxs-lookup"><span data-stu-id="a893b-102">Single Sign-On: Event 11037</span></span>
## <a name="details"></a><span data-ttu-id="a893b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a893b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a893b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a893b-104">Product Name</span></span>|<span data-ttu-id="a893b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a893b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a893b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a893b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a893b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a893b-107">Event ID</span></span>|<span data-ttu-id="a893b-108">11037</span><span class="sxs-lookup"><span data-stu-id="a893b-108">11037</span></span>|  
|<span data-ttu-id="a893b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a893b-109">Event Source</span></span>|<span data-ttu-id="a893b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a893b-110">ENTSSO</span></span>|  
|<span data-ttu-id="a893b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a893b-111">Component</span></span>|<span data-ttu-id="a893b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a893b-112">N/A</span></span>|  
|<span data-ttu-id="a893b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a893b-113">Symbolic Name</span></span>|<span data-ttu-id="a893b-114">SSO_INFO_PS_MAPPING_INVALID</span><span class="sxs-lookup"><span data-stu-id="a893b-114">SSO_INFO_PS_MAPPING_INVALID</span></span>|  
|<span data-ttu-id="a893b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a893b-115">Message Text</span></span>|<span data-ttu-id="a893b-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="a893b-116">External password change.</span></span> <span data-ttu-id="a893b-117">Le mot de passe n'a pas été modifié pour le compte externe, car le mappage n'est plus valide.%r</span><span class="sxs-lookup"><span data-stu-id="a893b-117">The password was not changed for the external account because the mapping is no longer valid.%r</span></span><br /><br /> <span data-ttu-id="a893b-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="a893b-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a893b-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="a893b-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="a893b-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="a893b-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="a893b-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="a893b-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a893b-122">Explication</span><span class="sxs-lookup"><span data-stu-id="a893b-122">Explanation</span></span>  
 <span data-ttu-id="a893b-123">Le mappage ne fait plus partie du groupe Utilisateurs d'applications.</span><span class="sxs-lookup"><span data-stu-id="a893b-123">The mapping is no longer a part of the Application Users group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a893b-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a893b-124">User Action</span></span>  
 <span data-ttu-id="a893b-125">Ce message indique le nom du compte externe et de l'application.</span><span class="sxs-lookup"><span data-stu-id="a893b-125">The message lists the name of the external account and application.</span></span> <span data-ttu-id="a893b-126">Vous pouvez vous en servir pour déterminer la raison pour  laquelle le mappage n'est plus valide.</span><span class="sxs-lookup"><span data-stu-id="a893b-126">You can use this information to find out why the mapping is no longer valid.</span></span>