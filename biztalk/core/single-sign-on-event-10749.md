---
title: "Single Sign-On : Événement 10749 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 864c887cb6c115a2f766f9c06cbaa292fdbeace2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10749"></a><span data-ttu-id="9e80e-102">Single Sign-On : Événement 10749</span><span class="sxs-lookup"><span data-stu-id="9e80e-102">Single Sign-On: Event 10749</span></span>
## <a name="details"></a><span data-ttu-id="9e80e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9e80e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e80e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9e80e-104">Product Name</span></span>|<span data-ttu-id="9e80e-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9e80e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9e80e-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9e80e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9e80e-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9e80e-107">Event ID</span></span>|<span data-ttu-id="9e80e-108">10749</span><span class="sxs-lookup"><span data-stu-id="9e80e-108">10749</span></span>|  
|<span data-ttu-id="9e80e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9e80e-109">Event Source</span></span>|<span data-ttu-id="9e80e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9e80e-110">ENTSSO</span></span>|  
|<span data-ttu-id="9e80e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="9e80e-111">Component</span></span>|<span data-ttu-id="9e80e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9e80e-112">N\A</span></span>|  
|<span data-ttu-id="9e80e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9e80e-113">Symbolic Name</span></span>|<span data-ttu-id="9e80e-114">SSO_WARN_PS_CLIENT_PING</span><span class="sxs-lookup"><span data-stu-id="9e80e-114">SSO_WARN_PS_CLIENT_PING</span></span>|  
|<span data-ttu-id="9e80e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9e80e-115">Message Text</span></span>|<span data-ttu-id="9e80e-116">Impossible de contacter le serveur d'authentification unique de destination.</span><span class="sxs-lookup"><span data-stu-id="9e80e-116">Could not contact the destination SSO server.</span></span><br /><br /> <span data-ttu-id="9e80e-117">Vérifiez que le service d'authentification unique est en cours d'exécution sur ce serveur et qu'il peut être contacté.%r</span><span class="sxs-lookup"><span data-stu-id="9e80e-117">Check that the SSO service is running on that server and that it can be contacted.%r</span></span><br /><br /> <span data-ttu-id="9e80e-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="9e80e-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="9e80e-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="9e80e-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="9e80e-120">Nom du serveur SSO : %3 %r</span><span class="sxs-lookup"><span data-stu-id="9e80e-120">SSO Server Name: %3%r</span></span><br /><br /> <span data-ttu-id="9e80e-121">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="9e80e-121">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e80e-122">Explication</span><span class="sxs-lookup"><span data-stu-id="9e80e-122">Explanation</span></span>  
 <span data-ttu-id="9e80e-123">Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu contacter le serveur d'authentification unique de destination spécifié.</span><span class="sxs-lookup"><span data-stu-id="9e80e-123">This Warning event indicates that SSO Password Sync could not contact the specified destination SSO server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e80e-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9e80e-124">User Action</span></span>  
 <span data-ttu-id="9e80e-125">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9e80e-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="9e80e-126">Utilisez le composant logiciel enfichable Serveurs ENTSSO pour vérifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="9e80e-126">Use the ENTSSO Servers Snap-In to check the server.</span></span>  
  
-   <span data-ttu-id="9e80e-127">Démarrez le service d'authentification unique de l'entreprise s'il n'est pas en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="9e80e-127">Start the Enterprise Single Sign-On Service if it is not running.</span></span>  
  
-   <span data-ttu-id="9e80e-128">Vérifiez la connexion réseau au serveur d'authentification unique de destination.</span><span class="sxs-lookup"><span data-stu-id="9e80e-128">Check the network connection to the destination SSO server.</span></span>  
  
-   <span data-ttu-id="9e80e-129">Vérifiez le pare-feu sur le serveur d'authentification unique de destination.</span><span class="sxs-lookup"><span data-stu-id="9e80e-129">Check firewall on the destination SSO Server.</span></span>  
  
 <span data-ttu-id="9e80e-130">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9e80e-130">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="9e80e-131">Comment utiliser le composant logiciel enfichable de serveurs</span><span class="sxs-lookup"><span data-stu-id="9e80e-131">How to Use the Servers Snap-in</span></span>](../core/how-to-use-the-servers-snap-in.md)