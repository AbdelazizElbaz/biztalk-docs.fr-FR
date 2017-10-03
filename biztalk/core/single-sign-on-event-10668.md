---
title: "Single Sign-On : Événement 10668 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eb3dd4d-04b5-4713-93c1-76af012d6920
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 006855842ea2d789290200d5c5a9692b6e046e8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10668"></a><span data-ttu-id="71db4-102">Single Sign-On : Événement 10668</span><span class="sxs-lookup"><span data-stu-id="71db4-102">Single Sign-On: Event 10668</span></span>
## <a name="details"></a><span data-ttu-id="71db4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="71db4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71db4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="71db4-104">Product Name</span></span>|<span data-ttu-id="71db4-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="71db4-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="71db4-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="71db4-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="71db4-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="71db4-107">Event ID</span></span>|<span data-ttu-id="71db4-108">10668</span><span class="sxs-lookup"><span data-stu-id="71db4-108">10668</span></span>|  
|<span data-ttu-id="71db4-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="71db4-109">Event Source</span></span>|<span data-ttu-id="71db4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="71db4-110">ENTSSO</span></span>|  
|<span data-ttu-id="71db4-111">Composant</span><span class="sxs-lookup"><span data-stu-id="71db4-111">Component</span></span>|<span data-ttu-id="71db4-112">N\A</span><span class="sxs-lookup"><span data-stu-id="71db4-112">N\A</span></span>|  
|<span data-ttu-id="71db4-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="71db4-113">Symbolic Name</span></span>|<span data-ttu-id="71db4-114">SSO_WARN_NO_OLD_WINDOWS_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="71db4-114">SSO_WARN_NO_OLD_WINDOWS_PASSWORD</span></span>|  
|<span data-ttu-id="71db4-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="71db4-115">Message Text</span></span>|<span data-ttu-id="71db4-116">Impossible de modifier le mot de passe Windows car l'ancien mot de passe Windows pour ce compte n'est pas disponible dans la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="71db4-116">Cannot change the Windows password because the old Windows password for this account is not available in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="71db4-117">Utilisez les outils d'administration SSO afin de définir les informations d'identification externes pour ce compte Windows.%r</span><span class="sxs-lookup"><span data-stu-id="71db4-117">Use the SSO administration tools to set the external credentials for this Windows account.%r</span></span><br /><br /> <span data-ttu-id="71db4-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="71db4-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="71db4-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="71db4-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="71db4-120">Compte Windows : %3</span><span class="sxs-lookup"><span data-stu-id="71db4-120">Windows Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71db4-121">Explication</span><span class="sxs-lookup"><span data-stu-id="71db4-121">Explanation</span></span>  
 <span data-ttu-id="71db4-122">Cet événement d'avertissement indique que la synchronisation des mots de passe ne peut pas modifier le mot de passe Windows car l'ancien mot de passe Windows pour ce compte n'est pas disponible dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="71db4-122">This Warning event indicates that Password Sync cannot change the Windows password because the old Windows password for this account is not available in the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71db4-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="71db4-123">User Action</span></span>  
 <span data-ttu-id="71db4-124">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="71db4-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="71db4-125">Identifiez les applications affectées à cet adaptateur (nom dans le message du journal des événements), puis définissez les informations d'identification externes pour ce compte Windows à l'aide des outils d'administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="71db4-125">Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this Windows account.</span></span> <span data-ttu-id="71db4-126">Vous devez définir le mot de passe externe (pour le compte Windows donné) dans toutes ces applications.</span><span class="sxs-lookup"><span data-stu-id="71db4-126">You must set the external password (for the given Windows Account) in all of those Applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="71db4-127">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="71db4-127">More info</span></span>
  
-   [<span data-ttu-id="71db4-128">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="71db4-128">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="71db4-129">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="71db4-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>