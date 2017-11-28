---
title: "Single Sign-On : Événement 10699 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cff26533-e4d7-47b5-92d5-bd8c72fab89a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b6ceb4ffe1e25a3828f406b881d4070b74a8d9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10699"></a><span data-ttu-id="cda98-102">Single Sign-On : Événement 10699</span><span class="sxs-lookup"><span data-stu-id="cda98-102">Single Sign-On: Event 10699</span></span>
## <a name="details"></a><span data-ttu-id="cda98-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cda98-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cda98-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cda98-104">Product Name</span></span>|<span data-ttu-id="cda98-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cda98-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cda98-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cda98-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cda98-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cda98-107">Event ID</span></span>|<span data-ttu-id="cda98-108">10699</span><span class="sxs-lookup"><span data-stu-id="cda98-108">10699</span></span>|  
|<span data-ttu-id="cda98-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cda98-109">Event Source</span></span>|<span data-ttu-id="cda98-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cda98-110">ENTSSO</span></span>|  
|<span data-ttu-id="cda98-111">Composant</span><span class="sxs-lookup"><span data-stu-id="cda98-111">Component</span></span>|<span data-ttu-id="cda98-112">N\A</span><span class="sxs-lookup"><span data-stu-id="cda98-112">N\A</span></span>|  
|<span data-ttu-id="cda98-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cda98-113">Symbolic Name</span></span>|<span data-ttu-id="cda98-114">SSO_INFO_EXTERNAL_PASSWORD_CHANGE_RECEIVED_REPLAY</span><span class="sxs-lookup"><span data-stu-id="cda98-114">SSO_INFO_EXTERNAL_PASSWORD_CHANGE_RECEIVED_REPLAY</span></span>|  
|<span data-ttu-id="cda98-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cda98-115">Message Text</span></span>|<span data-ttu-id="cda98-116">Une modification de mot de passe externe a été reçue depuis un adaptateur (depuis un fichier de reprise).%r</span><span class="sxs-lookup"><span data-stu-id="cda98-116">An external password change was received from an adapter (from replay file).%r</span></span><br /><br /> <span data-ttu-id="cda98-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="cda98-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="cda98-118">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="cda98-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="cda98-119">Compte externe : %3 %r</span><span class="sxs-lookup"><span data-stu-id="cda98-119">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="cda98-120">L’utilisateur client : %4 %r</span><span class="sxs-lookup"><span data-stu-id="cda98-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="cda98-121">Enregistrer le nombre : %5</span><span class="sxs-lookup"><span data-stu-id="cda98-121">Record Number: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cda98-122">Explication</span><span class="sxs-lookup"><span data-stu-id="cda98-122">Explanation</span></span>  
 <span data-ttu-id="cda98-123">Cette information indique qu'un mot de passe externe a été reçu depuis un adaptateur enregistré dans un fichier de reprise.</span><span class="sxs-lookup"><span data-stu-id="cda98-123">This Information event indicates that an external password change was received from an adapter that was recorded to a replay file.</span></span> <span data-ttu-id="cda98-124">SSO effectue de nouveau des modifications du mot de passe externe stocké à partir du fichier de reprise.</span><span class="sxs-lookup"><span data-stu-id="cda98-124">SSO is replaying the stored external password changes from the replay file.</span></span>  
  
 <span data-ttu-id="cda98-125">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="cda98-125">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="cda98-126">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="cda98-126">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cda98-127">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cda98-127">User Action</span></span>  
  
-   <span data-ttu-id="cda98-128">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cda98-128">No user action is necessary.</span></span>  
  
 <span data-ttu-id="cda98-129">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="cda98-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="cda98-130">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cda98-130">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="cda98-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cda98-131">Password Synchronization</span></span>](../core/password-synchronization2.md)