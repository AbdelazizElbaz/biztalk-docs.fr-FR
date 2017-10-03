---
title: "Single Sign-On : Événement 10685 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47844a979e93789f4baa94fbcbd58fd23762db84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10685"></a><span data-ttu-id="8469f-102">Single Sign-On : Événement 10685</span><span class="sxs-lookup"><span data-stu-id="8469f-102">Single Sign-On: Event 10685</span></span>
## <a name="details"></a><span data-ttu-id="8469f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8469f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8469f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8469f-104">Product Name</span></span>|<span data-ttu-id="8469f-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8469f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8469f-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8469f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8469f-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8469f-107">Event ID</span></span>|<span data-ttu-id="8469f-108">10685</span><span class="sxs-lookup"><span data-stu-id="8469f-108">10685</span></span>|  
|<span data-ttu-id="8469f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8469f-109">Event Source</span></span>|<span data-ttu-id="8469f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8469f-110">ENTSSO</span></span>|  
|<span data-ttu-id="8469f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8469f-111">Component</span></span>|<span data-ttu-id="8469f-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8469f-112">N\A</span></span>|  
|<span data-ttu-id="8469f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8469f-113">Symbolic Name</span></span>|<span data-ttu-id="8469f-114">SSO_WARN_REPLAY_CANNOT_OPEN</span><span class="sxs-lookup"><span data-stu-id="8469f-114">SSO_WARN_REPLAY_CANNOT_OPEN</span></span>|  
|<span data-ttu-id="8469f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8469f-115">Message Text</span></span>|<span data-ttu-id="8469f-116">Impossible d'ouvrir le fichier de relecture ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="8469f-116">Could not open the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="8469f-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="8469f-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="8469f-118">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="8469f-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8469f-119">Explication</span><span class="sxs-lookup"><span data-stu-id="8469f-119">Explanation</span></span>  
 <span data-ttu-id="8469f-120">Cet événement d'avertissement indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu ouvrir le fichier de relecture ou de progression.</span><span class="sxs-lookup"><span data-stu-id="8469f-120">This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to open the replay or progress file.</span></span> <span data-ttu-id="8469f-121">Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant.</span><span class="sxs-lookup"><span data-stu-id="8469f-121">If SSO cannot open a replay file, it will proceed to the next replay file.</span></span>  
  
 <span data-ttu-id="8469f-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="8469f-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="8469f-123">Un fichier de progression indique jusqu'à quel point l'authentification unique a pu lire le fichier de relecture au cas où le contact avec la base de données SSO est à nouveau perdu pendant la relecture du fichier.</span><span class="sxs-lookup"><span data-stu-id="8469f-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is lost again part-way through playing back of a replay file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8469f-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8469f-124">User Action</span></span>  
 <span data-ttu-id="8469f-125">Pour résoudre cet événement d’avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8469f-125">To resolve this Warning event, do the following:</span></span>  
  
-   <span data-ttu-id="8469f-126">Vous devez rechercher les événements associés dans les journaux des événements système et de l'application pour déterminer la raison pour laquelle l'authentification unique n'a pas pu contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="8469f-126">You should check the System and Application Event logs for associated events to determine why SSO was unable to contact the SSO database.</span></span>  
  
 <span data-ttu-id="8469f-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8469f-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8469f-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8469f-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="8469f-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8469f-129">Password Synchronization</span></span>](../core/password-synchronization2.md)