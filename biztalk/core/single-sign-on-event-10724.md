---
title: "Single Sign-On : Événement 10724 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 022a6f73-a24b-4058-91a5-b831f6875409
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd9e65b18b66f119e3cc2acf7f078f17466e46b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10724"></a><span data-ttu-id="e89ca-102">Single Sign-On : Événement 10724</span><span class="sxs-lookup"><span data-stu-id="e89ca-102">Single Sign-On: Event 10724</span></span>
## <a name="details"></a><span data-ttu-id="e89ca-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e89ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e89ca-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e89ca-104">Product Name</span></span>|<span data-ttu-id="e89ca-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="e89ca-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e89ca-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e89ca-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e89ca-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e89ca-107">Event ID</span></span>|<span data-ttu-id="e89ca-108">10724</span><span class="sxs-lookup"><span data-stu-id="e89ca-108">10724</span></span>|  
|<span data-ttu-id="e89ca-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e89ca-109">Event Source</span></span>|<span data-ttu-id="e89ca-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e89ca-110">ENTSSO</span></span>|  
|<span data-ttu-id="e89ca-111">Composant</span><span class="sxs-lookup"><span data-stu-id="e89ca-111">Component</span></span>|<span data-ttu-id="e89ca-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e89ca-112">N\A</span></span>|  
|<span data-ttu-id="e89ca-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e89ca-113">Symbolic Name</span></span>|<span data-ttu-id="e89ca-114">SSO_ERROR_REPLAY_SECURITY_2</span><span class="sxs-lookup"><span data-stu-id="e89ca-114">SSO_ERROR_REPLAY_SECURITY_2</span></span>|  
|<span data-ttu-id="e89ca-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e89ca-115">Message Text</span></span>|<span data-ttu-id="e89ca-116">La valeur d'origine de la sécurité du fichier de relecture ou de progression a été modifiée.%r</span><span class="sxs-lookup"><span data-stu-id="e89ca-116">The security on the replay or progress file has been changed from its original value.%r</span></span><br /><br /> <span data-ttu-id="e89ca-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="e89ca-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="e89ca-118">Sécurité du fichier : %2 %r</span><span class="sxs-lookup"><span data-stu-id="e89ca-118">Current File Security: %2%r</span></span><br /><br /> <span data-ttu-id="e89ca-119">Sécurité du fichier d’origine : %3</span><span class="sxs-lookup"><span data-stu-id="e89ca-119">Original File Security: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e89ca-120">Explication</span><span class="sxs-lookup"><span data-stu-id="e89ca-120">Explanation</span></span>  
 <span data-ttu-id="e89ca-121">Cet événement d'erreur indique que la sécurité des fichiers de relecture ou de progression a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="e89ca-121">This Error event indicates that the security on the replay or progress files has been changed.</span></span>  
  
 <span data-ttu-id="e89ca-122">Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="e89ca-122">Replay files are stored in the replay files directory.</span></span> <span data-ttu-id="e89ca-123">Par défaut, le compte du service d'authentification unique est utilisé pour créer les fichiers de relecture et le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="e89ca-123">By default, the SSO service account is used to create both the replay files and the replay files directory.</span></span> <span data-ttu-id="e89ca-124">L'authentification unique vérifie qu'aucune modification n'a été apportée à la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture depuis leur création.</span><span class="sxs-lookup"><span data-stu-id="e89ca-124">SSO verifies that no changes have been made to the security configuration of the replay files and replay files directory since they were created.</span></span> <span data-ttu-id="e89ca-125">Si le répertoire des fichiers de relecture a été créé avec un autre compte, cette erreur peut être renvoyée lorsque la synchronisation des mots de passe tente de créer un fichier de relecture dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="e89ca-125">If the replay files directory was created with a different account, this error can be returned when Password Sync attempts to create a replay file in that directory.</span></span> <span data-ttu-id="e89ca-126">Il est fortement recommandé aux utilisateurs de ne pas modifier la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="e89ca-126">It is strongly recommended that users not change any security configuration of the replay files and replay files directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e89ca-127">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e89ca-127">User Action</span></span>  
 <span data-ttu-id="e89ca-128">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e89ca-128">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="e89ca-129">Consultez les autorisations du compte utilisé pour créer le répertoire des fichiers de relecture.</span><span class="sxs-lookup"><span data-stu-id="e89ca-129">Check permission for the account used to create the replay files.</span></span> <span data-ttu-id="e89ca-130">En général, il s'agit du compte du système de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="e89ca-130">This is typically the SSO system account.</span></span>  
  
 <span data-ttu-id="e89ca-131">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e89ca-131">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="e89ca-132">Comment configurer la synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="e89ca-132">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="e89ca-133">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="e89ca-133">Password Synchronization</span></span>](../core/password-synchronization2.md)