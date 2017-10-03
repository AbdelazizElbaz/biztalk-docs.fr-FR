---
title: "Single Sign-On : Événement 10723 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00536f3e-26d6-4e19-a98f-e687bb1b6611
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d1bb94e6bb528d58d895b528135674a3e47f83b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10723"></a><span data-ttu-id="cabf3-102">Single Sign-On : Événement 10723</span><span class="sxs-lookup"><span data-stu-id="cabf3-102">Single Sign-On: Event 10723</span></span>
## <a name="details"></a><span data-ttu-id="cabf3-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cabf3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cabf3-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cabf3-104">Product Name</span></span>|<span data-ttu-id="cabf3-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cabf3-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cabf3-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cabf3-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cabf3-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cabf3-107">Event ID</span></span>|<span data-ttu-id="cabf3-108">10723</span><span class="sxs-lookup"><span data-stu-id="cabf3-108">10723</span></span>|  
|<span data-ttu-id="cabf3-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cabf3-109">Event Source</span></span>|<span data-ttu-id="cabf3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cabf3-110">ENTSSO</span></span>|  
|<span data-ttu-id="cabf3-111">Composant</span><span class="sxs-lookup"><span data-stu-id="cabf3-111">Component</span></span>|<span data-ttu-id="cabf3-112">N\A</span><span class="sxs-lookup"><span data-stu-id="cabf3-112">N\A</span></span>|  
|<span data-ttu-id="cabf3-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cabf3-113">Symbolic Name</span></span>|<span data-ttu-id="cabf3-114">SSO_ERROR_REPLAY_SECURITY_1</span><span class="sxs-lookup"><span data-stu-id="cabf3-114">SSO_ERROR_REPLAY_SECURITY_1</span></span>|  
|<span data-ttu-id="cabf3-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cabf3-115">Message Text</span></span>|<span data-ttu-id="cabf3-116">La sécurité du répertoire des fichiers de relecture ne correspond pas à celle du fichier de relecture ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="cabf3-116">The security on the replay files directory does not match the security on the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="cabf3-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="cabf3-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="cabf3-118">Sécurité du fichier : %2 %r</span><span class="sxs-lookup"><span data-stu-id="cabf3-118">File Security: %2%r</span></span><br /><br /> <span data-ttu-id="cabf3-119">Sécurité du répertoire : %3</span><span class="sxs-lookup"><span data-stu-id="cabf3-119">Directory Security: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cabf3-120">Explication</span><span class="sxs-lookup"><span data-stu-id="cabf3-120">Explanation</span></span>  
 <span data-ttu-id="cabf3-121">Cet événement d'erreur indique que la sécurité du répertoire des fichiers de relecture ne correspond pas à celle du fichier de relecture ou de progression.</span><span class="sxs-lookup"><span data-stu-id="cabf3-121">This Error event indicates that the security on the replay files directory does not match the security on the replay or progress file.</span></span>  
  
 <span data-ttu-id="cabf3-122">Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="cabf3-122">Replay files are stored in the replay files directory.</span></span> <span data-ttu-id="cabf3-123">Par défaut, le compte du service d'authentification unique est utilisé pour créer les fichiers de relecture et le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="cabf3-123">By default, the SSO service account is used to create both the replay files and the replay files directory.</span></span> <span data-ttu-id="cabf3-124">L'authentification unique vérifie qu'aucune modification n'a été apportée à la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture depuis leur création.</span><span class="sxs-lookup"><span data-stu-id="cabf3-124">SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created.</span></span> <span data-ttu-id="cabf3-125">Si le répertoire des fichiers de relecture a été créé avec un autre compte, cette erreur peut être renvoyée lorsque la synchronisation des mots de passe tente de créer un fichier de relecture dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="cabf3-125">If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory.</span></span> <span data-ttu-id="cabf3-126">Il est fortement recommandé aux utilisateurs de ne pas modifier la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="cabf3-126">It is strongly recommended that users not change any security configuration of the replay files and replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cabf3-127">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cabf3-127">User Action</span></span>  
 <span data-ttu-id="cabf3-128">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="cabf3-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="cabf3-129">Consultez le compte utilisé pour créer le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="cabf3-129">Check the account used to create the replay files directory.</span></span> <span data-ttu-id="cabf3-130">S'il est vide, réexécutez la synchronisation des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="cabf3-130">If the directory is empty, attempt running password sync again.</span></span> <span data-ttu-id="cabf3-131">Il peut être nécessaire de recréer le répertoire à l'aide du compte de service de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="cabf3-131">It may be necessary to re-create the directory using the same service account as the SSO service.</span></span> <span data-ttu-id="cabf3-132">Si vous ne pouvez pas recréer le répertoire des fichiers de relecture à l'aide de ce compte, consultez les autorisations du compte.</span><span class="sxs-lookup"><span data-stu-id="cabf3-132">If you cannot re-create a replay files directory using the same account as the SSO service, check permissions for that account.</span></span>  
  
 <span data-ttu-id="cabf3-133">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cabf3-133">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="cabf3-134">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cabf3-134">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="cabf3-135">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cabf3-135">Password Synchronization</span></span>](../core/password-synchronization2.md)