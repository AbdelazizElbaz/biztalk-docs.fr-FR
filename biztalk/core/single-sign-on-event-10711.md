---
title: "Single Sign-On : Événement 10711 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40722fe1-4be9-40d3-b5c5-a740a4b59f45
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6c6bb3f85d45edd971a38b7e7fa4c1df3efb3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10711"></a><span data-ttu-id="76d18-102">Single Sign-On : Événement 10711</span><span class="sxs-lookup"><span data-stu-id="76d18-102">Single Sign-On: Event 10711</span></span>
## <a name="details"></a><span data-ttu-id="76d18-103">Détails</span><span class="sxs-lookup"><span data-stu-id="76d18-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76d18-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="76d18-104">Product Name</span></span>|<span data-ttu-id="76d18-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="76d18-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="76d18-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="76d18-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="76d18-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="76d18-107">Event ID</span></span>|<span data-ttu-id="76d18-108">10711</span><span class="sxs-lookup"><span data-stu-id="76d18-108">10711</span></span>|  
|<span data-ttu-id="76d18-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="76d18-109">Event Source</span></span>|<span data-ttu-id="76d18-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="76d18-110">ENTSSO</span></span>|  
|<span data-ttu-id="76d18-111">Composant</span><span class="sxs-lookup"><span data-stu-id="76d18-111">Component</span></span>|<span data-ttu-id="76d18-112">N\A</span><span class="sxs-lookup"><span data-stu-id="76d18-112">N\A</span></span>|  
|<span data-ttu-id="76d18-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="76d18-113">Symbolic Name</span></span>|<span data-ttu-id="76d18-114">SSO_WARN_PS_MISSING_INITIAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="76d18-114">SSO_WARN_PS_MISSING_INITIAL_CREDS</span></span>|  
|<span data-ttu-id="76d18-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="76d18-115">Message Text</span></span>|<span data-ttu-id="76d18-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="76d18-116">External password change.</span></span> <span data-ttu-id="76d18-117">Certains champs d'informations d'identification externes manquants pour ce mappage ont été définis sur des valeurs par défaut.%r</span><span class="sxs-lookup"><span data-stu-id="76d18-117">Some missing external credential fields for this mapping have been set to default values.%r</span></span><br /><br /> <span data-ttu-id="76d18-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="76d18-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="76d18-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="76d18-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="76d18-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="76d18-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="76d18-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="76d18-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="76d18-122">Explication</span><span class="sxs-lookup"><span data-stu-id="76d18-122">Explanation</span></span>  
 <span data-ttu-id="76d18-123">Cet événement d'avertissement indique qu'une modification de mot de passe externe a été reçue avec des informations d'identification manquantes.</span><span class="sxs-lookup"><span data-stu-id="76d18-123">This Warning event indicates that an external password change was received with missing credentials.</span></span> <span data-ttu-id="76d18-124">Les valeurs par défaut ont été utilisées dans ces champs.</span><span class="sxs-lookup"><span data-stu-id="76d18-124">Default values were used in those fields.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="76d18-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="76d18-125">User Action</span></span>  
 <span data-ttu-id="76d18-126">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="76d18-126">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="76d18-127">Le cas échéant, définissez les informations d'identification manquantes.</span><span class="sxs-lookup"><span data-stu-id="76d18-127">If necessary, set the credentials to match.</span></span>  
  
 <span data-ttu-id="76d18-128">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="76d18-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="76d18-129">Applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="76d18-129">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  
  
-   [<span data-ttu-id="76d18-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="76d18-130">Password Synchronization</span></span>](../core/password-synchronization2.md)