---
title: "Single Sign-On : Événement 11043 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128d68fb-1905-49b3-9b67-30a9442569cc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc211e4726c68a16f860dd0431a234765e80b76a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11043"></a><span data-ttu-id="48af0-102">Single Sign-On : Événement 11043</span><span class="sxs-lookup"><span data-stu-id="48af0-102">Single Sign-On: Event 11043</span></span>
## <a name="details"></a><span data-ttu-id="48af0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="48af0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48af0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="48af0-104">Product Name</span></span>|<span data-ttu-id="48af0-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="48af0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="48af0-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="48af0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="48af0-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="48af0-107">Event ID</span></span>|<span data-ttu-id="48af0-108">11043</span><span class="sxs-lookup"><span data-stu-id="48af0-108">11043</span></span>|  
|<span data-ttu-id="48af0-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="48af0-109">Event Source</span></span>|<span data-ttu-id="48af0-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="48af0-110">ENTSSO</span></span>|  
|<span data-ttu-id="48af0-111">Composant</span><span class="sxs-lookup"><span data-stu-id="48af0-111">Component</span></span>|<span data-ttu-id="48af0-112">Néant</span><span class="sxs-lookup"><span data-stu-id="48af0-112">N/A</span></span>|  
|<span data-ttu-id="48af0-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="48af0-113">Symbolic Name</span></span>|<span data-ttu-id="48af0-114">SSO_WARN_PS_ADAPTER_REPORTED_FAILURE</span><span class="sxs-lookup"><span data-stu-id="48af0-114">SSO_WARN_PS_ADAPTER_REPORTED_FAILURE</span></span>|  
|<span data-ttu-id="48af0-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="48af0-115">Message Text</span></span>|<span data-ttu-id="48af0-116">L'adaptateur de synchronisation de mot de passe a signalé un échec lors de la modification du mot de passe externe.</span><span class="sxs-lookup"><span data-stu-id="48af0-116">The password sync adapter reported a failure while attempting to change the external password.</span></span> <span data-ttu-id="48af0-117">Le mot de passe externe n'a pas été mis à jour dans la base de données SSO.%r</span><span class="sxs-lookup"><span data-stu-id="48af0-117">The external password was not updated in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="48af0-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="48af0-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="48af0-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="48af0-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="48af0-120">Compte externe : %3 %r</span><span class="sxs-lookup"><span data-stu-id="48af0-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="48af0-121">Message d’erreur : %4 %r</span><span class="sxs-lookup"><span data-stu-id="48af0-121">Error Message: %4%r</span></span><br /><br /> <span data-ttu-id="48af0-122">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="48af0-122">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="48af0-123">Explication</span><span class="sxs-lookup"><span data-stu-id="48af0-123">Explanation</span></span>  
 <span data-ttu-id="48af0-124">Lorsque l'authentification unique envoie une modification de mot de passe à un adaptateur de synchronisation de mot de passe, le mot de passe externe doit être modifié avant que l'authentification unique de l'entreprise le fasse dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="48af0-124">When ENTSSO sends a password change to a password sync adapter, the external password must be successfully changed before ENTSSO makes it in the SSO database.</span></span> <span data-ttu-id="48af0-125">Ce n'est pas ce qui s'est passé dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="48af0-125">In this case, that did not occur.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="48af0-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="48af0-126">User Action</span></span>  
 <span data-ttu-id="48af0-127">Notez les informations dans le message d'avertissement et consultez votre administrateur système.</span><span class="sxs-lookup"><span data-stu-id="48af0-127">Note the information in the warning message and consult your system administrator.</span></span>