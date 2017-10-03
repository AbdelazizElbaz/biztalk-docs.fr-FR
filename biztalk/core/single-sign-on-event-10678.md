---
title: "Single Sign-On : Événement 10678 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6af92ce1-fdac-432f-be6b-cf8958aee776
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daa6639e361abf364e012ec9a4f19f049bbcd08f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10678"></a><span data-ttu-id="e3440-102">Single Sign-On : Événement 10678</span><span class="sxs-lookup"><span data-stu-id="e3440-102">Single Sign-On: Event 10678</span></span>
## <a name="details"></a><span data-ttu-id="e3440-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e3440-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3440-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e3440-104">Product Name</span></span>|<span data-ttu-id="e3440-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e3440-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e3440-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e3440-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e3440-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e3440-107">Event ID</span></span>|<span data-ttu-id="e3440-108">10678</span><span class="sxs-lookup"><span data-stu-id="e3440-108">10678</span></span>|  
|<span data-ttu-id="e3440-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e3440-109">Event Source</span></span>|<span data-ttu-id="e3440-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e3440-110">ENTSSO</span></span>|  
|<span data-ttu-id="e3440-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e3440-111">Component</span></span>|<span data-ttu-id="e3440-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e3440-112">N\A</span></span>|  
|<span data-ttu-id="e3440-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e3440-113">Symbolic Name</span></span>|<span data-ttu-id="e3440-114">SSO_WARN_PASSWORD_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="e3440-114">SSO_WARN_PASSWORD_MISMATCH</span></span>|  
|<span data-ttu-id="e3440-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e3440-115">Message Text</span></span>|<span data-ttu-id="e3440-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="e3440-116">External password change.</span></span> <span data-ttu-id="e3440-117">L'ancien mot de passe fourni par l'adaptateur ne correspond pas au mot de passe existant pour le compte externe.%r</span><span class="sxs-lookup"><span data-stu-id="e3440-117">The old password supplied by the adapter does not match the existing password for the external account.%r</span></span><br /><br /> <span data-ttu-id="e3440-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="e3440-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="e3440-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="e3440-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="e3440-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="e3440-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="e3440-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="e3440-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3440-122">Explication</span><span class="sxs-lookup"><span data-stu-id="e3440-122">Explanation</span></span>  
 <span data-ttu-id="e3440-123">Cet événement d'avertissement indique que l'ancien mot de passe fourni par l'adaptateur ne correspond pas au mot de passe existant pour le compte externe.</span><span class="sxs-lookup"><span data-stu-id="e3440-123">This Warning event indicates that the old password supplied by the adapter does not match the existing password for the external account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3440-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e3440-124">User Action</span></span>  
 <span data-ttu-id="e3440-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e3440-125">To resolve this warning do the following:</span></span>  
  
-   <span data-ttu-id="e3440-126">Identifiez les applications affectées à cet adaptateur (nom dans le message du journal des événements), puis définissez les informations d'identification externes pour ce compte externe à l'aide des outils d'administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="e3440-126">Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this external account.</span></span> <span data-ttu-id="e3440-127">Vous devez définir le mot de passe externe (pour le compte donné) dans toutes ces applications.</span><span class="sxs-lookup"><span data-stu-id="e3440-127">You must set the external password (for the given account) in all of those Applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="e3440-128">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="e3440-128">More info</span></span>
  
-   [<span data-ttu-id="e3440-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="e3440-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="e3440-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="e3440-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>