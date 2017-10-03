---
title: "Single Sign-On : Événement 10526 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69a78b337cfdf90ea35367bd8fb20569e56717b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10526"></a><span data-ttu-id="6ecee-102">Single Sign-On : Événement 10526</span><span class="sxs-lookup"><span data-stu-id="6ecee-102">Single Sign-On: Event 10526</span></span>
## <a name="details"></a><span data-ttu-id="6ecee-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6ecee-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ecee-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6ecee-104">Product Name</span></span>|<span data-ttu-id="6ecee-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="6ecee-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6ecee-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6ecee-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6ecee-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6ecee-107">Event ID</span></span>|<span data-ttu-id="6ecee-108">10526</span><span class="sxs-lookup"><span data-stu-id="6ecee-108">10526</span></span>|  
|<span data-ttu-id="6ecee-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6ecee-109">Event Source</span></span>|<span data-ttu-id="6ecee-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6ecee-110">ENTSSO</span></span>|  
|<span data-ttu-id="6ecee-111">Composant</span><span class="sxs-lookup"><span data-stu-id="6ecee-111">Component</span></span>|<span data-ttu-id="6ecee-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6ecee-112">N\A</span></span>|  
|<span data-ttu-id="6ecee-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6ecee-113">Symbolic Name</span></span>|<span data-ttu-id="6ecee-114">SSO_ERROR_GENERATE_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="6ecee-114">SSO_ERROR_GENERATE_SECRET_FAILED</span></span>|  
|<span data-ttu-id="6ecee-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6ecee-115">Message Text</span></span>|<span data-ttu-id="6ecee-116">Échec lors de la génération d'un nouveau secret principal.%r</span><span class="sxs-lookup"><span data-stu-id="6ecee-116">Failed to generate a new master secret.%r</span></span><br /><br /> <span data-ttu-id="6ecee-117">L’utilisateur client : %1 %r</span><span class="sxs-lookup"><span data-stu-id="6ecee-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="6ecee-118">Ordinateur client :%2%r</span><span class="sxs-lookup"><span data-stu-id="6ecee-118">Client Computer:%2%r</span></span><br /><br /> <span data-ttu-id="6ecee-119">ID de suivi : %3 %r</span><span class="sxs-lookup"><span data-stu-id="6ecee-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="6ecee-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="6ecee-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ecee-121">Explication</span><span class="sxs-lookup"><span data-stu-id="6ecee-121">Explanation</span></span>  
 <span data-ttu-id="6ecee-122">Cet événement d'erreur indique que la tentative de génération d'un nouveau secret principal par un utilisateur a échoué.</span><span class="sxs-lookup"><span data-stu-id="6ecee-122">This Error event indicates that a user attempt to generate a new master secret has failed.</span></span> <span data-ttu-id="6ecee-123">Ceci peut être du à des problèmes d'autorisation (seuls les administrateurs de l'authentification unique peuvent générer le secret principal) ou un problème est survenu lors de l'écriture du secret principal dans le fichier de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6ecee-123">This might be due to permissions issues (you must be an SSO Administrator to generate the master secret) or possibly there were problems writing the master secret to the backup file.</span></span> <span data-ttu-id="6ecee-124">Dans ce cas, le journal des événements de l'application doit contenir des messages associés.</span><span class="sxs-lookup"><span data-stu-id="6ecee-124">In these cases there should be related messages in the Application event log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ecee-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6ecee-125">User Action</span></span>  
 <span data-ttu-id="6ecee-126">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ecee-126">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="6ecee-127">Recherchez les événements ou erreurs associés dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="6ecee-127">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="6ecee-128">Vérifiez que vous disposez des autorisations d'administrateur de l'authentification unique appropriées.</span><span class="sxs-lookup"><span data-stu-id="6ecee-128">Check that you have the appropriate SSO Administrator permissions.</span></span>  
  
 <span data-ttu-id="6ecee-129">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="6ecee-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="6ecee-130">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="6ecee-130">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="6ecee-131">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="6ecee-131">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)