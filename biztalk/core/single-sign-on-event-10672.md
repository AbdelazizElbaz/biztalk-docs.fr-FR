---
title: "Single Sign-On : Événement 10672 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2422c7d-51bc-4f12-8830-193d71d2bce9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03eb6a72be53f928c8c173ac84556f709df0723c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10672"></a><span data-ttu-id="0900e-102">Single Sign-On : Événement 10672</span><span class="sxs-lookup"><span data-stu-id="0900e-102">Single Sign-On: Event 10672</span></span>
## <a name="details"></a><span data-ttu-id="0900e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0900e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0900e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0900e-104">Product Name</span></span>|<span data-ttu-id="0900e-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="0900e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="0900e-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0900e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="0900e-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0900e-107">Event ID</span></span>|<span data-ttu-id="0900e-108">10672</span><span class="sxs-lookup"><span data-stu-id="0900e-108">10672</span></span>|  
|<span data-ttu-id="0900e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0900e-109">Event Source</span></span>|<span data-ttu-id="0900e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0900e-110">ENTSSO</span></span>|  
|<span data-ttu-id="0900e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="0900e-111">Component</span></span>|<span data-ttu-id="0900e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0900e-112">N\A</span></span>|  
|<span data-ttu-id="0900e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0900e-113">Symbolic Name</span></span>|<span data-ttu-id="0900e-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="0900e-114">SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="0900e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0900e-115">Message Text</span></span>|<span data-ttu-id="0900e-116">Un changement de mot de passe Windows a endommagé plusieurs comptes figurant sur le même système externe.%r</span><span class="sxs-lookup"><span data-stu-id="0900e-116">A Windows password change would have caused changes to more than one account on the same external system.%r</span></span><br /><br /> <span data-ttu-id="0900e-117">Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="0900e-117">This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="0900e-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="0900e-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="0900e-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="0900e-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="0900e-120">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="0900e-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="0900e-121">Compte externe 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="0900e-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="0900e-122">Compte externe 2 : %5</span><span class="sxs-lookup"><span data-stu-id="0900e-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0900e-123">Explication</span><span class="sxs-lookup"><span data-stu-id="0900e-123">Explanation</span></span>  
 <span data-ttu-id="0900e-124">Cet avertissement indique qu'un changement de mot de passe Windows a endommagé plusieurs comptes figurant sur le même système externe.</span><span class="sxs-lookup"><span data-stu-id="0900e-124">This Warning event indicates that a Windows password change would have caused changes to more than one account on the same external system.</span></span> <span data-ttu-id="0900e-125">Cette modification ne s'est pas produite car la configuration de l'adaptateur ne le permettait pas.</span><span class="sxs-lookup"><span data-stu-id="0900e-125">This change was prevented because the adapter configuration would not allow it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0900e-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0900e-126">User Action</span></span>  
  
-   <span data-ttu-id="0900e-127">Utilisez les outils d’administration de l’authentification unique pour configurer le **autoriser les conflits de mappage** propriété pour l’adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="0900e-127">Use the SSO Admin tools to configure the **Allow Mapping Conflicts** property for the Password Sync Adapter.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="0900e-128">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="0900e-128">More info</span></span>
  
-   <span data-ttu-id="0900e-129">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="0900e-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="0900e-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="0900e-130">Password Synchronization</span></span>](../core/password-synchronization2.md)