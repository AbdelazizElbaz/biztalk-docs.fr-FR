---
title: "Single Sign-On : Événement 10669 répond | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88a583d-7385-42dd-841e-aa2d2215dd69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 334180225d47cb9a86577cab75490ea0b6f2225a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10669"></a><span data-ttu-id="8aeee-102">Single Sign-On : Événement 10669 répond</span><span class="sxs-lookup"><span data-stu-id="8aeee-102">Single Sign-On: Event 10669</span></span>
## <a name="details"></a><span data-ttu-id="8aeee-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8aeee-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8aeee-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8aeee-104">Product Name</span></span>|<span data-ttu-id="8aeee-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8aeee-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8aeee-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8aeee-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8aeee-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8aeee-107">Event ID</span></span>|<span data-ttu-id="8aeee-108">10669</span><span class="sxs-lookup"><span data-stu-id="8aeee-108">10669</span></span>|  
|<span data-ttu-id="8aeee-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8aeee-109">Event Source</span></span>|<span data-ttu-id="8aeee-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8aeee-110">ENTSSO</span></span>|  
|<span data-ttu-id="8aeee-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8aeee-111">Component</span></span>|<span data-ttu-id="8aeee-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8aeee-112">N\A</span></span>|  
|<span data-ttu-id="8aeee-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8aeee-113">Symbolic Name</span></span>|<span data-ttu-id="8aeee-114">SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED</span><span class="sxs-lookup"><span data-stu-id="8aeee-114">SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED</span></span>|  
|<span data-ttu-id="8aeee-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8aeee-115">Message Text</span></span>|<span data-ttu-id="8aeee-116">Échec du changement du mot de passe Windows.%r</span><span class="sxs-lookup"><span data-stu-id="8aeee-116">Failed to change the Windows password.%r</span></span><br /><br /> <span data-ttu-id="8aeee-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="8aeee-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="8aeee-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="8aeee-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="8aeee-119">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="8aeee-119">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="8aeee-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="8aeee-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8aeee-121">Explication</span><span class="sxs-lookup"><span data-stu-id="8aeee-121">Explanation</span></span>  
 <span data-ttu-id="8aeee-122">Cet avertissement indique que SSO n'est pas parvenu à modifier un mot de passe Windows.</span><span class="sxs-lookup"><span data-stu-id="8aeee-122">This Warning event indicates that SSO failed to change a Windows password.</span></span> <span data-ttu-id="8aeee-123">SSO appelle la fonction NetUserChangePassword de Win32 pour modifier le mot de passe Windows associé au mappage.</span><span class="sxs-lookup"><span data-stu-id="8aeee-123">SSO calls the Win32 function NetUserChangePassword function to change the Windows password associated with the mapping.</span></span> <span data-ttu-id="8aeee-124">En cas d'échec de cette fonction, ce message d'erreur est émis.</span><span class="sxs-lookup"><span data-stu-id="8aeee-124">If this function fails this error message is issued.</span></span> <span data-ttu-id="8aeee-125">Le code d'erreur correspondra à celui renvoyé par la fonction NetUserChangePassword.</span><span class="sxs-lookup"><span data-stu-id="8aeee-125">The error code will be the one returned from NetUserChangePassword.</span></span> <span data-ttu-id="8aeee-126">Pour plus d'informations, consultez la documentation relative à cette fonction dans MSDN.</span><span class="sxs-lookup"><span data-stu-id="8aeee-126">See the documentation for this function in MSDN for details.</span></span> <span data-ttu-id="8aeee-127">Cet échec est probablement dû au fait que l'ancien mot de passe était incorrect ou que le nouveau mot de passe ne correspond pas à la stratégie de création des mots de passe Windows.</span><span class="sxs-lookup"><span data-stu-id="8aeee-127">Most likely causes of failure are that the old password was incorrect, or that the new password does not meet the required Windows password policy.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8aeee-128">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8aeee-128">User Action</span></span>  
 <span data-ttu-id="8aeee-129">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8aeee-129">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="8aeee-130">Vérifiez l'ancien mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8aeee-130">Verify the old password.</span></span> <span data-ttu-id="8aeee-131">Si l'ancien mot de passe est incorrect, il peut être défini manuellement dans la base de données SSO à l'aide des outils de ligne de commande ou du logiciel MMC d'administration.</span><span class="sxs-lookup"><span data-stu-id="8aeee-131">If the old password is incorrect then it can be set manually in the SSO database using the command line tools or Admin MMC.</span></span>  
  
-   <span data-ttu-id="8aeee-132">Assurez-vous que le nouveau mot de passe correspond à la stratégie de création de mots de passe Windows requise.</span><span class="sxs-lookup"><span data-stu-id="8aeee-132">Verify the new password meets the required Windows password policy.</span></span> <span data-ttu-id="8aeee-133">Si le mot de passe ne correspond pas à cette stratégie, pensez à utiliser des filtres de mots de passe.</span><span class="sxs-lookup"><span data-stu-id="8aeee-133">If the password does not meet the Windows password policy then consider using password filters.</span></span>  
  
 <span data-ttu-id="8aeee-134">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8aeee-134">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8aeee-135">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8aeee-135">Password Synchronization</span></span>](../core/password-synchronization2.md)