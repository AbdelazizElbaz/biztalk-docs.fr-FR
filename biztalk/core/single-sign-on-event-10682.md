---
title: "Single Sign-On : Événement 10682 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79aeff556fbbbbbbbcf41f63a37ab3b47311d697
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10682"></a><span data-ttu-id="a6c0b-102">Single Sign-On : Événement 10682</span><span class="sxs-lookup"><span data-stu-id="a6c0b-102">Single Sign-On: Event 10682</span></span>
## <a name="details"></a><span data-ttu-id="a6c0b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a6c0b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6c0b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a6c0b-104">Product Name</span></span>|<span data-ttu-id="a6c0b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a6c0b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a6c0b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a6c0b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a6c0b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a6c0b-107">Event ID</span></span>|<span data-ttu-id="a6c0b-108">10682</span><span class="sxs-lookup"><span data-stu-id="a6c0b-108">10682</span></span>|  
|<span data-ttu-id="a6c0b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a6c0b-109">Event Source</span></span>|<span data-ttu-id="a6c0b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a6c0b-110">ENTSSO</span></span>|  
|<span data-ttu-id="a6c0b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a6c0b-111">Component</span></span>|<span data-ttu-id="a6c0b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a6c0b-112">N\A</span></span>|  
|<span data-ttu-id="a6c0b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a6c0b-113">Symbolic Name</span></span>|<span data-ttu-id="a6c0b-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span><span class="sxs-lookup"><span data-stu-id="a6c0b-114">SSO_WARN_REPLAY_INVALID_DIR_FOUND</span></span>|  
|<span data-ttu-id="a6c0b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a6c0b-115">Message Text</span></span>|<span data-ttu-id="a6c0b-116">Un répertoire a été trouvé dans le répertoire de fichiers de reprise - il sera ignored.%r</span><span class="sxs-lookup"><span data-stu-id="a6c0b-116">A directory was found in the replay files directory - it will be ignored.%r</span></span><br /><span data-ttu-id="a6c0b-117">Répertoire : %1</span><span class="sxs-lookup"><span data-stu-id="a6c0b-117">Directory: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a6c0b-118">Explication</span><span class="sxs-lookup"><span data-stu-id="a6c0b-118">Explanation</span></span>  
 <span data-ttu-id="a6c0b-119">Cet événement d'avertissement indique qu'un répertoire a été détecté dans le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-119">This Warning event indicates that a directory was found in the replay files directory.</span></span> <span data-ttu-id="a6c0b-120">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="a6c0b-121">Dans ce cas, les modifications de mot de passe sont stockées dans un fichier chiffré temporaire et relues dans la base de données de l’authentification unique lorsqu’il est disponible.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-121">In this case the password changes are stored in a temporary encrypted file, and are replayed back to the SSO database when it becomes available again.</span></span> <span data-ttu-id="a6c0b-122">Le répertoire des fichiers de relecture ne contient habituellement que des fichiers de relecture. Ce message d'erreur est généré si un répertoire est détecté.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-122">The replay files directory is expected to contain only replay files – this error message is issued if a directory is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a6c0b-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6c0b-123">User Action</span></span>  
 <span data-ttu-id="a6c0b-124">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6c0b-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="a6c0b-125">Modifiez votre répertoire de relecture à l'aide de l'outil de ligne de commande ssoconfig -replayFiles.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-125">Use command line tool ssoconfig -replayFiles to  change your replay directory.</span></span>  
  
-   <span data-ttu-id="a6c0b-126">Supprimez le répertoire incorrect si celui-ci n'est pas en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="a6c0b-126">Delete the bad directory if it is not in use.</span></span>  
  
 <span data-ttu-id="a6c0b-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="a6c0b-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="a6c0b-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="a6c0b-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="a6c0b-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="a6c0b-129">Password Synchronization</span></span>](../core/password-synchronization2.md)