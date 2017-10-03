---
title: "Single Sign-On : Événement 10743 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2908bc9-1fac-4ab9-869f-0c5512864da4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8368b39ff73307e36a4789d85c9771657bdf8e26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10743"></a><span data-ttu-id="95b04-102">Single Sign-On : Événement 10743</span><span class="sxs-lookup"><span data-stu-id="95b04-102">Single Sign-On: Event 10743</span></span>
## <a name="details"></a><span data-ttu-id="95b04-103">Détails</span><span class="sxs-lookup"><span data-stu-id="95b04-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95b04-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="95b04-104">Product Name</span></span>|<span data-ttu-id="95b04-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="95b04-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="95b04-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="95b04-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="95b04-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="95b04-107">Event ID</span></span>|<span data-ttu-id="95b04-108">10743</span><span class="sxs-lookup"><span data-stu-id="95b04-108">10743</span></span>|  
|<span data-ttu-id="95b04-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="95b04-109">Event Source</span></span>|<span data-ttu-id="95b04-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="95b04-110">ENTSSO</span></span>|  
|<span data-ttu-id="95b04-111">Composant</span><span class="sxs-lookup"><span data-stu-id="95b04-111">Component</span></span>|<span data-ttu-id="95b04-112">N\A</span><span class="sxs-lookup"><span data-stu-id="95b04-112">N\A</span></span>|  
|<span data-ttu-id="95b04-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="95b04-113">Symbolic Name</span></span>|<span data-ttu-id="95b04-114">SSO_ERROR_REPLAY_STOPPED</span><span class="sxs-lookup"><span data-stu-id="95b04-114">SSO_ERROR_REPLAY_STOPPED</span></span>|  
|<span data-ttu-id="95b04-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="95b04-115">Message Text</span></span>|<span data-ttu-id="95b04-116">La relecture des modifications de mot de passe externe stocké s'est arrêtée en raison d'erreurs.%r</span><span class="sxs-lookup"><span data-stu-id="95b04-116">Replay of stored external password changes stopped due to errors.%r</span></span><br /><br /> <span data-ttu-id="95b04-117">Fichier de relecture : %1 %r</span><span class="sxs-lookup"><span data-stu-id="95b04-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="95b04-118">Données supplémentaires : %2 %r</span><span class="sxs-lookup"><span data-stu-id="95b04-118">Additional Data: %2%r</span></span><br /><br /> <span data-ttu-id="95b04-119">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="95b04-119">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95b04-120">Explication</span><span class="sxs-lookup"><span data-stu-id="95b04-120">Explanation</span></span>  
 <span data-ttu-id="95b04-121">Cet événement d'erreur indique que la relecture des modifications de mot de passe externe stocké s'est arrêtée en raison d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="95b04-121">This Error event indicates that replay of stored external password changes stopped due to errors.</span></span>  
  
 <span data-ttu-id="95b04-122">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="95b04-122">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="95b04-123">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="95b04-123">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95b04-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="95b04-124">User Action</span></span>  
 <span data-ttu-id="95b04-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="95b04-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="95b04-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="95b04-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="95b04-127">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="95b04-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="95b04-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="95b04-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="95b04-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="95b04-129">Password Synchronization</span></span>](../core/password-synchronization2.md)