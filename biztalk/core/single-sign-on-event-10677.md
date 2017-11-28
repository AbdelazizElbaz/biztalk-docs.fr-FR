---
title: "Single Sign-On : Événement 10677 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2894792b-e1c9-4c24-875d-9193cbb5cd35
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 876048e9c86cf908be9eda121340ec60354803c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10677"></a><span data-ttu-id="af627-102">Single Sign-On : Événement 10677</span><span class="sxs-lookup"><span data-stu-id="af627-102">Single Sign-On: Event 10677</span></span>
## <a name="details"></a><span data-ttu-id="af627-103">Détails</span><span class="sxs-lookup"><span data-stu-id="af627-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af627-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="af627-104">Product Name</span></span>|<span data-ttu-id="af627-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="af627-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="af627-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="af627-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="af627-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="af627-107">Event ID</span></span>|<span data-ttu-id="af627-108">10677</span><span class="sxs-lookup"><span data-stu-id="af627-108">10677</span></span>|  
|<span data-ttu-id="af627-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="af627-109">Event Source</span></span>|<span data-ttu-id="af627-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="af627-110">ENTSSO</span></span>|  
|<span data-ttu-id="af627-111">Composant</span><span class="sxs-lookup"><span data-stu-id="af627-111">Component</span></span>|<span data-ttu-id="af627-112">N\A</span><span class="sxs-lookup"><span data-stu-id="af627-112">N\A</span></span>|  
|<span data-ttu-id="af627-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="af627-113">Symbolic Name</span></span>|<span data-ttu-id="af627-114">SSO_WARN_NO_EXISTING_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="af627-114">SSO_WARN_NO_EXISTING_PASSWORD</span></span>|  
|<span data-ttu-id="af627-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="af627-115">Message Text</span></span>|<span data-ttu-id="af627-116">Changement du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="af627-116">External password change.</span></span> <span data-ttu-id="af627-117">L'ancien mot de passe ne peut pas être vérifié car il n'y a pas d'informations d'identification pour ce compte externe.%r</span><span class="sxs-lookup"><span data-stu-id="af627-117">The old password cannot be verified because there are no existing credentials for this external account.%r</span></span><br /><br /> <span data-ttu-id="af627-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="af627-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="af627-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="af627-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="af627-120">Nom de l’application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="af627-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="af627-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="af627-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="af627-122">Explication</span><span class="sxs-lookup"><span data-stu-id="af627-122">Explanation</span></span>  
 <span data-ttu-id="af627-123">Cet événement d'avertissement indique qu'un mot de passe externe a été modifié car l'ancien mot de passe n'a pas d'informations d'identification existantes.</span><span class="sxs-lookup"><span data-stu-id="af627-123">This Warning event indicates that an external password change cannot occur because the old password does not have existing credentials.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="af627-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="af627-124">User Action</span></span>  
 <span data-ttu-id="af627-125">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="af627-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="af627-126">Identifiez les applications affectées à cet adaptateur (nom dans le message du journal des événements), puis définissez les informations d'identification externes pour ce compte externe à l'aide des outils d'administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="af627-126">Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this external account.</span></span> <span data-ttu-id="af627-127">Vous devez définir le mot de passe externe (pour le compte donné) dans toutes ces applications.</span><span class="sxs-lookup"><span data-stu-id="af627-127">You must set the external password (for the given account) in all of those Applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="af627-128">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="af627-128">More info</span></span>
  
-   [<span data-ttu-id="af627-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="af627-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="af627-130">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="af627-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>