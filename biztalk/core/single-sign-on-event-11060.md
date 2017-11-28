---
title: "Single Sign-On : Événement 11060 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1423b7385e6c0b8f78fb815ec48b749556cd291f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11060"></a><span data-ttu-id="6de8d-102">Single Sign-On : Événement 11060</span><span class="sxs-lookup"><span data-stu-id="6de8d-102">Single Sign-On: Event 11060</span></span>
## <a name="details"></a><span data-ttu-id="6de8d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6de8d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6de8d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6de8d-104">Product Name</span></span>|<span data-ttu-id="6de8d-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="6de8d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6de8d-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6de8d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6de8d-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6de8d-107">Event ID</span></span>|<span data-ttu-id="6de8d-108">11060</span><span class="sxs-lookup"><span data-stu-id="6de8d-108">11060</span></span>|  
|<span data-ttu-id="6de8d-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6de8d-109">Event Source</span></span>|<span data-ttu-id="6de8d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6de8d-110">ENTSSO</span></span>|  
|<span data-ttu-id="6de8d-111">Composant</span><span class="sxs-lookup"><span data-stu-id="6de8d-111">Component</span></span>|<span data-ttu-id="6de8d-112">Néant</span><span class="sxs-lookup"><span data-stu-id="6de8d-112">N/A</span></span>|  
|<span data-ttu-id="6de8d-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6de8d-113">Symbolic Name</span></span>|<span data-ttu-id="6de8d-114">SSO_WARN_PS_MIIS_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="6de8d-114">SSO_WARN_PS_MIIS_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="6de8d-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6de8d-115">Message Text</span></span>|<span data-ttu-id="6de8d-116">Les modifications de mot de passe Windows issus de MIIS seront uniquement acceptés à partir du compte de service SSO.%r</span><span class="sxs-lookup"><span data-stu-id="6de8d-116">Windows password changes from MIIS will only be accepted from the SSO service account.%r</span></span><br /><br /> <span data-ttu-id="6de8d-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="6de8d-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="6de8d-118">L’utilisateur client : %2 %r</span><span class="sxs-lookup"><span data-stu-id="6de8d-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="6de8d-119">Compte du Service SSO : %3 %r</span><span class="sxs-lookup"><span data-stu-id="6de8d-119">SSO Service Account: %3%r</span></span><br /><br /> <span data-ttu-id="6de8d-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="6de8d-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6de8d-121">Explication</span><span class="sxs-lookup"><span data-stu-id="6de8d-121">Explanation</span></span>  
 <span data-ttu-id="6de8d-122">Une modification de mot de passe a été reçue par le serveur ENTSSO depuis le serveur MIIS (Microsoft Identity Integration Server).</span><span class="sxs-lookup"><span data-stu-id="6de8d-122">A password change has been received by the ENTSSO server from Microsoft Identity Integration Server (MIIS).</span></span> <span data-ttu-id="6de8d-123">Toutefois, le serveur ENTSSO acceptera uniquement les modifications de mot de passe depuis le serveur MIIS si l'utilisateur client (l'appelant) possède le même compte que le compte de service SSO.</span><span class="sxs-lookup"><span data-stu-id="6de8d-123">However, the ENTSSO server will only accept password changes from MIIS if the Client User (the caller) is the same account as the SSO service account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6de8d-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6de8d-124">User Action</span></span>  
 <span data-ttu-id="6de8d-125">Vérifiez la configuration de l'appelant pour la synchronisation de mot de passe dans MIIS.</span><span class="sxs-lookup"><span data-stu-id="6de8d-125">Check the configuration of the caller for password sync in MIIS.</span></span> <span data-ttu-id="6de8d-126">Pour plus d’informations, consultez [comment configurer l’authentification pour la synchronisation de mot de passe MIIS](../core/how-to-configure-entsso-for-miis-password-sync.md).</span><span class="sxs-lookup"><span data-stu-id="6de8d-126">For more information, see [How to Configure ENTSSO for MIIS Password Sync](../core/how-to-configure-entsso-for-miis-password-sync.md).</span></span>