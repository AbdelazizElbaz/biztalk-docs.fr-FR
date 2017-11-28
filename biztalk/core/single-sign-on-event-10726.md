---
title: "Single Sign-On : Événement 10726 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12fbac2d-30ca-4f4c-989b-d770b0f623d9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5784ba85018ab6d02393ca3f684a08b21718ec47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10726"></a><span data-ttu-id="b9bec-102">Single Sign-On : Événement 10726</span><span class="sxs-lookup"><span data-stu-id="b9bec-102">Single Sign-On: Event 10726</span></span>
## <a name="details"></a><span data-ttu-id="b9bec-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b9bec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9bec-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b9bec-104">Product Name</span></span>|<span data-ttu-id="b9bec-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b9bec-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b9bec-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b9bec-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b9bec-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b9bec-107">Event ID</span></span>|<span data-ttu-id="b9bec-108">10726</span><span class="sxs-lookup"><span data-stu-id="b9bec-108">10726</span></span>|  
|<span data-ttu-id="b9bec-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b9bec-109">Event Source</span></span>|<span data-ttu-id="b9bec-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b9bec-110">ENTSSO</span></span>|  
|<span data-ttu-id="b9bec-111">Composant</span><span class="sxs-lookup"><span data-stu-id="b9bec-111">Component</span></span>|<span data-ttu-id="b9bec-112">N\A</span><span class="sxs-lookup"><span data-stu-id="b9bec-112">N\A</span></span>|  
|<span data-ttu-id="b9bec-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b9bec-113">Symbolic Name</span></span>|<span data-ttu-id="b9bec-114">SSO_ERROR_REPLAY_CORRUPTION</span><span class="sxs-lookup"><span data-stu-id="b9bec-114">SSO_ERROR_REPLAY_CORRUPTION</span></span>|  
|<span data-ttu-id="b9bec-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b9bec-115">Message Text</span></span>|<span data-ttu-id="b9bec-116">Des données endommagées ont été détectées dans le fichier de reprise ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="b9bec-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="b9bec-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="b9bec-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="b9bec-118">Données supplémentaires : %2 %r</span><span class="sxs-lookup"><span data-stu-id="b9bec-118">Additional Data: %2%r</span></span><br /><br /> <span data-ttu-id="b9bec-119">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="b9bec-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b9bec-120">Explication</span><span class="sxs-lookup"><span data-stu-id="b9bec-120">Explanation</span></span>  
 <span data-ttu-id="b9bec-121">Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu lire le fichier de relecture car celui-ci est endommagé.</span><span class="sxs-lookup"><span data-stu-id="b9bec-121">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="b9bec-122">Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="b9bec-122">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="b9bec-123">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="b9bec-123">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="b9bec-124">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="b9bec-124">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b9bec-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b9bec-125">User Action</span></span>  
 <span data-ttu-id="b9bec-126">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b9bec-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="b9bec-127">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="b9bec-127">Check System and Application event logs for associated events.</span></span>  
  
-   <span data-ttu-id="b9bec-128">Supprimez le fichier de reprise.</span><span class="sxs-lookup"><span data-stu-id="b9bec-128">Delete the replay file.</span></span>  
  
 <span data-ttu-id="b9bec-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b9bec-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="b9bec-130">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="b9bec-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="b9bec-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="b9bec-131">Password Synchronization</span></span>](../core/password-synchronization2.md)