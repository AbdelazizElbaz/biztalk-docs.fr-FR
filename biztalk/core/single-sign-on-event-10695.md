---
title: "Single Sign-On : Événement 10695 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02c5dc1d-5626-4d24-ac4f-fcd2ae61cd98
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59c0b19fb479dd55980898e64783eecf44d438fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10695"></a><span data-ttu-id="8e8bc-102">Single Sign-On : Événement 10695</span><span class="sxs-lookup"><span data-stu-id="8e8bc-102">Single Sign-On: Event 10695</span></span>
## <a name="details"></a><span data-ttu-id="8e8bc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8e8bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e8bc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8e8bc-104">Product Name</span></span>|<span data-ttu-id="8e8bc-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8e8bc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8e8bc-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8e8bc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8e8bc-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8e8bc-107">Event ID</span></span>|<span data-ttu-id="8e8bc-108">10695</span><span class="sxs-lookup"><span data-stu-id="8e8bc-108">10695</span></span>|  
|<span data-ttu-id="8e8bc-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8e8bc-109">Event Source</span></span>|<span data-ttu-id="8e8bc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8e8bc-110">ENTSSO</span></span>|  
|<span data-ttu-id="8e8bc-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8e8bc-111">Component</span></span>|<span data-ttu-id="8e8bc-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8e8bc-112">N\A</span></span>|  
|<span data-ttu-id="8e8bc-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8e8bc-113">Symbolic Name</span></span>|<span data-ttu-id="8e8bc-114">SSO_ERROR_REPLAY_INCORRECT_FILE_NAME</span><span class="sxs-lookup"><span data-stu-id="8e8bc-114">SSO_ERROR_REPLAY_INCORRECT_FILE_NAME</span></span>|  
|<span data-ttu-id="8e8bc-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8e8bc-115">Message Text</span></span>|<span data-ttu-id="8e8bc-116">Des données endommagées ont été détectées dans le fichier de reprise ou de progression.%r</span><span class="sxs-lookup"><span data-stu-id="8e8bc-116">Corruption was detected in the replay or progress file.%r</span></span><br /><br /> <span data-ttu-id="8e8bc-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="8e8bc-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="8e8bc-118">Déchiffrer le nom de fichier : %2</span><span class="sxs-lookup"><span data-stu-id="8e8bc-118">Decrypted File Name: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8e8bc-119">Explication</span><span class="sxs-lookup"><span data-stu-id="8e8bc-119">Explanation</span></span>  
 <span data-ttu-id="8e8bc-120">Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu lire le fichier de relecture car celui-ci est endommagé.</span><span class="sxs-lookup"><span data-stu-id="8e8bc-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="8e8bc-121">Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="8e8bc-121">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="8e8bc-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="8e8bc-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="8e8bc-123">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="8e8bc-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8e8bc-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8e8bc-124">User Action</span></span>  
 <span data-ttu-id="8e8bc-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8e8bc-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="8e8bc-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="8e8bc-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="8e8bc-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="8e8bc-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="8e8bc-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8e8bc-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="8e8bc-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8e8bc-129">Password Synchronization</span></span>](../core/password-synchronization2.md)