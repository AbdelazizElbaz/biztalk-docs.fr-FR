---
title: "Single Sign-On : Événement 10742 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abb3acb03e60d1d7a7e705ac8b36aa5157616f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10742"></a><span data-ttu-id="5d96b-102">Single Sign-On : Événement 10742</span><span class="sxs-lookup"><span data-stu-id="5d96b-102">Single Sign-On: Event 10742</span></span>
## <a name="details"></a><span data-ttu-id="5d96b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5d96b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d96b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5d96b-104">Product Name</span></span>|<span data-ttu-id="5d96b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="5d96b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5d96b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5d96b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5d96b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5d96b-107">Event ID</span></span>|<span data-ttu-id="5d96b-108">10742</span><span class="sxs-lookup"><span data-stu-id="5d96b-108">10742</span></span>|  
|<span data-ttu-id="5d96b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5d96b-109">Event Source</span></span>|<span data-ttu-id="5d96b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5d96b-110">ENTSSO</span></span>|  
|<span data-ttu-id="5d96b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5d96b-111">Component</span></span>|<span data-ttu-id="5d96b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5d96b-112">N\A</span></span>|  
|<span data-ttu-id="5d96b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5d96b-113">Symbolic Name</span></span>|<span data-ttu-id="5d96b-114">SSO_WARN_NO_UPDATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="5d96b-114">SSO_WARN_NO_UPDATE_ADAPTER</span></span>|  
|<span data-ttu-id="5d96b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5d96b-115">Message Text</span></span>|<span data-ttu-id="5d96b-116">L'utilisateur du client doit être un membre du compte Administrateurs SSO ou du compte Administrateurs d'application pour mettre à jour l'adaptateur.%r</span><span class="sxs-lookup"><span data-stu-id="5d96b-116">The client user must be a member of the SSO Administrators account or the Application Administrators account to update the adapter.%r</span></span><br /><br /> <span data-ttu-id="5d96b-117">L’utilisateur client : %1 %r</span><span class="sxs-lookup"><span data-stu-id="5d96b-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="5d96b-118">Les administrateurs SSO : %2 %r</span><span class="sxs-lookup"><span data-stu-id="5d96b-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="5d96b-119">Administrateurs d’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="5d96b-119">Application Administrators: %3%r</span></span><br /><br /> <span data-ttu-id="5d96b-120">Carte : %4 %r</span><span class="sxs-lookup"><span data-stu-id="5d96b-120">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="5d96b-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="5d96b-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5d96b-122">Explication</span><span class="sxs-lookup"><span data-stu-id="5d96b-122">Explanation</span></span>  
 <span data-ttu-id="5d96b-123">Cet événement de type avertissement indique qu'une tentative de mise à jour de l'adaptateur spécifié a été effectuée, mais n'a pas pu aboutir car le compte utilisateur employé n'est pas un membre du compte Administrateurs SSO ou du compte Administrateurs d'application.</span><span class="sxs-lookup"><span data-stu-id="5d96b-123">This Warning event indicates that an attempt to update the specified adapter was made, but could not be completed because the user account used is not a member of the SSO Administrators account or the Application Administrators account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5d96b-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5d96b-124">User Action</span></span>  
 <span data-ttu-id="5d96b-125">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d96b-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="5d96b-126">Ajoutez un compte utilisateur au compte Administrateurs SSO ou au compte Administrateurs d'application.</span><span class="sxs-lookup"><span data-stu-id="5d96b-126">Add user account to the SSO Administrators account or the Application Administrators account.</span></span>  
  
-   <span data-ttu-id="5d96b-127">Relancez la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="5d96b-127">Retry update.</span></span>  
  
 <span data-ttu-id="5d96b-128">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5d96b-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="5d96b-129">Comment administrer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="5d96b-129">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)