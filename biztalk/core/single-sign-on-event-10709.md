---
title: "Single Sign-On : Événement 10709 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e86890-88dd-49f0-bb2c-1234507e8be5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a28807d9307ba1217e5b48e24facfe36711536f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10709"></a><span data-ttu-id="d9504-102">Single Sign-On : Événement 10709</span><span class="sxs-lookup"><span data-stu-id="d9504-102">Single Sign-On: Event 10709</span></span>
## <a name="details"></a><span data-ttu-id="d9504-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d9504-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9504-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d9504-104">Product Name</span></span>|<span data-ttu-id="d9504-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="d9504-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="d9504-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d9504-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="d9504-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d9504-107">Event ID</span></span>|<span data-ttu-id="d9504-108">10709</span><span class="sxs-lookup"><span data-stu-id="d9504-108">10709</span></span>|  
|<span data-ttu-id="d9504-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d9504-109">Event Source</span></span>|<span data-ttu-id="d9504-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d9504-110">ENTSSO</span></span>|  
|<span data-ttu-id="d9504-111">Composant</span><span class="sxs-lookup"><span data-stu-id="d9504-111">Component</span></span>|<span data-ttu-id="d9504-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d9504-112">N\A</span></span>|  
|<span data-ttu-id="d9504-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d9504-113">Symbolic Name</span></span>|<span data-ttu-id="d9504-114">SSO_WARN_PS_PCNS_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="d9504-114">SSO_WARN_PS_PCNS_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="d9504-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d9504-115">Message Text</span></span>|<span data-ttu-id="d9504-116">Les modifications de mot de passe Windows reçues de PCNS sont uniquement acceptées à partir des contrôleurs de domaine dans le domaine d'accès.%r</span><span class="sxs-lookup"><span data-stu-id="d9504-116">Windows password changes from PCNS will only be accepted from Domain Controllers in the access domain.%r</span></span><br /><br /> <span data-ttu-id="d9504-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="d9504-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="d9504-118">L’utilisateur client : %2 %r</span><span class="sxs-lookup"><span data-stu-id="d9504-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="d9504-119">Domaine d’accès : %3 %r</span><span class="sxs-lookup"><span data-stu-id="d9504-119">Access Domain: %3%r</span></span><br /><br /> <span data-ttu-id="d9504-120">Sid d’accès : %4 %r</span><span class="sxs-lookup"><span data-stu-id="d9504-120">Access Sid: %4%r</span></span><br /><br /> <span data-ttu-id="d9504-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="d9504-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9504-122">Explication</span><span class="sxs-lookup"><span data-stu-id="d9504-122">Explanation</span></span>  
 <span data-ttu-id="d9504-123">Cet événement d'avertissement indique qu'une modification de mot de passe Windows a été reçue du service de notification de modification de mot de passe (PCNS, Password Change Notification Service) sur un serveur en dehors du domaine du serveur d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="d9504-123">This Warning event indicates that a Windows password change was received from Password Change Notification Services (PCNS) on a server outside the ENTSSO server's domain.</span></span> <span data-ttu-id="d9504-124">Les modifications de mot de passe Windows sont uniquement acceptées à partir des contrôleurs de domaine dans le même domaine que le serveur d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="d9504-124">Windows password changes will only be accepted from domain controllers in the same domain as the ENTSSO server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9504-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d9504-125">User Action</span></span>  
 <span data-ttu-id="d9504-126">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d9504-126">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="d9504-127">Configurez un serveur d'authentification unique de l'entreprise dans le même domaine que PCNS.</span><span class="sxs-lookup"><span data-stu-id="d9504-127">Configure an ENTSSO server in the same domain as PCNS.</span></span>  
  
 <span data-ttu-id="d9504-128">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d9504-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="d9504-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="d9504-129">Password Synchronization</span></span>](../core/password-synchronization2.md)