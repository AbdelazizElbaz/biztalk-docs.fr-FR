---
title: "Single Sign-On : Événement 10697 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4263ecbd-939e-4374-b0b6-aada3b2af900
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c2c130a3e3473933939d896ab9c4714865bf62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10697"></a><span data-ttu-id="78aa8-102">Single Sign-On : Événement 10697</span><span class="sxs-lookup"><span data-stu-id="78aa8-102">Single Sign-On: Event 10697</span></span>
## <a name="details"></a><span data-ttu-id="78aa8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="78aa8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78aa8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="78aa8-104">Product Name</span></span>|<span data-ttu-id="78aa8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="78aa8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="78aa8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="78aa8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="78aa8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="78aa8-107">Event ID</span></span>|<span data-ttu-id="78aa8-108">10697</span><span class="sxs-lookup"><span data-stu-id="78aa8-108">10697</span></span>|  
|<span data-ttu-id="78aa8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="78aa8-109">Event Source</span></span>|<span data-ttu-id="78aa8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="78aa8-110">ENTSSO</span></span>|  
|<span data-ttu-id="78aa8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="78aa8-111">Component</span></span>|<span data-ttu-id="78aa8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="78aa8-112">N\A</span></span>|  
|<span data-ttu-id="78aa8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="78aa8-113">Symbolic Name</span></span>|<span data-ttu-id="78aa8-114">SSO_ERROR_PROGRESS_FILE_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="78aa8-114">SSO_ERROR_PROGRESS_FILE_MISMATCH</span></span>|  
|<span data-ttu-id="78aa8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="78aa8-115">Message Text</span></span>|<span data-ttu-id="78aa8-116">Le fichier de progression est endommagé.%r</span><span class="sxs-lookup"><span data-stu-id="78aa8-116">Corruption was detected in the progress file.%r</span></span><br /><br /> <span data-ttu-id="78aa8-117">Fichier de relecture : %1 %r</span><span class="sxs-lookup"><span data-stu-id="78aa8-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="78aa8-118">Données supplémentaires : %2</span><span class="sxs-lookup"><span data-stu-id="78aa8-118">Additional Data: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78aa8-119">Explication</span><span class="sxs-lookup"><span data-stu-id="78aa8-119">Explanation</span></span>  
 <span data-ttu-id="78aa8-120">Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu ouvrir le fichier de progression en raison d'une incohérence avec le fichier de relecture correspondant.</span><span class="sxs-lookup"><span data-stu-id="78aa8-120">This Error event indicates that SSO has re-established contact with the SSO database, but was unable to open the progress file because of a mismatch with the corresponding replay file.</span></span> <span data-ttu-id="78aa8-121">Si l'authentification unique ne peut pas ouvrir un fichier de progression, elle commence à l'enregistrement de début du premier fichier de relecture.</span><span class="sxs-lookup"><span data-stu-id="78aa8-121">If SSO cannot open a progress file, it will start at the beginning record of the first replay file.</span></span>  
  
 <span data-ttu-id="78aa8-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="78aa8-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="78aa8-123">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="78aa8-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78aa8-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="78aa8-124">User Action</span></span>  
 <span data-ttu-id="78aa8-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="78aa8-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="78aa8-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="78aa8-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="78aa8-127">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="78aa8-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="78aa8-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="78aa8-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="78aa8-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="78aa8-129">Password Synchronization</span></span>](../core/password-synchronization2.md)