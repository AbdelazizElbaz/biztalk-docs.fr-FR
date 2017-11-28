---
title: "Single Sign-On : Événement 10532 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7a9d477ec54a3c959f2afdf4c687c65b88523ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10532"></a><span data-ttu-id="94daf-102">Single Sign-On : Événement 10532</span><span class="sxs-lookup"><span data-stu-id="94daf-102">Single Sign-On: Event 10532</span></span>
## <a name="details"></a><span data-ttu-id="94daf-103">Détails</span><span class="sxs-lookup"><span data-stu-id="94daf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94daf-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="94daf-104">Product Name</span></span>|<span data-ttu-id="94daf-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="94daf-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="94daf-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="94daf-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="94daf-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="94daf-107">Event ID</span></span>|<span data-ttu-id="94daf-108">10532</span><span class="sxs-lookup"><span data-stu-id="94daf-108">10532</span></span>|  
|<span data-ttu-id="94daf-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="94daf-109">Event Source</span></span>|<span data-ttu-id="94daf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="94daf-110">ENTSSO</span></span>|  
|<span data-ttu-id="94daf-111">Composant</span><span class="sxs-lookup"><span data-stu-id="94daf-111">Component</span></span>|<span data-ttu-id="94daf-112">CO</span><span class="sxs-lookup"><span data-stu-id="94daf-112">CO</span></span>|  
|<span data-ttu-id="94daf-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="94daf-113">Symbolic Name</span></span>|<span data-ttu-id="94daf-114">SSO_WARN_LOST_SECRET_SERVER</span><span class="sxs-lookup"><span data-stu-id="94daf-114">SSO_WARN_LOST_SECRET_SERVER</span></span>|  
|<span data-ttu-id="94daf-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="94daf-115">Message Text</span></span>|<span data-ttu-id="94daf-116">Impossible d'extraire les secrets principaux.</span><span class="sxs-lookup"><span data-stu-id="94daf-116">Failed to retrieve master secrets.</span></span> <span data-ttu-id="94daf-117">Vérifiez que le nom du serveur de secret principal est correct et disponible.%r</span><span class="sxs-lookup"><span data-stu-id="94daf-117">Verify that the master secret server name is correct and that it is available.%r</span></span><br /><br /> <span data-ttu-id="94daf-118">Nom du serveur de secret principal : %1 %r</span><span class="sxs-lookup"><span data-stu-id="94daf-118">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="94daf-119">Code d’erreur : %2</span><span class="sxs-lookup"><span data-stu-id="94daf-119">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94daf-120">Explication</span><span class="sxs-lookup"><span data-stu-id="94daf-120">Explanation</span></span>  
 <span data-ttu-id="94daf-121">Cet événement d'avertissement indique qu'une demande d'obtention du secret principal a échoué.</span><span class="sxs-lookup"><span data-stu-id="94daf-121">This Warning event indicates that a request to get the master secret has failed.</span></span> <span data-ttu-id="94daf-122">Ceci peut être dû au fait que l'authentification unique de l'entreprise ne soit pas exécutée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="94daf-122">This might be because the Enterprise Single Sign-On service is not running on the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94daf-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="94daf-123">User Action</span></span>  
 <span data-ttu-id="94daf-124">Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="94daf-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="94daf-125">Recherchez les événements ou erreurs associés dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="94daf-125">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="94daf-126">Vérifiez que le nom du serveur de secret principal est correct.</span><span class="sxs-lookup"><span data-stu-id="94daf-126">Verify the master secret server name is correct.</span></span>  
  
-   <span data-ttu-id="94daf-127">Vérifiez que le serveur de secret principal est en ligne et que l'authentification unique de l'entreprise est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="94daf-127">Verify the master secret server is online and that the Enterprise Single Sign-On service is running.</span></span>  
  
 <span data-ttu-id="94daf-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="94daf-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="94daf-129">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="94daf-129">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="94daf-130">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="94daf-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)