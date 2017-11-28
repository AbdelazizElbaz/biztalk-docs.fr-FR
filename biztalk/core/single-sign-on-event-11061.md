---
title: "Single Sign-On : Événement 11061 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52fb18e2-4482-4cdb-b8ed-d579a95acd7c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86ad25248952697e27fc732ddead6732065acf7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11061"></a><span data-ttu-id="9cb70-102">Single Sign-On : Événement 11061</span><span class="sxs-lookup"><span data-stu-id="9cb70-102">Single Sign-On: Event 11061</span></span>
## <a name="details"></a><span data-ttu-id="9cb70-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9cb70-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cb70-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9cb70-104">Product Name</span></span>|<span data-ttu-id="9cb70-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9cb70-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9cb70-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9cb70-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9cb70-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9cb70-107">Event ID</span></span>|<span data-ttu-id="9cb70-108">11061</span><span class="sxs-lookup"><span data-stu-id="9cb70-108">11061</span></span>|  
|<span data-ttu-id="9cb70-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9cb70-109">Event Source</span></span>|<span data-ttu-id="9cb70-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9cb70-110">ENTSSO</span></span>|  
|<span data-ttu-id="9cb70-111">Composant</span><span class="sxs-lookup"><span data-stu-id="9cb70-111">Component</span></span>|<span data-ttu-id="9cb70-112">Néant</span><span class="sxs-lookup"><span data-stu-id="9cb70-112">N/A</span></span>|  
|<span data-ttu-id="9cb70-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9cb70-113">Symbolic Name</span></span>|<span data-ttu-id="9cb70-114">SSO_WARN_BAD_PASSWORD_FILTER</span><span class="sxs-lookup"><span data-stu-id="9cb70-114">SSO_WARN_BAD_PASSWORD_FILTER</span></span>|  
|<span data-ttu-id="9cb70-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9cb70-115">Message Text</span></span>|<span data-ttu-id="9cb70-116">La chaîne du filtre de mot de passe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="9cb70-116">The password filter string is not valid.</span></span> <span data-ttu-id="9cb70-117">Aucun filtre de mot de passe ne sera utilisé.%r</span><span class="sxs-lookup"><span data-stu-id="9cb70-117">No password filter will be used.%r</span></span><br /><br /> <span data-ttu-id="9cb70-118">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="9cb70-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="9cb70-119">Chaîne de filtre de mot de passe : %2 %r</span><span class="sxs-lookup"><span data-stu-id="9cb70-119">Password Filter String: %2%r</span></span><br /><br /> <span data-ttu-id="9cb70-120">Nombre de jetons traités : %3 %r</span><span class="sxs-lookup"><span data-stu-id="9cb70-120">Number Of Tokens Processed: %3%r</span></span><br /><br /> <span data-ttu-id="9cb70-121">Données supplémentaires : %4 %r</span><span class="sxs-lookup"><span data-stu-id="9cb70-121">Additional Data: %4%r</span></span><br /><br /> <span data-ttu-id="9cb70-122">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="9cb70-122">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9cb70-123">Explication</span><span class="sxs-lookup"><span data-stu-id="9cb70-123">Explanation</span></span>  
 <span data-ttu-id="9cb70-124">Un filtre de mot de passe non valide a été créé manuellement.</span><span class="sxs-lookup"><span data-stu-id="9cb70-124">An invalid password filter has been created manually.</span></span> <span data-ttu-id="9cb70-125">Une erreur est survenue au cours de ce processus (consultez la chaîne du filtre de mot de passe dans l'avertissement pour déterminer l'emplacement de l'erreur).</span><span class="sxs-lookup"><span data-stu-id="9cb70-125">At some point in this process an error was introduced (see Password Filter String in the warning text for the location of the error).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9cb70-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9cb70-126">User Action</span></span>  
 <span data-ttu-id="9cb70-127">Pour créer le filtre de mot de passe à l’aide de l’Assistant Création d’un filtre de mot de passe, consultez [comment utiliser des filtres de mot de passe](../core/how-to-use-password-filters.md).</span><span class="sxs-lookup"><span data-stu-id="9cb70-127">To create the Password Filter using the Create Password Filter Wizard, see [How to Use Password Filters](../core/how-to-use-password-filters.md).</span></span>