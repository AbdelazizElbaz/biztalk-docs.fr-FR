---
title: "Single Sign-On : Événement 10727 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ff7ac94-6f1e-4e56-853e-efc50b1fa1b6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceadb1bc742a11e05e54757b44618020c93b0d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10727"></a><span data-ttu-id="aa14a-102">Single Sign-On : Événement 10727</span><span class="sxs-lookup"><span data-stu-id="aa14a-102">Single Sign-On: Event 10727</span></span>
## <a name="details"></a><span data-ttu-id="aa14a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="aa14a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa14a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="aa14a-104">Product Name</span></span>|<span data-ttu-id="aa14a-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="aa14a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="aa14a-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="aa14a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="aa14a-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="aa14a-107">Event ID</span></span>|<span data-ttu-id="aa14a-108">10727</span><span class="sxs-lookup"><span data-stu-id="aa14a-108">10727</span></span>|  
|<span data-ttu-id="aa14a-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="aa14a-109">Event Source</span></span>|<span data-ttu-id="aa14a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="aa14a-110">ENTSSO</span></span>|  
|<span data-ttu-id="aa14a-111">Composant</span><span class="sxs-lookup"><span data-stu-id="aa14a-111">Component</span></span>|<span data-ttu-id="aa14a-112">N\A</span><span class="sxs-lookup"><span data-stu-id="aa14a-112">N\A</span></span>|  
|<span data-ttu-id="aa14a-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="aa14a-113">Symbolic Name</span></span>|<span data-ttu-id="aa14a-114">SSO_WARN_REPLAY_RECORD_FAILED</span><span class="sxs-lookup"><span data-stu-id="aa14a-114">SSO_WARN_REPLAY_RECORD_FAILED</span></span>|  
|<span data-ttu-id="aa14a-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="aa14a-115">Message Text</span></span>|<span data-ttu-id="aa14a-116">Échec de la relecture de la modification du mot de passe externe stocké.%r</span><span class="sxs-lookup"><span data-stu-id="aa14a-116">Replay of the stored external password change failed.%r</span></span><br /><br /> <span data-ttu-id="aa14a-117">Carte : %1 %r</span><span class="sxs-lookup"><span data-stu-id="aa14a-117">Adapter: %1%r</span></span><br /><br /> <span data-ttu-id="aa14a-118">Nom du fichier : %2 %r</span><span class="sxs-lookup"><span data-stu-id="aa14a-118">File Name: %2%r</span></span><br /><br /> <span data-ttu-id="aa14a-119">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="aa14a-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa14a-120">Explication</span><span class="sxs-lookup"><span data-stu-id="aa14a-120">Explanation</span></span>  
 <span data-ttu-id="aa14a-121">Cet avertissement indique que l'authentification unique n'a pas pu relire une modification de mot de passe enregistrée dans le fichier de relecture.</span><span class="sxs-lookup"><span data-stu-id="aa14a-121">This Warning indicates that SSO was unable to replay a password change recorded in the replay file.</span></span>  
  
 <span data-ttu-id="aa14a-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="aa14a-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="aa14a-123">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="aa14a-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa14a-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="aa14a-124">User Action</span></span>  
 <span data-ttu-id="aa14a-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aa14a-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="aa14a-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="aa14a-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="aa14a-127">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="aa14a-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="aa14a-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="aa14a-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="aa14a-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="aa14a-129">Password Synchronization</span></span>](../core/password-synchronization2.md)