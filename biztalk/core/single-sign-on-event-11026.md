---
title: "Single Sign-On : Événement 11026 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e39b252d-2ed0-4006-aac2-4dce6504afb2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecee6d3c3e6dcf01b8489c4041f4aab717eba585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11026"></a><span data-ttu-id="ba745-102">Single Sign-On : Événement 11026</span><span class="sxs-lookup"><span data-stu-id="ba745-102">Single Sign-On: Event 11026</span></span>
## <a name="details"></a><span data-ttu-id="ba745-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ba745-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba745-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ba745-104">Product Name</span></span>|<span data-ttu-id="ba745-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ba745-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ba745-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ba745-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ba745-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ba745-107">Event ID</span></span>|<span data-ttu-id="ba745-108">11026</span><span class="sxs-lookup"><span data-stu-id="ba745-108">11026</span></span>|  
|<span data-ttu-id="ba745-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ba745-109">Event Source</span></span>|<span data-ttu-id="ba745-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ba745-110">ENTSSO</span></span>|  
|<span data-ttu-id="ba745-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ba745-111">Component</span></span>|<span data-ttu-id="ba745-112">Néant</span><span class="sxs-lookup"><span data-stu-id="ba745-112">N/A</span></span>|  
|<span data-ttu-id="ba745-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ba745-113">Symbolic Name</span></span>|<span data-ttu-id="ba745-114">SSO_WARN_EXISTING_GROUP_MAPPING</span><span class="sxs-lookup"><span data-stu-id="ba745-114">SSO_WARN_EXISTING_GROUP_MAPPING</span></span>|  
|<span data-ttu-id="ba745-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ba745-115">Message Text</span></span>|<span data-ttu-id="ba745-116">Le nouveau mappage de groupe n'a pas pu être créé en raison d'un conflit avec un nom existant.</span><span class="sxs-lookup"><span data-stu-id="ba745-116">A new group mapping could not be created because there is a conflict with an existing mapping.</span></span> <span data-ttu-id="ba745-117">Supprimez le mappage existant, puis réessayez.%r</span><span class="sxs-lookup"><span data-stu-id="ba745-117">Please delete the existing mapping and try again.%r</span></span><br /><br /> <span data-ttu-id="ba745-118">Mappage existant : %1 %r</span><span class="sxs-lookup"><span data-stu-id="ba745-118">Existing Mapping: %1%r</span></span><br /><br /> <span data-ttu-id="ba745-119">Nouveau mappage : %2 %r</span><span class="sxs-lookup"><span data-stu-id="ba745-119">New Mapping: %2%r</span></span><br /><br /> <span data-ttu-id="ba745-120">Compte externe : %3 %r</span><span class="sxs-lookup"><span data-stu-id="ba745-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="ba745-121">Nom de l’application : %4</span><span class="sxs-lookup"><span data-stu-id="ba745-121">Application Name: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ba745-122">Explication</span><span class="sxs-lookup"><span data-stu-id="ba745-122">Explanation</span></span>  
 <span data-ttu-id="ba745-123">Ceci est probablement dû au fait que votre système utilise une ancienne version de l'authentification unique de l'entreprise, ainsi que des applications de groupe anciennes.</span><span class="sxs-lookup"><span data-stu-id="ba745-123">The most likely cause is that your system is using an old version of Enterprise Single Sign-On, and old group applications.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ba745-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ba745-124">User Action</span></span>  
 <span data-ttu-id="ba745-125">Supprimez puis recréez le mappage, comme indiqué dans l'avertissement.</span><span class="sxs-lookup"><span data-stu-id="ba745-125">Delete and recreate the mapping as suggested in the warning.</span></span> <span data-ttu-id="ba745-126">En cas d'échec, vous devrez peut-être mettre à niveau vers une version plus récente de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ba745-126">If this fails, you may need to upgrade to a more recent version of Enterprise Single Sign-On.</span></span>