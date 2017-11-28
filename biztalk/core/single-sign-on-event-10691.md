---
title: "Single Sign-On : Événement 10691 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fcefb49-c068-41e9-850d-99864c0899bf
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da914bff656ff63e65cd041e57e291beea5128e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10691"></a><span data-ttu-id="fee7e-102">Single Sign-On : Événement 10691</span><span class="sxs-lookup"><span data-stu-id="fee7e-102">Single Sign-On: Event 10691</span></span>
## <a name="details"></a><span data-ttu-id="fee7e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="fee7e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fee7e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fee7e-104">Product Name</span></span>|<span data-ttu-id="fee7e-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="fee7e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fee7e-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fee7e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fee7e-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fee7e-107">Event ID</span></span>|<span data-ttu-id="fee7e-108">10691</span><span class="sxs-lookup"><span data-stu-id="fee7e-108">10691</span></span>|  
|<span data-ttu-id="fee7e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fee7e-109">Event Source</span></span>|<span data-ttu-id="fee7e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fee7e-110">ENTSSO</span></span>|  
|<span data-ttu-id="fee7e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="fee7e-111">Component</span></span>|<span data-ttu-id="fee7e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fee7e-112">N\A</span></span>|  
|<span data-ttu-id="fee7e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fee7e-113">Symbolic Name</span></span>|<span data-ttu-id="fee7e-114">SSO_ERROR_REPLAY_FILE_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="fee7e-114">SSO_ERROR_REPLAY_FILE_MISMATCH</span></span>|  
|<span data-ttu-id="fee7e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fee7e-115">Message Text</span></span>|<span data-ttu-id="fee7e-116">Le fichier de relecture est endommagé.%r</span><span class="sxs-lookup"><span data-stu-id="fee7e-116">Corruption was detected in the replay file.%r</span></span><br /><br /> <span data-ttu-id="fee7e-117">Fichier de relecture : %1 %r</span><span class="sxs-lookup"><span data-stu-id="fee7e-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="fee7e-118">Données supplémentaires : %2</span><span class="sxs-lookup"><span data-stu-id="fee7e-118">Additional Data: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fee7e-119">Explication</span><span class="sxs-lookup"><span data-stu-id="fee7e-119">Explanation</span></span>  
 <span data-ttu-id="fee7e-120">Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu ouvrir le fichier de relecture en raison d'une incohérence avec le fichier de progression correspondant.</span><span class="sxs-lookup"><span data-stu-id="fee7e-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to open the replay file because of a mismatch with the corresponding progress file.</span></span> <span data-ttu-id="fee7e-121">Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="fee7e-121">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="fee7e-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="fee7e-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="fee7e-123">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="fee7e-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fee7e-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fee7e-124">User Action</span></span>  
 <span data-ttu-id="fee7e-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fee7e-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="fee7e-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="fee7e-126">Check System and Application event logs for associated events.</span></span>  
  
-   <span data-ttu-id="fee7e-127">Supprimez le fichier de reprise.</span><span class="sxs-lookup"><span data-stu-id="fee7e-127">Delete the replay file.</span></span>  
  
 <span data-ttu-id="fee7e-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="fee7e-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="fee7e-129">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="fee7e-129">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="fee7e-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="fee7e-130">Password Synchronization</span></span>](../core/password-synchronization2.md)