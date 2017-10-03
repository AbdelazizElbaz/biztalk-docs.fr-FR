---
title: "Single Sign-On : Événement 10741 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b6b093-d136-498f-a3b5-c413150da956
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52ad76e20937bfa4af1dbec6d71ba59003874435
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10741"></a><span data-ttu-id="1a823-102">Single Sign-On : Événement 10741</span><span class="sxs-lookup"><span data-stu-id="1a823-102">Single Sign-On: Event 10741</span></span>
## <a name="details"></a><span data-ttu-id="1a823-103">Détails</span><span class="sxs-lookup"><span data-stu-id="1a823-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a823-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="1a823-104">Product Name</span></span>|<span data-ttu-id="1a823-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="1a823-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1a823-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="1a823-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1a823-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1a823-107">Event ID</span></span>|<span data-ttu-id="1a823-108">10741</span><span class="sxs-lookup"><span data-stu-id="1a823-108">10741</span></span>|  
|<span data-ttu-id="1a823-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="1a823-109">Event Source</span></span>|<span data-ttu-id="1a823-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1a823-110">ENTSSO</span></span>|  
|<span data-ttu-id="1a823-111">Composant</span><span class="sxs-lookup"><span data-stu-id="1a823-111">Component</span></span>|<span data-ttu-id="1a823-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1a823-112">N\A</span></span>|  
|<span data-ttu-id="1a823-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="1a823-113">Symbolic Name</span></span>|<span data-ttu-id="1a823-114">SSO_WARN_SAVING_REPLAY_FILE</span><span class="sxs-lookup"><span data-stu-id="1a823-114">SSO_WARN_SAVING_REPLAY_FILE</span></span>|  
|<span data-ttu-id="1a823-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="1a823-115">Message Text</span></span>|<span data-ttu-id="1a823-116">Enregistrement du fichier de relecture ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="1a823-116">Saving replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="1a823-117">Fichier enregistré : %1 %r</span><span class="sxs-lookup"><span data-stu-id="1a823-117">Saved File: %1%r</span></span><br /><br /> <span data-ttu-id="1a823-118">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="1a823-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a823-119">Explication</span><span class="sxs-lookup"><span data-stu-id="1a823-119">Explanation</span></span>  
 <span data-ttu-id="1a823-120">Cet événement d'avertissement indique que l'authentification unique enregistre un fichier de relecture ou de progression.</span><span class="sxs-lookup"><span data-stu-id="1a823-120">This Warning event indicates that SSO is saving a replay or progress file.</span></span>  
  
 <span data-ttu-id="1a823-121">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="1a823-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="1a823-122">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="1a823-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a823-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="1a823-123">User Action</span></span>  
  
-   <span data-ttu-id="1a823-124">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1a823-124">No user action is necessary.</span></span>  
  
 <span data-ttu-id="1a823-125">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1a823-125">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="1a823-126">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="1a823-126">Password Synchronization</span></span>](../core/password-synchronization2.md)