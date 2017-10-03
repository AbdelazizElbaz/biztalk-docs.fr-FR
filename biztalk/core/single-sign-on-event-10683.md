---
title: "Single Sign-On : Événement 10683 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83cd1b96-cd79-4ddc-952b-94a7de216666
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c383a02400523686f00011c5eb6f71c9542ec5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10683"></a><span data-ttu-id="34af0-102">Single Sign-On : Événement 10683</span><span class="sxs-lookup"><span data-stu-id="34af0-102">Single Sign-On: Event 10683</span></span>
## <a name="details"></a><span data-ttu-id="34af0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="34af0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34af0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="34af0-104">Product Name</span></span>|<span data-ttu-id="34af0-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="34af0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="34af0-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="34af0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="34af0-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="34af0-107">Event ID</span></span>|<span data-ttu-id="34af0-108">10683</span><span class="sxs-lookup"><span data-stu-id="34af0-108">10683</span></span>|  
|<span data-ttu-id="34af0-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="34af0-109">Event Source</span></span>|<span data-ttu-id="34af0-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="34af0-110">ENTSSO</span></span>|  
|<span data-ttu-id="34af0-111">Composant</span><span class="sxs-lookup"><span data-stu-id="34af0-111">Component</span></span>|<span data-ttu-id="34af0-112">N\A</span><span class="sxs-lookup"><span data-stu-id="34af0-112">N\A</span></span>|  
|<span data-ttu-id="34af0-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="34af0-113">Symbolic Name</span></span>|<span data-ttu-id="34af0-114">SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD</span><span class="sxs-lookup"><span data-stu-id="34af0-114">SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD</span></span>|  
|<span data-ttu-id="34af0-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="34af0-115">Message Text</span></span>|<span data-ttu-id="34af0-116">Un fichier de relecture a été supprimé car il était trop old.%r</span><span class="sxs-lookup"><span data-stu-id="34af0-116">A replay file was deleted because it was too old.%r</span></span><br /><span data-ttu-id="34af0-117">Fichier de relecture : %1</span><span class="sxs-lookup"><span data-stu-id="34af0-117">Replay File: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="34af0-118">Explication</span><span class="sxs-lookup"><span data-stu-id="34af0-118">Explanation</span></span>  
 <span data-ttu-id="34af0-119">Cet événement d'avertissement indique que le fichier de relecture a été supprimé car il était trop ancien.</span><span class="sxs-lookup"><span data-stu-id="34af0-119">This Warning event indicates that the replay file was deleted because it was too old.</span></span> <span data-ttu-id="34af0-120">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="34af0-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="34af0-121">Dans ce cas, les modifications de mot de passe sont stockées dans un fichier chiffré temporaire et relus dans la base de données SSO lorsque celle-ci redevient disponible.</span><span class="sxs-lookup"><span data-stu-id="34af0-121">In this case the password changes are stored in a temporary encrypted file and are replayed back to the SSO database when it again becomes available.</span></span> <span data-ttu-id="34af0-122">Si un fichier trop ancien est détecté lors de la relecture subséquente des fichiers dans la base de données SSO, il est ignoré.</span><span class="sxs-lookup"><span data-stu-id="34af0-122">When it is time to replay the files back to the SSO database, if a file is detected that is too old, it is discarded.</span></span> <span data-ttu-id="34af0-123">Toutes les modifications de mot de passe anciennes sont ignorées par le système de synchronisation de mot de passe de l’authentification unique ; le `password sync age` paramètre détermine les demandes de modification de la durée de vie maximale pour le mot de passe et qui peut être contrôlé à l’aide des outils de la ligne de commande **ssoconfig – syncAge** ou la console MMC d’administration SSO.</span><span class="sxs-lookup"><span data-stu-id="34af0-123">All old password changes are discarded by the SSO password sync system; the `password sync age` parameter determines the maximum age for password change requests and that can be controlled using the command line tools **ssoconfig –syncAge** or the SSO Admin MMC.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34af0-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="34af0-124">User Action</span></span>  
  
-   <span data-ttu-id="34af0-125">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="34af0-125">No user action is necessary.</span></span>  
  
 <span data-ttu-id="34af0-126">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="34af0-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="34af0-127">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="34af0-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="34af0-128">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="34af0-128">Password Synchronization</span></span>](../core/password-synchronization2.md)