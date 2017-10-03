---
title: "Single Sign-On : Événement 10717 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14691e0f-a399-4b4d-9dd5-516bf8d3a167
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70195251b599daebd50b57f0b137dd026dd032e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10717"></a><span data-ttu-id="6042a-102">Single Sign-On : Événement 10717</span><span class="sxs-lookup"><span data-stu-id="6042a-102">Single Sign-On: Event 10717</span></span>
## <a name="details"></a><span data-ttu-id="6042a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6042a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6042a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6042a-104">Product Name</span></span>|<span data-ttu-id="6042a-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="6042a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6042a-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6042a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6042a-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6042a-107">Event ID</span></span>|<span data-ttu-id="6042a-108">10717</span><span class="sxs-lookup"><span data-stu-id="6042a-108">10717</span></span>|  
|<span data-ttu-id="6042a-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6042a-109">Event Source</span></span>|<span data-ttu-id="6042a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6042a-110">ENTSSO</span></span>|  
|<span data-ttu-id="6042a-111">Composant</span><span class="sxs-lookup"><span data-stu-id="6042a-111">Component</span></span>|<span data-ttu-id="6042a-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6042a-112">N\A</span></span>|  
|<span data-ttu-id="6042a-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6042a-113">Symbolic Name</span></span>|<span data-ttu-id="6042a-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span><span class="sxs-lookup"><span data-stu-id="6042a-114">SSO_ERROR_NEW_REPLAY_DIR_FAILED</span></span>|  
|<span data-ttu-id="6042a-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6042a-115">Message Text</span></span>|<span data-ttu-id="6042a-116">Échec lors de la création du répertoire des fichiers de relecture.%r</span><span class="sxs-lookup"><span data-stu-id="6042a-116">Failed to create the replay files directory.%r</span></span><br /><br /> <span data-ttu-id="6042a-117">L’utilisateur client : %1 %r</span><span class="sxs-lookup"><span data-stu-id="6042a-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="6042a-118">Répertoire des fichiers de relecture : %2 %r</span><span class="sxs-lookup"><span data-stu-id="6042a-118">Replay Files Directory: %2%r</span></span><br /><br /> <span data-ttu-id="6042a-119">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="6042a-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6042a-120">Explication</span><span class="sxs-lookup"><span data-stu-id="6042a-120">Explanation</span></span>  
 <span data-ttu-id="6042a-121">Cet événement d'erreur indique que le répertoire des fichiers de relecture n'a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="6042a-121">This Error event indicates that a replay files directory could not be created.</span></span>  
  
 <span data-ttu-id="6042a-122">Lorsque des modifications de mot de passe sont reçues d'un adaptateur de synchronisation de mot de passe par le service d'authentification unique, ils sont stockés dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="6042a-122">When password changes are received by the SSO service from a password sync adapter, they are stored in the SSO database.</span></span> <span data-ttu-id="6042a-123">Si la base de données SSO est temporairement indisponible, les modifications de mot de passe sont stockées localement dans les fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="6042a-123">If the SSO database is temporarily unavailable, the password changes are stored locally in replay files.</span></span> <span data-ttu-id="6042a-124">Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="6042a-124">Replay files are stored in the replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6042a-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6042a-125">User Action</span></span>  
 <span data-ttu-id="6042a-126">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6042a-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="6042a-127">Consultez le répertoire des fichiers de relecture. S'il n'y en a pas, essayez d'en créer un manuellement à l'aide du compte du service d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="6042a-127">Check the replay files directory, if one does not exist, attempt to create it manually using the same service account as the SSO service.</span></span> <span data-ttu-id="6042a-128">Si vous ne pouvez pas créer le répertoire des fichiers de relecture à l'aide de ce compte, consultez les autorisations du compte.</span><span class="sxs-lookup"><span data-stu-id="6042a-128">If you cannot create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  
  
 <span data-ttu-id="6042a-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6042a-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="6042a-130">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="6042a-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="6042a-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="6042a-131">Password Synchronization</span></span>](../core/password-synchronization2.md)