---
title: "Single Sign-On : Événement 10686 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3e71f2a-e51d-4736-b06a-117142d30dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600226ef7440b8be9d7927481170291b6c63faae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10686"></a><span data-ttu-id="646d8-102">Single Sign-On : Événement 10686</span><span class="sxs-lookup"><span data-stu-id="646d8-102">Single Sign-On: Event 10686</span></span>
## <a name="details"></a><span data-ttu-id="646d8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="646d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="646d8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="646d8-104">Product Name</span></span>|<span data-ttu-id="646d8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="646d8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="646d8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="646d8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="646d8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="646d8-107">Event ID</span></span>|<span data-ttu-id="646d8-108">10686</span><span class="sxs-lookup"><span data-stu-id="646d8-108">10686</span></span>|  
|<span data-ttu-id="646d8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="646d8-109">Event Source</span></span>|<span data-ttu-id="646d8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="646d8-110">ENTSSO</span></span>|  
|<span data-ttu-id="646d8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="646d8-111">Component</span></span>|<span data-ttu-id="646d8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="646d8-112">N\A</span></span>|  
|<span data-ttu-id="646d8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="646d8-113">Symbolic Name</span></span>|<span data-ttu-id="646d8-114">SSO_INFO_REPLAY_STARTED</span><span class="sxs-lookup"><span data-stu-id="646d8-114">SSO_INFO_REPLAY_STARTED</span></span>|  
|<span data-ttu-id="646d8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="646d8-115">Message Text</span></span>|<span data-ttu-id="646d8-116">Relecture des modifications de mot de passe externe stocké.%r</span><span class="sxs-lookup"><span data-stu-id="646d8-116">Replaying stored external password changes.%r</span></span><br /><br /> <span data-ttu-id="646d8-117">Fichier de relecture : %1</span><span class="sxs-lookup"><span data-stu-id="646d8-117">Replay File: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="646d8-118">Explication</span><span class="sxs-lookup"><span data-stu-id="646d8-118">Explanation</span></span>  
 <span data-ttu-id="646d8-119">Cet événement d'informations indique que l'authentification unique relit le fichier des modifications de mot de passe externe stocké.</span><span class="sxs-lookup"><span data-stu-id="646d8-119">This Information event indicates that SSO is replaying the stored external password changes file.</span></span> <span data-ttu-id="646d8-120">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="646d8-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="646d8-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="646d8-121">User Action</span></span>  
  
-   <span data-ttu-id="646d8-122">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="646d8-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="646d8-123">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="646d8-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="646d8-124">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="646d8-124">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="646d8-125">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="646d8-125">Password Synchronization</span></span>](../core/password-synchronization2.md)