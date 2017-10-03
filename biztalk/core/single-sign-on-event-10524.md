---
title: "Single Sign-On : Événement 10524 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55e26da3-f67f-4f87-92e5-2f8765b19989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c79da37aaa54f44daaa39048fcdf58e67064f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10524"></a><span data-ttu-id="3a3ed-102">Single Sign-On : Événement 10524</span><span class="sxs-lookup"><span data-stu-id="3a3ed-102">Single Sign-On: Event 10524</span></span>
## <a name="details"></a><span data-ttu-id="3a3ed-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3a3ed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a3ed-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3a3ed-104">Product Name</span></span>|<span data-ttu-id="3a3ed-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="3a3ed-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="3a3ed-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3a3ed-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="3a3ed-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3a3ed-107">Event ID</span></span>|<span data-ttu-id="3a3ed-108">10524</span><span class="sxs-lookup"><span data-stu-id="3a3ed-108">10524</span></span>|  
|<span data-ttu-id="3a3ed-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3a3ed-109">Event Source</span></span>|<span data-ttu-id="3a3ed-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3a3ed-110">ENTSSO</span></span>|  
|<span data-ttu-id="3a3ed-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3a3ed-111">Component</span></span>|<span data-ttu-id="3a3ed-112">N\A</span><span class="sxs-lookup"><span data-stu-id="3a3ed-112">N\A</span></span>|  
|<span data-ttu-id="3a3ed-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3a3ed-113">Symbolic Name</span></span>|<span data-ttu-id="3a3ed-114">SSO_ERROR_RESTORE_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="3a3ed-114">SSO_ERROR_RESTORE_SECRET_FAILED</span></span>|  
|<span data-ttu-id="3a3ed-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3a3ed-115">Message Text</span></span>|<span data-ttu-id="3a3ed-116">Échec lors de la restauration des secrets principaux.%r</span><span class="sxs-lookup"><span data-stu-id="3a3ed-116">Failed to restore the master secrets.%r</span></span><br /><br /> <span data-ttu-id="3a3ed-117">Nom du fichier : %1 %r</span><span class="sxs-lookup"><span data-stu-id="3a3ed-117">File Name: %1%r</span></span><br /><br /> <span data-ttu-id="3a3ed-118">MSID actuel : %2 %r</span><span class="sxs-lookup"><span data-stu-id="3a3ed-118">Current MSID: %2%r</span></span><br /><br /> <span data-ttu-id="3a3ed-119">MSID précédent : %3 %r</span><span class="sxs-lookup"><span data-stu-id="3a3ed-119">Previous MSID: %3%r</span></span><br /><br /> <span data-ttu-id="3a3ed-120">L’utilisateur client : %4 %r</span><span class="sxs-lookup"><span data-stu-id="3a3ed-120">Client User: %4%r</span></span><br /><br /> <span data-ttu-id="3a3ed-121">Code d’erreur : %5</span><span class="sxs-lookup"><span data-stu-id="3a3ed-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a3ed-122">Explication</span><span class="sxs-lookup"><span data-stu-id="3a3ed-122">Explanation</span></span>  
 <span data-ttu-id="3a3ed-123">Cet événement d'erreur indique que la restauration des secrets principaux à partir d'un fichier de sauvegarde tentée par un utilisateur a échoué.</span><span class="sxs-lookup"><span data-stu-id="3a3ed-123">This Error event indicates that a user attempt to restore the master secrets from a backup file failed.</span></span> <span data-ttu-id="3a3ed-124">Ceci peut être du à des problèmes d'autorisation (vous devez être administrateur de l'authentification unique pour restaurer le secret principal) ou à l'endommagement du fichier de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="3a3ed-124">This might be due to permissions issues (you must be an SSO Administrator to restore the master secret) or possibly due to file corruption of the backup file.</span></span> <span data-ttu-id="3a3ed-125">Dans ce cas, le journal des événements de l'application doit contenir des messages associés.</span><span class="sxs-lookup"><span data-stu-id="3a3ed-125">In these cases there should be related messages in the Application event log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a3ed-126">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3a3ed-126">User Action</span></span>  
 <span data-ttu-id="3a3ed-127">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a3ed-127">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="3a3ed-128">Recherchez les événements ou erreurs associés dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="3a3ed-128">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="3a3ed-129">Vérifiez que vous disposez des autorisations d'administrateur de l'authentification unique appropriées.</span><span class="sxs-lookup"><span data-stu-id="3a3ed-129">Check that you have the appropriate SSO Administrator permissions.</span></span>  
  
 <span data-ttu-id="3a3ed-130">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="3a3ed-130">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="3a3ed-131">Comment restaurer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="3a3ed-131">How to Restore the Master Secret</span></span>](../core/how-to-restore-the-master-secret.md)  
  
-   [<span data-ttu-id="3a3ed-132">Comment sauvegarder le Secret principal</span><span class="sxs-lookup"><span data-stu-id="3a3ed-132">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="3a3ed-133">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="3a3ed-133">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)