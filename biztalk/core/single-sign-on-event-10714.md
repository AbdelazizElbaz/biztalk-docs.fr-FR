---
title: "Single Sign-On : Événement 10714 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59d8509f-cc3e-40fa-ba3d-3dcb0e73c67a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba63ab9197dcf9629f03f3d6c96f064345aaa46e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10714"></a><span data-ttu-id="951fb-102">Single Sign-On : Événement 10714</span><span class="sxs-lookup"><span data-stu-id="951fb-102">Single Sign-On: Event 10714</span></span>
## <a name="details"></a><span data-ttu-id="951fb-103">Détails</span><span class="sxs-lookup"><span data-stu-id="951fb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="951fb-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="951fb-104">Product Name</span></span>|<span data-ttu-id="951fb-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="951fb-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="951fb-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="951fb-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="951fb-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="951fb-107">Event ID</span></span>|<span data-ttu-id="951fb-108">10714</span><span class="sxs-lookup"><span data-stu-id="951fb-108">10714</span></span>|  
|<span data-ttu-id="951fb-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="951fb-109">Event Source</span></span>|<span data-ttu-id="951fb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="951fb-110">ENTSSO</span></span>|  
|<span data-ttu-id="951fb-111">Composant</span><span class="sxs-lookup"><span data-stu-id="951fb-111">Component</span></span>|<span data-ttu-id="951fb-112">N\A</span><span class="sxs-lookup"><span data-stu-id="951fb-112">N\A</span></span>|  
|<span data-ttu-id="951fb-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="951fb-113">Symbolic Name</span></span>|<span data-ttu-id="951fb-114">SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="951fb-114">SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED</span></span>|  
|<span data-ttu-id="951fb-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="951fb-115">Message Text</span></span>|<span data-ttu-id="951fb-116">Nouvelles tentatives expirées, notification supprimée.%r</span><span class="sxs-lookup"><span data-stu-id="951fb-116">Retries expired, discarding notification.%r</span></span><br /><br /> <span data-ttu-id="951fb-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="951fb-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="951fb-118">Adaptateur : %2</span><span class="sxs-lookup"><span data-stu-id="951fb-118">Adapter: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="951fb-119">Explication</span><span class="sxs-lookup"><span data-stu-id="951fb-119">Explanation</span></span>  
 <span data-ttu-id="951fb-120">Cet événement d'avertissement indique que les tentatives de notification de la synchronisation de mot de passe ont expiré et que la notification a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="951fb-120">This Warning event indicates that the Password Sync notification retries have expired, and the notification has been discarded.</span></span>  
  
 <span data-ttu-id="951fb-121">Lorsqu'une modification de mot de passe (entre Windows et un système externe) est remise à un adaptateur de synchronisation de mot de passe, celui-ci confirme le traitement de la modification de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="951fb-121">When a password change (from Windows to an external system) is delivered to a password sync adapter, the password sync adapter acknowledges that it has successfully processed the password change.</span></span> <span data-ttu-id="951fb-122">Si la modification de mot de passe n'est pas exécutée au cours d'un délai spécifié, ou si un autre problème survient lors de la modification, elle est à nouveau remise à l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="951fb-122">If the password change does not occur within a specified amount of time, or if another problem occurs during the change, the password change is delivered to the password sync adapter again.</span></span> <span data-ttu-id="951fb-123">Cette opération est effectuée un nombre de fois limité (nombre maximal de tentatives) avant que la notification de modification de mot de passe ne soit supprimée.</span><span class="sxs-lookup"><span data-stu-id="951fb-123">This is done a limited number of times (max retries) and then the password change notification is discarded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="951fb-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="951fb-124">User Action</span></span>  
 <span data-ttu-id="951fb-125">Pour résoudre cet avertissement, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="951fb-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="951fb-126">Consultez les événements associés dans les journaux des événements système et de l'application.</span><span class="sxs-lookup"><span data-stu-id="951fb-126">Check System and Application event logs for associated events.</span></span>  
  
 <span data-ttu-id="951fb-127">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="951fb-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="951fb-128">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="951fb-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="951fb-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="951fb-129">Password Synchronization</span></span>](../core/password-synchronization2.md)