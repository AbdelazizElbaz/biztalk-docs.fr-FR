---
title: "Single Sign-On : Événement 10750 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32b8c29159edc0cf6fa7281b5a717af509e3a63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10750"></a><span data-ttu-id="cffc6-102">Single Sign-On : Événement 10750</span><span class="sxs-lookup"><span data-stu-id="cffc6-102">Single Sign-On: Event 10750</span></span>
## <a name="details"></a><span data-ttu-id="cffc6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="cffc6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cffc6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="cffc6-104">Product Name</span></span>|<span data-ttu-id="cffc6-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cffc6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="cffc6-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="cffc6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="cffc6-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="cffc6-107">Event ID</span></span>|<span data-ttu-id="cffc6-108">10750</span><span class="sxs-lookup"><span data-stu-id="cffc6-108">10750</span></span>|  
|<span data-ttu-id="cffc6-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="cffc6-109">Event Source</span></span>|<span data-ttu-id="cffc6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cffc6-110">ENTSSO</span></span>|  
|<span data-ttu-id="cffc6-111">Composant</span><span class="sxs-lookup"><span data-stu-id="cffc6-111">Component</span></span>|<span data-ttu-id="cffc6-112">N\A</span><span class="sxs-lookup"><span data-stu-id="cffc6-112">N\A</span></span>|  
|<span data-ttu-id="cffc6-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="cffc6-113">Symbolic Name</span></span>|<span data-ttu-id="cffc6-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span><span class="sxs-lookup"><span data-stu-id="cffc6-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span></span>|  
|<span data-ttu-id="cffc6-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cffc6-115">Message Text</span></span>|<span data-ttu-id="cffc6-116">PasswordChangeNotify : Type de nom utilisateur Incorrect.</span><span class="sxs-lookup"><span data-stu-id="cffc6-116">PasswordChangeNotify: Incorrect User Name Type.</span></span> <span data-ttu-id="cffc6-117">La seule valeur acceptée est USER_NAME_TYPE_NT4.</span><span class="sxs-lookup"><span data-stu-id="cffc6-117">The only accepted value is USER_NAME_TYPE_NT4.</span></span><br /><br /> <span data-ttu-id="cffc6-118">La cible n'est pas correctement configurée dans Active Directory.%r</span><span class="sxs-lookup"><span data-stu-id="cffc6-118">The target is incorrectly configured in Active Directory.%r</span></span><br /><br /> <span data-ttu-id="cffc6-119">Type de nom d’utilisateur : %1 %r</span><span class="sxs-lookup"><span data-stu-id="cffc6-119">User Name Type: %1%r</span></span><br /><br /> <span data-ttu-id="cffc6-120">L’utilisateur client : %2 %r</span><span class="sxs-lookup"><span data-stu-id="cffc6-120">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="cffc6-121">Code d’erreur : %3</span><span class="sxs-lookup"><span data-stu-id="cffc6-121">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cffc6-122">Explication</span><span class="sxs-lookup"><span data-stu-id="cffc6-122">Explanation</span></span>  
 <span data-ttu-id="cffc6-123">Cet événement d'erreur indique que la synchronisation des mots de passe a reçu une modification de mot de passe du service de notification de modification de mot de passe (PCNS, Password Change Notification Service), mais celle-ci utilisait un format incorrect.</span><span class="sxs-lookup"><span data-stu-id="cffc6-123">This Error event indicates that Password Sync received a password change from the Password Change Notification Service (PCNS), but the password change was in the wrong format.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cffc6-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cffc6-124">User Action</span></span>  
 <span data-ttu-id="cffc6-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="cffc6-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="cffc6-126">Vérifiez la configuration de PCNS.</span><span class="sxs-lookup"><span data-stu-id="cffc6-126">Check the PCNS configuration.</span></span> <span data-ttu-id="cffc6-127">PCNS peut seulement être exécuté sur un contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="cffc6-127">PCNS can run only on a domain controller.</span></span>  
  
-   <span data-ttu-id="cffc6-128">Configurez le type de nom d'utilisateur sur USER_NAME_TYPE_NT4 dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cffc6-128">Configure User Name Type to USER_NAME_TYPE_NT4 in Active Directory.</span></span>  
  
 <span data-ttu-id="cffc6-129">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cffc6-129">For more information, see the following resources:</span></span>  
  
-   <span data-ttu-id="cffc6-130">Pour plus d'informations sur la spécification du type de nom d'utilisateur, consultez la documentation d'Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cffc6-130">Refer to Active Directory documentation for information on how to specify User Name Type.</span></span>  
  
-   [<span data-ttu-id="cffc6-131">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cffc6-131">Password Synchronization</span></span>](../core/password-synchronization2.md)