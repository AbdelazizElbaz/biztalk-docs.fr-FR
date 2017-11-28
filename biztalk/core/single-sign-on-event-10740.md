---
title: "Single Sign-On : Événement 10740 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928760bebef1119207ee6a3021cd39c22ceacad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10740"></a><span data-ttu-id="60ccc-102">Single Sign-On : Événement 10740</span><span class="sxs-lookup"><span data-stu-id="60ccc-102">Single Sign-On: Event 10740</span></span>
## <a name="details"></a><span data-ttu-id="60ccc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="60ccc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60ccc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="60ccc-104">Product Name</span></span>|<span data-ttu-id="60ccc-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="60ccc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="60ccc-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="60ccc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="60ccc-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="60ccc-107">Event ID</span></span>|<span data-ttu-id="60ccc-108">10740</span><span class="sxs-lookup"><span data-stu-id="60ccc-108">10740</span></span>|  
|<span data-ttu-id="60ccc-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="60ccc-109">Event Source</span></span>|<span data-ttu-id="60ccc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="60ccc-110">ENTSSO</span></span>|  
|<span data-ttu-id="60ccc-111">Composant</span><span class="sxs-lookup"><span data-stu-id="60ccc-111">Component</span></span>|<span data-ttu-id="60ccc-112">N\A</span><span class="sxs-lookup"><span data-stu-id="60ccc-112">N\A</span></span>|  
|<span data-ttu-id="60ccc-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="60ccc-113">Symbolic Name</span></span>|<span data-ttu-id="60ccc-114">SSO_WARN_INVALID_WINDOWS_USER</span><span class="sxs-lookup"><span data-stu-id="60ccc-114">SSO_WARN_INVALID_WINDOWS_USER</span></span>|  
|<span data-ttu-id="60ccc-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="60ccc-115">Message Text</span></span>|<span data-ttu-id="60ccc-116">Le compte Windows n'est pas valide pour la mise à jour de l'application.%r</span><span class="sxs-lookup"><span data-stu-id="60ccc-116">The Windows Account is not valid for application update.%r</span></span><br /><br /> <span data-ttu-id="60ccc-117">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="60ccc-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="60ccc-118">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="60ccc-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="60ccc-119">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="60ccc-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="60ccc-120">Explication</span><span class="sxs-lookup"><span data-stu-id="60ccc-120">Explanation</span></span>  
 <span data-ttu-id="60ccc-121">Cet événement d'avertissement indique que le compte Windows (spécifié dans le message de l'événement) n'est pas valide pour la mise à jour de l'application.</span><span class="sxs-lookup"><span data-stu-id="60ccc-121">This Warning event indicates that the Windows Account (specified in the event message) is not valid for application update.</span></span> <span data-ttu-id="60ccc-122">Ceci peut survenir lors de la modification du compte Windows pour une application de type Groupe d'hôtes.</span><span class="sxs-lookup"><span data-stu-id="60ccc-122">This can occur when changing the Windows account for a Host Group application.</span></span> <span data-ttu-id="60ccc-123">Les applications de ce type sont utilisées pour l'authentification unique entre des systèmes externes et des systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="60ccc-123">Host Group applications are used for single sign-on from external systems to Windows systems.</span></span> <span data-ttu-id="60ccc-124">Ils peuvent mapper un ensemble d'utilisateurs externes à un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="60ccc-124">They can map a set of external users to a single Windows account.</span></span> <span data-ttu-id="60ccc-125">Le compte Windows auxquels ils sont mappés est défini dans le champ Utilisateurs d'applications de l'application.</span><span class="sxs-lookup"><span data-stu-id="60ccc-125">The Windows account they are mapped to is defined in the Application Users field of the application.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60ccc-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="60ccc-126">User Action</span></span>  
 <span data-ttu-id="60ccc-127">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="60ccc-127">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="60ccc-128">Vérifiez que le compte Windows que vous utilisez est valide.</span><span class="sxs-lookup"><span data-stu-id="60ccc-128">Check that the Windows account your are using is valid.</span></span>  
  
-   <span data-ttu-id="60ccc-129">Recréez le compte Windows avec les propriétés correctes.</span><span class="sxs-lookup"><span data-stu-id="60ccc-129">Recreate the Windows account with the correct Windows account properties.</span></span>  
  
 <span data-ttu-id="60ccc-130">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="60ccc-130">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="60ccc-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="60ccc-131">Password Synchronization</span></span>](../core/password-synchronization2.md)