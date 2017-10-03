---
title: "Single Sign-On : Événement 10676 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3805e59e5e8984652ec40af9f93db793d5d3b5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10676"></a><span data-ttu-id="f7bf6-102">Single Sign-On : Événement 10676</span><span class="sxs-lookup"><span data-stu-id="f7bf6-102">Single Sign-On: Event 10676</span></span>
## <a name="details"></a><span data-ttu-id="f7bf6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f7bf6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7bf6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f7bf6-104">Product Name</span></span>|<span data-ttu-id="f7bf6-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="f7bf6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f7bf6-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f7bf6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f7bf6-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f7bf6-107">Event ID</span></span>|<span data-ttu-id="f7bf6-108">10676</span><span class="sxs-lookup"><span data-stu-id="f7bf6-108">10676</span></span>|  
|<span data-ttu-id="f7bf6-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f7bf6-109">Event Source</span></span>|<span data-ttu-id="f7bf6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f7bf6-110">ENTSSO</span></span>|  
|<span data-ttu-id="f7bf6-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f7bf6-111">Component</span></span>|<span data-ttu-id="f7bf6-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f7bf6-112">N\A</span></span>|  
|<span data-ttu-id="f7bf6-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f7bf6-113">Symbolic Name</span></span>|<span data-ttu-id="f7bf6-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="f7bf6-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span></span>|  
|<span data-ttu-id="f7bf6-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f7bf6-115">Message Text</span></span>|<span data-ttu-id="f7bf6-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="f7bf6-116">External password change.</span></span> <span data-ttu-id="f7bf6-117">Lors de la modification du mot de passe relatif à un compte externe, l'adaptateur doit fournir l'ancien mot de passe.%r</span><span class="sxs-lookup"><span data-stu-id="f7bf6-117">When changing the password for an external account the adapter must supply the old password.%r</span></span><br /><br /> <span data-ttu-id="f7bf6-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="f7bf6-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="f7bf6-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="f7bf6-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="f7bf6-120">Compte externe : %3</span><span class="sxs-lookup"><span data-stu-id="f7bf6-120">External Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f7bf6-121">Explication</span><span class="sxs-lookup"><span data-stu-id="f7bf6-121">Explanation</span></span>  
 <span data-ttu-id="f7bf6-122">Cette erreur indique que l'adaptateur de synchronisation de mot de passe a été configuré de manière à ce qu'un ancien mot de passe du système externe soit indiqué, ce qui n'a pas été le cas dans la situation présente.</span><span class="sxs-lookup"><span data-stu-id="f7bf6-122">This Error event indicates that the password sync adapter was configured to expect an old password from the external system, but an old password was not provided.</span></span> <span data-ttu-id="f7bf6-123">Cela signifie que le système externe (l'adaptateur de synchronisation de mot de passe externe) n'est pas configuré ou ne fonctionne pas comme prévu ou que l'adaptateur de synchronisation de mot de passe est configuré de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="f7bf6-123">Either the external system (the external password sync adapter) is not configured or working as expected or the password sync adapter is incorrectly configured.</span></span> <span data-ttu-id="f7bf6-124">Cette erreur peut également renvoyer le nom symbolique de code d'erreur ENTSSO_E_REQUIRE_OLD_PASSWORD.</span><span class="sxs-lookup"><span data-stu-id="f7bf6-124">This error may also return error code symbolic name ENTSSO_E_REQUIRE_OLD_PASSWORD.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f7bf6-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f7bf6-125">User Action</span></span>  
 <span data-ttu-id="f7bf6-126">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7bf6-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="f7bf6-127">Utilisez les outils d’administration SSO pour définir la propriété configurable par l’utilisateur **vérifier un ancien mot de passe** sous l’onglet de propriétés Options de l’adaptateur de synchronisation de mot de passe. Cette propriété peut également être définie lors de la création d'adaptateurs par le biais des outils de ligne de commande (ssops.exe), avec le nom d'indicateur `verifyOldPassword`, ainsi que lors de la création d'un adaptateur de synchronisation de mot de passe à l'aide de l'Assistant de l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f7bf6-127">Use the SSO administration tools to set the user configurable property **Verify Old Password** on the Password Sync Adapter Options properties tab. This property can also be set when creating adapters via the command line tools (ssops.exe) with the flag name `verifyOldPassword` and also when creating a new password sync adapter using the Password Sync Adapter wizard.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="f7bf6-128">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="f7bf6-128">More info</span></span>
  
-   [<span data-ttu-id="f7bf6-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="f7bf6-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="f7bf6-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="f7bf6-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>