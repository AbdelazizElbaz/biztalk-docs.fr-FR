---
title: "Single Sign-On : Événement 10680 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88ea12ff-d181-423f-9054-b0c656cc4558
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd7b1804578e1b0880eaa564f68a24f0841280fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10680"></a><span data-ttu-id="c3ebe-102">Single Sign-On : Événement 10680</span><span class="sxs-lookup"><span data-stu-id="c3ebe-102">Single Sign-On: Event 10680</span></span>
## <a name="details"></a><span data-ttu-id="c3ebe-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c3ebe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3ebe-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c3ebe-104">Product Name</span></span>|<span data-ttu-id="c3ebe-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c3ebe-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c3ebe-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c3ebe-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c3ebe-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c3ebe-107">Event ID</span></span>|<span data-ttu-id="c3ebe-108">10680</span><span class="sxs-lookup"><span data-stu-id="c3ebe-108">10680</span></span>|  
|<span data-ttu-id="c3ebe-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c3ebe-109">Event Source</span></span>|<span data-ttu-id="c3ebe-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c3ebe-110">ENTSSO</span></span>|  
|<span data-ttu-id="c3ebe-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c3ebe-111">Component</span></span>|<span data-ttu-id="c3ebe-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c3ebe-112">N\A</span></span>|  
|<span data-ttu-id="c3ebe-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c3ebe-113">Symbolic Name</span></span>|<span data-ttu-id="c3ebe-114">SSO_WARN_PS_GET_CREDS_FAILED</span><span class="sxs-lookup"><span data-stu-id="c3ebe-114">SSO_WARN_PS_GET_CREDS_FAILED</span></span>|  
|<span data-ttu-id="c3ebe-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c3ebe-115">Message Text</span></span>|<span data-ttu-id="c3ebe-116">Le mot de passe n'a pas été modifié pour le compte externe car les informations d'identification externes existantes n'ont pas pu être obtenues auprès de la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="c3ebe-116">The password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.%r</span></span><br /><br /> <span data-ttu-id="c3ebe-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="c3ebe-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="c3ebe-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="c3ebe-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="c3ebe-119">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="c3ebe-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="c3ebe-120">Compte externe : %4 %r</span><span class="sxs-lookup"><span data-stu-id="c3ebe-120">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="c3ebe-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="c3ebe-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c3ebe-122">Explication</span><span class="sxs-lookup"><span data-stu-id="c3ebe-122">Explanation</span></span>  
 <span data-ttu-id="c3ebe-123">Cet événement d'avertissement indique que le mot de passe n'a pas été modifié pour le compte externe car les informations d'identification externes existantes n'ont pas pu être obtenues auprès de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="c3ebe-123">This Warning event indicates that the password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c3ebe-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3ebe-124">User Action</span></span>  
 <span data-ttu-id="c3ebe-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3ebe-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="c3ebe-126">Vérifiez les informations d'identification externes.</span><span class="sxs-lookup"><span data-stu-id="c3ebe-126">Verify external credentials.</span></span>  
  
-   <span data-ttu-id="c3ebe-127">Les informations d'identification externes ne sont pas valides. Utilisez les outils d'administration de l'authentification unique pour définir les informations d'identification externes pour ce compte externe.</span><span class="sxs-lookup"><span data-stu-id="c3ebe-127">The external credentials are not valid, use the SSO administration tools to set the external credentials for this external account.</span></span> <span data-ttu-id="c3ebe-128">Vous devez définir le mot de passe externe (pour le compte donné) dans toutes les applications associées.</span><span class="sxs-lookup"><span data-stu-id="c3ebe-128">You must set the external password (for the given account) in all associated applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="c3ebe-129">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="c3ebe-129">More info</span></span>
  
-   [<span data-ttu-id="c3ebe-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c3ebe-130">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="c3ebe-131">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ebe-131">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>