---
title: "Single Sign-On : Événement 11017 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a4f7264-18aa-4eca-97c9-d5fd7e90e2cc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25ef3f3be84e775fe522b508f7726f3e4e88870b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11017"></a><span data-ttu-id="74477-102">Single Sign-On : Événement 11017</span><span class="sxs-lookup"><span data-stu-id="74477-102">Single Sign-On: Event 11017</span></span>
## <a name="details"></a><span data-ttu-id="74477-103">Détails</span><span class="sxs-lookup"><span data-stu-id="74477-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74477-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="74477-104">Product Name</span></span>|<span data-ttu-id="74477-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="74477-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="74477-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="74477-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="74477-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="74477-107">Event ID</span></span>|<span data-ttu-id="74477-108">11017</span><span class="sxs-lookup"><span data-stu-id="74477-108">11017</span></span>|  
|<span data-ttu-id="74477-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="74477-109">Event Source</span></span>|<span data-ttu-id="74477-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="74477-110">ENTSSO</span></span>|  
|<span data-ttu-id="74477-111">Composant</span><span class="sxs-lookup"><span data-stu-id="74477-111">Component</span></span>|<span data-ttu-id="74477-112">Néant</span><span class="sxs-lookup"><span data-stu-id="74477-112">N/A</span></span>|  
|<span data-ttu-id="74477-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="74477-113">Symbolic Name</span></span>|<span data-ttu-id="74477-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK</span><span class="sxs-lookup"><span data-stu-id="74477-114">SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK</span></span>|  
|<span data-ttu-id="74477-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="74477-115">Message Text</span></span>|<span data-ttu-id="74477-116">Le mappage n'est pas valide car le compte Windows ne figure pas dans le compte Utilisateurs d'applications pour l'application.</span><span class="sxs-lookup"><span data-stu-id="74477-116">The mapping is not valid because the Windows account is not in the Application Users account for the application.</span></span> <span data-ttu-id="74477-117">Le mappage a été supprimé.%r</span><span class="sxs-lookup"><span data-stu-id="74477-117">The mapping has been deleted.%r</span></span><br /><br /> <span data-ttu-id="74477-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="74477-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="74477-119">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="74477-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="74477-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="74477-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="74477-121">Utilisateurs de l’application : %4</span><span class="sxs-lookup"><span data-stu-id="74477-121">Application Users: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74477-122">Explication</span><span class="sxs-lookup"><span data-stu-id="74477-122">Explanation</span></span>  
 <span data-ttu-id="74477-123">Le compte Windows spécifié n'a jamais fait partie du compte Utilisateurs d'applications, ou il en a fait partie avant d'être modifié ou supprimé.</span><span class="sxs-lookup"><span data-stu-id="74477-123">Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed.</span></span> <span data-ttu-id="74477-124">Le mappage a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="74477-124">The mapping has been deleted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74477-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="74477-125">User Action</span></span>  
 <span data-ttu-id="74477-126">Consultez les informations du compte de synchronisation de mot de passe pour votre système et assurez-vous qu'elles sont valides.</span><span class="sxs-lookup"><span data-stu-id="74477-126">Check the password sync account information for your system, and make sure your information is valid.</span></span> <span data-ttu-id="74477-127">Recréez ensuite le mappage.</span><span class="sxs-lookup"><span data-stu-id="74477-127">Then recreate the mapping.</span></span> <span data-ttu-id="74477-128">L'utilisation de l'Assistant Création d'un mappage réduit le risque d'informations de mappage non valides.</span><span class="sxs-lookup"><span data-stu-id="74477-128">Note that using the Create Mapping Wizard reduces the risk of invalid mapping information.</span></span>