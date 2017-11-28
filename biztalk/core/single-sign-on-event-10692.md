---
title: "Single Sign-On : Événement 10692 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78a476ca-32eb-4f37-a807-25850503db6e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2dce820864338cd5ba3b8ecf4a469ae75550a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10692"></a><span data-ttu-id="adc68-102">Single Sign-On : Événement 10692</span><span class="sxs-lookup"><span data-stu-id="adc68-102">Single Sign-On: Event 10692</span></span>
## <a name="details"></a><span data-ttu-id="adc68-103">Détails</span><span class="sxs-lookup"><span data-stu-id="adc68-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="adc68-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="adc68-104">Product Name</span></span>|<span data-ttu-id="adc68-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="adc68-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="adc68-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="adc68-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="adc68-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="adc68-107">Event ID</span></span>|<span data-ttu-id="adc68-108">10692</span><span class="sxs-lookup"><span data-stu-id="adc68-108">10692</span></span>|  
|<span data-ttu-id="adc68-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="adc68-109">Event Source</span></span>|<span data-ttu-id="adc68-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="adc68-110">ENTSSO</span></span>|  
|<span data-ttu-id="adc68-111">Composant</span><span class="sxs-lookup"><span data-stu-id="adc68-111">Component</span></span>|<span data-ttu-id="adc68-112">N\A</span><span class="sxs-lookup"><span data-stu-id="adc68-112">N\A</span></span>|  
|<span data-ttu-id="adc68-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="adc68-113">Symbolic Name</span></span>|<span data-ttu-id="adc68-114">SSO_WARN_REPLAY_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="adc68-114">SSO_WARN_REPLAY_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="adc68-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="adc68-115">Message Text</span></span>|<span data-ttu-id="adc68-116">La modification du mot de passe externe ne peut pas être relue car l'appelant d'origine n'est plus membre du compte d'accès pour l'adaptateur.%r</span><span class="sxs-lookup"><span data-stu-id="adc68-116">The external password change cannot be replayed because the original caller is no longer a member of the access account for the adapter.%r</span></span><br /><br /> <span data-ttu-id="adc68-117">Fichier de relecture : %1 %r</span><span class="sxs-lookup"><span data-stu-id="adc68-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="adc68-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="adc68-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="adc68-119">Appelant d’origine : %3 %r</span><span class="sxs-lookup"><span data-stu-id="adc68-119">Original Caller: %3%r</span></span><br /><br /> <span data-ttu-id="adc68-120">Compte d’accès : %4</span><span class="sxs-lookup"><span data-stu-id="adc68-120">Access Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="adc68-121">Explication</span><span class="sxs-lookup"><span data-stu-id="adc68-121">Explanation</span></span>  
 <span data-ttu-id="adc68-122">Cet événement d'avertissement indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu effectuer une modification (dans la base de données SSO) spécifiée dans le fichier de relecture car le compte qui a spécifié la modification à l'origine n'est plus valide.</span><span class="sxs-lookup"><span data-stu-id="adc68-122">This Warning event indicates that SSO has re-established contact with the SSO database, but was unable to make a change (in the SSO database) specified in the replay file because the account that originally specified the change is no longer valid.</span></span>  
  
 <span data-ttu-id="adc68-123">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="adc68-123">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="adc68-124">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="adc68-124">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="adc68-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="adc68-125">User Action</span></span>  
 <span data-ttu-id="adc68-126">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="adc68-126">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="adc68-127">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="adc68-127">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="adc68-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="adc68-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="adc68-129">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="adc68-129">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="adc68-130">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="adc68-130">Password Synchronization</span></span>](../core/password-synchronization2.md)