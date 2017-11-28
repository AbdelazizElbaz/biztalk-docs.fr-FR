---
title: "Single Sign-On : Événement 10674 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad0c0d9e-1e6d-4c3e-86e0-9e336a18f3d6
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d239353276657e85c7fbdcfa634c3c1268723724
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10674"></a><span data-ttu-id="af9c8-102">Single Sign-On : Événement 10674</span><span class="sxs-lookup"><span data-stu-id="af9c8-102">Single Sign-On: Event 10674</span></span>
## <a name="details"></a><span data-ttu-id="af9c8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="af9c8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af9c8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="af9c8-104">Product Name</span></span>|<span data-ttu-id="af9c8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="af9c8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="af9c8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="af9c8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="af9c8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="af9c8-107">Event ID</span></span>|<span data-ttu-id="af9c8-108">10674</span><span class="sxs-lookup"><span data-stu-id="af9c8-108">10674</span></span>|  
|<span data-ttu-id="af9c8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="af9c8-109">Event Source</span></span>|<span data-ttu-id="af9c8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="af9c8-110">ENTSSO</span></span>|  
|<span data-ttu-id="af9c8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="af9c8-111">Component</span></span>|<span data-ttu-id="af9c8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="af9c8-112">N\A</span></span>|  
|<span data-ttu-id="af9c8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="af9c8-113">Symbolic Name</span></span>|<span data-ttu-id="af9c8-114">SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="af9c8-114">SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="af9c8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="af9c8-115">Message Text</span></span>|<span data-ttu-id="af9c8-116">Une modification de mot de passe externe aurait entraîné la modification de plusieurs comptes Windows.%r</span><span class="sxs-lookup"><span data-stu-id="af9c8-116">An external password change would have caused changes to more than one Windows account.%r</span></span><br /><br /> <span data-ttu-id="af9c8-117">Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="af9c8-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="af9c8-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="af9c8-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="af9c8-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="af9c8-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="af9c8-120">Compte externe : %3 %r</span><span class="sxs-lookup"><span data-stu-id="af9c8-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="af9c8-121">Compte Windows 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="af9c8-121">Windows Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="af9c8-122">Le compte Windows 2 : %5</span><span class="sxs-lookup"><span data-stu-id="af9c8-122">Windows Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="af9c8-123">Explication</span><span class="sxs-lookup"><span data-stu-id="af9c8-123">Explanation</span></span>  
 <span data-ttu-id="af9c8-124">Cet événement d'avertissement indique qu'une modification de mot de passe externe aurait entraîné la modification de plusieurs comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="af9c8-124">This Warning event indicates that an external password change would have caused changes to more than one Windows account.</span></span> <span data-ttu-id="af9c8-125">Cette modification ne s'est pas produite car la configuration de l'adaptateur ne le permettait pas.</span><span class="sxs-lookup"><span data-stu-id="af9c8-125">This change was prevented because the adapter configuration would not allow it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="af9c8-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="af9c8-126">User Action</span></span>  
 <span data-ttu-id="af9c8-127">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="af9c8-127">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="af9c8-128">Si les conflits de mappage sont attendus et autorisés, utilisez les outils d’administration de l’authentification unique pour configurer le **autoriser les conflits de mappage** propriété pour l’adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="af9c8-128">If mapping conflicts are expected and allowed, use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="af9c8-129">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="af9c8-129">More info</span></span>
  
-   <span data-ttu-id="af9c8-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="af9c8-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="af9c8-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="af9c8-131">Password Synchronization</span></span>](../core/password-synchronization2.md)