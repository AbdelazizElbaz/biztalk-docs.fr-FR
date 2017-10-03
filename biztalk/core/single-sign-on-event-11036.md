---
title: "Single Sign-On : Événement 11036 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63b11005248471c222f63c88439a0e60571b341e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11036"></a><span data-ttu-id="28eeb-102">Single Sign-On : Événement 11036</span><span class="sxs-lookup"><span data-stu-id="28eeb-102">Single Sign-On: Event 11036</span></span>
## <a name="details"></a><span data-ttu-id="28eeb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="28eeb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28eeb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="28eeb-104">Product Name</span></span>|<span data-ttu-id="28eeb-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="28eeb-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="28eeb-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="28eeb-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="28eeb-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="28eeb-107">Event ID</span></span>|<span data-ttu-id="28eeb-108">11036</span><span class="sxs-lookup"><span data-stu-id="28eeb-108">11036</span></span>|  
|<span data-ttu-id="28eeb-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="28eeb-109">Event Source</span></span>|<span data-ttu-id="28eeb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="28eeb-110">ENTSSO</span></span>|  
|<span data-ttu-id="28eeb-111">Composant</span><span class="sxs-lookup"><span data-stu-id="28eeb-111">Component</span></span>|<span data-ttu-id="28eeb-112">Néant</span><span class="sxs-lookup"><span data-stu-id="28eeb-112">N/A</span></span>|  
|<span data-ttu-id="28eeb-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="28eeb-113">Symbolic Name</span></span>|<span data-ttu-id="28eeb-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span><span class="sxs-lookup"><span data-stu-id="28eeb-114">SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC</span></span>|  
|<span data-ttu-id="28eeb-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="28eeb-115">Message Text</span></span>|<span data-ttu-id="28eeb-116">Changement du mot de passe Windows.</span><span class="sxs-lookup"><span data-stu-id="28eeb-116">Windows password change.</span></span> <span data-ttu-id="28eeb-117">Le mappage détecté pour ce compte Windows a été ignoré car l'adaptateur configuré pour cette application ne prend pas en charge la synchronisation des mots de passe vers les systèmes externes.%r</span><span class="sxs-lookup"><span data-stu-id="28eeb-117">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.%r</span></span><br /><br /> <span data-ttu-id="28eeb-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="28eeb-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="28eeb-119">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="28eeb-119">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="28eeb-120">Application : %3 %r</span><span class="sxs-lookup"><span data-stu-id="28eeb-120">Application: %3%r</span></span><br /><br /> <span data-ttu-id="28eeb-121">Carte : %4 %r</span><span class="sxs-lookup"><span data-stu-id="28eeb-121">Adapter: %4%r</span></span><br /><br /> <span data-ttu-id="28eeb-122">Utilisateur client : %5</span><span class="sxs-lookup"><span data-stu-id="28eeb-122">Client User: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="28eeb-123">Explication</span><span class="sxs-lookup"><span data-stu-id="28eeb-123">Explanation</span></span>  
 <span data-ttu-id="28eeb-124">Le mappage détecté pour ce compte Windows a été ignoré car l'adaptateur configuré pour cette application ne prend pas en charge la synchronisation des mots de passe vers les systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="28eeb-124">A mapping for this Windows account has been detected but ignored because the adapter configured for this application does not support password sync to external systems.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="28eeb-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="28eeb-125">User Action</span></span>  
 <span data-ttu-id="28eeb-126">Vérifiez la configuration de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="28eeb-126">Check your adapter configuration.</span></span>  
  
 <span data-ttu-id="28eeb-127">Pour plus d’informations sur la synchronisation de mot de passe, consultez [synchronisation de mot de passe](../core/password-synchronization2.md).</span><span class="sxs-lookup"><span data-stu-id="28eeb-127">For information on Password Sync, see [Password Synchronization](../core/password-synchronization2.md).</span></span>