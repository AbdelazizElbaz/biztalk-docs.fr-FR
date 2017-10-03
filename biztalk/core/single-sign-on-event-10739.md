---
title: "Single Sign-On : Événement 10739 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1039c832-80ff-4cc2-97b4-2671672b6b12
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8a3dc964d830155a63a5ada8817e8b44aaa4c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10739"></a><span data-ttu-id="59495-102">Single Sign-On : Événement 10739</span><span class="sxs-lookup"><span data-stu-id="59495-102">Single Sign-On: Event 10739</span></span>
## <a name="details"></a><span data-ttu-id="59495-103">Détails</span><span class="sxs-lookup"><span data-stu-id="59495-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59495-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="59495-104">Product Name</span></span>|<span data-ttu-id="59495-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="59495-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="59495-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="59495-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="59495-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="59495-107">Event ID</span></span>|<span data-ttu-id="59495-108">10739</span><span class="sxs-lookup"><span data-stu-id="59495-108">10739</span></span>|  
|<span data-ttu-id="59495-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="59495-109">Event Source</span></span>|<span data-ttu-id="59495-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="59495-110">ENTSSO</span></span>|  
|<span data-ttu-id="59495-111">Composant</span><span class="sxs-lookup"><span data-stu-id="59495-111">Component</span></span>|<span data-ttu-id="59495-112">N\A</span><span class="sxs-lookup"><span data-stu-id="59495-112">N\A</span></span>|  
|<span data-ttu-id="59495-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="59495-113">Symbolic Name</span></span>|<span data-ttu-id="59495-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="59495-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span></span>|  
|<span data-ttu-id="59495-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="59495-115">Message Text</span></span>|<span data-ttu-id="59495-116">Échec de la mise à jour du mot de passe Windows dans la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="59495-116">Failed to update the Windows password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="59495-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="59495-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="59495-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="59495-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="59495-119">Compte Windows : %3\\%4 %r</span><span class="sxs-lookup"><span data-stu-id="59495-119">Windows Account: %3\\%4%r</span></span><br /><br /> <span data-ttu-id="59495-120">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="59495-120">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59495-121">Explication</span><span class="sxs-lookup"><span data-stu-id="59495-121">Explanation</span></span>  
 <span data-ttu-id="59495-122">Cet événement d'avertissement indique que l'authentification unique n'a pas pu mettre à jour le mot de passe Windows dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="59495-122">This Warning event indicates that SSO failed to update the Windows password in the SSO database.</span></span> <span data-ttu-id="59495-123">Il y a plusieurs causes d'échec possibles indiquées dans le message d'avertissement. Dans certains cas, cet avertissement peut indiquer un problème de configuration ou il se peut que le mappage ait été supprimé tandis que la modification du mot de passe était en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="59495-123">There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59495-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="59495-124">User Action</span></span>  
 <span data-ttu-id="59495-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="59495-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="59495-126">Essayez à nouveau de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="59495-126">Retry the password change.</span></span>  
  
-   <span data-ttu-id="59495-127">Si les autres tentatives échouent, modifiez le mot de passe manuellement à l'aide de l'interface utilisateur ou des outils de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="59495-127">If additional attempts continue to fail, change the password manually using the UI or command line tools.</span></span>  
  
 <span data-ttu-id="59495-128">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="59495-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="59495-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="59495-129">Password Synchronization</span></span>](../core/password-synchronization2.md)