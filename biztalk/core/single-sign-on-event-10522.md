---
title: "Single Sign-On : Événement 10522 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd634a57-01dc-44bd-bcf9-668689db7b77
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b56999d7898af01d0009a7722d78aed0dbf5dbf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10522"></a><span data-ttu-id="c795e-102">Single Sign-On : Événement 10522</span><span class="sxs-lookup"><span data-stu-id="c795e-102">Single Sign-On: Event 10522</span></span>
## <a name="details"></a><span data-ttu-id="c795e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c795e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c795e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c795e-104">Product Name</span></span>|<span data-ttu-id="c795e-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c795e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c795e-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c795e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c795e-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c795e-107">Event ID</span></span>|<span data-ttu-id="c795e-108">10522</span><span class="sxs-lookup"><span data-stu-id="c795e-108">10522</span></span>|  
|<span data-ttu-id="c795e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c795e-109">Event Source</span></span>|<span data-ttu-id="c795e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c795e-110">ENTSSO</span></span>|  
|<span data-ttu-id="c795e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c795e-111">Component</span></span>|<span data-ttu-id="c795e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c795e-112">N\A</span></span>|  
|<span data-ttu-id="c795e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c795e-113">Symbolic Name</span></span>|<span data-ttu-id="c795e-114">SSO_ERROR_REENCRYPT</span><span class="sxs-lookup"><span data-stu-id="c795e-114">SSO_ERROR_REENCRYPT</span></span>|  
|<span data-ttu-id="c795e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c795e-115">Message Text</span></span>|<span data-ttu-id="c795e-116">Échec du rechiffrement de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="c795e-116">SSO database re-encryption failed.</span></span> <span data-ttu-id="c795e-117">Nouvelle tentative dans %1 minutes.%r</span><span class="sxs-lookup"><span data-stu-id="c795e-117">Will try again in %1 minutes.%r</span></span><br /><br /> <span data-ttu-id="c795e-118">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="c795e-118">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c795e-119">Explication</span><span class="sxs-lookup"><span data-stu-id="c795e-119">Explanation</span></span>  
 <span data-ttu-id="c795e-120">Cet événement de type erreur indique que le rechiffrement de la base de données SSO a échoué.</span><span class="sxs-lookup"><span data-stu-id="c795e-120">This Error event indicates that the SSO database re-encryption failed.</span></span> <span data-ttu-id="c795e-121">Lorsque le service SSO démarre sur le serveur de secret principal, il commence par vérifier s'il existe des informations dans la base de données SSO qui soient encore chiffrées avec le secret principal précédent.</span><span class="sxs-lookup"><span data-stu-id="c795e-121">When the SSO service starts on the master secret server, the first thing it does is to check if there is anything in the SSO database still encrypted with the previous master secret.</span></span> <span data-ttu-id="c795e-122">S'il en trouve, il déchiffre ces informations (via le secret précédent), puis il les chiffre à nouveau avec le secret principal actuel.</span><span class="sxs-lookup"><span data-stu-id="c795e-122">If it finds anything, it decrypts that information (using the previous secret) and re-encrypts it using the current master secret.</span></span> <span data-ttu-id="c795e-123">Si ce processus échoue pour une raison quelconque, ce message d'événement est émis.</span><span class="sxs-lookup"><span data-stu-id="c795e-123">If for any reason this process fails, then this event message is issued.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c795e-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c795e-124">User Action</span></span>  
 <span data-ttu-id="c795e-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c795e-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="c795e-126">Vérifiez le code d'erreur pour déterminer quelle peut être la cause sous-jacente de cette erreur.</span><span class="sxs-lookup"><span data-stu-id="c795e-126">Check the error code to determine what the underlying cause of the error might be.</span></span> <span data-ttu-id="c795e-127">Il peut s'agir d'un problème lié au réseau ou à la base de données.</span><span class="sxs-lookup"><span data-stu-id="c795e-127">This could be a network or database issue.</span></span> <span data-ttu-id="c795e-128">Si cette erreur se produit par intermittence, aucune action n'est requise, car une nouvelle tentative de rechiffrement sera effectuée rapidement.</span><span class="sxs-lookup"><span data-stu-id="c795e-128">If it is intermittent, then no action is required because re-encryption will be attempted again after a short delay.</span></span> <span data-ttu-id="c795e-129">Sinon, arrêtez le service SSO et tentez de résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="c795e-129">If the issue is not intermittent, stop the SSO service and attempt to resolve the issue.</span></span> <span data-ttu-id="c795e-130">Une fois le problème résolu, redémarrez le service SSO. Le rechiffrement sera alors effectué automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c795e-130">Once the issue is resolved then restart the SSO service, Restarting the SSO service will automatically perform the re-encryption.</span></span>  
  
 <span data-ttu-id="c795e-131">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="c795e-131">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c795e-132">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="c795e-132">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="c795e-133">Serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="c795e-133">Master Secret Server</span></span>](../core/master-secret-server.md)