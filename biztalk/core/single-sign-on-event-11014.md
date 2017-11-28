---
title: "Single Sign-On : Événement 11014 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71e4c9bd-8bda-46ca-9e76-f7b4fa033167
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 138a580122beb34b82f642dfa4d60aa6d422b445
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11014"></a><span data-ttu-id="7840c-102">Single Sign-On : Événement 11014</span><span class="sxs-lookup"><span data-stu-id="7840c-102">Single Sign-On: Event 11014</span></span>
## <a name="details"></a><span data-ttu-id="7840c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7840c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7840c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7840c-104">Product Name</span></span>|<span data-ttu-id="7840c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7840c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7840c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7840c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7840c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7840c-107">Event ID</span></span>|<span data-ttu-id="7840c-108">11014</span><span class="sxs-lookup"><span data-stu-id="7840c-108">11014</span></span>|  
|<span data-ttu-id="7840c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7840c-109">Event Source</span></span>|<span data-ttu-id="7840c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7840c-110">ENTSSO</span></span>|  
|<span data-ttu-id="7840c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="7840c-111">Component</span></span>|<span data-ttu-id="7840c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="7840c-112">N/A</span></span>|  
|<span data-ttu-id="7840c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7840c-113">Symbolic Name</span></span>|<span data-ttu-id="7840c-114">SSO_ERROR_ACCESS_CHECK</span><span class="sxs-lookup"><span data-stu-id="7840c-114">SSO_ERROR_ACCESS_CHECK</span></span>|  
|<span data-ttu-id="7840c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7840c-115">Message Text</span></span>|<span data-ttu-id="7840c-116">Échec du contrôle d'accès.%r</span><span class="sxs-lookup"><span data-stu-id="7840c-116">Access check failed.%r</span></span><br /><br /> <span data-ttu-id="7840c-117">L’utilisateur client : %1\\%2 %r</span><span class="sxs-lookup"><span data-stu-id="7840c-117">Client User: %1\\%2%r</span></span><br /><br /> <span data-ttu-id="7840c-118">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="7840c-118">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="7840c-119">Données supplémentaires : %4 %r</span><span class="sxs-lookup"><span data-stu-id="7840c-119">Additional Data: %4%r</span></span><br /><br /> <span data-ttu-id="7840c-120">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="7840c-120">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7840c-121">Explication</span><span class="sxs-lookup"><span data-stu-id="7840c-121">Explanation</span></span>  
 <span data-ttu-id="7840c-122">Le contrôle d'accès a échoué pour le client et l'application indiqués.</span><span class="sxs-lookup"><span data-stu-id="7840c-122">The access check failed for the client and application listed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7840c-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7840c-123">User Action</span></span>  
 <span data-ttu-id="7840c-124">Les autres informations doivent permettent de résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="7840c-124">The additional information should enable you to fix the problem.</span></span> <span data-ttu-id="7840c-125">Pour éviter cette erreur à l'avenir, vous pouvez abaisser le niveau d'audit.</span><span class="sxs-lookup"><span data-stu-id="7840c-125">To avoid this error in the future, you can also lower the audit level.</span></span>