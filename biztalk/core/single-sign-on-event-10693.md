---
title: "Single Sign-On : Événement 10693 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672bac7d-0ccc-4a42-a49d-57e387f4cf3a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f653af187e7ca36f45418e724fb73a2c6b1b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10693"></a><span data-ttu-id="e5abe-102">Single Sign-On : Événement 10693</span><span class="sxs-lookup"><span data-stu-id="e5abe-102">Single Sign-On: Event 10693</span></span>
## <a name="details"></a><span data-ttu-id="e5abe-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e5abe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5abe-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e5abe-104">Product Name</span></span>|<span data-ttu-id="e5abe-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e5abe-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e5abe-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e5abe-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e5abe-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e5abe-107">Event ID</span></span>|<span data-ttu-id="e5abe-108">10693</span><span class="sxs-lookup"><span data-stu-id="e5abe-108">10693</span></span>|  
|<span data-ttu-id="e5abe-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e5abe-109">Event Source</span></span>|<span data-ttu-id="e5abe-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e5abe-110">ENTSSO</span></span>|  
|<span data-ttu-id="e5abe-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e5abe-111">Component</span></span>|<span data-ttu-id="e5abe-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e5abe-112">N\A</span></span>|  
|<span data-ttu-id="e5abe-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e5abe-113">Symbolic Name</span></span>|<span data-ttu-id="e5abe-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span><span class="sxs-lookup"><span data-stu-id="e5abe-114">SSO_WARNING_REPLAY_CANNOT_CREATE</span></span>|  
|<span data-ttu-id="e5abe-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e5abe-115">Message Text</span></span>|<span data-ttu-id="e5abe-116">Impossible de créer le fichier de relecture ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="e5abe-116">Could not create the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="e5abe-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="e5abe-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="e5abe-118">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="e5abe-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e5abe-119">Explication</span><span class="sxs-lookup"><span data-stu-id="e5abe-119">Explanation</span></span>  
 <span data-ttu-id="e5abe-120">Cet événement d'avertissement indique que l'authentification unique n'a pas pu créer un fichier de relecture et/ou de progression après la perte de la connexion à la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="e5abe-120">This Warning event indicates that SSO was unable to create a replay and\or progress file when connection to the SSO database was lost.</span></span>  
  
 <span data-ttu-id="e5abe-121">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="e5abe-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="e5abe-122">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="e5abe-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5abe-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e5abe-123">User Action</span></span>  
 <span data-ttu-id="e5abe-124">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e5abe-124">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="e5abe-125">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="e5abe-125">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="e5abe-126">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="e5abe-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="e5abe-127">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="e5abe-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="e5abe-128">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="e5abe-128">Password Synchronization</span></span>](../core/password-synchronization2.md)