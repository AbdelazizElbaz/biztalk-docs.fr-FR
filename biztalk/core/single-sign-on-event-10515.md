---
title: "Single Sign-On : Événement 10515 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41edc008-b6d3-401d-97af-80b36ab0ba55
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e2b884ae52af96ceaae83f8b092ed15b6b12e3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10515"></a><span data-ttu-id="35ccc-102">Single Sign-On : Événement 10515</span><span class="sxs-lookup"><span data-stu-id="35ccc-102">Single Sign-On: Event 10515</span></span>
## <a name="details"></a><span data-ttu-id="35ccc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="35ccc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35ccc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="35ccc-104">Product Name</span></span>|<span data-ttu-id="35ccc-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="35ccc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="35ccc-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="35ccc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="35ccc-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="35ccc-107">Event ID</span></span>|<span data-ttu-id="35ccc-108">10515</span><span class="sxs-lookup"><span data-stu-id="35ccc-108">10515</span></span>|  
|<span data-ttu-id="35ccc-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="35ccc-109">Event Source</span></span>|<span data-ttu-id="35ccc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="35ccc-110">ENTSSO</span></span>|  
|<span data-ttu-id="35ccc-111">Composant</span><span class="sxs-lookup"><span data-stu-id="35ccc-111">Component</span></span>|<span data-ttu-id="35ccc-112">N\A</span><span class="sxs-lookup"><span data-stu-id="35ccc-112">N\A</span></span>|  
|<span data-ttu-id="35ccc-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="35ccc-113">Symbolic Name</span></span>|<span data-ttu-id="35ccc-114">SSO_ERROR_POLL_DATABASE</span><span class="sxs-lookup"><span data-stu-id="35ccc-114">SSO_ERROR_POLL_DATABASE</span></span>|  
|<span data-ttu-id="35ccc-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="35ccc-115">Message Text</span></span>|<span data-ttu-id="35ccc-116">Contact perdu avec la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="35ccc-116">Lost contact with the SSO database.</span></span> <span data-ttu-id="35ccc-117">Vérifiez que la base de données SSO est disponible.</span><span class="sxs-lookup"><span data-stu-id="35ccc-117">Check that the SSO database is available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35ccc-118">Explication</span><span class="sxs-lookup"><span data-stu-id="35ccc-118">Explanation</span></span>  
 <span data-ttu-id="35ccc-119">Cet événement d'erreur indique que le service d'authentification unique a perdu le contact avec la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="35ccc-119">This Error event indicates that the SSO Service has lost contact with the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35ccc-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="35ccc-120">User Action</span></span>  
 <span data-ttu-id="35ccc-121">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="35ccc-121">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="35ccc-122">Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="35ccc-122">Verify that the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="35ccc-123">Vérifiez la connectivité réseau à SQL Server si vous utilisez un serveur distant.</span><span class="sxs-lookup"><span data-stu-id="35ccc-123">Verify network connectivity to SQL Server if on a remote server.</span></span>  
  
 <span data-ttu-id="35ccc-124">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="35ccc-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="35ccc-125">Mise en œuvre Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="35ccc-125">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="35ccc-126">Comment afficher les informations de base de données SSO</span><span class="sxs-lookup"><span data-stu-id="35ccc-126">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="35ccc-127">Configuration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="35ccc-127">Configuring SSO</span></span>](../core/configuring-sso.md)  
  
 <span data-ttu-id="35ccc-128">Voir aussi documentation en ligne de SQL Server</span><span class="sxs-lookup"><span data-stu-id="35ccc-128">See also SQL Server Books Online</span></span>