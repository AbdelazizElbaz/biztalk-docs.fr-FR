---
title: "Single Sign-On : Événement 11019 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec07b00-d567-4518-89eb-340e4f92429b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4b2d2494a404566c7350a9e9988d429a3e335c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11019"></a><span data-ttu-id="1b88a-102">Single Sign-On : Événement 11019</span><span class="sxs-lookup"><span data-stu-id="1b88a-102">Single Sign-On: Event 11019</span></span>
## <a name="details"></a><span data-ttu-id="1b88a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1b88a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b88a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1b88a-104">Product Name</span></span>|<span data-ttu-id="1b88a-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1b88a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1b88a-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1b88a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1b88a-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1b88a-107">Event ID</span></span>|<span data-ttu-id="1b88a-108">11019</span><span class="sxs-lookup"><span data-stu-id="1b88a-108">11019</span></span>|  
|<span data-ttu-id="1b88a-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1b88a-109">Event Source</span></span>|<span data-ttu-id="1b88a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1b88a-110">ENTSSO</span></span>|  
|<span data-ttu-id="1b88a-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1b88a-111">Component</span></span>|<span data-ttu-id="1b88a-112">Néant</span><span class="sxs-lookup"><span data-stu-id="1b88a-112">N/A</span></span>|  
|<span data-ttu-id="1b88a-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1b88a-113">Symbolic Name</span></span>|<span data-ttu-id="1b88a-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED</span><span class="sxs-lookup"><span data-stu-id="1b88a-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED</span></span>|  
|<span data-ttu-id="1b88a-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1b88a-115">Message Text</span></span>|<span data-ttu-id="1b88a-116">Le mappage n'est pas valide car le compte Windows ne figure pas dans le compte Utilisateurs d'applications pour l'application.</span><span class="sxs-lookup"><span data-stu-id="1b88a-116">The mapping is not valid because the Windows account is not in the Application Users account for the application.</span></span> <span data-ttu-id="1b88a-117">Échec lors de la suppression du mappage.</span><span class="sxs-lookup"><span data-stu-id="1b88a-117">Failed to delete the mapping.</span></span> <span data-ttu-id="1b88a-118">Le mappage sera ignoré.%r</span><span class="sxs-lookup"><span data-stu-id="1b88a-118">The mapping will be ignored.%r</span></span><br /><br /> <span data-ttu-id="1b88a-119">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="1b88a-119">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="1b88a-120">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="1b88a-120">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="1b88a-121">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="1b88a-121">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="1b88a-122">Utilisateurs de l’application : %4 %r</span><span class="sxs-lookup"><span data-stu-id="1b88a-122">Application Users: %4%r</span></span><br /><br /> <span data-ttu-id="1b88a-123">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="1b88a-123">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b88a-124">Explication</span><span class="sxs-lookup"><span data-stu-id="1b88a-124">Explanation</span></span>  
 <span data-ttu-id="1b88a-125">Le compte Windows spécifié n'a jamais fait partie du compte Utilisateurs d'applications, ou il en a fait partie avant d'être modifié ou supprimé.</span><span class="sxs-lookup"><span data-stu-id="1b88a-125">Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed.</span></span> <span data-ttu-id="1b88a-126">Le mappage n'a pas été supprimé.</span><span class="sxs-lookup"><span data-stu-id="1b88a-126">The mapping has not been deleted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b88a-127">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1b88a-127">User Action</span></span>  
 <span data-ttu-id="1b88a-128">Consultez les informations du compte de synchronisation de mot de passe pour votre système et assurez-vous qu'elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="1b88a-128">Check the password sync account information for your system, and make sure your information is valid.</span></span> <span data-ttu-id="1b88a-129">Recréez ensuite le mappage.</span><span class="sxs-lookup"><span data-stu-id="1b88a-129">Then recreate the mapping.</span></span> <span data-ttu-id="1b88a-130">L'utilisation de l'Assistant Création d'un mappage réduit le risque d'informations de mappage non valides.</span><span class="sxs-lookup"><span data-stu-id="1b88a-130">Note that using the Create Mapping Wizard reduces the risk of invalid mapping information.</span></span> <span data-ttu-id="1b88a-131">Vous pouvez supprimer le mappage avec échec.</span><span class="sxs-lookup"><span data-stu-id="1b88a-131">You can delete the failed mapping.</span></span> <span data-ttu-id="1b88a-132">Si vous ne le supprimez pas, il sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="1b88a-132">If you do not delete it, it will be ignored.</span></span>