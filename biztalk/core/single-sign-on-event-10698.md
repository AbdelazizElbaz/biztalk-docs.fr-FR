---
title: "Single Sign-On : Événement 10698 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f467934d-fef5-4962-a341-18f272d84108
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ca4d65927e7e9d01f7c73eb64a19bc613496f5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10698"></a><span data-ttu-id="0d31f-102">Single Sign-On : Événement 10698</span><span class="sxs-lookup"><span data-stu-id="0d31f-102">Single Sign-On: Event 10698</span></span>
## <a name="details"></a><span data-ttu-id="0d31f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0d31f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d31f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0d31f-104">Product Name</span></span>|<span data-ttu-id="0d31f-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="0d31f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="0d31f-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0d31f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="0d31f-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0d31f-107">Event ID</span></span>|<span data-ttu-id="0d31f-108">10698</span><span class="sxs-lookup"><span data-stu-id="0d31f-108">10698</span></span>|  
|<span data-ttu-id="0d31f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0d31f-109">Event Source</span></span>|<span data-ttu-id="0d31f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0d31f-110">ENTSSO</span></span>|  
|<span data-ttu-id="0d31f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="0d31f-111">Component</span></span>|<span data-ttu-id="0d31f-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0d31f-112">N\A</span></span>|  
|<span data-ttu-id="0d31f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0d31f-113">Symbolic Name</span></span>|<span data-ttu-id="0d31f-114">SSO_INFO_REPLAY_FILE_DELETED</span><span class="sxs-lookup"><span data-stu-id="0d31f-114">SSO_INFO_REPLAY_FILE_DELETED</span></span>|  
|<span data-ttu-id="0d31f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0d31f-115">Message Text</span></span>|<span data-ttu-id="0d31f-116">Le fichier de reprise ou de progression a été supprimé.%r</span><span class="sxs-lookup"><span data-stu-id="0d31f-116">The replay or progress file was deleted.%r</span></span><br /><br /> <span data-ttu-id="0d31f-117">Nom du fichier : %1</span><span class="sxs-lookup"><span data-stu-id="0d31f-117">File Name: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d31f-118">Explication</span><span class="sxs-lookup"><span data-stu-id="0d31f-118">Explanation</span></span>  
 <span data-ttu-id="0d31f-119">Cette information indique que le système SSO a supprimé un fichier de reprise et/ou de progression.</span><span class="sxs-lookup"><span data-stu-id="0d31f-119">This Information event indicates that SSO has deleted a replay and\or progress file.</span></span>  
  
 <span data-ttu-id="0d31f-120">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="0d31f-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="0d31f-121">Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.</span><span class="sxs-lookup"><span data-stu-id="0d31f-121">A progress file indicates how far through SSO was able to read the replay file in-case contact with the SSO database is again lost.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d31f-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0d31f-122">User Action</span></span>  
  
-   <span data-ttu-id="0d31f-123">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0d31f-123">No user action is necessary.</span></span>  
  
 <span data-ttu-id="0d31f-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0d31f-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="0d31f-125">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="0d31f-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="0d31f-126">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="0d31f-126">Password Synchronization</span></span>](../core/password-synchronization2.md)