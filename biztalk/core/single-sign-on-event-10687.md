---
title: "Single Sign-On : Événement 10687 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b3fe2c-a7ba-47e1-a753-4eaa64b01a60
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 368e9bbad42e49ebd71bc1a581b0fb18bbcc2d5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10687"></a><span data-ttu-id="6ab38-102">Single Sign-On : Événement 10687</span><span class="sxs-lookup"><span data-stu-id="6ab38-102">Single Sign-On: Event 10687</span></span>
## <a name="details"></a><span data-ttu-id="6ab38-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6ab38-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ab38-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6ab38-104">Product Name</span></span>|<span data-ttu-id="6ab38-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="6ab38-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6ab38-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6ab38-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6ab38-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6ab38-107">Event ID</span></span>|<span data-ttu-id="6ab38-108">10687</span><span class="sxs-lookup"><span data-stu-id="6ab38-108">10687</span></span>|  
|<span data-ttu-id="6ab38-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6ab38-109">Event Source</span></span>|<span data-ttu-id="6ab38-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6ab38-110">ENTSSO</span></span>|  
|<span data-ttu-id="6ab38-111">Composant</span><span class="sxs-lookup"><span data-stu-id="6ab38-111">Component</span></span>|<span data-ttu-id="6ab38-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6ab38-112">N\A</span></span>|  
|<span data-ttu-id="6ab38-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6ab38-113">Symbolic Name</span></span>|<span data-ttu-id="6ab38-114">SSO_INFO_REPLAY_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="6ab38-114">SSO_INFO_REPLAY_COMPLETE</span></span>|  
|<span data-ttu-id="6ab38-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6ab38-115">Message Text</span></span>|<span data-ttu-id="6ab38-116">La relecture des modifications de mot de passe externe stocké est terminée.%r</span><span class="sxs-lookup"><span data-stu-id="6ab38-116">Replay of stored external password changes completed.%r</span></span><br /><br /> <span data-ttu-id="6ab38-117">Fichier de relecture : %1 %r</span><span class="sxs-lookup"><span data-stu-id="6ab38-117">Replay File: %1%r</span></span><br /><br /> <span data-ttu-id="6ab38-118">Données supplémentaires : %2</span><span class="sxs-lookup"><span data-stu-id="6ab38-118">Additional Data: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ab38-119">Explication</span><span class="sxs-lookup"><span data-stu-id="6ab38-119">Explanation</span></span>  
 <span data-ttu-id="6ab38-120">Cet événement d'informations indique que l'authentification unique a terminé de relire le fichier des modifications de mot de passe externe stocké.</span><span class="sxs-lookup"><span data-stu-id="6ab38-120">This Information event indicates that SSO has completed replaying the stored external password changes file.</span></span> <span data-ttu-id="6ab38-121">Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="6ab38-121">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ab38-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6ab38-122">User Action</span></span>  
  
-   <span data-ttu-id="6ab38-123">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6ab38-123">No user action is necessary.</span></span>  
  
 <span data-ttu-id="6ab38-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="6ab38-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="6ab38-125">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="6ab38-125">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="6ab38-126">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="6ab38-126">Password Synchronization</span></span>](../core/password-synchronization2.md)