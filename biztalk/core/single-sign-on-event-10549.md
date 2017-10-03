---
title: "Single Sign-On : Événement 10549 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a18eb63-700c-4f49-acc4-890abe2a00ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a59feecdcf5daeef7013dd99eca1e778d49278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10549"></a><span data-ttu-id="44651-102">Single Sign-On : Événement 10549</span><span class="sxs-lookup"><span data-stu-id="44651-102">Single Sign-On: Event 10549</span></span>
## <a name="details"></a><span data-ttu-id="44651-103">Détails</span><span class="sxs-lookup"><span data-stu-id="44651-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44651-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="44651-104">Product Name</span></span>|<span data-ttu-id="44651-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="44651-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="44651-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="44651-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="44651-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="44651-107">Event ID</span></span>|<span data-ttu-id="44651-108">10549</span><span class="sxs-lookup"><span data-stu-id="44651-108">10549</span></span>|  
|<span data-ttu-id="44651-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="44651-109">Event Source</span></span>|<span data-ttu-id="44651-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="44651-110">ENTSSO</span></span>|  
|<span data-ttu-id="44651-111">Composant</span><span class="sxs-lookup"><span data-stu-id="44651-111">Component</span></span>|<span data-ttu-id="44651-112">CO</span><span class="sxs-lookup"><span data-stu-id="44651-112">CO</span></span>|  
|<span data-ttu-id="44651-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="44651-113">Symbolic Name</span></span>|<span data-ttu-id="44651-114">SSO_ERROR_CREATE_DATABASE_FAILED</span><span class="sxs-lookup"><span data-stu-id="44651-114">SSO_ERROR_CREATE_DATABASE_FAILED</span></span>|  
|<span data-ttu-id="44651-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="44651-115">Message Text</span></span>|<span data-ttu-id="44651-116">Échec lors de la création et de l'initialisation de la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="44651-116">Creation and initialization of the SSO database failed.%r</span></span><br /><br /> <span data-ttu-id="44651-117">Nom du serveur SQL : %1 %r</span><span class="sxs-lookup"><span data-stu-id="44651-117">SQL Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="44651-118">Nom de base de données SSO : %2 %r</span><span class="sxs-lookup"><span data-stu-id="44651-118">SSO Database Name: %2%r</span></span><br /><br /> <span data-ttu-id="44651-119">L’utilisateur client : %3 %r</span><span class="sxs-lookup"><span data-stu-id="44651-119">Client User: %3%r</span></span><br /><br /> <span data-ttu-id="44651-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="44651-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="44651-121">Explication</span><span class="sxs-lookup"><span data-stu-id="44651-121">Explanation</span></span>  
 <span data-ttu-id="44651-122">Cette erreur indique que la création et l'initialisation de la base de données SSO a échoué.</span><span class="sxs-lookup"><span data-stu-id="44651-122">This Error indicates that creation and initialization of the SSO database failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="44651-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="44651-123">User Action</span></span>  
 <span data-ttu-id="44651-124">Pour résoudre cette erreur, entreprenez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="44651-124">To resolve this error do the following:</span></span>  
  
-   <span data-ttu-id="44651-125">Recherchez les messages associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="44651-125">Check the system and application event logs for associated messages.</span></span>  
  
-   <span data-ttu-id="44651-126">Réexécutez le programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="44651-126">Run Setup again.</span></span>  
  
 <span data-ttu-id="44651-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="44651-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="44651-128">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="44651-128">Installing SSO</span></span>](../core/installing-sso.md)