---
title: "Single Sign-On : Événement 10690 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0998f8dc-47de-4dc3-8905-3844177a7c54
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c320db046a61e77577bb6fe2778904ab445f253
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10690"></a><span data-ttu-id="81f7c-102">Single Sign-On : Événement 10690</span><span class="sxs-lookup"><span data-stu-id="81f7c-102">Single Sign-On: Event 10690</span></span>
## <a name="details"></a><span data-ttu-id="81f7c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="81f7c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81f7c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="81f7c-104">Product Name</span></span>|<span data-ttu-id="81f7c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="81f7c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="81f7c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="81f7c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="81f7c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="81f7c-107">Event ID</span></span>|<span data-ttu-id="81f7c-108">10690</span><span class="sxs-lookup"><span data-stu-id="81f7c-108">10690</span></span>|  
|<span data-ttu-id="81f7c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="81f7c-109">Event Source</span></span>|<span data-ttu-id="81f7c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="81f7c-110">ENTSSO</span></span>|  
|<span data-ttu-id="81f7c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="81f7c-111">Component</span></span>|<span data-ttu-id="81f7c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="81f7c-112">N\A</span></span>|  
|<span data-ttu-id="81f7c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="81f7c-113">Symbolic Name</span></span>|<span data-ttu-id="81f7c-114">SSO_ERROR_REPLAY_INCORRECT_RECORD_NUMBER</span><span class="sxs-lookup"><span data-stu-id="81f7c-114">SSO_ERROR_REPLAY_INCORRECT_RECORD_NUMBER</span></span>|  
|<span data-ttu-id="81f7c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="81f7c-115">Message Text</span></span>|<span data-ttu-id="81f7c-116">Le fichier de relecture est endommagé.%r</span><span class="sxs-lookup"><span data-stu-id="81f7c-116">Corruption was detected in the replay file.%r</span></span><br /><br /> <span data-ttu-id="81f7c-117">Fichier de relecture : %1</span><span class="sxs-lookup"><span data-stu-id="81f7c-117">Replay File: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81f7c-118">Explication</span><span class="sxs-lookup"><span data-stu-id="81f7c-118">Explanation</span></span>  
 <span data-ttu-id="81f7c-119">Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu lire le fichier de relecture car celui-ci est endommagé.</span><span class="sxs-lookup"><span data-stu-id="81f7c-119">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to read the replay file because of corruption.</span></span> <span data-ttu-id="81f7c-120">Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="81f7c-120">If SSO cannot open a replay file, it will proceed to the next replay file (if there is one).</span></span>  
  
 <span data-ttu-id="81f7c-121">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="81f7c-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="81f7c-122">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="81f7c-122">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81f7c-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="81f7c-123">User Action</span></span>  
 <span data-ttu-id="81f7c-124">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="81f7c-124">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="81f7c-125">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="81f7c-125">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="81f7c-126">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="81f7c-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="81f7c-127">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="81f7c-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="81f7c-128">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="81f7c-128">Password Synchronization</span></span>](../core/password-synchronization2.md)