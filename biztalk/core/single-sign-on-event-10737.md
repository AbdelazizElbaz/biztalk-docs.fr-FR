---
title: "Single Sign-On : Événement 10737 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2102930b-8b1f-4d48-a14d-e8884dc7f9aa
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b89397206529cffb6048cc0f5578b3bac5cb1fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10737"></a><span data-ttu-id="1683d-102">Single Sign-On : Événement 10737</span><span class="sxs-lookup"><span data-stu-id="1683d-102">Single Sign-On: Event 10737</span></span>
## <a name="details"></a><span data-ttu-id="1683d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1683d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1683d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1683d-104">Product Name</span></span>|<span data-ttu-id="1683d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1683d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1683d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1683d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1683d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1683d-107">Event ID</span></span>|<span data-ttu-id="1683d-108">10737</span><span class="sxs-lookup"><span data-stu-id="1683d-108">10737</span></span>|  
|<span data-ttu-id="1683d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1683d-109">Event Source</span></span>|<span data-ttu-id="1683d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1683d-110">ENTSSO</span></span>|  
|<span data-ttu-id="1683d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1683d-111">Component</span></span>|<span data-ttu-id="1683d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1683d-112">N\A</span></span>|  
|<span data-ttu-id="1683d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1683d-113">Symbolic Name</span></span>|<span data-ttu-id="1683d-114">SSO_WARN_PS_SET_EXTERNAL_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="1683d-114">SSO_WARN_PS_SET_EXTERNAL_PASSWORD</span></span>|  
|<span data-ttu-id="1683d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1683d-115">Message Text</span></span>|<span data-ttu-id="1683d-116">Échec de la mise à jour du mot de passe externe dans la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="1683d-116">Failed to update the external password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="1683d-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="1683d-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="1683d-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="1683d-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="1683d-119">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="1683d-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="1683d-120">Compte externe : %4 %r</span><span class="sxs-lookup"><span data-stu-id="1683d-120">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="1683d-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="1683d-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1683d-122">Explication</span><span class="sxs-lookup"><span data-stu-id="1683d-122">Explanation</span></span>  
 <span data-ttu-id="1683d-123">Cet événement d'avertissement indique que l'authentification unique n'a pas pu mettre à jour le mot de passe externe dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="1683d-123">This Warning event indicates that SSO failed to update the external password in the SSO database.</span></span> <span data-ttu-id="1683d-124">Il y a plusieurs causes d'échec possibles indiquées dans le message d'avertissement. Dans certains cas, cet avertissement peut indiquer un problème de configuration ou il se peut que le mappage ait été supprimé tandis que la modification du mot de passe était en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="1683d-124">There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1683d-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1683d-125">User Action</span></span>  
 <span data-ttu-id="1683d-126">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1683d-126">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="1683d-127">Essayez à nouveau de modifier le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1683d-127">Retry the password change.</span></span>  
  
-   <span data-ttu-id="1683d-128">Si les autres tentatives échouent, modifiez le mot de passe manuellement à l'aide de l'interface utilisateur ou des outils de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="1683d-128">If additional attempts continue to fail, change the password manually using the UI or command line tools.</span></span>  
  
 <span data-ttu-id="1683d-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1683d-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="1683d-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1683d-130">Password Synchronization</span></span>](../core/password-synchronization2.md)